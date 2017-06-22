## Connecting with CIC {#ConnectToCIC}
To allow your client to connect with CIC, the following steps must be completed.
* [Creating Clova access token](#CreateClovaAccessToken)
* [Creating connection](#CreateConnection)
* [Authorization](#Authorization)
* [Managing connection](#ManageConnection)

### Creating Clova access token {#CreateClovaAccessToken}
To use Clova, the user must authenticate his or her NAVER account in your client (device or app). When your client attempts to connect with CIC, it requires a Clova access token which can be obtained from the Clova authorization server by providing the authorized NAVER account credentials.  You should use the [Clova Auth API](/CIC/References/Clova_Auth_API.md) for this process.

![](/CIC/Resources/Images/CIC_Authorization.png)

<a class="ignoreOnPDF" target="_blank" href="/CIC/Resources/Images/CIC_Authorization.png">View a larger image</a>

Below are the steps for obtaining a Clova access token.

<ol>
<li><p>Add an interface in your client (client app or app paired with your client device) with which a user can authenticate his or her NAVER account (<a href="https://developers.naver.com/docs/login/overview/" target="_blank">NAVER Login SDK</a>). You must use a client app or a paired app to complete this step because user's speech input alone cannot handle account authentication.</p>
</li>
<li><p>Obtain an access token for the NAVER account using the account credentials provided by the user.</p>
</li>
<li><p>Obtain an authorization code by passing the NAVER account access token and <a href="#ClientAuthInfo">client credentials</a> to the parameters of the <a href="/CIC/References/Clova_Auth_API.html#authorize">/authorize</a> API. This is an example of requesting an authorization code.</p>
<pre><code>https://auth.clova.ai/authorize?client_id=7Jlaksjdflq1rOuTpA%3D%3D
                               &amp;device_id=test_device
                               &amp;model_id=test_model
                               &amp;response_type=code
                               &amp;state=95%2FKjaJfMlakjdfTVbES5ccZQ%3D%3D
</code></pre>
<p>An authorization code is returned as follows.</p>
<pre><code>{
    "code": "cnl__eCSTdsdlkjfweyuxXvnlA",
    "state": "95/KjaJfMlakjdfTVbES5ccZQ=="
}
</code></pre></li>
<li><p>(Skip if necessary) Send the authorization code to the client device.</p>
</li>
<li><p>Obtain a Clova access token by passing the authorization code and <a href="#ClientAuthInfo">client credentials</a> to the parameters of the <a href="/CIC/References/Clova_Auth_API.html#token">/token</a> API. This is an example of requesting a Clova access token.</p>
<pre><code>http://auth.clova.ai:15828/token?client_id=7JWI64WVIsdfasdfrOuTpA%3D%3D
                                &amp;client_secret=66qo65asdfasdfaA7JasdfasfOqwnOq1rOyfgeydtCDrvYasfasf%3D
                                &amp;code=cnl__eCSTdsdlkjfweyuxXvnlA
                                &amp;device_id=test_device
                                &amp;grant_type=authorization_code
                                &amp;model_id=test_model
</code></pre>
<p>The Clova access token is returned as follows.</p>
<pre><code>{
    "access_token": "XHapQasdfsdfFsdfasdflQQ7w",
    "expires_in": 332000,
    "refresh_token": "GW-Ipsdfasdfdfs3IbHFBA",
    "token_type": "Bearer"
}
</code></pre>
</li>
</ol>

<div class="note">
<p><strong>Note!</strong></p>
<p>When attempting to obtain a Clova access token using NAVER account credentials, your client may have to ask the user to agree to the terms of use or provide a WebView to display age verification information. Related guidelines will be ready soon. In the meantime, when you develop with a test account, use the Clova mobile app to agree to the terms of use and complete age verification.</p>
</div>


### Connecting with CIC {#CreateConnection}
CIC uses the HTTP/2 protocol and its base URL is as follows.

{% raw %}
```
https://prod-ni-cic.clova.ai/
```
{% endraw %}

When your client attempts to establish an initial connection with CIC, the first thing to do is creating a "Downchannel." A Downchannel is used to receive Directive messages from CIC. The Directive messages in this particular case are not response messages prompted by Event messages; they are messages initiated by CIC itself (cloud-initiated) when certain conditions are met or when any special need arises. For example, when a new alarm (push) is arrived, a Directive message for the alarm is sent through a Downchannel.

To create a Downchannel, you send a request to */v1/directives* using *GET*. Once a Downchannel is created, CIC maintains the connection.

{% raw %}
```
:method: GET
:scheme: https
:path = /v1/directives
Authorization: Bearer {{ClovaAccessToken}}
```
{% endraw %}

<div class="note">
<p><strong>Note!</strong></p>
<ul><li>When your client app or device is started, it must always maintain one active Downchannel connection with CIC. If any new request is sent to */v1/directives* when one active Downchannel is already present, that Downchannel will be closed.</li><li>See <a href="#Authorization">Authorization</a> for more details on the Authorization field of a header.</li></ul>
</div>


### Authorization {#Authorization}
When your client sends a request to CIC, it should provide a [Clova access token](#CreateClovaAccessToken). Enter the type and value of a Clova access token separated by space into the Authorization field of a header as follows. See [HTTP/2 message format](/CIC/References/HTTP2_Message_Format.md) for more details on the HTTP format.

{% raw %}
```
:method: {{GET|POST}}
:scheme: https
:path = /v1/events
Authorization: Bearer {{ClovaAccessToken}}
```
{% endraw %}

Every time your client sends a new request (Event message), it should provide a Clova access token as the following picture shows.

![](/CIC/Resources/Images/CIC_Message_Interaction_Diagram.png)

### Managing connection {#ManageConnection}

Once your client establishes a connection to CIC, it must do the following to manage the connection properly.

| Task  | Description  |
|----------|-----------------------------------|
| Maintain DownChannel | When the existing Downchannel is closed or disconnected, your client must [create a new Downchannel](##CreateConnection) immediately to prevent from failing to receive any Directive messages being sent from CIC. |
| Perform ping-pong | Your client must send HTTP/2 PING frames to CIC with the interval of 1 minute. If your client fails to receive HTTP/2 PING ACK responses from CIC, it must create a new connection immediately to ensure that the connection is maintained between your client and CIC. Refer to [HTTP/2 PING Payload Format](https://http2.github.io/http2-spec/#rfc.figure.12) for more details on the HTTP/2 PING frame. |

<div class="note">
<p><strong>Note!</strong></p>
<p>When your client is unable to send HTTP/2 PING frames, it must send GET requests to /ping every 1 minute,  at which point, an HTTP 204 No Content response is received. As is the case with HTTP/2 PING frames, if your client fails to receive a response, it must create a new connection immediately.</p>
<p>This is an example of sending a GET request to /ping.</p>
<pre><code>:method = GET
:scheme = https
:path = /ping
Authorization = Bearer {{YOUR_ACCESS_TOKEN}}
</code></pre>
</div>
