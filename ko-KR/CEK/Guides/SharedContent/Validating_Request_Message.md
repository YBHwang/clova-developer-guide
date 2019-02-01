### 요청 메시지 검증 {#RequestMessageValidation}

Extension이 CEK로부터 HTTP 요청을 받을 때, 해당 요청이 제 3자가 아닌 Clova로부터 전송된 신뢰할 수 있는 요청인지 검증할 필요가 있습니다. [HTTP 헤더](#HTTPHeader)에 있는 `SignatureCEK`와 RSA 공개 키를 사용하여 다음과 같이 요청 메시지를 검증할 수 있습니다.

<ol>
  <li><p>Clova의 서명용 RSA 공개 키를 아래 URL에서 다운로드 합니다.</p>
<p>{{ book.ServiceEnv.PublicKeyURLforCEKMessageValidation }}</p></li>
  <li><p><a href="/CEK/References/CEK_API.md#HTTPHeader">HTTP 헤더</a>에서 `SignatureCEK` 필드의 값을 확보합니다.</p><p>`SignatureCEK` 필드의 값은 HTTP 요청 메시지의 본문을 Base64로 인코딩한 <a href="https://tools.ietf.org/html/rfc3447" target="_blank">RSA PKCS#1 v1.5</a> 서명 값(signature)입니다.</p></li>
  <li>1번 항목에서 다운로드한 RSA 공개 키와 2번 항목에서 획득한 `SignatureCEK` 헤더 값을 이용하여 다음과 같이 <a href="https://tools.ietf.org/html/rfc3447#section-5.2" target="_blank">검증(verify)</a>합니다.</li>
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
  <p>메시지 검증에 실패하면 해당 요청을 폐기합니다.</p>
</div>
