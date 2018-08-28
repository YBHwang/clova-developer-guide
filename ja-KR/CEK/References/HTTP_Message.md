## HTTPメッセージ {#HTTPMessage}
CEKとExtensionは、HTTP/1.1プロトコルを使用して、基本的なHTTPリクエストとHTTPレスポンスのやり取りを行います。CEKとExtensionが通信する際、HTTPメッセージのボディには、JSON形式のメッセージが含まれます。ここでは、CEKとExtensionがやり取りするHTTPメッセージの構成について説明します。

* [HTTPヘッダー](#HTTPHeader)
* [HTTPボディ](#HTTPBody)
* [リクエストメッセージを検証する](#RequestMessageValidation)

### HTTPヘッダー {#HTTPHeader}
CEKからExtensionに解析されたユーザーの発話情報を送信するとき、HTTPリクエストを使用します。そのとき、HTTPリクエストのヘッダーは、以下のように構成されます。

{% if book.TargetCountryCode == "KR" %}
{% raw %}

```
POST /APIpath HTTP/1.1
Host: your.extension.endpoint
Content-Type: application/json;charset-UTF-8
Accept: application/json
Accept-Charset: utf-8
```
{% endraw %}

* HTTP/1.1バージョンでHTTPS通信し、POSTメソッドを使用します。
* Hostとリクエストパスは、Extensionの開発者があらかじめ定義したURIに設定されます。
* ボディのデータフォーマットはJSONで、UTF-8エンコーディングを使用します。
{% elif book.TargetCountryCode == "JP" %}
{% raw %}

```
POST /APIpath HTTP/1.1
Host: your.extension.endpoint
Content-Type: application/json;charset-UTF-8
Accept: application/json
Accept-Charset: utf-8
SignatureCEK：{{ SignatureCEK }}
```
{% endraw %}

* HTTP/1.1バージョンでHTTPS通信し、POSTメソッドを使用します。
* Hostとリクエストパスは、Extensionの開発者があらかじめ定義したURIに設定されます。
* ボディのデータフォーマットはJSONで、UTF-8エンコーディングを使用します。
* `SignatureCEK`フィールドとRSA公開鍵を使用して、[CEKから送信されたリクエストかどうかを検証する](#RequestMessageValidation)ことができます。
{% endif %}

逆に、ExtensionからClovaに処理結果を返すときには、HTTPレスポンスを使用します。そのとき、HTTPレスポンスのヘッダーは、以下のように構成します。
{% raw %}
```
HTTP/1.1 200 OK
Content-Type: application/json;charset-UTF-8
```
{% endraw %}
* CEKからのHTTPリクエストに対するレスポンスとして、処理結果を返します。
* ボディのデータはJSON形式で、UTF-8エンコーディングを使用します。

### HTTPボディ {#HTTPBody}
HTTPリクエストメッセージとレスポンスメッセージのボディはJSON形式で、解析されたユーザーの発話情報や、Extensionの処理結果が含まれています。それぞれのメッセージの構成は、使用するExtensionの種類によって異なります。メッセージ構成の詳細については、[Custom Extensionのメッセージ](#CustomExtMessage)と[Clova Home Extensionメッセージ](#ClovaHomeExtMessage)を参照してください。

{% if book.TargetCountryCode == "JP" %}
### リクエストメッセージを検証する {#RequestMessageValidation}

ExtensionがCEKからのHTTPリクエストを受信したとき、そのリクエストが第三者ではなく、Clovaから送信された信頼できるリクエストかどうかを検証する必要があります。[HTTPヘッダー](#HTTPHeader)の`SignatureCEK`とRSA公開鍵を使用して、以下のようにリクエストメッセージを検証します。

**ハッシュ値を生成してメッセージを検証する**
<ol>
  <li><p>Clovaの署名用RSA公開鍵を以下のURLからダウンロードします。</p>
<p>https://clova-cek-requests.line.me/.well-known/signature-public-key.pem</p></li>
  <li><p>`SignatureCEK`ヘッダーの値を取得します。</p><p>`SignatureCEK`ヘッダーの値はHTTPリクエストのボディをBase64エンコードした<a href="https://tools.ietf.org/html/rfc3447" target="_blank">署名(signature)</a>の値です。</p></li>
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
{% endif %}
