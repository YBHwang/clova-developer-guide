### Validating a request message {#RequestMessageValidation}

When an extension receives an HTTP request from CEK, you need to validate the integrity of the request to check that the request was sent from Clova and not from a third party. Using `SignatureCEK` in the [HTTP header](#HTTPHeader) and the RSA public key, you can validate the request message as follows:

<ol>
  <li><p>Download the RSA public key for Clova signature from the URL below.</p>
<p>{{ book.ServiceEnv.PublicKeyURLforCEKMessageValidation }}</p></li>
  <li><p>Obtain the `SignatureCEK` field value from the <a href="/CEK/References/CEK_API.html#HTTPHeader">HTTP header</a>.</p><p>`SignatureCEK` The field value is the <a href="https://tools.ietf.org/html/rfc3447" target="_blank">RSA PKCS#1 v1.5</a> signature value that has encoded the body of the HTTP request message in Base64.</p></li>
  <li><a href="https://tools.ietf.org/html/rfc3447#section-5.2" target="_blank">Verify</a> as follows using the RSA public key downloaded in step 1 and the `SignatureCEK` header value acquired in step 2.</li>
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
  <p>If message verification fails, discard the request.</p>
</div>
