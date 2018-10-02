### リクエストメッセージを検証する {#RequestMessageValidation}

ExtensionがCEKからのHTTPリクエストを受信したとき、そのリクエストが第三者ではなく、Clovaから送信された信頼できるリクエストかどうかを検証する必要があります。[HTTPヘッダー](#HTTPHeader)の`SignatureCEK`とRSA公開鍵を使用して、以下のようにリクエストメッセージを検証することができます。

<ol>
  <li><p>Clovaの署名用RSA公開鍵を以下のURLからダウンロードします。</p>
<p>{{ book.PublicKeyURLforCEKMessageValidation }}</p></li>
  <li><p><a href="/CEK/References/CEK_API.html#HTTPHeader">HTTPヘッダー</a>から`SignatureCEK`フィールドの値を取得します。</p><p>`SignatureCEK`フィールドの値は、HTTPリクエストメッセージのボディをBase64エンコードした<a href="https://tools.ietf.org/html/rfc3447" target="_blank">RSA PKCS#1 v1.5</a>署名(signature)です。</p></li>
  <li>ステップ1でダウンロードしたRSA公開鍵と、ステップ2で取得した`SignatureCEK`ヘッダーの値を使用して、以下のように<a href="https://tools.ietf.org/html/rfc3447#section-5.2" target="_blank">検証(verify)</a>します。</li>
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
  <p><strong>メモ</strong></p>
  <p>メッセージの検証に失敗した場合、そのリクエストを廃棄します。</p>
</div>
