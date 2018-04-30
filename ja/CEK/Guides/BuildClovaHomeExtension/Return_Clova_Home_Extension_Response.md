## Clova Home Extensionレスポンスを返す {#ReturnClovaHomeExtensionResponse}

Clova Home Extensionは、処理結果をCEKに返す必要があります(HTTPSレスポンス)。Clova Home Extensionレスポンスには、次のような特徴があります。

* デバイス状態のリクエストを受信した場合、IoTサービスからデバイスの状態を取得するため、デバイスの現在の状態とは異なることがあります。
* デバイス操作のリクエストを受信した場合、結果としてデバイスの最終状態変更を返すのではなく、IoTサービスにユーザーのリクエストがちゃんと届いたか確認する程度の応答を返します。
* リクエストが正常に処理された場合、以下のように[Clova Home Extensionリクエスト](#HandleClovaHomeExtensionRequest)に対応する[インターフェース](/CEK/References/CEK_API.md#ClovaHomeExtInterface)を使用して応答する必要があります。

「照明をつけて」のような操作のリクエスト([`TurnOnRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#TurnOnRequest))をIoTサービスに送信し、IoTサービスから正常に処理されたとの応答を受け取った場合、以下のように[`TurnOnConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#TurnOnConfirmation)メッセージで結果をCEKに返す必要があります。

{% raw %}
```json
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "TurnOnConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

もし、ユーザーのリクエストを処理する際にエラーが発生した場合、[Error API](/CEK/References/ClovaHomeInterface/Error_Interfaces.md)を使用してエラーをCEKに返す必要があります。Clovaは受信したAPIに応じてエラーを処理します。

以下は、デバイスにアクセスできず、`TargetOfflineError`エラーメッセージを返すサンプルです。

{% raw %}
```json
{
  "header": {
    "messageId": "fef949b7-eb94-4bda-a417-2cfb604194c3",
    "namespace": "ClovaHome",
    "name": "TargetOfflineError",
    "payloadVersion": "1.0"
  },
  "payload": {
  }
}
```
{% endraw %}


<div class="note">
<p><strong>メモ</strong></p>
<p>エラーメッセージを返す際にも、レスポンスはHTTP 200 OKを使用します。</p>
</div>