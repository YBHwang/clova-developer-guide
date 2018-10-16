## HTTP messages {#HTTPMessage}
CEK and the extensions communicate via the HTTP/1.1 protocol and exchange basic HTTPS requests and HTTPS responses. During this communication, a JSON format message is contained in the HTTP message body. This section explains the configuration of HTTP messages exchanged between CEK and the extension.

* [HTTP header](#HTTPHeader)
* [HTTP body](#HTTPBody)
* [Validating request messages](#RequestMessageValidation)

### HTTP header {#HTTPHeader}
An HTTP request is used when CEK sends the analyzed information of a user utterance to the extension. The HTTP request header is configured as follows:

{% raw %}

```
POST /APIpath HTTP/1.1
Host: YOUR_EXTENSION_ENDPOINT
Content-Type: application/json;charset-UTF-8
Accept: application/json
Accept-Charset: utf-8
SignatureCEK：{{ SignatureCEK }}
```
{% endraw %}

* HTTP communication is performed with HTTP/1.1 and uses the POST method.
* The values for the host and request target path are filled with the URI defined by you.
* The data type of the request body is in JSON format and uses UTF-8 encoding.
* You can [validate whether or not a request is sent from Clova](#RequestMessageValidation) using the `SignatureCEK` field and the RSA public key.

However, an HTTP response is used when the extension sends processed result to Clova. You must configure the HTTP response header as follows:
{% raw %}
```
HTTP/1.1 200 OK
Content-Type: application/json;charset-UTF-8
```
{% endraw %}
* The processed results are returned as a response to the HTTP request from CEK.
* The data type of the body is in JSON format and uses UTF-8 encoding.

### HTTP body {#HTTPBody}
Both the body of the HTTP request and response messages are in JSON format, and it contains the information about the user utterance analysis or the processed results of the extension. The configuration of each message varies depending on the extension type. For more information on message configurations, see [Custom extension messages](#CustomExtMessage) and [Clova Home extension messages](#ClovaHomeExtMessage).

### Validating request messages {#RequestMessageValidation}
When the extension receives an HTTP request from CEK, you need to validate the integrity of the request meaning that the request was sent from Clova and not from a third party. Using the `SignatureCEK` field and RSA public key in the [HTTP header](#HTTPHeader), you can validate the request message as follows:

**Validating a request messages with an RSA public key**
<ol>
<li><p>Make sure that `context.System.application.applicationId` is identical to the `ExtensionId`, which was set beforehand.</p></li>
<li><p>Download the RSA public key for Clova signature from the URL below.</p>
<p>https://clova-cek-requests.line.me/.well-known/signature-public-key.pem</p></li>
<li><p>Obtain the <code>SignatureCEK</code> header value.</p>
<p>The <code>SignatureCEK</code> header value must be a Base64-encoded <a href="https://tools.ietf.org/html/rfc3447" target="_blank">RSA PKCS #1 v1.5</a> signature value of the HTTP body.</p></li>
<li>Using the RSA public key downloaded in step 1, <a href="https://tools.ietf.org/html/rfc3447#section-5.2" target="_blank">verify</a> the <code>SignatureCEK</code> header value acquired in step 2 as follows:</li>
</ol>

```java
String signatureStr = req.getHeader("SignatureCEK");
byte[] body = getBody(req);
String publicKeyStr = downloadPublicKey();
publicKeyStr = publicKeyStr.replaceAll("\\n", "")
    .replaceAll("-----BEGIN PUBLIC KEY-----", "")
    .replaceAll("-----END PUBLIC KEY-----", "");
X509EncodedKeySpec pubKeySpec = new X509EncodedKeySpec(Base64.getDecoder().decode(publicKeyStr));
KeyFactory keyFactory = KeyFactory.getInstance("RSA");
PublicKey pubKey = keyFactory.generatePublic(pubKeySpec);
Signature sig = Signature.getInstance("SHA256withRSA");
sig.initVerify(pubKey);
sig.update(body);
byte[] signature = Base64.getDecoder().decode(signatureStr);
boolean valid = sig.verify(signature);
```

<div class="note">
  <p><strong>Note!</strong></p>
  <p>If message verification fails, you must discard the extension.</p>
</div>
