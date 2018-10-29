# Linking user accounts
Clova can provide third-party services that require permissions for user account access through a [custom extension](/CEK/Guides/Build_Custom_Extension.md) or a [Clova Home extension](/CEK/Guides/Build_Clova_Home_Extension.md). For example, paid content services such as music streaming or other services like shopping, finance, messaging, and home IoT can be connected to Clova. Clova supports account linking that connects the user account of the third-party service and the Clova user account through [OAuth 2.0](https://tools.ietf.org/html/rfc6749).

Account linking is used when a custom extension provides a third-party service that requires users to authenticate their accounts. Account linking is not required for third-party services that do not require authentication. If the service only requires information to identify users, you can use the combination of values for the device identifier (`context.System.device.deviceId`) and user account identifier (`context.System.user.userId` or `session.user.userId`) provided in the [custom extension message](/CEK/References/CEK_API.md#CustomExtMessage).


<div class="note">
<p><strong>Note!</strong></p>
<p>Clova Home extensions must use account linking.</p>
</div>

This documentation includes the following topics:
* [Understanding account linking](#UnderstandAccountLinking)
* [Applying account linking](#ApplyAccountLinking)

## Understanding account linking {#UnderstandAccountLinking}
Before applying account linking to the extension, you must first understand how account linking works. This section covers the following topics:
* [Setting up account linking](#SetupAccountLinking)
* [Invoking an extension after account linking](#ExtensionInvokingAfterAccountLinking)

### Setting up up account linking {#SetupAccountLinking}
When a user enables a custom extension or Clova Home extension that requires authentication, the account linking setup is performed as follows:

![](/CEK/Resources/Images/CEK_Account_Linking_Setup_Sequence_Diagram.png)

1. The user enables a custom extension or Clova Home extension.

2. The login page of the third-party service is displayed on the client app or the app paired with the client device. This method uses the **[authorization URL](#BuildAuthServer)** of the authorization server registered by the extension developer.

3. Once the user completes account authentication, an authorization code is returned.

4. The client sends the received authorization code to Clova.

5. Clova requests an access token and a refresh token to **[access token URI](#RegisterAccountLinkingInfo)**. Then, the authorization code is delivered and the acquired access tokens and refresh tokens are stored in the Clova account information of the user.

6. The user can now able to use the service that requires account authentication.

<div class="note">
<p><strong>Note!</strong></p>
<p>When a user disables a custom extension or Clova Home extension, the access token stored in the Clova account of a user is removed. Therefore, account linking must be performed again if the user enables the extension again.</p>
</div>

### Invoking an extension after account linking {#ExtensionInvokingAfterAccountLinking}
Once an account is linked, CEK invokes the extension as follows:

1. CEK invokes the extension as usual to handle the user request.

2. **If the access token is expired** a new access token is requested to the **[access token URI](#RegisterAccountLinkingInfo)** using the refresh token.

3. CEK sends the user request by including the access token in the message to the extension.
   * If it is a custom extension, the access token is delivered to the `context.System.user.accessToken`and `session.user.accessToken` fields.
   * If it is a Clova Home extension, the access token is delivered to the `payload.accessToken` field.

4. The extension must respond as follows for the following conditions:
   * If the access token is valid, the extension must handle the user request and return the result.
   * If the access token is invalid, the extension must return the result to allow [setting up account linking](#SetupAccountLinking).

## Applying account linking {#ApplyAccountLinking}
To apply account linking to the extension under development, complete the following steps:

1. [Building an authorization server](#BuildAuthServer)
2. [Implementing account permissions verification](#AddValidationLogic)
3. [Registering account linking information](#RegisterAccountLinkingInfo)

### Building an authorization server {#BuildAuthServer}

To apply account linking to an extension, there must be a login page for the user to authenticate their account and also a server to issue an access token once authentication is complete.

The login page for user authentication must meet the following requirements:
* The page must be provided using the HTTPS protocol.
* The page must support mobile browsing.
* The page must not contain pop-up windows.
* The page must move to the redirect URL (`redirect_uri`) once authentication is complete. At this time, the authorization code must be sent as a parameter.
* The page must continue sending the `state` parameter to the redirect URL (`redirect_uri`).


The URL of the page providing the login UI for user account authentication is referred to as the **authorization URL**. An authorization URL must be entered when [registering an extension](/DevConsole/Guides/CEK/Register_Extension.md) on the Clova developer console. When a user [sets up account linking](/DevConsole/Guides/CEK/Register_Extension.md#SetAccountLinking) for the extension, the **authorization URL** is called along with the following parameters:

| Parameter name   | Description                                                                                                                                                      |
|:---------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------|
| `state`         | State value used to check the expiry of an authentication session. This value expires after 5 minutes, so the user must re-authenticate once the session expires.       |
| `client_id`     | ID used by Clova to get the access token for the third-party service.You must register a `cliend_id` in advance on the Clova developer console.     |
| `response_type` | Parameter that has a defined OAuth 2.0 authorization type. Use the `"code"` type. You can specify the type on the Clova developer console. Currently, only `"code"` type is supported.|
| `scope`         | `scope` field of OAuth. You can use to define the access level. You must register the `scope` in advance on the Clova developer console.                            |
| `redirect_uri`  |URL used to redirect the user after authentication (redirect URL). The `redirect_uri` value can be verified when [setting up account linking](/DevConsole/Guides/CEK/Register_Extension.md#SetAccountLinking) to register the extension on the Clova developer console. Currently, `{{ book.RedirectURLforAccountLinking }}` is used. |

<div class="note">
  <p><strong>Note!</strong></p>
  <p>For more information on parameters, see <a href="https://tools.ietf.org/html/rfc6749#section-4">Obtaining authorization</a> in the OAuth 2.0 authorization framework.</p>
</div>

Here is an example of a URL when a client app or app paired with a client device requests a login page.

<pre><code>https://yourdomain.com/login?state=qwer123
                            &client_id=clova-extension
                            &scope=listen_music%20basic_profile
                            &response_type=code
                            &redirect_uri={{ book.RedirectURLforAccountLinking }}
</code></pre>


<div class="note">
<p><strong>Note!</strong></p>
<p>The <code>redirect_uri</code> can be found on the <a href="/DevConsole/Guides/CEK/Register_Extension.md#RedirectURI">Setting up account linking</a> page of the Clova developer console.</p>
</div>


The URL to move after authentication (`redirect_uri`) must deliver the following parameters:

| Parameter name  | Description                                                                                                                                                      |
|:---------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------|
| `vendorId`     | ID assigned to the extension developer: This ID is registered in the Clova developer console in order to distinguish between a company and a third-party service. It is included in `redirect_uri` in advance. |
| `state`        | State value used to check the expiry of an authentication session. Enter the `state` parameter received from **authorization URL**.                                                 |
| `code`         | Authorization code. If the `response_type` value is `"code"`, enter the authorization code in the parameter.                                                                  |
| `token_type`   | Type of access token. It must be delivered with access token type (`access_token`). The value is always `"Bearer"`.                                                         |

Here is an example of a redirect URL the user is sent to once user account authentication is complete.

<pre><code>{{ book.RedirectURLforAccountLinking }}?vendorId=YourServiceOrCompanyID
                                &state=qwer123
                                &code=nl__eCSTdsdlkjfweyuxXvnl
</code></pre>


If Clova acquires an authorization code for account linking, Clova requests an access token again from the **[access token URI](#RegisterAccountLinkingInfo),** which you preregistered on the Clova developer console. Clova sends the acquired authorization code as a parameter, then the authorization server must issue an access token with permission to access the account of the third-party service and a refresh token to renew the access token.

### Implementing account permissions verification {#AddValidationLogic}
To apply account linking, the extension developer must write the code for verifying the validity of the access token. Each extension message delivered to the custom extension and Clova Home extension contains the `accessToken` fields as shown below.
Once you obtain the access token from the fields below, you must check the existence and validity of this value.

* Custom Extension: `context.System.user.accessToken`, `session.user.accessToken`
* Clova Home Extension: `payload.accessToken`

{% raw %}
```json
// Example 1: Example of a custom extension message
{
  "version": "1.0",
  "session": {
    "new": false,
    "sessionAttributes": {},
    "sessionId": "a29cfead-c5ba-474d-8745-6c1a6625f0c5",
    "user": {
      "userId": "U399a1e08a8d474521fc4bbd8c7b4148f",
      "accessToken": "XHapQasdfsdfFsdfasdflQQ7"
    }
  },
  "context": {
    "System": {
      "application": {
        "applicationId": "com.yourdomain.extension.pizzabot"
      },
      "user": {
        "userId": "U399a1e08a8d474521fc4bbd8c7b4148f",
        "accessToken": "XHapQasdfsdfFsdfasdflQQ7"
      },
      "device": {
        "deviceId": "096e6b27-1717-33e9-b0a7-510a48658a9b",
        "display": {
          "size": "l100",
          "orientation": "landscape",
          "dpi": 96,
          "contentLayer": {
            "width": 640,
            "height": 360
          }
        }
      }
    }
  },
  "request": {
    "type": "IntentRequest",
    "intent": {
      "name": "OrderPizza",
      "slots": {
        "pizzaType": {
          "name": "pizzaType",
          "value": "Pepperoni"
        }
      }
    }
  }
}

// Example 2: Example of a Clova Home extension message
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "HealthCheckRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33"
  }
}
```
{% endraw %}

<div class="note">
  <p><strong>Note!</strong></p>
  <p>If an access token does not exist or is invalid, the extension must send a response to CEK to ask the client to perform account linking again.</p>
</div>


### Registering account linking information {#RegisterAccountLinkingInfo}
After building an authorization server and applying account linking to the extension, you need to register the information mentioned in [Building an authorization server](/DevConsole/ClovaDevConsole_Overview.md) on the [Clova developer console](#BuildAuthServer). In the extension registered on the Clova developer console, [enter the account linking information](/DevConsole/Guides/CEK/Register_Extension.md#SetAccountLinking) as follows:

| Field name                 | Description                                                                                                                                                                             |
|:-----------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Authorization URL`                    | URL the user will access for [account authentication](#SetupAccountLinking).                                                                                                          |
| `Client ID`                    | Client ID granted to differentiate services when requesting the user [account authentication](#SetupAccountLinking) page.                                                       |
| `Authorization Grant Type`     | Authorization method of OAuth 2.0. Currently, only the authorization code grant method is supported.                                                                                    |
| `Access Token URI`             | Address to acquire an access token with the authorization code. Enter this field if the authorization code grant method is set.                                                               |
| `Client Secret`                | Client secret that must be delivered with a **client ID** when acquiring an access token with the authorization code. Enter this field if the authorization code grant method is set.          |
| `Client Authentication Scheme` | Scheme used when requesting access token with the access token URI.                                                                                                    |
| `Privacy Policy URL`           | Page where privacy policy details on the service are provided. It is displayed on the Clova app or paired app.                                                                              |
