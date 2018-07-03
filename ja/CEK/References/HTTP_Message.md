## HTTPメッセージ {#HTTPMessage}
CEKとExtensionが通信する際、HTTP/1.1プロトコルを使用して基本的なHTTPSリクエストとHTTPSレスポンスをやり取りします。CEKとExtensionが通信する際、HTTPメッセージのボディには、JSON形式のメッセージが含まれます。ここでは、CEKとExtensionがやり取りするHTTPメッセージの構成について説明します。

* [HTTPヘッダー](#HTTPHeader)
* [HTTPボディ](#HTTPBody)
* [リクエストメッセージを検証する](#RequestMessageValidation)

### HTTPヘッダー {#HTTPHeader}
CEKがExtensionに解析されたユーザーの発話情報を渡す際、HTTPSリクエストを使用します。その際、HTTPSリクエストのヘッダーは、次のように構成されます。

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
* リクエストボディのデータはJSON形式で、UTF-8エンコーディングを使用します。
* `SignatureCEK`フィールドと公開鍵を使用して、[CEKから送信されたリクエストかどうかを検証](#RequestMessageValidation)することができます。

逆に、ExtensionがCEKに処理結果を返す際、HTTPSレスポンスを使用します。その際、HTTPSレスポンスのヘッダーは、次のように基本的なものだけで構成されます。
{% raw %}
```
HTTP/1.1 200 OK
Content-Type: application/json;charset-UTF-8
```
{% endraw %}
* CEKから渡されたHTTPSリクエストに対するレスポンスとして、処理結果を返します。
* ボディのデータはJSON形式で、UTF-8エンコーディングを使用します。

### HTTPボディ {#HTTPBody}
HTTPSリクエストメッセージとレスポンスメッセージのボディはJSON形式で、解析されたユーザーの発話情報や、Extensionの処理結果が含まれています。それぞれのメッセージの構成は、使用するExtensionの種類によって異なります。メッセージ構成の詳細については、[Custom Extensionメッセージ](#CustomExtMessage)と[Clova Home Extensionメッセージ](#ClovaHomeExtMessage)を参照してください。

### リクエストメッセージを検証する {#RequestMessageValidation}
ExtensionがCEKからHTTPSリクエストを受信するとき、そのリクエストが第三者ではなく、Clovaから送信された信頼できるリクエストかどうかを検証する必要があります。[HTTPヘッダー](#HTTPHeader)にある`SignatureCEK`フィールドと公開鍵を使用して、以下のようにリクエストメッセージを検証できます。

**ハッシュ値を生成してメッセージを検証する**
1. 公開鍵(`https://clova-cek-requests.line.me/.well-known/signature-public-key.pem`)をダウンロードします
2. `SignatureCEK`の値をBase64でデコードします。
3. リクエストボディをSHA-256でハッシュ値を生成します。
4. ステップ1でダウンロードした公開鍵、ステップ2で`SignatureCEK`をデコードした値、3で生成したハッシュ値を使用して<a href="https://en.wikipedia.org/wiki/Digital_Signature_Algorithm#Verifying" target="_blank">検証(verify)</a>します。

<div class="note">
  <p><strong>メモ</strong></p>
  <p><strong>ハッシュ値を生成してメッセージを検証する</strong>で比較した2つの値が一致しない場合、そのリクエストを破棄することを推奨します。</p>
</div>
