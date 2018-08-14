## 오디오 콘텐츠 제공하기 {#ProvideAudioContent}

{% if book.TargetCountryCode == "KR" %}
Custom extension을 통해 사용자에게 음악이나 podcast와 같은 오디오 콘텐츠를 제공할 수 있습니다. 이를 위해 [Custom extension 메시지](/CEK/References/CEK_API.md#CustomExtMessage)의 명세에서 오디오 콘텐츠 재생 관련 [CIC API](/CIC/References/CIC_API.md)를 활용해야 합니다. 오디오 콘텐츠를 사용자에게 제공하려면 다음에 해당하는 내용을 extension에 구현해야 합니다. **특히, 필수 구현 항목은 반드시 구현해야 합니다.**

* 필수 구현
  * [오디오 콘텐츠 재생 지시](#DirectClientToPlayAudio)
  * [오디오 콘텐츠 재생 제어](#ControlAudioPlayback)
  * [오디오 콘텐츠의 메타 정보 제공](#ProvidingMetaDataForDisplay)

* 선택 구현
  * [재생 상태 변경 및 경과 보고 수집](#CollectPlaybackStatusAndProgress)
  * [보안을 위한 오디오 콘텐츠 URL 갱신](#UpdateAudioURLForSecurity)
  * [재생 제어의 동작 방식 변경](#CustomizePlaybackControl)

<div class="note">
  <p><strong>Note!</strong></p>
  <p>오디오 콘텐츠를 재생하는 custom extension을 구현하려면 <a href="/DevConsole/Guides/CEK/Register_Extension.md">Clova developer console에 extension을 등록</a>할 때 <a href="/DevConsole/Guides/CEK/Register_Extension.md#InputExtensionInfo">기본 정보</a>로 {{ book.DevConsole.cek_audioplayer }} 항목을 <strong>네</strong>로 선택해야 합니다.</p>
</div>
{% elif book.TargetCountryCode == "JP" %}
Custom extension을 통해 사용자에게 음악이나 podcast와 같은 오디오 콘텐츠를 제공할 수 있습니다. 이를 위해 [Custom extension 메시지](/CEK/References/CEK_API.md#CustomExtMessage)의 [`EventRequest`](/CEK/References/CEK_API.md#CustomExtEventRequest) 타입의 요청 메시지와 [응답 메시지](/CEK/References/CEK_API.md#CustomExtResponseMessage) 명세에서 [오디오 콘텐츠 재생 관련 CIC API](/CEK/References/CEK_API.md#CICAPIforAudioPlayback)를 활용해야 합니다. 오디오 콘텐츠를 사용자에게 제공하려면 다음에 해당 하는 내용을 extension에 구현해야 합니다.

* 필수 구현
  * [오디오 콘텐츠 재생 지시](#DirectClientToPlayAudio)
  * [오디오 콘텐츠 재생 제어](#ControlAudioPlayback)
  * [오디오 콘텐츠의 메타 정보 제공](#ProvidingMetaDataForDisplay)

* 선택 구현
  * [재생 상태 변경 및 경과 보고 수집](#CollectPlaybackStatusAndProgress)
  * [보안을 위한 오디오 콘텐츠 URL 갱신](#UpdateAudioURLForSecurity)
  * [재생 제어의 동작 방식 변경](#CustomizePlaybackControl)

<div class="note">
  <p><strong>Note!</strong></p>
  <p>오디오 콘텐츠를 재생하는 custom extension을 구현하려면 <a href="/DevConsole/Guides/CEK/Register_Extension.md">Clova developer console에 extension을 등록</a>할 때 <a href="/DevConsole/Guides/CEK/Register_Extension.md#InputExtensionInfo">기본 정보</a>로 {{ book.DevConsole.cek_audioplayer }} 항목을 <strong>네</strong>로 선택해야 합니다.</p>
</div>
{% endif %}

### 오디오 콘텐츠 재생 지시 {#DirectClientToPlayAudio}

사용자가 음악이나 음악과 같은 방식으로 음원을 재생하도록 요청하면 해당 오디오 콘텐츠를 클라이언트에게 전달해야 합니다. 사용자의 음원 재생 요청이  [`IntentRequest`](/CEK/References/CEK_API.md#CustomExtIntentRequest) 타입의 요청 메시지로 custom extension에게 전달될 것이며, custom extension은 해당 `IntentRequest` 타입의 요청 메시지에 대한 [응답 메시지](/CEK/References/CEK_API.md#CustomExtResponseMessage)를 보내야 합니다. 이때, 이 메시지에 클라이언트가 오디오 콘텐츠를 재생하도록 지시하는 {{ "[`AudioPlayer.Play`](/CIC/References/CICInterface/AudioPlayer.md#Play)" if book.TargetCountryCode == "KR" else "[`AudioPlayer.Play`](/CEK/References/CEK_API.md#Play)" }} 지시 메시지를 포함시키면 됩니다.

<div class="note">
  <p><strong>Note!</strong></p>
  <p>제공하려는 오디오 콘텐츠는 <a href="/Design/Design_Guideline_For_Client_Hardware.md#SupportedAudioCompressionFormat">플랫폼이 지원하는 오디오 압축 포맷</a>이어야 합니다.</p>
</div>

<div class="danger">
  <p><strong>Caution!</strong></p>
  <p>재생 지시와 관련된 내용은 오디오 콘텐츠를 제공하는 custom extension의 메인 기능이며, 필수 구현 항목입니다.</p>
</div>

다음은 `AudioPlayer.Play` 지시 메시지를 custom extension의 응답 메시지에 포함한 예입니다.
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
  <p><strong>Note!</strong></p>
  <p><a href="/CEK/Guides/Build_Custom_Extension.md#ReturnCustomExtensionResponse">응답 메시지로 반환</a>할 때 <code>response.outputSpeech</code> 필드도 함께 지정할 수 있습니다. 예를 들면 "요청하신 오디오를 들려드릴게요" 라는 음성 출력(TTS)을 먼저 사용자에게 들려준 후 오디오의 재생을 시작할 수 있습니다.</p>
</div>

### 오디오 콘텐츠 재생 제어 {#ControlAudioPlayback}
클라이언트가 오디오를 재생 중일 때 사용자가 "이전", "다음" 등과 같이 재생 제어와 관련된 발화를 하면 사용자의 요청이 `IntentRequest` 타입의 요청 메시지 형태로 custom extension에 전달될 수 있습니다. 현재 CEK는 custom extension으로 재생 제어와 관련된 사용자의 의도를 다음과 같은 [built-in intent](/Design/Design_Guideline_For_Extension.md#BuiltinIntent)로 전달하고 있습니다.

* `Clova.NextIntent`
* `Clova.PauseIntent`
* `Clova.PreviousIntent`
* `Clova.ResumeIntent`
* `Clova.StopIntent`

<div class="danger">
  <p><strong>Caution!</strong></p>
  <p>재생 제어와 관련된 내용은 필수 구현 항목입니다. 특히, <code>Clova.PauseIntent</code>와 <code>Clova.StopIntent</code> built-in intent에 대응하는 동작을 구현하지 않으면, 사용자에게 심각한 불편을 줄 수 있습니다.</p>
</div>

사용자가 "잠깐 멈춰", "다시 재생해", "중지 해줘"와 같이 발화하면, custom extension은 재생 일시 정지, 재생 재개, 재생 중지 요청에 대응해야 합니다. 이때, 클라이언트는 각각의 요청에 대해 `Clova.PauseIntent`, `Clova.ResumeIntent`, `Clova.StopIntent` built-in intent를 `IntentRequest` 타입 요청 메시지로 받게 됩니다. Custom extension은 이에 대응하여 각각 다음과 같은 지시 메시지를 [응답 메시지](/CEK/References/CEK_API.md#CustomExtResponseMessage)로 CEK에게 전달해야 합니다.

{% if book.TargetCountryCode == "KR" %}
* [`PlaybackController.Pause`](/CIC/References/CICInterface/PlaybackController.md#Pause) 지시 메시지: 클라이언트에게 재생 중인 오디오 스트림을 일시 정지하도록 지시
* [`PlaybackController.Resume`](/CIC/References/CICInterface/PlaybackController.md#Resume) 지시 메시지: 클라이언트에게 오디오 스트림 재생을 재개하도록 지시
* [`PlaybackController.Stop`](/CIC/References/CICInterface/PlaybackController.md#Stop) 지시 메시지: 클라이언트에게 오디오 스트림 재생을 중지하도록 지시
{% elif book.TargetCountryCode == "JP" %}
* [`PlaybackController.Pause`](/CEK/References/CEK_API.md#Pause) 지시 메시지: 클라이언트에게 재생 중인 오디오 스트림을 일시 정지하도록 지시
* [`PlaybackController.Resume`](/CEK/References/CEK_API.md##Resume) 지시 메시지: 클라이언트에게 오디오 스트림 재생을 재개하도록 지시
* [`PlaybackController.Stop`](/CEK/References/CEK_API.md##Stop) 지시 메시지: 클라이언트에게 오디오 스트림 재생을 중지하도록 지시
{% endif %}

다음은 `PlaybackController.Pause` 지시 메시지를 custom extension의 응답 메시지에 포함한 예입니다.
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

사용자가 "이전", "다음"에 해당하는 발화를 하여 `Clova.NextIntent`나 `Clova.PreviousIntent` built-in intent를 `IntentReqeust` 타입 요청 메시지로 받게 되면, [응답 메시지](/CEK/References/CEK_API.md#CustomExtResponseMessage)로 사용자가 이전 혹은 다음에 들어야 하는 [오디오 콘텐츠를 재생하도록 지시(`AudioPlayer.Play`)](#DirectClientToPlayAudio)하면 됩니다.

<div class="note">
  <p><strong>Note!</strong></p>
  <p>만약, 이전이나 다음에 해당하는 오디오 콘텐츠가 없거나 유효하지 않으면 "재생할 수 있는 이전 또는 다음 곡이 없습니다."와 같은 음성 출력을 <a href="/CEK/Guides/Build_Custom_Extension.md#ReturnCustomExtensionResponse">응답 메시지로 반환</a>하면 됩니다.</p>
</div>

### 오디오 콘텐츠의 메타 정보 제공 {#ProvidingMetaDataForDisplay}

[오디오 콘텐츠의 재생을 지시](#DirectClientToPlayAudio)하는 {{ "[`AudioPlayer.Play`](/CIC/References/CICInterface/AudioPlayer.md#Play)" if book.TargetCountryCode == "KR" else "[`AudioPlayer.Play`](/CEK/References/CEK_API.md#Play)" }} 지시 메시지에는 제목, 앨범, 가수, 가사 등과 같은 정보는 포함되어 있지 않습니다. Custom extension은 클라이언트가 요청할 때 이런 메타 정보를 제공해야 합니다.

클라이언트는 콘텐츠에 대한 재생 메타 정보를 얻기 위해 {{ "[`TemplateRuntime.ReqeusetPlayerInfo`](/CIC/References/CICInterface/TemplateRuntime.md#ReqeusetPlayerInfo)" if book.TargetCountryCode == "KR" else "[`TemplateRuntime.ReqeusetPlayerInfo`](/CEK/References/CEK_API.md#ReqeusetPlayerInfo)" }} 이벤트 메시지를 Clova에게 전송합니다. 이때, 이벤트 메시지의 내용이 [`EventRequest`](/CEK/References/CEK_API.md#CustomExtEventRequest) 타입의 요청 메시지로 다음과 같이 전달됩니다. 참고로 아래 예는 `eJyr5lIqSSyITy4tKs4vUrJSUE` 토큰을 가지는 콘텐츠를 기준으로 다음 10 곡에 대한 메타 정보를 요청한 것을 의미합니다.

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

Custom extension은 응답 메시지를 통해 클라이언트가 요청한 콘텐츠의 메타 정보를 전송해야 합니다. {{ "[`TemplateRuntime.RenderPlayerInfo`](/CIC/References/CICInterface/TemplateRuntime.md#RenderPlayerInfo)" if book.TargetCountryCode == "KR" else "[`TemplateRuntime.RenderPlayerInfo`](/CEK/References/CEK_API.md#RenderPlayerInfo)" }} 지시 메시지를 응답 메시지에 포함시켜야 합니다.

```json
{
  "version": "0.1.0",
  "sessionAttributes": {},
  "response": {
    "card": {},
    "directives": [
      {
        "header": {
          "namespace": "TemplateRuntime",
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
              "titleText": "Symphony No.4 In A Op.90 'Italian' - III. Con Moto Moderato",
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

### 재생 상태 변경 및 경과 보고 수집 {#CollectPlaybackStatusAndProgress}

{% if book.TargetCountryCode == "KR" %}
[`AudioPlayer.Play`](/CIC/References/CICInterface/AudioPlayer.md#Play) 지시 메시지에 의해 오디오를 재생하는 클라이언트는 재생의 시작, 일시 정지, 재개, 중지, 종료 시점에 [`AudioPlayer.PlayStarted`](/CIC/References/CICInterface/AudioPlayer.md#PlayStarted), [`AudioPlayer.PlayPaused`](/CIC/References/CICInterface/AudioPlayer.md#PlayPaused), [`AudioPlayer.PlayResumed`](/CIC/References/CICInterface/AudioPlayer.md#PlayResumed), [`AudioPlayer.PlayStopped`](/CIC/References/CICInterface/AudioPlayer.md#PlayStopped), [`AudioPlayer.PlayFinished`](/CIC/References/CICInterface/AudioPlayer.md#PlayFinished)와 같은 이벤트 메시지를 Clova로 전송합니다. 이때 Clova는 이 이벤트 메시지의 내용을 [`EventReqeust`](/CEK/References/CEK_API.md#CustomExtEventRequest) 타입 요청 메시지로 custom extension에 전송합니다.

뿐만 아니라 클라이언트는 [오디오 콘텐츠를 재생하도록 지시(`AudioPlayer.Play`)](#DirectClientToPlayAudio) 받은 후 `AudioPlayer.Play` 지시 메시지의 `progressReport` 필드에 정의한 설정에 따라 재생 경과 보고를 하게 됩니다. 이 또한 [`EventReqeust`](/CEK/References/CEK_API.md#CustomExtEventRequest) 타입 요청 메시지로 custom extension에 전송됩니다. 클라이언트는 다음과 같은 경과 보고용 이벤트 메시지를 전송합니다.

* [`AudioPlayer.ProgressReportDelayPassed`](/CIC/References/CICInterface/AudioPlayer.md#ProgressReportDelayPassed) 이벤트 메시지: 재생 시작 후 특정 시간이 지난 후 재새 경과 보고
* [`AudioPlayer.ProgressReportPositionPassed`](/CIC/References/CICInterface/AudioPlayer.md#ProgressReportPositionPassed) 이벤트 메시지: 오디오 콘텐츠의 특정 위치(offset)를 재생할 때 경과 보고
* [`AudioPlayer.ProgressReportIntervalPassed`](/CIC/References/CICInterface/AudioPlayer.md#ProgressReportIntervalPassed) 이벤트 메시지: 재생 중인 상황에서 특정 주기로 반복하여 경과 보고
{% elif book.TargetCountryCode == "JP" %}
[`AudioPlayer.Play`](/CEK/References/CEK_API.md#Play) 지시 메시지에 의해 오디오를 재생하는 클라이언트는 재생의 시작, 일시 정지, 재개, 중지, 종료 시점에 [`AudioPlayer.PlayStarted`](/CEK/References/CEK_API.md#PlayStarted), [`AudioPlayer.PlayPaused`](/CEK/References/CEK_API.md#PlayPaused), [`AudioPlayer.PlayResumed`](/CEK/References/CEK_API.md#PlayResumed), [`AudioPlayer.PlayStopped`](/CEK/References/CEK_API.md#PlayStopped), [`AudioPlayer.PlayFinished`](/CEK/References/CEK_API.md#PlayFinished)와 같은 이벤트 메시지를 Clova로 전송합니다. 이때 Clova는 이 이벤트 메시지의 내용을 [`EventReqeust`](/CEK/References/CEK_API.md#CustomExtEventRequest) 타입 요청 메시지로 custom extension에 전송합니다.

뿐만 아니라 클라이언트는 [오디오 콘텐츠를 재생하도록 지시(`AudioPlayer.Play`)](#DirectClientToPlayAudio) 받은 후 `AudioPlayer.Play` 지시 메시지의 `progressReport` 필드에 정의한 설정에 따라 재생 경과 보고를 하게 됩니다. 이 또한 [`EventReqeust`](/CEK/References/CEK_API.md#CustomExtEventRequest) 타입 요청 메시지로 custom extension에 전송됩니다. 클라이언트는 다음과 같은 경과 보고용 이벤트 메시지를 전송합니다.

* [`AudioPlayer.ProgressReportDelayPassed`](/CEK/References/CEK_API.md#ProgressReportDelayPassed) 이벤트 메시지: 재생 시작 후 특정 시간이 지난 후 재새 경과 보고
* [`AudioPlayer.ProgressReportPositionPassed`](/CEK/References/CEK_API.md#ProgressReportPositionPassed) 이벤트 메시지: 오디오 콘텐츠의 특정 위치(offset)를 재생할 때 경과 보고
* [`AudioPlayer.ProgressReportIntervalPassed`](/CEK/References/CEK_API.md#ProgressReportIntervalPassed) 이벤트 메시지: 재생 중인 상황에서 특정 주기로 반복하여 경과 보고
{% endif %}

다음은 `EventRequest` 타입 요청 메시지를 통해 전달된 보고의 예입니다.
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
    "System": "{ ... }"
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

위 `EventRequest` 타입 요청 메시지는 클라이언트가 총 5분짜리 오디오 콘텐츠에서 1분이되는 시점에 재생을 중지한 것을 보고하고 있습니다. 이와 같이 custom extension은 클라이언트의 재생 상태 변화를 추적할 수 있습니다. 예를 들면, `AudioPlayer.PlayStopped`와 `AudioPlayer.PlayFinished` 이벤트 메시지 정보가 포함된 `EventRequest` 타입 요청 메시지를 수집하여 오디오를 끝까지 듣거나 듣지 않는 사용자를 구분하고 이를 통계 데이터로 만들 수 있습니다.

또, `AudioPlayer.ProgressReportIntervalPassed` 이벤트 메시지가 포함된 `EventRequest` 타입 요청 메시지를 이용하여 완전히 정확한 것은 아니지만 사용자가 오디오 콘텐츠를 어디까지 들었는지 파악할 수 있습니다. 만약, 사용자가 다음 번에 같은 오디오 콘텐츠에 대한 재생을 요청하면 이 데이터를 기반으로 마지막으로 들었던 위치부터 재생할 수 있습니다.

<div class="danger">
  <p><strong>Caution!</strong></p>
  <p>재생 상태 보고와 관련된 <code>EventRequest</code> 타입 요청 메시지 중 <code>AudioPlayer.PlayFinished</code> 이벤트 메시지 정보가 포함된 메시지를 받으면 custom extension은 재생 완료에 대한 클라이언트의 다음 동작을 응답 메시지로 전달해야 합니다. 이와 관련된 동작으로 다음 <a href="#DirectClientToPlayAudio">오디오 콘텐츠 재생을 지시</a>할 수도 있고 재생 중지와 같은 <a href="#ControlAudioPlayback">재생 제어</a>를 지시할 수도 있습니다.</p>
</div>

{% if book.TargetCountryCode == "KR" %}
참고로 이 절에서 언급한 `AudioPlayer` 네임스페이스 이벤트 메시지에는 `AudioPlayer.PlaybackState` 문맥 정보(context)가 첨부됩니다. 이 정보 역시 `EventRequest` 타입 요청 메시지가 전송될 때 함께 첨부되므로, custom extension은 첨부된 [`AudioPlayer.PlaybackState`](/CIC/References/Context_Objects.md#PlaybackState) 문맥 정보로부터 오디오 콘텐츠의 ID, 재생 상태, 오디오 콘텐츠의 재생 위치 등을 파악할 수 있습니다.
{% elif book.TargetCountryCode == "JP" %}
참고로 이 절에서 언급한 `AudioPlayer` 네임스페이스 이벤트 메시지에는 `AudioPlayer.PlaybackState` 문맥 정보(context)가 첨부됩니다. 이 정보 역시 `EventRequest` 타입 요청 메시지가 전송될 때 함께 첨부되므로, custom extension은 첨부된 `AudioPlayer.PlaybackState` 문맥 정보로부터 오디오 콘텐츠의 ID, 재생 상태, 오디오 콘텐츠의 재생 위치 등을 파악할 수 있습니다.
{% endif %}

다음은 `AudioPlayer.PlaybackState` 문맥 정보가 전달된 예입니다.
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

### 보안을 위한 오디오 콘텐츠 URL 갱신 {#UpdateAudioURLForSecurity}

Custom extension이 클라이언트에게 [오디오 콘텐츠 재생을 지시](#DirectClientToPlayAudio)할 때 [응답 메시지](/CEK/References/CEK_API.md#CustomExtResponseMessage)에 {{ "[`AudioPlayer.Play`](/CIC/References/CICInterface/AudioPlayer.md#Play)" if book.TargetCountryCode == "KR" else "[`AudioPlayer.Play`](/CEK/References/CEK_API.md#Play)" }} 지시 메시지를 포함시켜야 합니다. 이때, `AudioPlayer.Play` 지시 메시지의 `audioItem.stream.url` 필드에 오디오 콘텐츠를 재생시킬 수 있는 URL을 입력하여 전달하게 됩니다.

다만, 서비스 제공자에 따라 보안 이슈로 영구적으로 유효한 URL을 첨부하기 어려울 수 있습니다. 예를 들면, 이 URL이 노출된다면 콘텐츠를 획득하기 위한 공격이 발생할 수도 있을 것입니다. 따라서 짧은 만료 기간을 가진 인스턴스 URL을 많이 사용는 편입니다. 또한, 클라이언트가 `AudioPlayer.Play` 지시 메시지를 받았더라도 그보다 우선 순위가 높거나 먼저 시작된 작업 또는 네트워크 상황에 의해 오디오 콘텐츠의 재생 시작이 지연될 수도 있습니다. 이때 URL 유효 기간이 만료되어 오디오 콘텐츠를 제대로 재생할 수 없을 수도 있습니다.

이를 위해 Clova는 클라이언트가 오디오 콘텐츠의 재생 가능한 URL을 재생 직전에 취득할 수 있도록 하는 방법을 제공하고 있습니다. 우선 다음과 같이 `AudioPlayer.Play` 지시 메시지 중 `urlPlayable` 필드를 `false`로 지정하고, `url` 필드에 URL이 아닌 다른 형식의 값을 입력합니다.

```json
{
  "audioItem": {
    "audioItemId": "9CPWU-c82302b2-ea29-4f6c-ba6e-20fd268d8c3b-c1570067",
    "title": "Symphony No.4 In A Op.90 'Italian' - III. Con Moto Moderato",
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

나중에 클라이언트가 `AudioPlayer.Play` 지시 메시지를 수행할 때 `urlPlayable` 필드가 `false`이면, 유효한 오디오 콘텐츠의 URL을 얻기 위해 {{ "[`AudioPlayer.StreamRequested`](/CIC/References/CICInterface/AudioPlayer.md#StreamRequested)" if book.TargetCountryCode == "KR" else "[`AudioPlayer.StreamRequested`](/CEK/References/CEK_API.md#StreamRequested)" }} 이벤트 메시지를 Clova로 전송하게 됩니다. 이때, 이벤트 메시지의 내용이 [`EventRequest`](/CEK/References/CEK_API.md#CustomExtEventRequest) 타입의 요청 메시지로 다음과 같이 전달됩니다.

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
        "title": "Symphony No.4 In A Op.90 'Italian' - III. Con Moto Moderato",
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

Custom extension은 이 시점에 재생 가능한 오디오 콘텐츠의 URL을 [응답 메시지](/CEK/References/CEK_API.md#CustomExtResponseMessage)로 전달하면 됩니다. 이를 위해 `AudioPlayer.StreamDeliver` 지시 메시지를 응답 메시지에 포함시켜야 합니다. 클라이언트는 다음과 같은 `AudioPlayer.StreamDeliver` 지시 메시지의 본문을 통해 `AudioPlayer.Play` 지시 메시지에 대한 작업을 마저 수행할 수 있게 됩니다.

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

### 재생 제어의 동작 방식 변경 {#CustomizePlaybackControl}

음원을 제공하는 서비스나 음원 콘텐츠의 특징에 따라서 재생 일시 정지, 재생 재개, 재생 중지와 같은 [재생 제어](ControlAudioPlayback) 동작을 조금 다른 방식으로 구현해야 할 수도 있습니다. 예를 들면, 실시간 스트리밍 콘텐츠는 일시 정지 기능을 적용하는 것이 불가능할 수도 있습니다. 이때 사용자의 요청에 의해 `Clova.PauseIntent` [built-in intent](/Design/Design_Guideline_For_Extension.md#BuiltinIntent) 요청을 받았더라도 그에 대한 대응을 처리하지 못한다고 응답하거나 또는 `Clova.StopIntent`와 같은 대응을 처리해줄 수도 있습니다. `Clova.StopIntent`와 같은 대응을 처리한다면 [응답 메시지](/CEK/References/CEK_API.md#CustomExtResponseMessage)에 {{ "[`PlaybackController.Pause`](/CIC/References/CICInterface/PlaybackController.md#Pause)" if book.TargetCountryCode == "KR" else "[`PlaybackController.Pause`](/CEK/References/CEK_API.md#Pause)" }} 지시 메시지 대신에 {{ "[`PlaybackController.Stop`](/CIC/References/CICInterface/PlaybackController.md#Stop)" if book.TargetCountryCode == "KR" else "[`PlaybackController.Stop`](/CEK/References/CEK_API.md#Stop)" }} 지시 메시지를 응답으로 반환하도록 구현할 수 있습니다.

<div class="note">
  <p><strong>Note!</strong></p>
  <p>사용자의 혼란을 막기 위해 실시간 스트리밍 콘텐츠와 같이 특수한 상황에만 재생 제어의 동작 방식을 변경하고 되도록이면 기본 방식으로 구현할 것을 권장합니다.</p>
</div>
