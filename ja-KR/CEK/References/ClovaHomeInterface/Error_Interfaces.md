# Error
Clova Home ExtensionがCEKにエラーを返す際に使用されるインターフェースです。以下のエラーメッセージを使用できます。


| メッセージ         | タイプ  | 説明                                   |
|------------------|-----------|---------------------------------------------|
| [`ActionTemporarilyBlockedError`](#ActionTemporarilyBlockedError)  | Error Response | 短い時間内に、デバイスが処理できないほど多くのアクションがリクエストされたり、ユーザーおよびデバイスの安全のためにリクエストがキャンセルされた場合、CEKにこのメッセージをレスポンスとして返す必要があります。 |
| [`ConditionsNotMetError`](#ConditionsNotMetError)          | Error Response | デバイスが動作するための特定の要件(ステータス)が満たされていない場合、CEKにこのメッセージをレスポンスとして返す必要があります。 |
| [`DeviceFailureError`](#DeviceFailureError)                | Error Response | デバイスに障害が発生した場合、CEKにこのメッセージをレスポンスとして返す必要があります。              |
| [`DriverInternalError`](#DriverInternalError)              | Error Response | 内部エラーが発生した場合、CEKにこのメッセージをレスポンスとして返す必要があります。                |
| [`ExpiredAccessTokenError`](#ExpiredAccessTokenError)      | Error Response | [アカウント連携](/CEK/Guides/Link_User_Account.md)を行うとき、[認可サーバー](/CEK/Guides/Link_User_Account.md#BuildAuthServer)から発行されたアクセストークンが期限切れである場合、CEKにこのメッセージをレスポンスとして返す必要があります。  |
| [`InvalidAccessTokenError`](#InvalidAccessTokenError)      | Error Response | ユーザーが使用しているアクセストークンに対する権限が解除された場合、CEKにこのメッセージをレスポンスとして返す必要があります。         |
| [`NoSuchTargetError`](#NoSuchTargetError)                  | Error Response | デバイスが存在しない場合、CEKにこのメッセージをレスポンスとして返す必要があります。                            |
| [`NotSupportedInCurrentModeError`](#NotSupportedInCurrentModeError) | Error Response | デバイスの現在のモードでサポートされていないリクエストを受信した場合、CEKにこのメッセージをレスポンスとして返す必要があります。  |
| [`TargetOfflineError`](#TargetOfflineError)                | Error Response | デバイスがオフラインになっていてアクセスできなかった場合、CEKにこのメッセージをレスポンスとして返す必要があります。 |
| [`UnsupportedOperationError`](#UnsupportedOperationError)  | Error Response | デバイスでサポートされていないリクエストを受信した場合、CEKにこのメッセージをレスポンスとして返す必要があります。   |
| [`ValueNotFoundError`](#ValueNotFoundError)                | Error Response | デバイスが測定値やステータス値を測定したり、または保存したりすることができず、リクエストされた値を提供できない場合、CEKにこのメッセージをレスポンスとして返す必要があります。  |
| [`ValueNotSupportedError`](#ValueNotSupportedError)        | Error Response | デバイスでサポートされていない値を指定しようとするリクエストを受信した場合、CEKにこのメッセージをレスポンスとして返す必要があります。  |
| [`ValueOutOfRangeError`](#ValueOutOfRangeError)            | Error Response | デバイスが処理できる範囲外の値を設定しようとするリクエストを受信した場合、CEKにこのメッセージをレスポンスとして返す必要があります。 |

<div class="note">
<p><strong>メモ</strong></p>
<p>エラーメッセージの種類は追加される予定です。</p>
</div>

## ActionTemporarilyBlockedError {#ActionTemporarilyBlockedError}
短い時間内にデバイスが処理できない数のアクションがリクエストされたり、ユーザーおよびデバイスの安全のためにリクエストがキャンセルされた場合、CEKにこのメッセージをレスポンスとして返す必要があります。CEKはこのメッセージを受け取ると、あらかじめ用意されたエラーメッセージをクライアントに送信します。

### Payload fields

なし

### 備考
* エラーが発生した場合にも、エラーメッセージはリクエスト成功のHTTPレスポンス(200 OK)でCEKに返す必要があります。
* エラーメッセージの名前で状況を判断するため、`payload`は必要ありません。

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "63788c00-5b27-4ce7-b1f4-4f56bc12d3f4",
    "namespace": "ClovaHome",
    "name": "ActionTemporarilyBlockedError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### 次の項目も参照してください。

なし

## ConditionsNotMetError {#ConditionsNotMetError}
デバイスが動作するための特定の要件(ステータス)が満たされていない場合、CEKにこのメッセージをレスポンスとして返す必要があります。CEKはこのメッセージを受け取ると、あらかじめ用意されたエラーメッセージをクライアントに送信します。

### Payload fields

| フィールド名       | データ型    | フィールドの説明                     | 必須/選択 |
|---------------|---------|-----------------------------|:---------:|
| `state`       | string  | 満たされていない条件や状態を表す値。このフィールドはユーザーにTTSとして再生されるので、ユーザーにとってわかりやすい言葉で作成される必要があります。以下のように、ユーザーに現在の状況をレポートします。<pre><code>{デバイス}の{state}状態ではサポートしていない機能です。確認してから、再度試してください。</code></pre>  | 必須    |

### 備考
* エラーが発生した場合にも、エラーメッセージはリクエスト成功のHTTPレスポンス(200 OK)でCEKに返す必要があります。

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "4ea1e527-7be3-4b54-b531-93d245b97303",
    "namespace": "ClovaHome",
    "name": "ConditionsNotMetError",
    "payloadVersion": "1.0"
  },
  "payload": {
    "state": "省電力モード"
  }
}
```
{% endraw %}

### 次の項目も参照してください。
* [`NotSupportedInCurrentModeError`](#NotSupportedInCurrentModeError)

## DeviceFailureError {#DeviceFailureError}
デバイスに障害が発生した場合、CEKにこのメッセージをレスポンスとして返す必要があります。CEKはこのメッセージを受け取ると、あらかじめ用意されたエラーメッセージをクライアントに送信します。

### Payload fields

なし

### 備考
* エラーが発生した場合にも、エラーメッセージはリクエスト成功のHTTPレスポンス(200 OK)でCEKに返す必要があります。
* エラーメッセージの名前で状況を判断するため、`payload`は必要ありません。

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "4ea1e527-7be3-4b54-b531-93d245b97303",
    "namespace": "ClovaHome",
    "name": "DeviceFailureError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### 次の項目も参照してください。
* [`DriverInternalError`](#DriverInternalError)
* [`TargetOfflineError`](#TargetOfflineError)

## DriverInternalError {#DriverInternalError}
内部エラーが発生した場合、CEKにこのメッセージをレスポンスとして返す必要があります。CEKはこのメッセージを受け取ると、あらかじめ用意されたエラーメッセージをクライアントに送信します。

### Payload fields

なし

### 備考
* エラーが発生した場合にも、エラーメッセージはリクエスト成功のHTTPレスポンス(200 OK)でCEKに返す必要があります。
* エラーメッセージの名前で状況を判断するため、`payload`は必要ありません。

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "fef949b7-eb94-4bda-a417-2cfb604194c3",
    "namespace": "ClovaHome",
    "name": "DriverInternalError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### 次の項目も参照してください。
* [`DeviceFailureError`](#DeviceFailureError)
* [`TargetOfflineError`](#TargetOfflineError)

## ExpiredAccessTokenError {#ExpiredAccessTokenError}
[アカウント連携](/CEK/Guides/Link_User_Account.md)を行うとき、[認可サーバー](/CEK/Guides/Link_User_Account.md#BuildAuthServer)から発行されたアクセストークンが期限切れである場合、CEKにこのメッセージをレスポンスとして返す必要があります。CEKはこのメッセージを受け取ると、あらかじめ用意されたエラーメッセージをクライアントに送信します。

### Payload fields

なし

### 備考
* エラーが発生した場合にも、エラーメッセージはリクエスト成功のHTTPレスポンス(200 OK)でCEKに返す必要があります。
* エラーメッセージの名前で状況を判断するため、`payload`は必要ありません。

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "1abd6113-4a36-47c3-851e-bee3254fe183",
    "namespace": "ClovaHome",
    "name": "ExpiredAccessTokenError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### 次の項目も参照してください。
* [`InvalidAccessTokenError`](#InvalidAccessTokenError)

## InvalidAccessTokenError {#InvalidAccessTokenError}
ユーザーが使用しているアクセストークンに対する権限が解除された場合、CEKにこのメッセージをレスポンスとして返す必要があります。CEKはこのメッセージを受け取ると、あらかじめ用意されたエラーメッセージをクライアントに送信します。

### Payload fields

なし

### 備考
* エラーが発生した場合にも、エラーメッセージはリクエスト成功のHTTPレスポンス(200 OK)でCEKに返す必要があります。
* エラーメッセージの名前で状況を判断するため、`payload`は必要ありません。

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "b8ac8b45-9fb9-4dc4-97ca-d55e9fc1ff8f",
    "namespace": "ClovaHome",
    "name": "InvalidAccessTokenError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### 次の項目も参照してください。
* [`ExpiredAccessTokenError`](#ExpiredAccessTokenError)

## NoSuchTargetError {#NoSuchTargetError}
デバイスが存在しない場合、CEKにこのメッセージをレスポンスとして返す必要があります。例えば、ユーザーがIoTサービスから特定のデバイスを削除しましたが、そのことがClovaアプリにまだ反映されていない状態でそのデバイスの操作をリクエストされた場合、このメッセージを返します。CEKはこのメッセージを受け取ると、あらかじめ用意されたエラーメッセージをクライアントに送信します。

### Payload fields

なし

### 備考
* エラーが発生した場合にも、エラーメッセージはリクエスト成功のHTTPレスポンス(200 OK)でCEKに返す必要があります。
* エラーメッセージの名前で状況を判断するため、`payload`は必要ありません。

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "d458e46c-6827-4940-9340-a7a9d427d7ab",
    "namespace": "ClovaHome",
    "name": "NoSuchTargetError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### 次の項目も参照してください。
* [`ConditionsNotMetError`](#ConditionsNotMetError)
* [`TargetOfflineError`](#TargetOfflineError)

## NotSupportedInCurrentModeError {#NotSupportedInCurrentModeError}
デバイスの現在のモードでサポートされていないリクエストを受信した場合、CEKにこのメッセージをレスポンスとして返す必要があります。例えば、エアコンの場合、除湿モードで動作している間は温度を調節できない製品があります。そのタイプのエアコンを使用しているユーザーが、除湿モードで温度調節をリクエストした場合、このメッセージを返します。CEKはこのメッセージを受け取ると、あらかじめ用意されたエラーメッセージをクライアントに送信します。

### Payload fields

なし

### 備考
* エラーが発生した場合にも、エラーメッセージはリクエスト成功のHTTPレスポンス(200 OK)でCEKに返す必要があります。
* エラーメッセージの名前で状況を判断するため、`payload`は必要ありません。

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "f321b946-b593-4279-a840-8e5af5a00146",
    "namespace": "ClovaHome",
    "name": "NotSupportedInCurrentModeError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### 次の項目も参照してください。
* [`UnsupportedOperationError`](#UnsupportedOperationError)

## TargetOfflineError {#TargetOfflineError}
デバイスがオフラインになっていてアクセスできなかった場合、CEKにこのメッセージをレスポンスとして返す必要があります。CEKはこのメッセージを受け取ると、あらかじめ用意されたエラーメッセージをクライアントに送信します。

### Payload fields

なし

### 備考
* エラーが発生した場合にも、エラーメッセージはリクエスト成功のHTTPレスポンス(200 OK)でCEKに返す必要があります。
* エラーメッセージの名前で状況を判断するため、`payload`は必要ありません。

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "fef949b7-eb94-4bda-a417-2cfb604194c3",
    "namespace": "ClovaHome",
    "name": "TargetOfflineError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### 次の項目も参照してください。
* [`DeviceFailureError`](#DeviceFailureError)
* [`DriverInternalError`](#DriverInternalError)

## UnsupportedOperationError {#UnsupportedOperationError}

デバイスでサポートされていないリクエストを受信した場合、CEKにこのメッセージをレスポンスとして返す必要があります。ユーザーがデバイスでサポートされていないアクションをリクエストした場合、CEKはすぐユーザーに有効な範囲外のリクエストであることを伝えます。ただし、`SetMode`のような動作は、Clova Home Extensionが[SetModeRequest](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetModeRequest)メッセージを受信して`mode`フィールドの値を確認するまで、範囲内の動作かどうかを判断できません。もし、Clova Home Extensionがメッセージを受信し、サポートされていないモードである場合、エラーレスポンスを返す必要があります。その際、`UnsupportedOperationError`メッセージをCEKに返します。

例えば、ユーザーのサーモスタット(`"THERMOSTAT"`タイプ)が`SetMode`動作をサポートし、スリープモード(`"sleep"`)、外出モード(`"away"`)をサポートしている場合を仮定します。その場合、ユーザーがそのデバイスに冷房モード(`"cool"`)を設定するようにリクエストすると、Clova Home Extensionは`UnsupportedOperationError`メッセージをCEKに返す必要があります。

### Payload fields

なし

### 備考
* エラーが発生した場合にも、エラーメッセージはリクエスト成功のHTTPレスポンス(200 OK)でCEKに返す必要があります。
* エラーメッセージの名前で状況を判断するため、`payload`は必要ありません。

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "e9a77ef6-748b-4f9b-aa3e-c14ece3fa726",
    "namespace": "ClovaHome",
    "name": "UnsupportedOperationError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### 次の項目も参照してください。
* [`NotSupportedInCurrentModeError`](#NotSupportedInCurrentModeError)

## ValueNotFoundError {#ValueNotFoundError}
デバイスが測定値やステータス値を測定したり、または保存したりすることができず、リクエストされた値を提供できない場合、CEKにこのメッセージをレスポンスとして返す必要があります。例えば、エアコンは、現在の温度などの値をデフォルトで提供する必要がありますが、欠陥や一時的な故障によって温度を測定できず、値を提供できないことがあります。このメッセージは、そのような状況で使用できます。

### Payload fields
なし

### 備考
* エラーが発生した場合にも、エラーメッセージはリクエスト成功のHTTPレスポンス(200 OK)でCEKに返す必要があります。
* エラーメッセージの名前で状況を判断するため、`payload`は必要ありません。

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "57109b11-ee04-45df-9dd2-c979bc8608ea",
    "namespace": "ClovaHome",
    "name": "ValueNotFoundError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### 次の項目も参照してください。

* [`ValueNotSupportedError`](#ValueNotSupportedError)
* [`ValueOutOfRangeError`](#ValueOutOfRangeError)

## ValueNotSupportedError {#ValueNotSupportedError}
デバイスでサポートされていない値を指定しようとするリクエストを受信した場合、CEKにこのメッセージをレスポンスとして返す必要があります。CEKはこのメッセージを受け取ると、あらかじめ用意されたエラーメッセージをクライアントに送信します。

### Payload fields

なし

### 備考
* エラーが発生した場合にも、エラーメッセージはリクエスト成功のHTTPレスポンス(200 OK)でCEKに返す必要があります。
* エラーメッセージの名前で状況を判断するため、`payload`は必要ありません。

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "9bfd7a41-2a4a-428a-b429-823cc6ae4813",
    "namespace": "ClovaHome",
    "name": "ValueNotSupportedError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### 次の項目も参照してください。

* [`ValueNotFoundError`](#ValueNotFoundError)
* [`ValueOutOfRangeError`](#ValueOutOfRangeError)

## ValueOutOfRangeError {#ValueOutOfRangeError}
デバイスが処理できる範囲外の値を設定しようとするリクエストを受信した場合、CEKにこのメッセージをレスポンスとして返す必要があります。例えば、エアコンが18から28までの設定温度の値をサポートしていて、ユーザーが16や30などの値を設定するようにリクエストした場合、このメッセージが返されます。`payload`にデバイスが処理できる最大値と最小値を含める必要があります。

### Payload fields

| フィールド名       | データ型    | フィールドの説明                     | 必須/選択 |
|---------------|---------|-----------------------------|:---------:|
| `maximumValue` | number | デバイスでサポートされる最大値 | 必須    |
| `minimumValue` | number | デバイスでサポートされる最小値 | 必須    |

### 備考
* エラーが発生した場合にも、エラーメッセージはリクエスト成功のHTTPレスポンス(200 OK)でCEKに返す必要があります。
* `payload`に入力された値は、ユーザーに設定値の有効範囲を案内する際に使用できます。

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "fef949b7-eb94-4bda-a417-2cfb604194c3",
    "namespace": "ClovaHome",
    "name": "ValueOutOfRangeError",
    "payloadVersion": "1.0"
  },
  "payload": {
    "minimumValue":18.0,
    "maximumValue":30.0
  }
}
```
{% endraw %}

### 次の項目も参照してください。

* [`ValueNotFoundError`](#ValueNotFoundError)
* [`ValueNotSupportedError`](#ValueNotSupportedError)
