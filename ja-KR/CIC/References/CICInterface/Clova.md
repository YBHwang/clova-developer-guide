# Clova

Clovaインターフェースは、CICからユーザーリクエストの認識結果をクライアントに送信する際に使用する名前空間です。ユーザーのリクエストを[`SpeechRecognizer.Recognize`](/CIC/References/CICInterface/SpeechRecognizer.md#Recognize)イベントで受信すると、Clovaはその意味を解析します。CICは認識された結果に応じて、以下のディレクティブをクライアントに送信します。クライアントは、以下のディレクティブを処理して、Clovaの機能をユーザーに提供する必要があります。

| メッセージ         | タイプ  | 説明                                   |
{% if book.DocMeta.TargetReaderType == "Internal" or book.DocMeta.TargetReaderType == "Uplus" %}|------------------|-----------|---------------------------------------------|
| [`ExpectLogin`](#ExpectLogin)                    | ディレクティブ | クライアントに対して、ユーザーの{{ book.ServiceEnv.OrientedService }}アカウント認証(ログイン)を行うように指示します。|{% else %}|------------------|-----------|---------------------------------------------|{% endif %}
| [`FinishExtension`](#FinishExtension)            | ディレクティブ | クライアントに対して、特定のExtensionを終了するように指示します。             |
| [`HandleDelegatedEvent`](#HandleDelegatedEvent)  | ディレクティブ | クライアントに対して、Clovaアプリから[委任されたユーザーのリクエストを処理する](/CIC/Guides/Implement_Client_Features.md#HandleDelegation)ように指示します。   |
| [`Hello`](#Hello)                                | ディレクティブ | クライアントに対して、ダウンチャネルが確立したことを通知します。       |
| [`Help`](#Help)                                  | ディレクティブ | クライアントに対して、あらかじめ用意されたヘルプを提供するように指示します。       |
| [`LaunchURI`](#LaunchURI)                        | ディレクティブ | クライアントに、URIで表現されるウェブサイトまたはアプリを開いたり、起動するように指示します。                         |
| [`ProcessDelegatedEvent`](#ProcessDelegatedEvent) | イベント    | クライアントが、[委任されたユーザーのリクエスト](/CIC/Guides/Implement_Client_Features.md#HandleDelegation)の結果をCICから受信するために使用します。  |
| [`RenderTemplate`](#RenderTemplate)              | ディレクティブ | クライアントに対して、テンプレートを表示するように指示します。                     |
| [`RenderText`](#RenderText)                      | ディレクティブ | クライアントに対して、テキストを表示するように指示します。                     |
| [`StartExtension`](#StartExtension)              | ディレクティブ | クライアントに対して、特定のExtensionを起動するように指示します。            |

{% if book.DocMeta.TargetReaderType == "Internal" or book.DocMeta.TargetReaderType == "Uplus" %}
## ExpectLoginディレクティブ {#ExpectLogin}

クライアントに対して、ユーザーの{{ book.ServiceEnv.OrientedService }}アカウント認証(ログイン)を行うように指示します。クライアントが[ゲストモード](/CIC/References/Clova_Auth_API.md#GuestMode)で動作しているときに、{{ book.ServiceEnv.OrientedService }}アカウント認証を必要とするサービスをユーザーに提供しようとする場合、CICはクライアントにこのディレクティブを送信します。

### Payload fields

なし

### 備考
ログインに成功したとき、前のリクエストの処理は継続されません。必要な場合、ユーザーから再度リクエストする必要があります。

### Message example

{% raw %}

```json
{
  "directive": {
    "header": {
      "messageId": "2ca2ec70-c39d-4741-8a34-8aedd3b24760",
      "namespace": "Clova",
      "name": "RequestLogin"
    },
    "payload": {}
  }
}
```

{% endraw %}

### 次の項目も参照してください。
* [Clovaアクセストークンを作成する](/CIC/Guides/Interact_with_CIC.md#CreateClovaAccessToken)
* [ゲストモード](/CIC/References/Clova_Auth_API.md#GuestMode)

{% endif %}

## FinishExtensionディレクティブ {#FinishExtension}

クライアントに対して、特定のExtensionを終了するように指示します。クライアントはFinishExtensionディレクティブを受信すると、それに対応するExtensionを終了する必要があります。

### Payload fields

| フィールド名       | データ型    | 説明                     | 任意 |
|---------------|---------|-----------------------------|:---------:|
| `extension`   | string  | 終了するExtensionの名前          | 常時     |

### Message example

{% raw %}

```json
{
  "directive": {
    "header": {
      "namespace": "Clova",
      "name": "FinishExtension",
      "messageId": "80855309-77b8-403f-bec5-b50f565d24a2",
      "dialogRequestId": "3db18cee-caac-4101-891f-b5f5c2e7fa9c"
    },
    "payload": {
      "extension": "SampleExtension"
    }
  }
}
```

{% endraw %}

### 次の項目も参照してください。
* [`Clova.StartExtension`](#StartExtension)

## HandleDelegatedEventディレクティブ {#HandleDelegatedEvent}

クライアントに対して、Clovaアプリから[委任されたユーザーのリクエストを処理する](/CIC/Guides/Implement_Client_Features.md#HandleDelegation)ように指示します。ユーザーはClovaアプリを使用する際、リクエストの処理結果をClovaアプリではなく、ユーザーが持っている別のクライアントデバイスで処理するように指定することができます。このディレクティブは、結果の処理を委任されたクライアントデバイスに送信されます。ディレクティブを受信したクライアントは、[`ProcessDelegatedEvent`](#ProcessDelegatedEvent)イベントをCICに送信して、ユーザーから委任されたリクエストの処理結果を受信する必要があります。

### Payload fields

| フィールド名       | データ型    | 説明                     | 任意 |
|---------------|---------|-----------------------------|:---------:|
| `delegationId` | string  | 委任されたリクエストのID。後で[`ProcessDelegatedEvent`](#ProcessDelegatedEvent)イベントを送信する際、`payload`に含まれる必要があります。         | 常時     |

### 備考

このディレクティブはイベントに対する応答ではなく、[ダウンチャネル](/CIC/Guides/Interact_with_CIC.md#CreateConnection)で送信されます。

### Message example

{% raw %}

```json
{
  "directive": {
    "header": {
      "messageId": "b17df741-2b5b-4db4-a608-85ecb1307b33",
      "namespace": "Clova",
      "name": "HandleDelegatedEvent"
    },
    "payload": {
      "delegationId": "99e86204-710a-4e94-b949-a763e78348a7"
    }
  }
}
```

{% endraw %}

### 次の項目も参照してください。
* [Clova.ProcessDelegatedEvent](#ProcessDelegatedEvent)
* [委任されたユーザーのリクエストを処理する](/CIC/Guides/Implement_Client_Features.md#HandleDelegation)

## Helloディレクティブ {#Hello}

クライアントに対して、ダウンチャネルが確立したことを通知します。クライアントは、このディレクティブでClovaサービスへ正常に[接続](/CIC/Guides/Interact_with_CIC.md#CreateConnection)できたかを確認できます。

### Payload fields

なし

### 備考
このディレクティブはダイアログID(`dialogRequestId`)を持ちません。

### Message example

{% raw %}

```json
{
  "directive": {
    "header": {
      "messageId": "2ca2ec70-c39d-4741-8a34-8aedd3b24760",
      "namespace": "Clova",
      "name": "Hello"
    },
    "payload": {}
  }
}
```

{% endraw %}

### 次の項目も参照してください。
* [CICに接続する](/CIC/Guides/Interact_with_CIC.md#ConnectToCIC)

## Helpディレクティブ {#Help}

クライアントに対して、ヘルプを提供するように指示します。ユーザーがヘルプをリクエストしたとき、このディレクティブを受信します。あらかじめ用意されたヘルプの音声を再生するか、ヘルプのUIを画面に表示する必要があります。

### Payload fields

なし

### Message example

{% raw %}

```json
{
  "directive": {
    "header": {
      "messageId": "2ca2ec70-c39d-4741-8a34-8aedd3b24760",
      "namespace": "Clova",
      "name": "Help"
    },
    "payload": {}
  }
}
```

{% endraw %}

### 次の項目も参照してください。
なし

## LaunchURIディレクティブ {#LaunchURI}

クライアントに、URIで表現されるウェブサイトまたはアプリを開いたり、起動するように指示します。このディレクティブを受信したクライアントは、`targets[].uri`フィールドを使用してウェブサイトまたはアプリを起動する必要があります。

### Payload fields

| フィールド名       | データ型    | 説明                     | 任意 |
|---------------|---------|-----------------------------|:---------:|
| `targets[]`              | object array | URIの情報を持つオブジェクト配列                       | 常時     |
| `targets[].description`  | string       | URIで表現される対象(アプリまたはウェブサイト)の説明           | 任意     |
| `targets[].iconImageUrl` | string       | URIで表現される対象のアイコン画像                 | 任意     |
| `targets[].marketUrl`    | string       | **URIで表現される対象がアプリの場合**、アプリストアのアドレス  | 任意     |
| `targets[].packageName`  | string       | **URIで表現される対象がアプリの場合**、アプリのパッケージ名  | 任意     |
| `targets[].title`        | string       | URIで表現される対象のタイトル                        |      |
| `targets[].uri`          | string       | 対象URIの情報                                  |      |

### 備考

* クライアントは、`targets[].uri`のURIから<a href="http://ogp.me/" target="_blank">Open Graph Protocol</a>のデータを利用してプレビューを表示できますが、一部のデータをすぐに表示するために、`targets[].iconImageUrl`、`targets[].title`、`targets[].description`などのフィールドを使用できます。
* **URIで表現される対象がアプリの場合**、`targets[].marketUrl`、`targets[].packageName`フィールドを使用できます。`targets[].marketUrl`は、アプリがインストールされていなく、対象のアプリを起動できない場合に使用されます。また、`targets[].packageName`は、`targets[].uri`でアプリを起動できない場合に参考できる付加情報です。
* クライアントは、`targets[]`フィールドの配列内のすべての対象を開いたり起動したりする必要があるわけではありません。配列の先頭の要素のURIで対象を開いたり起動したりするようにし、失敗した場合には次の要素情報で同じ動作を試す必要があります。配列構造は、対象を起動できない場合に備えて、候補群を一緒に渡すためのものです。

### Message example

```json
// App type example
{
  "directive": {
    "header": {
      "namespace": "Clova",
      "name": "LaunchURI",
      "messageId": "086ccadf-cd88-4cff-9706-cc4f0801c929",
      "dialogRequestId": "de20ea1a-ea39-4c2a-a033-73fa014b2fd5"
    },
    "payload": {
      "targets": [
        {
          "uri": "sampleapp2://main",
          "title": "Sample app2",
          "iconImageUrl": "https://example.com/sampleappicon.png",
          "marketUrl": "https://play.google.com/store/apps/details?id=com.example.sampleapp",
          "packageName": "com.example.sampleapp",
          "description": "Sample app2"
        },
        {
          "uri": "sampleapp://main",
          "title": "Sample app",
          "iconImageUrl": "https://example.com/sampleappicon.png",
          "marketUrl": "https://play.google.com/store/apps/details?id=com.example.sampleapp",
          "packageName": "com.example.sampleapp",
          "description": "Sample app"
        }
      ]
    }
  }
}

// Site type example
{
  "directive": {
    "header": {
      "namespace": "Clova",
      "name": "LaunchURI",
      "messageId": "fcb0919e-9847-46ec-90bc-ab0fe8216771",
      "dialogRequestId": "9ab7256a-6add-4b4a-a0b8-481f41d36a9d"
    },
    "payload": {
      "targets": [
        {
          "uri": "http://example.org",
          "title": "Example Domain"
        }
      ]
    }
  }
}
```

### 次の項目も参照してください。
なし

## ProcessDelegatedEventイベント {#ProcessDelegatedEvent}

クライアントが、[委任されたユーザーのリクエスト](/CIC/Guides/Implement_Client_Features.md#HandleDelegation)の結果をCICから受信するために使用します。このイベントをCICに送信する際、[`HandleDelegatedEvent`](#HandleDelegatedEvent)ディレクティブで受信した`delegationId`をこのメッセージの`payload`に含める必要があります。クライアントは、そのディレクティブに対する応答として、ユーザーがClovaアプリにリクエストしたことの処理結果を受信します。

### Context fields

{% include "/CIC/References/CICInterface/Context_Objects_List.md" %}

### Payload fields

| フィールド名       | データ型    | 説明                     | 必須/任意 |
|---------------|---------|-----------------------------|:---------:|
| `delegationId` | string  | 委任されたリクエストのID。[`HandleDelegatedEvent`](#HandleDelegatedEvent)ディレクティブで受信した`delegationId`をそのまま入力する必要があります。         |      |

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
      "namespace": "Clova",
      "name": "ProcessDelegatedEvent",
      "messageId": "b120c3e0-e6b9-4a3d-96de-71539e5f6214"
    },
    "payload": {
      "delegationId": "99e86204-710a-4e94-b949-a763e78348a7"
    }
  }
}
```
{% endraw %}

### 次の項目も参照してください。
* [`Clova.HandleDelegatedEvent`](#HandleDelegatedEvent)
* [`SpeechRecognizer.Recognize`](/CIC/References/CICInterface/SpeechRecognizer.md#Recognize)
* [委任されたユーザーのリクエストを処理する](/CIC/Guides/Implement_Client_Features.md#HandleDelegation)

## RenderTemplateディレクティブ {#RenderTemplate}

クライアントに対して、データをコンテンツテンプレートに基づいて表示するように指示します。ユーザーの音声から認識された結果のコンテンツが含まれます。

### Payload fields
`payload`は、[コンテンツテンプレート](/CIC/References/Content_Templates.md)の種類によって形式が異なります。現在、次のコンテンツテンプレートが提供されています。

* コンテンツのUIタイプごとのテンプレート
  * [CardList](/CIC/References/ContentTemplates/CardList.md)
  * [ImageList](/CIC/References/ContentTemplates/ImageList.md)
  * [ImageText](/CIC/References/ContentTemplates/ImageText.md)
  * [Popup](/CIC/References/ContentTemplates/Popup.md)
  * [Text](/CIC/References/ContentTemplates/Text.md)

* PIMSテンプレート
  * [ActionTimer](/CIC/References/ContentTemplates/ActionTimer.md)
  * [ActionTimerList](/CIC/References/ContentTemplates/ActionTimerList.md)
  * [Alarm](/CIC/References/ContentTemplates/Alarm.md)
  * [AlarmList](/CIC/References/ContentTemplates/AlarmList.md)
  * [Memo](/CIC/References/ContentTemplates/Memo.md)
  * [MemoList](/CIC/References/ContentTemplates/MemoList.md)
  * [Reminder](/CIC/References/ContentTemplates/Reminder.md)
  * [ReminderList](/CIC/References/ContentTemplates/ReminderList.md)
  * [Schedule](/CIC/References/ContentTemplates/Schedule.md)
  * [ScheduleList](/CIC/References/ContentTemplates/ScheduleList.md)
  * [Timer](/CIC/References/ContentTemplates/Timer.md)
  * [TimerList](/CIC/References/ContentTemplates/TimerList.md)

* 天気テンプレート
  * [Atmosphere](/CIC/References/ContentTemplates/Atmosphere.md)
  * [Humidity](/CIC/References/ContentTemplates/Humidity.md)
  * [TodayWeather](/CIC/References/ContentTemplates/TodayWeather.md)
  * [TomorrowWeather](/CIC/References/ContentTemplates/TomorrowWeather.md)
  * [WeeklyWeather](/CIC/References/ContentTemplates/WeeklyWeather.md)
  * [WindSpeed](/CIC/References/ContentTemplates/WindSpeed.md)

* 共通のフィールドおよび共有オブジェクト
  * [共通フィールド](/CIC/References/ContentTemplates/Common_Fields.md)
  * [共有オブジェクト](/CIC/References/ContentTemplates/Shared_Objects.md)

### Message example

{% raw %}

```json
{
  "directive": {
    "header": {
      "namespace": "Clova",
      "name": "RenderTemplate",
      "messageId": "c7b9882e-d3bf-45b6-b6f4-2fc47d04e60e",
      "dialogRequestId": "ca10e609-1d24-4418-bc2a-21b70c5ea1a7"
    },
    "payload": {
        {{TemplateFormat}}
    }
  }
}
```

{% endraw %}

### 次の項目も参照してください。
* [`Clova.RenderText`](#RenderText)
* [コンテンツテンプレート](/CIC/References/Content_Templates.md)

## RenderTextディレクティブ {#RenderText}

クライアントに対して、テキストメッセージを表示するように指示します。ユーザーに表示するテキストが含まれます。

### Payload fields

| フィールド名       | データ型    | 説明                     | 任意 |
|---------------|---------|-----------------------------|:---------:|
| `text`          | string  | ユーザーに表示するテキスト        | 常時     |

### Message example

{% raw %}

```json
{
  "directive": {
    "header": {
      "namespace": "Clova",
      "name": "RenderText",
      "messageId": "6f9d8b54-21dc-4811-8e14-b9b60717cbd4",
      "dialogRequestId": "5690395e-8c0d-4123-9d3f-937eaa9285dd"
    },
    "payload": {
      "text": "楽しい曲を再生します。"
    }
  }
}
```

{% endraw %}

### 次の項目も参照してください。
* [`Clova.RenderTemplate`](#RenderTemplate)

## StartExtensionディレクティブ {#StartExtension}

クライアントに対して、特定のExtensionを起動するように指示します。クライアントは、StartExtensionディレクティブを受信すると、それに対応するExtensionを開始する必要があります。

### Payload fields

| フィールド名       | データ型    | 説明                     | 任意 |
|---------------|---------|-----------------------------|:---------:|
| `extension`   | string  | 開始するExtensionの名前          | 常時     |

### Message example

{% raw %}

```json
{
  "directive": {
    "header": {
      "namespace": "Clova",
      "name": "StartExtension",
      "messageId": "103b8847-9109-42a5-8d3f-fc370a243d6f",
      "dialogRequestId": "8b509a36-9081-4783-b1cd-58d406205956"
    },
    "payload": {
      "extension": "SampleExtension"
    }
  }
}
```

{% endraw %}

### 次の項目も参照してください。
* [`Clova.FinishExtension`](#FinishExtension)
