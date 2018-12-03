## オーディオ再生を処理する {#HandleAudioPlayback}

Clovaはユーザーのリクエストに応じて、オーディオを再生したり、再生に関連するディレクティブをクライアントに送信します。クライアントは、Clovaがオーディオ再生に関連して送信するメッセージを処理して、クライアントのオーディオ再生状態をイベントを使ってCICに送信する必要があります。特に、CICにイベントを送信して、Clovaにクライアントの再生状態を知らせる必要があります。状況や条件に適切なイベントを使って、再生状態をレポートするようにしてください。ここでは、以下の内容について説明します。

* [オーディオを再生する](#PlayAudioStream)
* [オーディオ再生の進行状況をレポートする](#ReportAudioPlaybackProgress)
* [オーディオ再生をコントロールする](#ControlAudioPlayback)
* [オーディオ再生状態を共有する](#ShareAudioPlaybackState)

### オーディオを再生する {#PlayAudioStream}
ユーザーがオーディオの再生をリクエストすると、ClovaはCICを介して、ユーザーからリクエストされたオーディオアイテムを再生するようにクライアントに指示します。次は、オーディオを再生する動作の流れを示します。

![](/CIC/Resources/Images/CIC_Audio_Play_Work_Flow.png)

ユーザーがオーディオの再生をリクエストすると、CICは、最初にクライアントに[`AudioPlayer.Play`](/CIC/References/CICInterface/AudioPlayer.md#Play)ディレクティブを送信します。このディレクティブには、オーディオの再生に必要な情報が含まれています。この情報を使って、オーディオファイルを探したり、プレイヤーにオーディオアイテムの情報を表示したりする必要があります。次の[`AudioPlayer.Play`](/CIC/References/CICInterface/AudioPlayer.md#Play)ディレクティブを受信します。

```json
{
  "directive": {
    "header": {
      "namespace": "AudioPlayer",
      "name": "Play",
      "dialogRequestId": "34abac3-cb46-611c-5111-47eab87b7",
      "messageId": "ad13f0d6-bb11-ca23-99aa-312a0b213805"
    },
    "payload": {
      "audioItem": {
        "audioItemId": "90b77646-93ab-444f-acd9-60f9f278ca38",
        "episodeId": 22346122,
        "stream": {
          "beginAtInMilliseconds": 419704,
          "progressReport": {
            "progressReportDelayInMilliseconds": null,
            "progressReportIntervalInMilliseconds": 60000,
            "progressReportPositionInMilliseconds": null
          },
          "token": "eyJ1cmwiOiJodHRwczovL2FwaS1leC5wb2RiYmFuZy5jb20vY2xvdmEvZmlsZS8xMjU0OC8yMjYxODcwMSIsInBsYXlUeXBlIjoiTk9ORSIsInBvZGNhc3RJZCI6MTI1NDgsImVwaXNvZGVJZCI6MjI2MTg3MDF9",
          "url": "https://streaming.example.com/clova/file/12548/22618701",
          "urlPlayable": true
        },
        "type": "podcast"
      },
      "source": {
        "name": "Potbbang",
        "logoUrl": "https://img.musicservice.example.net/logo_180125.png"
      },
      "playBehavior": "REPLACE_ALL"
    }
  }
}
```

`payload`の主なフィールドには、以下のものがあります。

* `audioItem`：再生するオーディオアイテムのメタデータが含まれたオブジェクト
* `audioItem.stream`：再生に必要なオーディオストリームの情報を持っているオブジェクト
* `source`：オーディオストリーミングサービスの提供元

クライアントは、`audioItem.stream`フィールドに含まれた情報を使ってオーディオを再生し、`audioItem`フィールドと`source`フィールドの内容をプレイヤーのUIに表示したり、参照したりします。

受信した[`AudioPlayer.Play`](/CIC/References/CICInterface/AudioPlayer.md#Play)ディレクティブ内の`audioItem.stream.urlPlayable`フィールドの値が`false`の場合、`audioItem.stream`フィールドの情報ではオーディオアイテムをすぐに再生できません。これは、サービスの課金およびセキュリティなどのせいで、オーディオを再生する直前に、そのオーディオの実際の情報をもう一度照会する必要がある場合に発生します。次は、すぐに再生できない[`AudioPlayer.Play`](/CIC/References/CICInterface/AudioPlayer.md#Play)ディレクティブのサンプルです。

```json
{
  "directive": {
    "header": {
      "namespace": "AudioPlayer",
      "name": "Play",
      "dialogRequestId": "277b40c3-b046-4f61-a551-783b1547e7b7",
      "messageId": "4e4080d6-c440-498a-bb73-ae86c6312806"
    },
    "payload": {
      "audioItem": {
        "audioItemId": "9CPWU-8362fe7c-f75c-42c6-806b-6f3e00aba8f1-c1862201",
        "album": {
          "albumId": "2000240",
          "genres": [
            "Classic"
          ],
          "title": "Wonderland - Edvard Grieg : Piano Concerto, Lyric Pieces"
        },
        ...
        "stream": {
          "beginAtInMilliseconds": 0,
          "durationInMilliseconds": 60000,
          "progressReport": {
            "progressReportDelayInMilliseconds": null,
            "progressReportIntervalInMilliseconds": null,
            "progressReportPositionInMilliseconds": 60000
          },
          "token": "TR-NM-17716562",
          "url": "clova:TR-NM-17716562",
          "urlPlayable": false
        },
        "title": "Symphony No.4 In A Op.90 'Italian' - III.Con Moto Moderato",
        "type": "SampleMusicProvider"
      },
      "source": {
        "name": "Sample Music Provider",
        "logoUrl": "https://img.musicservice.example.net/logo_180125.png"
      },
      "playBehavior": "REPLACE_ALL"
    }
  }
}
```

`audioItem.stream.urlPlayable`フィールドの値が`false`の場合、[`AudioPlayer.Play`](/CIC/References/CICInterface/AudioPlayer.md#Play)ディレクティブで受け取った`audioItem.stream`フィールドの値をそのまま使用して、次のように再びCICに[`AudioPlayer.StreamRequested`](/CIC/References/CICInterface/AudioPlayer.md#StreamRequested)イベントを送信する必要があります。

```json
{
  "context": [
    ...
  ],
  "event": {
    "header": {
      "namespace": "AudioPlayer",
      "name": "StreamRequested",
      "messageId": "198cf12-4020-b98a-b73b-1234ab312806"
    },
    "payload": {
      "audioItemId": "9CPWU-8362fe7c-f75c-42c6-806b-6f3e00aba8f1-c1862201",
      "audioStream": {
        "beginAtInMilliseconds": 0,
        "durationInMilliseconds": 60000,
        "progressReport": {
          "progressReportDelayInMilliseconds": null,
          "progressReportIntervalInMilliseconds": null,
          "progressReportPositionInMilliseconds": 60000
        },
        "token": "TR-NM-17716562",
        "url": "clova:TR-NM-17716562",
        "urlPlayable": false
      }
    }
  }
}
```

上記のように[`AudioPlayer.StreamRequested`](/CIC/References/CICInterface/AudioPlayer.md#StreamRequested)イベントを送信すると、次のように実際に再生できる情報が含まれた[`AudioPlayer.StreamDeliver`](/CIC/References/CICInterface/AudioPlayer.md#StreamDeliver)ディレクティブをCICから受信します。クライアントは、新しく受信する情報でオーディオを再生します。

```json
{
  "directive": {
    "header": {
      "namespace": "AudioPlayer",
      "name": "StreamDeliver",
      "dialogRequestId": "277b40c3-b046-4f61-a551-783b1547e7b7",
      "messageId": "4e4080d6-c440-498a-bb73-ae86c6312806"
    },
    "payload": {
      "audioItemId": "9CPWU-8362fe7c-f75c-42c6-806b-6f3e00aba8f1-c1862201",
      "audioStream": {
          "format": "audio/mpeg",
          "progressReport": {
            "progressReportDelayInMilliseconds": null,
            "progressReportIntervalInMilliseconds": null,
            "progressReportPositionInMilliseconds": 60000
          },
          "token": "TR-NM-17716562",
          "url": "https://musicservice.example.net/b767313e.mp3",
          "urlPlayable": true
      }
    }
  }
}
```


### オーディオ再生の進行状況をレポートする {#ReportAudioPlaybackProgress}

Clovaは、オーディオ再生に関連して、ユーザーが今どのような状況にいるかを知る必要があります。クライアントはオーディオの再生を開始すると、次のように再生の進行状況をCICにレポートする必要があります。

![](/CIC/Resources/Images/CIC_Audio_Play_Progress_Reporting.png)

上記の流れのとおり、一部の再生の進行状況は、[`AudioPlayer.Play`](/CIC/References/CICInterface/AudioPlayer.md#Play)ディレクティブの`audioItem.stream.progressReport`フィールド、または[`AudioPlayer.StreamDeliver`](/CIC/References/CICInterface/AudioPlayer.md#StreamDeliver)ディレクティブの`audioStream.progressReport`フィールドの値によって、レポートするかどうかが決まります。次の表は、再生の進行状況をレポートする必要がある状況と条件、使用するイベントを示します。

| 再生ポイント                                 | 条件                         | レポートするときに使用するイベント |
|-----------------------------------------|----------------------------|----------------------|
| オーディオ再生を開始した直後                         | 常時                                                                      | [`AudioPlayer.PlayStarted`](/CIC/References/CICInterface/AudioPlayer.md#PlayStarted)イベント  |
| オーディオ再生を開始してから、指定された時間が経過するとき          | `progressReport.progressReportDelayInMilliseconds`フィールドが`null`ではない場合   | [`AudioPlayer.ProgressReportDelayPassed`](/CIC/References/CICInterface/AudioPlayer.md#ProgressReportDelayPassed)イベント  |
| オーディオ再生を開始してから、指定された間隔の時間が経過するとき  | `progressReport.progressReportIntervalInMilliseconds`フィールドが`null`ではない場合  | [`AudioPlayer.ProgressReportIntervalPassed`](/CIC/References/CICInterface/AudioPlayer.md#ProgressReportIntervalPassed)イベント  |
| オーディオ再生を開始してから、特定のオフセットが経過するとき  | `progressReport.progressReportPositionInMilliseconds`フィールドが`null`ではない場合  | [`AudioPlayer.ProgressReportPositionPassed`](/CIC/References/CICInterface/AudioPlayer.md#ProgressReportPositionPassed)イベント  |
| オーディオ再生が完了した直後                         | 常時                                                                      | [`AudioPlayer.PlayFinished`](/CIC/References/CICInterface/AudioPlayer.md#PlayFinished)イベント  |

Clovaは、上記のイベントから、ユーザーが今聞いているオーディオアイテムと、そのオーディオアイテムの再生ポイントを把握します。次は、[`AudioPlayer.ProgressReportIntervalPassed`](/CIC/References/CICInterface/AudioPlayer.md#ProgressReportIntervalPassed)イベントのサンプルです。

```json
{
  "context": [
    ...
  ],
  "event": {
    "header": {
      "namespace": "AudioPlayer",
      "name": "ProgressReportIntervalPassed",
      "messageId": "4e4080d6-c440-498a-bb73-ae86c6312806"
    },
    "payload": {
      "token": "TR-NM-4435786",
      "offsetInMilliseconds": 120000
    }
  }
}
```

### オーディオ再生をコントロールする {#ControlAudioPlayback}

ユーザーは、クライアントがオーディオ再生を一時停止(pause)、再開(resume)、停止(stop)、もう一度再生(replay)するようにClovaにリクエストすることができます。オーディオ再生のコントロールは、次の3つの方法でリクエストできます。

* ユーザーが発話で再生をコントロールする
* ユーザーがクライアントデバイスのボタンで再生をコントロールする
* ユーザーがClovaアプリからリモートで特定のクライアントの再生をコントロールする

Clovaは、ユーザーのオーディオ再生状況を把握する必要があります。そのため、オーディオ再生のコントロールは、クライアントでは直接行われません。再生のコントロールは、すべてClovaを介するディレクティブで行われ、主に[`PlaybackController`](/CIC/References/CICInterface/PlaybackController.md)インターフェースで実装される必要があります。また、その結果は[`AudioPlayer`](/CIC/References/CICInterface/AudioPlayer.md)インターフェースのイベントでレポートされる必要があります。

次は、オーディオの再生が一時停止する動作の流れを示します。

![](/CIC/Resources/Images/CIC_Audio_Playback_Control_Flow.png)

通常、ユーザーの発話から行われる再生のコントロールは、Clovaで解析され、該当する再生コントロールのディレクティブ([`PlaybackController.Pause`](/CIC/References/CICInterface/PlaybackController.md#Pause))がクライアントに送信されます。ユーザーがクライアントのボタンを押して一時停止するようにリクエストした場合、次のような[`PlaybackController.PauseCommandIssued`](/CIC/References/CICInterface/PlaybackController.md#PauseCommandIssued)イベントで一時停止ボタンが押されたことをClovaにレポートする必要があります。

```json
{
  "context": [
    ...
  ],
  "event": {
    "header": {
      "namespace": "PlaybackController",
      "name": "PauseCommandIssued",
      "messageId": "4e4080d6-c440-498a-bb73-ae86c6312806"
    },
    "payload": {}
  }
}
```

ユーザーがClovaアプリからリモートでクライアントの再生コントロールをリクエストした場合、Clovaはそのクライアントに[`PlaybackController.ExpectPauseCommand`](/CIC/References/CICInterface/PlaybackController.md#ExpectPauseCommand)のようなディレクティブを送信します。これは、ユーザーがリモートでボタンを押したときと同じ動作をするように指示するメッセージです。次のメッセージを受信した場合、[`PlaybackController.PauseCommandIssued`](/CIC/References/CICInterface/PlaybackController.md#PauseCommandIssued)イベントをClovaに送信する必要があります。

```json
// ユーザーが一時停止ボタンを押したときと同じ動作をするようにリクエストする
{
  "directive": {
    "header": {
      "namespace": "PlaybackController",
      "name": "ExpectPauseCommand",
      "dialogRequestId": "42390b12-ae91-4121-aa0a-37f74e8e422b",
      "messageId": "b1f88d7d-bbb8-44fa-a0a2-c5a7553e6f8a"
    },
    "payload": {}
  }
}
```

Clovaは、ユーザーからリクエストされた再生コントロールを、次のようなディレクティブ([`PlaybackController.Pause`](/CIC/References/CICInterface/PlaybackController.md#Pause))で渡します。クライアントは、受信したディレクティブに応じてオーディオの再生をコントロールします。

```json
{
  "directive": {
    "header": {
      "namespace": "PlaybackController",
      "name": "Pause",
      "dialogRequestId": "42390b12-ae91-4121-aa0a-37f74e8e422b",
      "messageId": "b1f88d7d-bbb8-44fa-a0a2-c5a7553e6f8a"
    },
    "payload": {}
  }
}
```

最後に、クライアントは再生コントロールが完了すると、プレイヤーの動作の変化をCICにレポートする必要があります。次は、オーディオの再生を一時停止した後、CICに送信する[AudioPlayer.PlayPaused](/CIC/References/CICInterface/AudioPlayer.md#PlayPaused)イベントです。

```json
{
  "context": [
    ...
  ],
  "event": {
    "header": {
      "namespace": "AudioPlayer",
      "name": "PlayPaused",
      "messageId": "4e4080d6-c440-498a-bb73-ae86c6312806"
    },
    "payload": {
      "token": "TR-NM-4435786",
      "offsetInMilliseconds": 83100
    }
  }
}
```

### オーディオ再生状態を共有する {#ShareAudioPlaybackState}

1つのクライアントは、ユーザーのアカウントに登録されているすべてのクライアントまたは特定のクライアントと、オーディオ再生状態を共有することができます。次は、オーディオ再生状態を共有される動作の流れを示します。

![](/CIC/Resources/Images/CIC_Playback_State_Sync_Work_Flow.png)

1. Clovaアプリは、{{ "[`AudioPlayer.RequestPlaybackState`](/CIC/References/CICInterface/AudioPlayer.md#RequestPlaybackState)イベントを使用して" if book.DocMeta.TargetReaderType == "Internal" }}CICに対して、ユーザーのアカウントに登録されているすべてのクライアント、または特定のクライアントのオーディオ再生状態をリクエストします。
2. CICは、[`AudioPlayer.ExpectReportPlaybackState`](/CIC/References/CICInterface/AudioPlayer.md#ExpectReportPlaybackState)ディレクティブで、ユーザーのアカウントに登録されているすべてのクライアント、または特定のクライアントに、現在のオーディオ再生状態をレポートするように指示します。
3. オーディオ再生状態をレポートするように指示されたクライアントは、[`AudioPlayer.ReportPlaybackState`](/CIC/References/CICInterface/AudioPlayer.md#ReportPlaybackState)イベントで、CICに現在のオーディオ再生状態をレポートします。
4. CICは、{{ "[`AudioPlayer.SynchronizePlaybackState`](/CIC/References/CICInterface/AudioPlayer.md#SynchronizePlaybackState)を使用して" if book.DocMeta.TargetReaderType == "Internal" }}他のクライアントのオーディオ再生状態をリクエストしたクライアントに状態情報を送信し、同期するように指示します。

クライアントは[`AudioPlayer.ExpectReportPlaybackState`](/CIC/References/CICInterface/AudioPlayer.md#ExpectReportPlaybackState)ディレクティブを受信すると、[`AudioPlayer.ReportPlaybackState`](/CIC/References/CICInterface/AudioPlayer.md#ReportPlaybackState)イベントをCICに送信する必要があります。そのとき、次の情報を`payload`フィールドに含める必要があります。

* オーディオプレイヤーの状態
* リピート再生するかどうか
* 再生しているオーディオの現在の再生ポイント(オーディオを再生しているとき)
* [`AudioPlayer.Play`](/CIC/References/CICInterface/AudioPlayer.md#Play)ディレクティブで受信した[`AudioStreamInfoObject`](/CIC/References/CICInterface/AudioPlayer.md#AudioStreamInfoObject)オブジェクト(オーディオを再生しているか、または一時停止しているとき)
* [`AudioPlayer.Play`](/CIC/References/CICInterface/AudioPlayer.md#Play)ディレクティブの`audioItem.stream.token`フィールドの値(オーディオを再生しているか、または位置停止しているとき)
* 再生しているオーディオアイテムの全体の長さ(任意)

```json
// オーディオを再生していないとき
{
  "context": [
    ...
  ],
  "event": {
    "header": {
      "namespace": "AudioPlayer",
      "name": "ReportPlaybackState",
      "messageId": "3e57f11a-a02d-4b6f-b183-fdfb6105c650"
    },
    "payload": {
      "playerActivity": "IDLE",
      "repeatMode": "NONE"
    }
  }
}

// オーディオを再生しているか、または一時停止しているとき
{
  "context": [
    ...
  ],
  "event": {
    "header": {
      "namespace": "AudioPlayer",
      "name": "ReportPlaybackState",
      "messageId": "aa1b20b1-7562-4236-a7a6-65a235571bac"
    },
    "payload": {
      "playerActivity": "PLAYING",
      "repeatMode": "NONE",
      "offsetInMilliseconds": 13000,
      "stream": {
        "beginAtInMilliseconds": 0,
        "progressReport": {
            "progressReportDelayInMilliseconds": null,
            "progressReportIntervalInMilliseconds": null,
            "progressReportPositionInMilliseconds": 30000
        },
        "token": "TR-NM-4435786",
        "urlPlayable": false,
        "url": "clova:TR-NM-4435786"
      },
      "token": "TR-NM-4435786"
    }
  }
}
```
