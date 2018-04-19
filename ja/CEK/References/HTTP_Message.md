## HTTPメッセージ {#HTTPMessage}
CEKとExtensionが通信する際、HTTP/1.1プロトコルを使用して一般的ななHTTPSリクエストとHTTPSレスポンスをやり取りします。CEKとExtensionが通信する際、HTTPメッセージのボディには、JSON形式のメッセージが含まれます。ここでは、CEKとExtensionがやり取りするHTTPメッセージの構成について説明します。

### HTTPヘッダー {#HTTPHeader}
CEKがExtensionに解析されたユーザーの発話情報を渡す際、HTTPSリクエストを使用します。その際、HTTPSリクエストのヘッダーは、次のように構成されます。

{% raw %}
```
POST /APIpath HTTP/1.1
Host: your.extension.endpoint
Content-Type: application/json;charset-UTF-8
Accept: application/json
Accept-Charset: utf-8
SignatureCEK: SIGNATURE
SignatureCEKCertChainUrl: SIGNATURE_CEK_CER_CHAIN_URL
```
{% endraw %}

* HTTP/1.1バージョンでHTTPS通信し、POSTメソッドを使用します。
* Hostとリクエストパスは、Extensionの開発者があらかじめ定義したURIに設定されます。
* ボディのデータはJSON形式で、UTF-8エンコーディングを使用します。
* Clovaからのリクエストであることを検証してください。

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
HTTPSリクエストメッセージとレスポンスメッセージのボディはJSON形式で、解析されたユーザーの発話情報や、Extensionの処理結果が含まれています。それぞれのメッセージの構成は、使用するExtensionの種類によって異なります。メッセージ構成の詳細については、[Custom Extensionメッセージ](#CustomExtMessage)を参照してください。


## 署名を確認する {#Signature}
リクエストを受け付けたとき、そのリクエストが不正な第三者から発信されたものではなく、Clovaからのリクエストであることを確認する必要があります。もし、Clova以外からのリクエストを受信した場合には必ず拒否をして下さい。

### リクエストの署名を確認する
[HTTPヘッダー](#HTTPHeader)には、リクエストの署名を確認するための2つのパラメータが含まれています。

<ol>
    <li><code>SignatureCEKCertChainUrl</code>のホスト名が<code>clova-cek-requests.line.me</code>であり、httpsから始まるURLであることを確認してください。もし、正しくないURLである場合、リクエストを拒否して下さい。
        <p>例) https://clova-cek-requests.line.me/cek/request-cert.crt</p>
    </li>
    <li>ClovaのPEMエンコード済みのX.509証明書チェーンを<code>SignatureCEKCertChainUrl</code>に指定されたURLからダウンロードしてください。</li>
    <li>ダウンロードした証明書のSubject Alternaive Names(SAN)セクションに<code>clova-cek-requests.line.me</code>ドメインが有ることを確認して下さい。</li>
    <li>信頼できるルート証明書によって全てのチェーンが作られていることを確認してください。</li>
    <li>ダウンロードした証明書の期限が有効期限内であることを確認してください。</li>
    <li>ここまでの確認に問題が無ければ、公開鍵を証明書から取得して下さい</li>
    <li><code>Signature</code>をBase64でデコードしてください。</li>
    <li>証明書から取得した公開鍵を使って<code>Signature</code>を復号化し、HTTPSリクエストボディのSHA-1値と一致することを確認して下さい。</li>
</ol>
