# Settings

Settingsインターフェースは、Clovaとクライアントの間で、クライアントの設定を更新したり、同期するときに使用する名前欄です。Settingsでは、次のイベントとディレクティブを提供します。

| メッセージ         | タイプ  | 説明                                 |
|------------------|-----------|-------------------------------------------|
| [`ExpectReport`](#ExpectReport) | ディレクティブ | クライアントに対して、現在の設定をレポートするように指示します。クライアントはこのディレクティブを受信すると、[`Settings.Report`](#Report)イベントをCICに送信する必要があります。 |
| [`Report`](#Report)             | イベント     | クライアントが現在の設定をCICにレポートします。クライアントがCICから[`Settings.ExpectReport`](#ExpectReport)ディレクティブを受信した場合、`Settings.Report`イベントをCICに送信する必要があります。  |
| [`Update`](#Update)             | ディレクティブ | クライアントに対して、`payload`に指定されている値を設定値として適用するように指示します。  |

<div class="note">
  <p><strong>メモ</strong></p>
  <p>設定を更新したり、同期したりする流れは、<a href="#WorkFlow">仕組み</a>を参照してください。</p>
</div>

## 仕組み {#WorkFlow}

以下の状況で、Settingsを使って設定を更新したり、同期したりする必要があります。

* ユーザーがClovaアプリでクライアントデバイスの設定を照会するとき、**設定を同期する**必要があります。
* ユーザーがクライアントデバイスの**設定をClovaアプリで変更**したとき、それをデバイスの設定に反映する必要があります。
* ユーザーがクライアントデバイスで**直接に設定を変更**したとき、それをClovaアプリに反映する必要があります。

Settingsを使って設定を更新したり、同期したりする仕組みは、以下の通りです。

![](/CIC/Resources/Images/CIC_Settings_Work_Flow.png)

CICがClovaアプリからクライアントデバイスの**設定同期**のリクエストを受け取ると、 CICとクライアントデバイスは、以下の順序で処理を行います。

1. CICは、`Settings.ExpectReport`ディレクティブを該当するクライアントデバイスに送信します。
2. クライアントデバイスは、`Settings.Report`イベントで現在の設定をCICに送信する必要があります。
3. CICは受信した設定をClovaアプリに送信します。

ユーザーがクライアントデバイスの**設定をClovaアプリで変更**したとき、CICはそのデバイスの設定変更に対するリクエストを受信します。そのとき、CICとクライアントデバイスは、以下の順序で処理を行います。

1. CICは、`Settings.Update`ディレクティブを該当するクライアントデバイスに送信します。
2. クライアントデバイスは、`Settings.Report`イベントで変更された設定をCICに送信する必要があります。
3. CICは受信した設定をClovaアプリに送信します。

もし、ユーザーがクライアントデバイスで**直接に設定を変更**したときは、以下の順序でClovaアプリの設定を更新します。

1. クライアントデバイスは、`Settings.Report`イベントで変更された設定をCICに送信する必要があります。
2. CICは受信した設定をClovaアプリに送信します。

## ExpectReportディレクティブ {#ExpectReport}
クライアントに対して、現在の設定をレポートするように指示します。クライアントはこのディレクティブを受信すると、[`Settings.Report`](#Report)イベントをCICに送信する必要があります。

### Payload fields

なし

### 備考

* このディレクティブはイベントに対する応答ではなく、[ダウンチャネル](/CIC/Guides/Interact_with_CIC.md#CreateConnection)で送信されます。

### Message example

```json
{
  "directive": {
    "header": {
      "namespace": "Settings",
      "name": "ExpectReport",
      "messageId": "29745c13-0d70-408e-a4cc-946afba67524"
    },
    "payload": {}
  }
}
```

### 次の項目も参照してください。
* [`Settings.Report`](#Report)

## Reportイベント {#Report}
クライアントが現在の設定をCICにレポートします。クライアントがCICから[`Settings.ExpectReport`](#ExpectReport)ディレクティブを受信した場合、`Settings.Report`イベントをCICに送信する必要があります。

### Context fields

{% include "/CIC/References/CICInterface/Context_Objects_List.md" %}

### Payload fields

| フィールド名       | データ型    | 説明                     | 必須/任意 |
|---------------|---------|-----------------------------|:---------:|
| `configuration` | object | 事前に定義されたクライアント設定を持つオブジェクト。このオブジェクトのサブフィールドは、すべてstringのデータ型になります。<div class="note"><p><strong>メモ</strong></p><p>クライアント設定の事前定義については、提携担当者までお問い合わせください。</p></div> |    |

### Message example
{% raw %}
```json
{
  "context": [
    {{Alerts.AlertsState}},
    {{AudioPlayer.PlayerState}},
    {{Device.DeviceState}},
    {{Device.Display}},
    {{Clova.Location}},
    {{Clova.SavedPlace}},
    {{Speaker.VolumeState}},
    {{SpeechSynthesizer.SpeechState}}
  ],
  "event": {
    "header": {
      "namespace": "Settings",
      "name": "Report",
      "messageId": "b120c3e0-e6b9-4a3d-96de-71539e5f6214"
    },
    "payload": {
      "configuration": {
        "key1": "value1",
        "key2": "value2",
        ...
      }
    }
  }
}
```
{% endraw %}

### 次の項目も参照してください。
* [`Settings.ExpectReport`](#ExpectReport)

## Updateディレクティブ {#Update}
クライアントに対して、`payload`に指定されている値を設定値として適用するように指示します。

### Payload fields

| フィールド名       | データ型    | 説明                     | 任意 |
|---------------|---------|-----------------------------|:---------:|
| `configuration` | object | 事前に定義されたクライアント設定を持つオブジェクト。このオブジェクトのサブフィールドは、すべてstringのデータ型になります。<div class="note"><p><strong>メモ</strong></p><p>クライアント設定の事前定義については、提携担当者までお問い合わせください。</p></div> |    |

### 備考

* このディレクティブはイベントに対する応答ではなく、[ダウンチャネル](/CIC/Guides/Interact_with_CIC.md#CreateConnection)で送信されます。

### Message example

{% raw %}

```json
{
  "directive": {
    "header": {
      "namespace": "Settings",
      "name": "Update",
      "messageId": "29745c13-0d70-408e-a4cc-946afba67524"
    },
    "payload": {
      "configuration": {
        "key1": "value1",
        "key2": "value2",
        ...
      }
    }
  }
}
```

{% endraw %}

### 次の項目も参照してください。
* [`Settings.Report`](#Report)
