## Custom Extensionでレスポンスを返す {#ReturnCustomExtensionResponse}
[リクエストメッセージを処理](#HandleCustomExtensionRequest)したら、CEKに[レスポンスメッセージ](/CEK/References/CEK_API.md#CustomExtResponseMessage)を返す必要があります(HTTPレスポンス)。リクエストメッセージのタイプによって異なる内容を返すこともありますが、レスポンスメッセージの構造に大差はありません。以下は、LaunchRequestタイプのリクエスト(「ピザボットを起動して」というユーザーリクエスト)を処理した後、返したレスポンスメッセージです。

{% raw %}
```json
{
  "version": "0.1.0",
  "sessionAttributes": {},
  "response": {
    "outputSpeech": {
      "type": "SimpleSpeech",
      "values": {
          "type": "PlainText",
          "lang": "ja",
          "value": "こんにちは。ピザボットです。どういったご用件ですか"
      }
    },
    "card": {},
    "directives": [],
    "shouldEndSession": false
  }
}
```
{% endraw %}

各フィールドは、次のような意味を持ちます。

* `version`：使用しているCustom Extensionのメッセージフォーマットのバージョンです。現在のバージョンはv0.1.0です。
* `response.outputSpeech`：ユーザーが英語で「Hi, nice to meet you」の文章を話すように設定します。
* `response.card`：クライアントの画面に表示するデータがありません。コンテンツテンプレート形式のデータで、クライアントの画面に表示するコンテンツをこのフィールドで渡すことができます。
* `response.shouldEndSession`：セッションを終了せず、引き続きユーザーの入力を受け付けます。このフィールドの値がtrueの場合、[`SessionEndedRequest`](#HandleSessionEndedRequest)リクエストを受け取る前に、Extensionからセッションを終了できます。

<div class="note">
  <p><strong>メモ</strong></p>
  <p><code>sessionAttributes</code>フィールドは、拡張のために予約されたフィールドです。<code>response.directives</code>フィールドはExtensionがCEKに渡すディレクティブです。<code>response.directives</code>フィールドで使用するディレクティブは、今後APIを提供する予定です。</p>
</div>

以下のように、場合によって複数の文章を出力するようにレスポンスメッセージを作成することができます。あるいは、インターネット上のオーディオファイルを再生するようにレスポンスメッセージを作成することもできます。

{% raw %}
```json
{
  "version": "0.1.0",
  "sessionAttributes": {},
  "response": {
    "outputSpeech": {
      "type": "SpeechList",
      "values": [
        {
          "type": "PlainText",
          "lang": "ja",
          "value": "歌を歌ってみます。"
        },
        {
          "type": "URL",
          "lang": "" ,
          "value": "https://tts.com/song.mp3"
        }
      ]
    },
    "card": {},
    "directives": [],
    "shouldEndSession": true
  }
}
```
{% endraw %}

各`response.outputSpeech`フィールドの説明は、次のとおりです。

* `response.outputSpeech.type`：複文タイプ(SpeechList)の音声情報です。
* `response.outputSpeech.values[0]`：テキスト形式の音声情報です。日本語で「歌を歌ってみます」と発話するように設定されています。
* `response.outputSpeech.values[1]`：URL形式の音声情報です。`value`フィールドに入力されたURLのファイルを再生するように設定されています。

<div class="note">
  <p><strong>メモ</strong></p>
  <p>単文や複文タイプの音声情報の他にも、画面を持たないデバイスのように、詳しい内容をGUIで表現できないクライアントのために、複合タイプ(SpeechSet)の音声情報もサポートしています。詳細については、Custom Extensionのメッセージフォーマットの<a href="/CEK/References/CEK_API.md#CustomExtResponseMessage">レスポンスメッセージ</a>を参照してください。</p>
</div>

音声出力だけでなく、クライアントデバイスの画面やクライアントアプリの画面にデータを出力する必要がある場合、次のように`response.card`フィールドにコンテンツテンプレートに合わせて表示するコンテンツを設定します。

{% raw %}
```json
{
  "version": "0.1.0",
  "sessionAttributes": {},
  "response": {
    "outputSpeech": {
      "type": "SimpleSpeech",
      "values": {
          "type": "PlainText",
          "lang": "ja",
          "value": "リオネル・メッシの写真です"
      }
    },
    "card": {
      "type": "ImageText",
      "imageUrl": {
        "type": "url",
        "value": ""
      },
      "mainText": {
        "type": "string",
        "value": "リオネル・メッシ"
      },
      "referenceText": {
        "type": "string",
        "value": "検索結果"
      },
      "referenceUrl": {
        "type": "url",
        "value": "https://m.search.naver.com/search.naver?where=m&sm=mob_lic&query=%eb%a6%ac%ec%98%a4%eb%84%ac+%eb%a9%94%ec%8b%9c+%ec%86%8c%ec%86%8d%ed%8c%80"
      },
      "subTextList": [
        {
          "type": "string",
          "value": "FCバルセロナ"
        }
      ],
      "thumbImageType": {
        "type": "string",
        "value": "人物"
      },
      "thumbImageUrl": {
        "type": "url",
        "value": "http://sstatic.naver.net/people/3/201607071816066361.jpg"
      }
    },
    "directives": [],
    "shouldEndSession": true
  }
}
```
{% endraw %}
