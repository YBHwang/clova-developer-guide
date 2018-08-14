## Clova.SavedPlace {#SavedPlace}
`Clova.SavedPlace`は、クライアントにあらかじめ保存されている位置情報をCICにレポートするときに使用されるメッセージ形式です。

### Object structure
{% raw %}
```json
{
  "header": {
    "namespace": "Clova",
    "name": "SavedPlace"
  },
  "payload": {
    "places": [
      {
        "latitude": {{string}},
        "longitude": {{string}},
        "refreshedAt": {{string}},
        "name": {{string}}
      }
    ]
  }
}
```
{% endraw %}

### Payload fields

| フィールド名       | データ型    | 説明                     | 必須/任意 |
|---------------|---------|-----------------------------|:---------:|
| `places[]`             | object array | あらかじめ保存された位置情報を持つオブジェクト配列                                          | 必須 |
| `places[].latitude`    | string       | 緯度                                                                          | 必須 |
| `places[].longitude`   | string       | 経度                                                                          | 必須 |
| `places[].name`        | string       | 保存された位置の名称。次の値を使用できます。<ul><li><code>"会社"</code></li><li><code>"家"</code></li></ul>       | 必須 |
| `places[].refreshedAt` | string       | 位置を保存した時刻(UTC基準、<a href="https://en.wikipedia.org/wiki/ISO_8601" target="_blank">ISO 8601</a>形式)  | 必須 |


### Object example
{% raw %}
```json
{
  "header": {
    "namespace": "Clova",
    "name": "SavedPlace"
  },
  "payload": {
    "places": [
      {
        "latitude": "37.3594915",
        "longitude": "127.1032242",
        "refreshedAt": "2017-04-06T13:34:15.074361+08:28",
        "name": "家"
      },
      {
        "latitude": "36.3542315",
        "longitude": "125.1345242",
        "refreshedAt": "2017-03-12T10:21:33.089723+08:28",
        "name": "会社"
      }
    ]
  }
}
```
{% endraw %}

### 次の項目も参照してください。
* [`SpeechRecognizer.Recognize`](/CIC/References/CICInterface/SpeechRecognizer.md#Recognize)