## オーディオコンテンツを提供する {#ProvideAudioContent}

{% if book.TargetCountryCode == "KR" %}
Custom Extensionで、ユーザーに音楽やポッドキャストなどのオーディオコンテンツを提供することができます。そのためには、[Custom Extensionメッセージ](/CEK/References/CEK_API.md#CustomExtMessage)の仕様のうち、[CIC API](/CIC/References/CIC_API.md)を使用する必要があります。ユーザーにオーディオコンテンツを提供するには、次の内容をExtensionに実装する必要があります。**特に、必須の実装項目は必ず実装される必要があります。**

* 必須
  * [オーディオコンテンツの再生を指示する](#DirectClientToPlayAudio)
  * [オーディオコンテンツの再生をコントロールする](#ControlAudioPlayback)
  * [オーディオコンテンツのメタデータを提供する](#ProvidingMetaDataForDisplay)

* 任意
  * [再生状態の変更および進行状況を収集する](#CollectPlaybackStatusAndProgress)
  * [セキュリティのためにオーディオコンテンツのURLを更新する](#UpdateAudioURLForSecurity)
  * [再生コントロールの動作方法を変更する](#CustomizePlaybackControl)
{% elif book.TargetCountryCode == "JP" %}
Custom Extensionで、ユーザーに音楽やポッドキャストなどのオーディオコンテンツを提供することができます。そのためには、[Custom Extensionメッセージ](/CEK/References/CEK_API.md#CustomExtMessage)の[`EventRequest`](/CEK/References/CEK_API.md#CustomExtEventRequest)タイプのリクエストメッセージと[レスポンスメッセージ](/CEK/References/CEK_API.md#CustomExtResponseMessage)の仕様のうち、[オーディオコンテンツ再生関連のCIC API](/CEK/References/CEK_API.md#CICAPIforAudioPlayback)を使用する必要があります。ユーザーにオーディオコンテンツを提供するには、次の内容をExtensionに実装する必要があります。

* 必須
  * [オーディオコンテンツの再生を指示する](#DirectClientToPlayAudio)
  * [オーディオコンテンツの再生をコントロールする](#ControlAudioPlayback)

* 任意
  * [再生状態の変更および進行状況を収集する](#CollectPlaybackStatusAndProgress)
  * [セキュリティのためにオーディオコンテンツのURLを更新する](#UpdateAudioURLForSecurity)
  * [再生コントロールの動作方法を変更する](#CustomizePlaybackControl)
  * [オーディオコンテンツのメタデータを提供する](#ProvidingMetaDataForDisplay)
{% endif %}

### オーディオコンテンツの再生を指示する {#DirectClientToPlayAudio}

ユーザーから音楽や、または音楽のような形でオーディオコンテンツの再生をリクエストされたとき、そのオーディオコンテンツの情報を渡す必要があります。ユーザーからのオーディオコンテンツ再生のリクエストが[`IntentRequest`](/CEK/References/CEK_API.md#CustomExtIntentRequest)タイプのリクエストでCustom Extensionに渡され、Custom Extensionはその`IntentRequest`タイプのリクエストメッセージに対する[レスポンスメッセージ](/CEK/References/CEK_API.md#CustomExtResponseMessage)を返す必要があります。そのとき、そのメッセージにクライアントがオーディオコンテンツを再生するように指示する{{ "[`AudioPlayer.Play`](/CIC/References/CICInterface/AudioPlayer.md#Play)" if book.TargetCountryCode == "KR" else "[`AudioPlayer.Play`](/CEK/References/CEK_API.md#Play)" }}ディレクティブを含めます。

<div class="danger">
  <p><strong>注意</strong></p>
  <p>再生指示に関連する内容は、オーディオコンテンツを提供するCustom Extensionの主要な機能で、必須の実装項目です。</p>
</div>

以下は、`AudioPlayer.Play`ディレクティブをCustom Extensionのレスポンスメッセージに含めたサンプルです。
```json
{
  "version": "0.1.0",
  "sessionAttributes": {},
  "response": {
    "card": {},
    "directives": [
      {
        "header": {
          "namespace": "AudioPlayer",
          "name": "Play"
        },
        "payload": {
          "audioItem": {
            "audioItemId": "90b77646-93ab-444f-acd9-60f9f278ca38",
            "episodeId": 22346122,
            "stream": {
              "beginAtInMilliseconds": 0,
              "episodeId": 22346122,
              "playType": "NONE",
              "podcastId": 12548,
              "progressReport": {
                "progressReportDelayInMilliseconds": null,
                "progressReportIntervalInMilliseconds": 60000,
                "progressReportPositionInMilliseconds": null
              },
              "url": "https://streaming.example.com/1212334548/2231122",
              "urlPlayable": true
            },
            "type": "podcast"
          },
          "source": {
            "name": "Potbbang",
            "logoUrl": "https://img.musicproviderdomain.net/logo_180125.png"
          },
          "playBehavior": "REPLACE_ALL"
        }
      }
    ],
    "outputSpeech": {},
    "shouldEndSession": true
  }
}
```

<div class="note">
  <p><strong>メモ</strong></p>
  <p><a href="/CEK/Guides/Build_Custom_Extension.html#ReturnCustomExtensionResponse">レスポンスメッセージで返す</a>とき、<code>response.outputSpeech</code>フィールドを指定することもできます。例えば、ユーザーに対して、「リクエストしたオーディオコンテンツを再生します」という音声出力(TTS)を先に再生してから、オーディオコンテンツの再生を開始することができます。</p>
</div>

### オーディオコンテンツの再生をコントロールする {#ControlAudioPlayback}
クライアントがオーディオを再生しているときに、ユーザーが「前」「次」などのように再生のコントロールに関連する発話を発した場合、ユーザーのリクエストは`IntentRequest`タイプのリクエストメッセージでCustom Extensionに渡されます。現在、CEKはCustom Extensionで再生のコントロールに関連するユーザーのインテントを、以下のような[ビルトインインテント](/Design/Design_Guideline_For_Extension.md#BuiltinIntent)として渡すようになっています。

* `Clova.NextIntent`
* `Clova.PauseIntent`
* `Clova.PreviousIntent`
* `Clova.ResumeIntent`
* `Clova.StopIntent`

<div class="danger">
  <p><strong>注意</strong></p>
  <p>再生のコントロールに関連する内容は、必須の実装項目です。特に、<code>Clova.PauseIntent</code>と<code>Clova.StopIntent</code>ビルトインインテントに対応するアクションが実装されていないと、ユーザーにとって、サービスを「使いにくい」と感じる原因となります。</p>
</div>

ユーザーが「ちょっと止めて」「再生を再開して」「停止して」などのように発話した場合、Custom Extensionは再生の一時停止、再生再開、再生停止のリクエストに対応する必要があります。その際、クライアントはそれぞれのリクエストに対し、`Clova.PauseIntent`、`Clova.ResumeIntent`、`Clova.StopIntent`ビルトインインテントを`IntentRequest`タイプのリクエストメッセージで受け取ります。Custom Extensionは、それに対応して、それぞれ以下のディレクティブを[レスポンスメッセージ](/CEK/References/CEK_API.md#CustomExtResponseMessage)でCEKに送信する必要があります。

{% if book.TargetCountryCode == "KR" %}
* [`PlaybackController.Pause`](/CIC/References/CICInterface/PlaybackController.md#Pause)ディレクティブ：クライアントに、再生中のオーディオストリームを一時停止するように指示する
* [`PlaybackController.Resume`](/CIC/References/CICInterface/PlaybackController.md#Resume)ディレクティブ：クライアントに、オーディオストリームの再生を再開するように指示する
* [`PlaybackController.Stop`](/CIC/References/CICInterface/PlaybackController.md#Stop)ディレクティブ：クライアントに、オーディオストリームの再生を停止するように指示する
{% elif book.TargetCountryCode == "JP" %}
* [`PlaybackController.Pause`](/CEK/References/CEK_API.md#Pause)ディレクティブ：クライアントに、再生中のオーディオストリームを一時停止するように指示する
* [`PlaybackController.Resume`](/CEK/References/CEK_API.md#Resume)ディレクティブ：クライアントに、オーディオストリームの再生を再開するように指示する
* [`PlaybackController.Stop`](/CEK/References/CEK_API.md#Stop)ディレクティブ：クライアントに、オーディオストリームの再生を停止するように指示する
{% endif %}

以下は、`PlaybackController.Pause`ディレクティブをCustom Extensionのレスポンスメッセージに含めたサンプルです。
```json
{
  "version": "0.1.0",
  "sessionAttributes": {},
  "response": {
    "card": {},
    "directives": [
      {
        "directive": {
          "header": {
            "namespace": "PlaybackController",
            "name": "Pause"
          },
          "payload": {}
        }
      }
    ],
    "outputSpeech": {},
    "shouldEndSession": true
  }
}
```

ユーザーが「前」「次」に該当する発話をして、`Clova.NextIntent`または`Clova.PreviousIntent`ビルトインインテントを`IntentReqeust`タイプのリクエストメッセージで受け取ると、[レスポンスメッセージ](/CEK/References/CEK_API.md#CustomExtResponseMessage)でユーザーが前に聞いた、または次に聞くはずの[オーディオコンテンツを再生するように指示する(`AudioPlayer.Play`)](#DirectClientToPlayAudio)必要があります。

<div class="note">
  <p><strong>メモ</strong></p>
  <p>前または次に該当するオーディオコンテンツがなかったり、有効ではない場合、「再生する前または次の曲がありません」などの音声出力を<a href="/CEK/Guides/Build_Custom_Extension.html#ReturnCustomExtensionResponse">レスポンスメッセージで返す</a>必要があります。</p>
</div>

### オーディオコンテンツのメタデータを提供する {#ProvidingMetaDataForDisplay}

[オーディオコンテンツの再生を指示する](#DirectClientToPlayAudio){{ "[`AudioPlayer.Play`](/CIC/References/CICInterface/AudioPlayer.md#Play)" if book.TargetCountryCode == "KR" else "[`AudioPlayer.Play`](/CEK/References/CEK_API.md#Play)" }}ディレクティブには、タイトル、アルバム、歌詞などの情報は含まれていません。Custom Extensionは、クライアントからリクエストされると、そのようなメタデータを提供する必要があります。

クライアントは、コンテンツの再生メタデータを取得するために、{{ "[`TeamplteRuntime.ReqeusetPlayerInfo`](/CIC/References/CICInterface/TeamplteRuntime.md#ReqeusetPlayerInfo)" if book.TargetCountryCode == "KR" else "[`TeamplteRuntime.ReqeusetPlayerInfo`](/CEK/References/CEK_API.md#ReqeusetPlayerInfo)" }}イベントをClovaに送信します。そのとき、イベントの内容は[`EventRequest`](/CEK/References/CEK_API.md#CustomExtEventRequest)タイプのリクエストメッセージで、以下のように送信されます。ちなみに、以下のサンプルは`eJyr5lIqSSyITy4tKs4vUrJSUE`トークンを持つコンテンツを基準に、次の10曲のメタデータをリクエストしたことを表しています。

```json
{
  "context": {
    ...
  },
  "request": {
    "type": "EventRequest",
    "requestId": "e5464288-50ff-4e99-928d-4a301e083d41",
    "timestamp": "2017-09-05T05:41:21Z",
    "event": {
      "namespace": "TemplateRuntime",
      "name": "RequestPlayerInfo",
      "payload": {
        "token": "eJyr5lIqSSyITy4tKs4vUrJSUE",
        "range": {
          "after": 10
        }
      }
    }
  },
  "session": {
      "new": true,
      "sessionAttributes": {},
      "sessionId": "69b20cc1-9166-41f3-a2dd-85b70f8e0bf5"
  },
  "version": "1.0"
}
```

Custom Extensionは、レスポンスメッセージを使って、クライアントからリクエストされたコンテンツのメタデータを返す必要があります。{{ "[`TeamplteRuntime.RenderPlayerInfo`](/CIC/References/CICInterface/TeamplteRuntime.md#RenderPlayerInfo)" if book.TargetCountryCode == "KR" else "[`TeamplteRuntime.RenderPlayerInfo`](/CEK/References/CEK_API.md#RenderPlayerInfo)" }}ディレクティブをレスポンスメッセージに含める必要があります。

```json
{
  "version": "0.1.0",
  "sessionAttributes": {},
  "response": {
    "card": {},
    "directives": [
      {
        "header": {
          "namespace": "TeamplteRuntime",
          "name": "RenderPlayerInfo"
        },
        "payload": {
          "controls": [
            {
              "enabled": true,
              "name": "PLAY_PAUSE",
              "selected": false,
              "type": "BUTTON"
            },
            {
              "enabled": true,
              "name": "NEXT",
              "selected": false,
              "type": "BUTTON"
            },
            {
              "enabled": true,
              "name": "PREVIOUS",
              "selected": false,
              "type": "BUTTON"
            }
          ],
          "displayType": "list",
          "playableItems": [
            {
              "artImageUrl": "http://musicmeta.musicproviderdomain.com/example/album/662058.jpg",
              "controls": [
                {
                  "enabled": true,
                  "name": "LIKE_DISLIKE",
                  "selected": false,
                  "type": "BUTTON"
                }
              ],
              "headerText": "Classic",
              "lyrics": [
                {
                  "data": null,
                  "format": "PLAIN",
                  "url": null
                }
              ],
              "isLive": false,
              "showAdultIcon": false,
              "titleSubText1": "Alice Sara Ott, Symphonie Orchester Des Bayerischen Rundfunks, Esa-Pekka Salonen",
              "titleSubText2": "Wonderland - Edvard Grieg : Piano Concerto, Lyric Pieces",
              "titleText": "Grieg : Piano Concerto In A Minor, Op.16 - 3. Allegro moderato molto e marcato (Live)",
              "token": "eJyr5lIqSSyITy4tKs4vUrJSUE"
            },
            {
              "artImageUrl": "http://musicmeta.musicproviderdomain.com/example/album/202646.jpg",
              "controls": [
                {
                  "enabled": true,
                  "name": "LIKE_DISLIKE",
                  "selected": false,
                  "type": "BUTTON"
                }
              ],
              "headerText": "Classic",
              "lyrics": [
                {
                  "data": null,
                  "format": "PLAIN",
                  "url": null
                }
              ],
              "isLive": true,
              "showAdultIcon": false,
              "titleSubText1": "Berliner Philharmoniker, Herbert Von Karajan",
              "titleSubText2": "Mendelssohn : Violin Concerto; A Midsummer Night`s Dream",
              "titleText": "Symphony No.4 In A Op.90 'Italian' - III.Con Moto Moderato",
              "token": "eJyr5lIqSSyITy4tKs4vUrJSUEo2"
            },
            ...
          ],
          "provider": {
            "logoUrl": "https://img.musicproviderdomain.net/logo_180125.png",
            "name": "SampleMusicProvider",
            "smallLogoUrl": "https://img.musicproviderdomain.net/smallLogo_180125.png"
          }
        }
      }
    ],
    "outputSpeech": {},
    "shouldEndSession": true
  }
}
```

### 再生状態の変更および進行状況のレポートを収集する {#CollectPlaybackStatusAndProgress}

{% if book.TargetCountryCode == "KR" %}
[`AudioPlayer.Play`](/CIC/References/CICInterface/AudioPlayer.md#Play)ディレクティブでオーディオを再生するクライアントは、再生が開始、一時停止、再開、終了するタイミングで、[`AudioPlayer.PlayStarted`](/CIC/References/CICInterface/AudioPlayer.md#PlayStarted)、[`AudioPlayer.PlayPaused`](/CIC/References/CICInterface/AudioPlayer.md#PlayPaused)、[`AudioPlayer.PlayResumed`](/CIC/References/CICInterface/AudioPlayer.md#PlayResumed)、[`AudioPlayer.PlayStopped`](/CIC/References/CICInterface/AudioPlayer.md#PlayStopped)、[`AudioPlayer.PlayFinished`](/CIC/References/CICInterface/AudioPlayer.md#PlayFinished)のようなイベントをClovaに送信します。そのとき、Clovaはそのイベントの内容を[`EventReqeust`](/CEK/References/CEK_API.md#CustomExtEventRequest)タイプのリクエストメッセージでCustom Extensionに送信します。

また、クライアントは[オーディオコンテンツを再生するように指示(`AudioPlayer.Play`)](#DirectClientToPlayAudio)を受けた後、`AudioPlayer.Play`ディレクティブの`progressReport`フィールドに定義されている設定に従って再生の進行状況をレポートします。その内容もまた、[`EventReqeust`](/CEK/References/CEK_API.md#CustomExtEventRequest)タイプのリクエストメッセージでCustom Extensionに送信されます。クライアントは、進行状況をレポートするために、以下のイベントを送信します。

* [`AudioPlayer.ProgressReportDelayPassed`](/CIC/References/CICInterface/AudioPlayer.md#ProgressReportDelayPassed)イベント：再生が開始してから特定の時間が経過した後、再生の進行状況をレポートする
* [`AudioPlayer.ProgressReportPositionPassed`](/CIC/References/CICInterface/AudioPlayer.md#ProgressReportPositionPassed)イベント：オーディオコンテンツの特定の位置(オフセット)を再生するときに、進行状況をレポートする
* [`AudioPlayer.ProgressReportIntervalPassed`](/CIC/References/CICInterface/AudioPlayer.md#ProgressReportIntervalPassed)イベント：再生中の場合、特定の間隔で繰り返し進行状況をレポートする
{% elif book.TargetCountryCode == "JP" %}
[`AudioPlayer.Play`](/CEK/References/CEK_API.md#Play)ディレクティブでオーディオを再生するクライアントは、再生が開始、一時停止、再開、終了するタイミングで、[`AudioPlayer.PlayStarted`](/CEK/References/CEK_API.md#PlayStarted)、[`AudioPlayer.PlayPaused`](/CEK/References/CEK_API.md#PlayPaused)、[`AudioPlayer.PlayResumed`](/CEK/References/CEK_API.md#PlayResumed)、[`AudioPlayer.PlayStopped`](/CEK/References/CEK_API.md#PlayStopped)、[`AudioPlayer.PlayFinished`](/CEK/References/CEK_API.md#PlayFinished)のようなイベントをClovaに送信します。そのとき、Clovaはそのイベントの内容を[`EventReqeust`](/CEK/References/CEK_API.md#CustomExtEventRequest)タイプのリクエストメッセージでCustom Extensionに送信します。

また、クライアントは[オーディオコンテンツを再生するように指示(`AudioPlayer.Play`)](#DirectClientToPlayAudio)を受けた後、`AudioPlayer.Play`ディレクティブの`progressReport`フィールドに定義されている設定に従って再生の進行状況をレポートします。その内容もまた、[`EventReqeust`](/CEK/References/CEK_API.md#CustomExtEventRequest)タイプのリクエストメッセージでCustom Extensionに送信されます。クライアントは、進行状況をレポートするために、以下のイベントを送信します。

* [`AudioPlayer.ProgressReportDelayPassed`](/CEK/References/CEK_API.md#ProgressReportDelayPassed)イベント：再生が開始してから特定の時間が経過した後、再生の進行状況をレポートする
* [`AudioPlayer.ProgressReportPositionPassed`](/CEK/References/CEK_API.md#ProgressReportPositionPassed)イベント：オーディオコンテンツの特定の位置(オフセット)を再生するときに、進行状況をレポートする
* [`AudioPlayer.ProgressReportIntervalPassed`](/CEK/References/CEK_API.md#ProgressReportIntervalPassed)イベント：再生中の場合、特定の間隔で繰り返し進行状況をレポートする
{% endif %}

以下は、`RequestEvent`タイプのリクエストメッセージで送信されたレポートのサンプルです。
```json

{
  "context": {
    "AudioPlayer": {
      "offsetInMilliseconds": 60000,
      "playerActivity": "STOPPED",
      "stream": {
        "token": "TR-NM-17413540",
        "url": "http://music.serviceprovider.net/content?id=17413540",
        "urlPlayable": true
      },
      "totalInmillisecodns": 300000
    },
    "System": "{ ...}"
  },
  "request": {
    "type": "EventRequest",
    "requestId": "e5464288-50ff-4e99-928d-4a301e083d41",
    "timestamp": "2017-09-05T05:41:21Z",
    "event": {
      "namespace": "AudioPlayer",
      "name": "PlayStopped",
      "payload": {}
    }
  },
  "session": {
    "new": true,
    "sessionAttributes": {},
    "sessionId": "69b20cc1-9166-41f3-a2dd-85b70f8e0bf5"
  },
  "version": "1.0"
}
```

上記の`EventRequest`タイプのリクエストメッセージは、クライアントが全部で5分のオーディオコンテンツで、1分になるタイミングで再生を中断したことをレポートしています。Custom Extensionは、このようにして、クライアントの再生状態の変化を追跡することができます。例えば、`AudioPlayer.PlayStopped`と`AudioPlayer.PlayFinished`イベントが含まれた`EventRequest`タイプのリクエストメッセージを収集して、オーディオを最後まで聞いたり、または最後まで聞かないユーザーを区別し、それを統計データにすることができます。

また、`AudioPlayer.ProgressReportIntervalPassed`イベントが含まれた`EventRequest`タイプのリクエストメッセージを使って、完全に正確なわけではないけれど、ユーザーがオーディオコンテンツをどの位置まで聞いたかを把握することができます。ユーザーが次に同じオーディオコンテンツの再生をリクエストする場合、そのデータに基づいて、最後に聞いた位置から再生することができます。

<div class="danger">
  <p><strong>注意</strong></p>
  <p>再生の進行状況のレポートに関する<code>EventRequest</code>タイプのリクエストメッセージのうち、<code>AudioPlayer.PlayFinished</code>イベントが含まれたメッセージを受け取った場合、Custom Extensionは、再生完了に対するクライアントの次のアクションをレスポンスメッセージで返す必要があります。そのアクションとして、次の<a href="#DirectClientToPlayAudio">オーディオコンテンツの再生を指示する</a>こともできますし、再生停止などの<a href="#ControlAudioPlayback">再生コントロール</a>を指示することもできます。</p>
</div>

{% if book.TargetCountryCode == "KR" %}
ちなみに、このセクションで扱っている`AudioPlayer`名前欄イベントには、`AudioPlayer.PlaybackState`コンテキストが含まれます。その情報もまた、`EventRequest`タイプのリクエストメッセージが送信されるときに含まれるので、Custom Extensionは含まれた[`AudioPlayer.PlaybackState`](/CIC/References/Context_Objects.html#PlaybackState)コンテキストからオーディオコンテンツのID、再生状態、オーディオコンテンツの再生位置などを把握できます。
{% elif book.TargetCountryCode == "JP" %}
ちなみに、このセクションで扱っている`AudioPlayer`名前欄イベントには、`AudioPlayer.PlaybackState`コンテキストが含まれます。その情報もまた、`EventRequest`タイプのリクエストメッセージが送信されるときに含まれるので、Custom Extensionは含まれた`AudioPlayer.PlaybackState`コンテキストからオーディオコンテンツのID、再生状態、オーディオコンテンツの再生位置などを把握できます。
{% endif %}

以下は、`AudioPlayer.PlaybackState`コンテキストが送信されたサンプルです。
```json
{
  "offsetInMilliseconds": 5077,
  "playerActivity": "PLAYING",
  "stream": {
    "token": "TR-NM-17413540",
    "url": "http://music.serviceprovider.net/content?id=17413540",
    "urlPlayable": true
  },
  "totalInMilliseconds": 195265
}
```

### セキュリティのためにオーディオコンテンツのURLを更新する {#UpdateAudioURLForSecurity}

Custom Extensionがクライアントに[オーディオコンテンツの再生を指示する](#DirectClientToPlayAudio)とき、[レスポンスメッセージ](/CEK/References/CEK_API.md#CustomExtResponseMessage)に{{ "[`AudioPlayer.Play`](/CIC/References/CICInterface/AudioPlayer.md#Play)" if book.TargetCountryCode == "KR" else "[`AudioPlayer.Play`](/CEK/References/CEK_API.md#Play)" }}ディレクティブを含める必要があります。そのとき、`AudioPlayer.Play`ディレクティブの`audioItem.stream.url`フィールドにオーディオコンテンツを再生できるURLを設定して送信します。

ただし、サービスの提供元によっては、セキュリティ上の問題により、永久に有効なURLを含めることができないことがあります。例えば、そのURLがさらされた場合、コンテンツを盗み取るための攻撃が発生する可能性がある場合などが考えられます。そのため、大抵の場合、比較的短い有効期限を持つインスタンスURLを使用します。また、クライアントが`AudioPlayer.Play`ディレクティブを受信していても、より優先順位の高いタスクや、先に開始したタスク、またはネットワークの状況によって、オーディオコンテンツの再生開始が遅延することがあります。その場合、URLの有効期限が切れ、オーディオコンテンツを正常に再生できない可能性があります。

そのため、Clovaはクライアントがオーディオコンテンツを再生できるURLを、再生の直前に取得する方法を提供しています。最初に、以下のように`AudioPlayer.Play`ディレクティブの`urlPlayable`フィールドを`false`に指定し、`url`フィールドにURLではない、他の形式の値を設定します。

```json
{
  "audioItem": {
    "audioItemId": "9CPWU-c82302b2-ea29-4f6c-ba6e-20fd268d8c3b-c1570067",
    "title": "Symphony No.4 In A Op.90 'Italian' - III.Con Moto Moderato",
    "artist": "Unknown",
    "stream": {
      "beginAtInMilliseconds": 0,
      "progressReport": {
        "progressReportDelayInMilliseconds": null,
        "progressReportIntervalInMilliseconds": null,
        "progressReportPositionInMilliseconds": 60000
      },
      "token": "TR-NM-17413540",
      "url": "clova:TR-NM-17413540",
      "urlPlayable": false
    }
  },
  "playBehavior": "REPLACE_ALL"
}
```

後にクライアントが`AudioPlayer.Play`ディレクティブを処理するとき、`urlPlayable`フィールドが`false`に指定されていると、有効なオーディオコンテンツのURLを取得するために{{ "[`AudioPlayer.StreamRequested`](/CIC/References/CICInterface/AudioPlayer.md#StreamRequested)" if book.TargetCountryCode == "KR" else "[`AudioPlayer.StreamRequested`](/CEK/References/CEK_API.md#StreamRequested)" }}イベントをClovaに送信します。そのとき、イベントの内容は[`EventRequest`](/CEK/References/CEK_API.md#CustomExtEventRequest)タイプのリクエストメッセージで、以下のように送信されます。

```json
{
  "context": {
    ...
  },
  "request": {
    "type": "EventRequest",
    "requestId": "e5464288-50ff-4e99-928d-4a301e083d41",
    "timestamp": "2017-09-05T05:41:21Z",
    "event": {
      "namespace": "AudioPlayer",
      "name": "StreamRequested",
      "payload": {
        "audioItemId": "9CPWU-c82302b2-ea29-4f6c-ba6e-20fd268d8c3b-c1570067",
        "title": "Symphony No.4 In A Op.90 'Italian' - III.Con Moto Moderato",
        "artist": "Unknown",
        "stream": {
          "beginAtInMilliseconds": 0,
          "progressReport": {
            "progressReportDelayInMilliseconds": null,
            "progressReportIntervalInMilliseconds": null,
            "progressReportPositionInMilliseconds": 60000
          },
          "token": "TR-NM-17413540",
          "url": "clova:TR-NM-17413540",
          "urlPlayable": false
        }
      }
    }
  },
  "session": {
    "new": true,
    "sessionAttributes": {},
    "sessionId": "69b20cc1-9166-41f3-a2dd-85b70f8e0bf5"
  },
  "version": "1.0"
}
```

Custom Extensionは、そのタイミングで、再生できるオーディオコンテンツのURLを[レスポンスメッセージ](/CEK/References/CEK_API.md#CustomExtResponseMessage)で返す必要があります。そのために、`AudioPlayer.StreamDeliver`ディレクティブをレスポンスメッセージに含める必要があります。クライアントは、以下のような`AudioPlayer.StreamDeliver`ディレクティブのボディを用いて、`AudioPlayer.Play`ディレクティブを引き続き処理することができます。

```json
{
  "version": "0.1.0",
  "sessionAttributes": {},
  "response": {
    "card": {},
    "directives": [
      {
        "header": {
          "namespace": "AudioPlayer",
          "name": "StreamDeliver"
        },
        "payload": {
          "audioItemId": "5313c879-25bb-461c-93fc-f85d95edf2a0",
          "stream": {
            "token": "b767313e-6790-4c28-ac18-5d9f8e432248",
            "url": "https://sample.musicservice.net/b767313e.mp3"
          }
        }
      }
    ],
    "outputSpeech": {},
    "shouldEndSession": true
  }
}
```

### 再生コントロールの動作方法を変更する {#CustomizePlaybackControl}

オーディオコンテンツを提供するサービスやコンテンツの特性によって、再生の一時停止、再生再開、再生停止などの[再生コントロール](ControlAudioPlayback)の動作を少し違った形で実装する必要があることがあります。例えば、リアルタイムのストリーミングコンテンツの場合、一時停止機能を適用できない可能性があります。その場合、ユーザーから`Clova.PauseIntent`[ビルトインインテント](/Design/Design_Guideline_For_Extension.md#BuiltinIntent)のリクエストがあっても、そのリクエストを処理できないと応答したり、または`Clova.StopIntent`のような対応を処理したりすることができます。`Clova.StopIntent`のような対応を処理する場合、[レスポンスメッセージ](/CEK/References/CEK_API.md#CustomExtResponseMessage)に{{ "[`PlaybackController.Pause`](/CIC/References/CICInterface/PlaybackController.md#Pause)" if book.TargetCountryCode == "KR" else "[`PlaybackController.Pause`](/CEK/References/CEK_API.md#Pause)" }}ディレクティブの代わりに{{ "[`PlaybackController.Stop`](/CIC/References/CICInterface/PlaybackController.md#Stop)" if book.TargetCountryCode == "KR" else "[`PlaybackController.Stop`](/CEK/References/CEK_API.md#Stop)" }}ディレクティブを応答として返すように実装することができます。

<div class="note">
  <p><strong>メモ</strong></p>
  <p>ユーザーの混乱を防ぐために、リアルタイムのストリーミングコンテンツなどの特殊な場合に限って再生コントロールの動作方法を変更し、なるべくデフォルト実装をすることを推奨します。</p>
</div>
