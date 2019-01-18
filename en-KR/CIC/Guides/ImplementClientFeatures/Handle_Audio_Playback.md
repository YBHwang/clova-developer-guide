## Handling audio playback {#HandleAudioPlayback}

Based on user request, Clova plays audio or sends directives related to playback to the client. The client must handle the messages related to audio playback sent from Clova and return the audio playback state of the client to CIC using event messages. It is particularly important to have Clova understand the playback state of the client by sending event messages to CIC, and this reporting process must be done using event messages that are suitable to the situation or conditions. This section explains the following:

* [Playing audio stream](#PlayAudioStream)
* [Reporting audio playback progress](#ReportAudioPlaybackProgress)
* [Controlling audio playback](#ControlAudioPlayback)
* [Sharing audio playback state](#ShareAudioPlaybackState)

### Playing audio stream {#PlayAudioStream}
When a user requests to play music, Clova directs the client to play the audio requested by the user via CIC. The action flow of playing the audio stream is shown below.

![](/CIC/Resources/Images/CIC_Audio_Play_Work_Flow.svg)

When a user requests to play music, CIC sends the [`AudioPlayer.Play`](/CIC/References/CICInterface/AudioPlayer.md#Play) directive to the client as the first step. This directive contains information required to play the audio stream. This information must be used to find the audio data or display the audio information on the audio player. An example of an [`AudioPlayer.Play`](/CIC/References/CICInterface/AudioPlayer.md#Play) directive that can be received is as follows:

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

A simple description of the main fields of `payload` is shown below.

* `audioItem`: The object containing the metadata of the audio to be played.
* `audioItem.stream`: The object containing the audio stream information required for playback.
* `source`: The source of the audio streaming service.

The client plays audio using the information contained in the `audioItem.stream` field. The information contained in the `audioItem` and `source` fields can be displayed on the UI of an audio player or can be used as reference information.

If the `audioItem.stream.urlPlayable` field value of the [`AudioPlayer.Play`](/CIC/References/CICInterface/AudioPlayer.md#Play) directive is set to `false`, the audio cannot be played instantly using the `audioItem.stream` field information. This occurs in situations where the actual audio information must be looked up once more before providing the audio to the user due to issues such as for service billing issue or security issue. An example of an [`AudioPlayer.Play`](/CIC/References/CICInterface/AudioPlayer.md#Play) directive that cannot be played instantly is shown below.

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
        "title": "Symphony No.4 In A Op.90 'Italian' - III. Con Moto Moderato",
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

Therefore, if the `audioItem.stream.urlPlayable` field value is set to `false`, the [`AudioPlayer.StreamRequested`](/CIC/References/CICInterface/AudioPlayer.md#StreamRequested) event message must be sent once more as shown below just before playing the audio using the `audioItem.stream` field value received in the received [`AudioPlayer.Play`](/CIC/References/CICInterface/AudioPlayer.md#Play) directive.

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

When the [`AudioPlayer.StreamRequested`](/CIC/References/CICInterface/AudioPlayer.md#StreamRequested) event message as shown above is sent, the [`AudioPlayer.StreamDeliver`](/CIC/References/CICInterface/AudioPlayer.md#StreamDeliver) directive that contains actual playable information is received from the CIC as shown below. The client can then play audio using the newly received information.

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


### Reporting audio playback progress {#ReportAudioPlaybackProgress}

For Clova to understand the current situation of the user in terms of audio playback, the client must start the audio playback and report the playback progress to CIC as follows:

![](/CIC/Resources/Images/CIC_Audio_Play_Progress_Reporting.svg)

As shown in the action flow above, whether or not some playback progress report is carried out or not depends on the values set in the `audioItem.stream.progressReport` field of the [`AudioPlayer.Play`](/CIC/References/CICInterface/AudioPlayer.md#Play) directive or the `audioStream.progressReport` field of the [`AudioPlayer.StreamDeliver`](/CIC/References/CICInterface/AudioPlayer.md#StreamDeliver) directive. The table below indicates the situations and the conditions where a report on the playback progress has to be made and the event messages that must be used.

| Point of playback                                 | Condition                         | Event message for reporting |
|-----------------------------------------|----------------------------|----------------------|
| Right after starting audio playback                         | Always                                                                      | [`AudioPlayer.PlayStarted`](/CIC/References/CICInterface/AudioPlayer.md#PlayStarted) event message  |
| After starting audio playback and passing a specific duration          | When the `progressReport.progressReportDelayInMilliseconds` field is not `null`   | [`AudioPlayer.ProgressReportDelayPassed`](/CIC/References/CICInterface/AudioPlayer.md#ProgressReportDelayPassed) event message  |
| After starting audio playback and whenever passing a specified interval  | When the `progressReport.progressReportIntervalInMilliseconds` field is not `null`  | [`AudioPlayer.ProgressReportIntervalPassed`](/CIC/References/CICInterface/AudioPlayer.md#ProgressReportIntervalPassed) event message  |
| After starting audio playback and passing a specific point in playback  | When the `progressReport.progressReportPositionInMilliseconds` field is not `null`  | [`AudioPlayer.ProgressReportPositionPassed`](/CIC/References/CICInterface/AudioPlayer.md#ProgressReportPositionPassed) event message  |
| Right after completing audio playback                         | Always                                                                      | [`AudioPlayer.PlayFinished`](/CIC/References/CICInterface/AudioPlayer.md#PlayFinished) event message  |

Using the received event messages, Clova identifies the audio currently being listened to by the user and the playback point of this audio. Below is an example of the [`AudioPlayer.ProgressReportIntervalPassed`](/CIC/References/CICInterface/AudioPlayer.md#ProgressReportIntervalPassed) event message.

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

### Controlling audio playback {#ControlAudioPlayback}

Users can request Clova to pause, resume, stop, or replay the audio playback on the client. This audio playback control can be requested using the three methods below.

* User attempts playback control using speech (general method)
* User attempts playback control using buttons on client device
* User attempts playback control of a specific client remotely from the Clova app

However, the playback control on the audio is not conducted directly on the client because Clova must first identify the audio playback status of the user. All such playback controls are performed via Clova and the audio playback control must be mainly implemented via the [`PlaybackController`](/CIC/References/CICInterface/PlaybackController.md) interface. Also, the result must be reported through the event messages of the [`AudioPlayer`](/CIC/References/CICInterface/AudioPlayer.md) interface.

The diagram below shows the action flow when pausing audio playback.

![](/CIC/Resources/Images/CIC_Audio_Playback_Control_Flow.svg)

Generally, Clova analyzes the audio control via user utterance and the corresponding playback control directive ([`PlaybackController.Pause`](/CIC/References/CICInterface/PlaybackController.md#Pause)) is sent to the client. However, if the user has requested to pause the audio by pressing a button from the client, the state of the user pressing the pause button must be reported to Clova using the [`PlaybackController.PauseCommandIssued`](/CIC/References/CICInterface/PlaybackController.md#PauseCommandIssued) event message shown below.

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

If the user has requested playback control of the client remotely using a Clova app, Clova sends a directive of a [`PlaybackController.ExpectPauseCommand`](/CIC/References/CICInterface/PlaybackController.md#ExpectPauseCommand) format to this client. This is a message which directs the client to act as if a user has remotely pressed the button. Once the message below is received, the client can send a [`PlaybackController.PauseCommandIssued`](/CIC/References/CICInterface/PlaybackController.md#PauseCommandIssued) event message like above to Cova.

```json
// Request to operate as if a user has pressed the pause button
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

Clova sends the playback control requested by the user as the directive ([`PlaybackController.Pause`](/CIC/References/CICInterface/PlaybackController.md#Pause)) below, and the client can simply control audio playback according to the directive.

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

As the last step, the client can complete the playback control and report the action change in the audio player to CIC. Below shows the [AudioPlayer.PlayPaused](/CIC/References/CICInterface/AudioPlayer.md#PlayPaused) event message sent to CIC after pausing the audio playback.

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

### Sharing audio playback state {#ShareAudioPlaybackState}

The client can receive a shared sound source playback state from all other or specific clients registered in the user account. The process to receive the shared audio playback state is as follows:

![](/CIC/Resources/Images/CIC_Playback_State_Sync_Work_Flow.svg)

1. Clova app requests the audio playback state of all or specific clients registered in the user account to CIC {{ "using the [`AudioPlayer.RequestPlaybackState`](/CIC/References/CICInterface/AudioPlayer.md#RequestPlaybackState) event message " if book.DocMeta.TargetReaderType == "Internal" }}.
2. CIC instructs all or specific clients registered in the user account to report the current audio playback state using the [`AudioPlayer.ExpectReportPlaybackState`](/CIC/References/CICInterface/AudioPlayer.md#ExpectReportPlaybackState) directive.
3. After receiving the report request, the client reports the current audio playback state using [`AudioPlayer.ReportPlaybackState`](/CIC/References/CICInterface/AudioPlayer.md#ReportPlaybackState) event message.
4. CIC instructs the client that made the request to synchronize information by sending the states of the information {{ "using [`AudioPlayer.SynchronizePlaybackState`](/CIC/References/CICInterface/AudioPlayer.md#SynchronizePlaybackState)" if book.DocMeta.TargetReaderType == "Internal" }}.

Therefore, the client must send the [`AudioPlayer.ReportPlaybackState`](/CIC/References/CICInterface/AudioPlayer.md#ReportPlaybackState) event message if the [`AudioPlayer.ExpectReportPlaybackState`](/CIC/References/CICInterface/AudioPlayer.md#ExpectReportPlaybackState) directive is received, and the information below must be included in the `payload` field.

* Audio play state
* Repeat state
* Current-time indicator of the audio playing (when audio is playing)
* [`AudioStreamInfoObject`](/CIC/References/CICInterface/AudioPlayer.md#AudioStreamInfoObject) object received from the [`AudioPlayer.Play`](/CIC/References/CICInterface/AudioPlayer.md#Play) directive (when audio is playing or paused)
* `audioItem.stream.token` field value of the [`AudioPlayer.Play`](/CIC/References/CICInterface/AudioPlayer.md#Play) directive (when audio is playing or paused)
* Total length of the playing media (optional)

```json
// When audio is not playing
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

// When audio is playing or paused
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
