## Custom extension messages {#CustomExtMessage}
Custom extension messages are used when exchanging information between CEK and the custom extension. Custom extension messages are classified as [request message](#CustomExtRequestMessage) and [response message](#CustomExtResponseMessage). Depending on the [request type](#CustomExtRequestType), request messages are classified into four types: `EventRequest`, `IntentRequest`, `LaunchRequest`, and `SessionEndedRequest`.

### Request messages {#CustomExtRequestMessage}
CEK uses request messages (HTTP Requests) to send user intents analyzed by Clova to the custom extension. This section explains the structure of request messages, message fields, request types, and the `request` field that varies by type.

#### Message structure

{% raw %}
```json
{
  "context": {
    "AudioPlayer": {
      "offsetInMilliseconds": {{number}},
      "playerActivity": {{string}},
      "stream": {{AudioStreamInfoObject}},
      "totalInMilliseconds": {{number}},
    },
    "System": {
      "application": {
        "applicationId": {{string}}
      },
      "device": {
        "deviceId": {{string}},
        "display": {
          "contentLayer": {
            "width": {{number}},
            "height": {{number}}
          },
          "dpi": {{number}},
          "orientation": {{string}},
          "size": {{string}}
        }
      },
      "user": {
        "userId": {{string}},
        "accessToken": {{string}}
      }
    }
  },
  "request": {{object}},
  "session": {
    "new": {{boolean}},
    "sessionAttributes": {{object}},
    "sessionId": {{string}},
    "user": {
      "userId": {{string}},
      "accessToken": {{string}}
    }
  },
  "version": {{string}}
}
```
{% endraw %}

#### Message fields
| Field name       | Data type    | Description                     | Included |
|---------------|---------|-----------------------------|:---------:|
| `context`                                  | object  | The object that has the context information of the client.                                | Always |
| `context.AudioPlayer`                      | object  | The object that holds the details of media content currently being played or played last. | Conditional |
| `context.AudioPlayer.offsetInMilliseconds` | number  | The most recent playback position (offset) of the recently played media. The unit is milliseconds and this field value may be empty if the `playerActivity` value is `"IDLE"`.                                       | Conditional |
| `context.AudioPlayer.playerActivity`       | string  | The value for indicating the state of player. Values are:<ul><li><code>"IDLE"</code>: Deactivated</li><li><code>"PLAYING"</code>: Playing</li><li><code>"PAUSED"</code>: Paused</li><li><code>"STOPPED"</code>: Stopped</li></ul> | Always |
| `context.AudioPlayer.stream`               | [AudioStreamInfoObject](/CIC/References/CICInterface/AudioPlayer.md#AudioStreamInfoObject) | The object that contains the details of the currently playing media. This field value may be empty if the `playerActivity` value is `"IDLE"`.    | Conditional |
| `context.AudioPlayer.totalInMilliseconds`  | number  | The total duration of the recently played media. The unit is milliseconds and this field value may be empty if the `playerActivity` value is `"IDLE"`.                                                                  | Conditional |
| `context.System`                           | object  | The object that has the context information of the client system.                          | Always |
| `context.System.application`               | object  | The object that has the information of the extension that must be executed by the user intent.       | Always |
| `context.System.application.applicationId` | string  | The extension ID.                                                 | Always |
| `context.System.device`                    | object  | The object that has the context information of the client device.                               | Always |
| `context.System.device.deviceId`           | string  | The client device ID. The device identification information is sent with the combined information of the model name and device serial number. | Always |
| `context.System.device.display`            | object  | The object that has the display information of the client device.                                                 | Always |
| `context.System.device.display.contentLayer`        | object | The object that contains the resolution of the client display used for content. This field is omitted if the value of `context.System.device.display.size` is `"none"`.  | Conditional |
| `context.System.device.display.contentLayer.width`  | number | The width of the content area shown on the display. The unit is pixels (px).             | Always |
| `context.System.device.display.contentLayer.height` | number | The height of the content area shown on the display. The unit is pixels (px).             | Always |
| `context.System.device.display.dpi`         | number | The DPI of the display. This field is omitted if the value of `context.System.device.display.size` is `"none"`.          | Conditional |
| `context.System.device.display.orientation` | string | The direction of the display. This field is omitted if the value of `context.System.device.display.size` is `"none"`.<ul><li><code>"landscape"</code>: Horizontal display</li><li><code>"portrait"</code>: Vertical display</li></ul>                      | Conditional |
| `context.System.device.display.size`        | string | The resolution of the display. A predefined size value or a random value for the resolution size (`"custom"`) may be entered already. Value (`"none"`) may also be entered if there is no display device. <ul><li><code>"none"</code>: No display in client device</li><li><code>"s100"</code>: Low resolution (160px X 107px)</li><li><code>"m100"</code>: Medium resolution (427px X 240px)</li><li><code>"l100"</code>: High resolution (640px X 360px)</li><li><code>"xl100"</code>: Ultrahigh resolution (xlarge type, 899px X 506px)</li><li><code>"custom"</code>: Resolution is not in a predefined specification.</li></ul><div class="note"><p><strong>Note!</strong></p><p>You must provide media content with image quality that is appropriate for screen ratio and DPI of the client device.</p></div> | Always |
| `context.System.user`                      | object  | The object that has authenticated basic user information in the client device.                 | Always |
| `context.System.user.userId`               | string  | Clova ID of the device default user.                                    | Always |
| `context.System.user.accessToken`          | string  | Access token of the user account for a specific service. The access token for the user account connected with the default device user is delivered. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user account](/CEK/Guides/Link_User_Account.md). | Always |
| `request`                                 | object  | The object that has the analyzed details of the user utterance. The field configuration will vary depending on the [request type](#CustomExtRequestType). | Always |
| `session`                                  | object  | The object that has the session information. A session is a logical unit used to distinguish user requests.     | Always |
| `session.new`                              | boolean | Distinguishes whether the request message is for a new session or the existing session. <ul><li>true: New session</li><li>false: Existing session</li></ul>  | Always |
| `session.sessionAttributes`                       | object  | The object that stores the information necessary for multi-turn dialogue with the user. Custom extension sends temporary information to CEK using the `response.sessionAttributes` field of [response message](#CustomExtResponseMessage) and receives the corresponding information for the `session.sessionAttributes` field again when receiving additional user requests. The object consists of a key-value pair and can be freely defined when implementing the custom extension. If there is no stored value, an empty object is delivered.   | Always |
| `session.sessionId`                        | string  | Session ID                                                    | Always |
| `session.user`                             | object  | The object that has the information of the current user.                             | Always |
| `session.user.userId`                      | string  | Clova ID of the current user. The value may be different from `context.System.user.userId`. | Always |
| `session.user.accessToken`                 | string  | Access token of the user account for a specific service. The access token for the user account connected with the current user is delivered. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user account](/CEK/Guides/Link_User_Account.md).| Conditional |
| `version`                                  | string  | Version of message format (CEK version).                          | Always |

#### Message example
{% raw %}
```json
// Example 1: EventRequest type
{
  "version": "0.1.0",
  "session": {
    "new": false,
    "sessionAttributes": {},
    "sessionId": "a29cfead-c5ba-474d-8745-6c1a6625f0c5",
    "user": {
      "userId": "V0qe",
      "accessToken": "XHapQasdfsdfFsdfasdflQQ7"
    }
  },
  "context": {
    "System": {
      "application": {
        "applicationId": "com.yourdomain.extension.pizzabot"
      },
      "user": {
        "userId": "V0qe",
        "accessToken": "XHapQasdfsdfFsdfasdflQQ7"
      },
      "device": {
        "deviceId": "096e6b27-1717-33e9-b0a7-510a48658a9b",
        "display": {
          "size": "l100",
          "orientation": "landscape",
          "dpi": 96,
          "contentLayer": {
            "width": 640,
            "height": 360
          }
        }
      }
    }
  },
  "request": {
    "type": "EventRequest",
    "requestId": "f09874hiudf-sdf-4wku-flksdjfo4hjsdf",
    "timestamp": "2018-06-11T09:19:23Z",
    "event" : {
      "namespace":"ClovaSkill",
      "name":"SkillEnabled",
      "payload": null
    }
  }
}

// Example 2: IntentRequest type
{
  "version": "0.1.0",
  "session": {
    "new": false,
    "sessionAttributes": {},
    "sessionId": "a29cfead-c5ba-474d-8745-6c1a6625f0c5",
    "user": {
      "userId": "V0qe",
      "accessToken": "XHapQasdfsdfFsdfasdflQQ7"
    }
  },
  "context": {
    "System": {
      "application": {
        "applicationId": "com.yourdomain.extension.pizzabot"
      },
      "user": {
        "userId": "V0qe",
        "accessToken": "XHapQasdfsdfFsdfasdflQQ7"
      },
      "device": {
        "deviceId": "096e6b27-1717-33e9-b0a7-510a48658a9b",
        "display": {
          "size": "l100",
          "orientation": "landscape",
          "dpi": 96,
          "contentLayer": {
            "width": 640,
            "height": 360
          }
        }
      }
    }
  },
  "request": {
    "type": "IntentRequest",
    "intent": {
      "name": "OrderPizza",
      "slots": {
        "pizzaType": {
          "name": "pizzaType",
          "value": "Pepperoni"
        }
      }
    }
  }
}

// Example 3: LaunchRequest type
{
  "version": "0.1.0",
  "session": {
    "new": true,
    "sessionAttributes": {},
    "sessionId": "a29cfead-c5ba-474d-8745-6c1a6625f0c5",
    "user": {
      "userId": "V0qe",
      "accessToken": "XHapQasdfsdfFsdfasdflQQ7"
    }
  },
  "context": {
    "System": {
      "application": {
        "applicationId": "com.yourdomain.extension.pizzabot"
      },
      "user": {
        "userId": "V0qe",
        "accessToken": "XHapQasdfsdfFsdfasdflQQ7"
      },
      "device": {
        "deviceId": "096e6b27-1717-33e9-b0a7-510a48658a9b",
        "display": {
          "size": "l100",
          "orientation": "landscape",
          "dpi": 96,
          "contentLayer": {
            "width": 640,
            "height": 360
          }
        }
      }
    }
  },
  "request": {
    "type": "LaunchRequest"
  }
}

// Example 4: SessionEndedRequest type
{
  "version": "0.1.0",
  "session": {
    "new": false,
    "sessionAttributes": {},
    "sessionId": "a29cfead-c5ba-474d-8745-6c1a6625f0c5",
    "user": {
      "userId": "V0qe",
      "accessToken": "XHapQasdfsdfFsdfasdflQQ7"
    }
  },
  "context": {
    "System": {
      "application": {
        "applicationId": "com.yourdomain.extension.pizzabot"
      },
      "user": {
        "userId": "V0qe",
        "accessToken": "XHapQasdfsdfFsdfasdflQQ7"
      },
      "device": {
        "deviceId": "096e6b27-1717-33e9-b0a7-510a48658a9b",
        "display": {
          "size": "l100",
          "orientation": "landscape",
          "dpi": 96,
          "contentLayer": {
            "width": 640,
            "height": 360
          }
        }
      }
    }
  },
  "request": {
    "type": "SessionEndedRequest"
  }
}
```
{% endraw %}

#### See also
* [Handling a custom extension request](/CEK/Guides/Build_Custom_Extension.md#HandleCustomExtensionRequest)
* [AudioStreamInfoObject](/CIC/References/CICInterface/AudioPlayer.md#AudioStreamInfoObject)

### Request types {#CustomExtRequestType}
Request messages are classified into the following four types and the field configuration of the request message `request` object varies for each request type.
* [`EventRequest`](#CustomExtEventRequest)
* [`IntentRequest`](#CustomExtIntentRequest)
* [`LaunchRequest`](#CustomExtLaunchRequest)
* [`SessionEndedRequest`](#CustomExtSessionEndedRequest)

#### EventRequest {#CustomExtEventRequest}
{% if book.TargetCountryCode == "KR" %}
`EventRequest` type is a request type used when changes in the client state or related requests need to be sent to the extension. CEK uses the `EventRequest` request type to [report the client audio playback state to the extension](/CEK/Guides/Build_Custom_Extension.md#CollectPlaybackStatusAndProgress) or to [request additional information about audio playback from the extension](/CEK/Guides/Build_Custom_Extension.md#ProvidingMetaDataForDisplay). You must develop the extension to handle the tasks of reporting the audio playback state or requesting additional information.

Use the `EventRequest` request type and the following [event messages](/CIC/References/CIC_API.md#Event) of [CIC API](/CIC/References/CIC_API.md) when reporting the audio playback state or requesting additional information from the extension.

* [`AudioPlayer.PlayFinished`](/CIC/References/CICInterface/AudioPlayer.md#PlayFinished)
* [`AudioPlayer.PlayPaused`](/CIC/References/CICInterface/AudioPlayer.md#PlayPaused)
* [`AudioPlayer.PlayResumed`](/CIC/References/CICInterface/AudioPlayer.md#PlayResumed)
* [`AudioPlayer.PlayStarted`](/CIC/References/CICInterface/AudioPlayer.md#PlayStarted)
* [`AudioPlayer.PlayStopped`](/CIC/References/CICInterface/AudioPlayer.md#PlayStopped)
* [`AudioPlayer.ProgressReportDelayPassed`](/CIC/References/CICInterface/AudioPlayer.md#ProgressReportDelayPassed)
* [`AudioPlayer.ProgressReportIntervalPassed`](/CIC/References/CICInterface/AudioPlayer.md#ProgressReportIntervalPassed)
* [`AudioPlayer.ProgressReportPositionPassed`](/CIC/References/CICInterface/AudioPlayer.md#ProgressReportPositionPassed)
* [`AudioPlayer.StreamRequested`](/CIC/References/CICInterface/AudioPlayer.md#StreamRequested)
* [`TemplateRuntime.RequestPlayerInfo`](/CIC/References/CICInterface/AudioPlayer.md#RequestPlayerInfo)
{% elif book.TargetCountryCode == "JP" %}
`EventRequest` type is a request type used when changes in the client state or related requests need to be sent to the extension. CEK uses the `EventRequest` request type to report the results of the user enabling or disabling specific skills, [report audio playback status of the client to the extension](/CEK/Guides/Build_Custom_Extension.md#CollectPlaybackStatusAndProgress), or [request additional information related to audio playback from the extension](/CEK/Guides/Build_Custom_Extension.md#ProvidingMetaDataForDisplay). You must develop the extension to handle the tasks of enabling or disabling skills, reporting the audio playback state, or requesting additional information.

Use the `EventRequest` request type and the following [CIC API](#CICAPIforAudioPlayback) when reporting the audio playback state or requesting additional information from the extension.

* [`AudioPlayer.PlayFinished`](#PlayFinished)
* [`AudioPlayer.PlayPaused`](#PlayPaused)
* [`AudioPlayer.PlayResumed`](#PlayResumed)
* [`AudioPlayer.PlayStarted`](#PlayStarted)
* [`AudioPlayer.PlayStopped`](#PlayStopped)
* [`AudioPlayer.ProgressReportDelayPassed`](#ProgressReportDelayPassed)
* [`AudioPlayer.ProgressReportIntervalPassed`](#ProgressReportIntervalPassed)
* [`AudioPlayer.ProgressReportPositionPassed`](#ProgressReportPositionPassed)
* [`AudioPlayer.StreamRequested`](#StreamRequested)
* [`TemplateRuntime.RequestPlayerInfo`](#RequestPlayerInfo)
{% endif %}

The `request` object field configuration of the `EventRequest` type message is as follows:

{% raw %}
```json
{
  "type": "EventRequest",
  "requestId": {{string}},
  "timestamp": {{string}},
  "event": {
    "namespace": {{string}},
    "name": {{string}},
    "payload": {{object}}
  }
}
```
{% endraw %}

| Field name       | Data type    | Description                     | Included |
|---------------|---------|-----------------------------|:---------:|
| `event`           | object  | The object that stores the information sent by the client to Clova.                                       | Always   |
| `event.name`      | string  | {{ "Name of the event message sent by the client to Clova." if book.TargetCountryCode == "KR" else "Name of the event message sent by the client to Clova or a name that distinguishes whether a skill action is enabled or disabled. The name to distinguish the action state of a skill is `SkillEnabled` or `SkillDisabled`." }} | Always   |
| `event.namespace` | string  | {{ "Namespace of the event message sent by the client to Clova." if book.TargetCountryCode == "KR" else "Namespace of the event message sent by the client to Clova or a namespace that distinguishes whether a skill action is enabled or disabled. The namespace to distinguish the action state of a skill is always set to `ClovaSkill`." }}   | Always  |
| `event.payload`   | object  | {{ "`payload` or partial information of the `payload` of the event message sent by the client to Clova. Some `EventRequest` type event messages may have an empty `payload`." if book.TargetCountryCode == "KR" else "`payload` or partial information of the `payload` of the event message sent by the client to Clova. Some event messages or `EventRequest` type event messages that distinguish whether a skill action is enabled or disabled may have an empty `payload`." }}  | Always  |
| `requestId`       | string  | Dialogue ID (`event.header.dialogRequestId`) generated when the client sends information to Clova.    | Always   |
| `timestamp`       | string  | The send time of when the client sends information to Clova (Timestamp, <a href="https://en.wikipedia.org/wiki/ISO_8601" target="_blank">ISO 8601</a>)<div class="note"><p><strong>Note!</strong></p><p>Since CEK does not guarantee the correct order in <code>EventRequest</code> type requests, you can use this field value to determine the order of client requests.</p></div>                    |<!-- -->|
| `type`            | string  | The type of request message. The value is always set to `"EventRequest"`.         | Always |

Here is an example of the `request` object field of the `EventRequest` type message.

{% if book.TargetCountryCode == "KR" %}
```json
// Example 1. When metadata on music is requested
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

// Example 2. When music is stopped
"request": {
  "type": "EventRequest",
  "requestId": "e5464288-50ff-4e99-928d-4a301e083d41",
  "timestamp": "2017-09-05T05:41:21Z",
  "event": {
    "namespace": "AudioPlayer",
    "name": "PlayStopped",
    "payload": {}
  }
}
```
{% elif book.TargetCountryCode == "JP" %}
```json
// Example 1. When a skill is enabled
"request": {
  "type": "EventRequest",
  "requestId": "f09874hiudf-sdf-4wku-flksdjfo4hjsdf",
  "timestamp": "2018-06-11T09:19:23Z",
  "event" : {
    "namespace":"ClovaSkill",
    "name":"SkillEnabled",
    "payload": null
  }
}

// Example 2. When a skill is disabled
"request": {
  "type": "EventRequest",
  "requestId": "f09874hiudf-sdf-4wku-flksdjfo4hjsdf",
  "timestamp": "2018-06-19T11:37:21Z",
  "event" : {
    "namespace":"ClovaSkill",
    "name":"SkillEnabled",
    "payload": null
  }
}

// Example 3. When metadata on music is requested
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

// Example 4. When music is stopped
"request": {
  "type": "EventRequest",
  "requestId": "e5464288-50ff-4e99-928d-4a301e083d41",
  "timestamp": "2017-09-05T05:41:21Z",
  "event": {
    "namespace": "AudioPlayer",
    "name": "PlayStopped",
    "payload": {}
  }
}
```
{% endif %}

#### IntentRequest {#CustomExtIntentRequest}
`IntentRequest` type is a request type that delivers a user request in order to have its details executed. When developing the service, you must [define an interaction model](/Design/Design_Guideline_For_Extension.md#DefineInteractionModel) for receiving user requests. The interaction model can be registered via the [Clova Developer Center](/DevConsole/ClovaDevConsole_Overview.md). In this process, the distinguished user request is defined as information type called an "intent." The analyzed utterance information of the user is converted to an intent and is delivered to the extension via the `intent` field.

The `request` object field configuration of the `IntentRequest` type message is as follows:

{% raw %}
```json
{
  "type": "IntentRequest",
  "intent": {
    "name": {{string}},
    "slots": {{object}}
  }
}
```
{% endraw %}

| Field name       | Data type    | Description                     | Included |
|---------------|---------|-----------------------------|:---------:|
| `intent`        | object  | Object that stores the analyzed details of a user request [intent](/Design/Design_Guideline_For_Extension.md#Intent).                          | Always |
| `intent.name`   | string  | The name of the Intent. The [intent](/Design/Design_Guideline_For_Extension.md#Intent) defined in the interaction model can be identified with this field.  | Always |
| `intent.slots`  | object  | The object that stores the information required when the extension handles the intent (slot). Configuration of this field may vary depending on the [intent](/Design/Design_Guideline_For_Extension.md#Intent) entered in `intent.name` field. | Always |
| `type`          | string  | The type of request message. The value is always set to `"IntentRequest"`.                                                                     | Always |

Here is an example of the `request` object field of the `IntentRequest` type message.

```json
"request": {
  "type": "IntentRequest",
  "intent": {
    "name": "OrderPizza",
    "slots": {
      "pizzaType": {
        "name": "pizzaType",
        "value": "Pepperoni"
      }
    }
  }
}
```

#### LaunchRequest {#CustomExtLaunchRequest}
`LaunchRequest` type is a request type that indicates that a user has started using a specific extension. For example, the user has declared they want to use a specific skill by saying "Start DiceDrawer." The [`IntentRequest`](#CustomExtIntentRequest) type message of the extension is received until the user declares they want to stop using the skill.

The `request` object field configuration of the `LaunchRequest` type message is as follows:

{% raw %}
```json
{
  "type": "LaunchRequest"
}
```
{% endraw %}

| Field name       | Data type    | Description                     | Included |
|---------------|---------|-----------------------------|:---------:|
| `type`          | string  | The type of request message. The value is always set to `"LaunchRequest"`. | Always |

#### SessionEndedRequest {#CustomExtSessionEndedRequest}
`SessionEndedRequest` request type that indicates that a user has finished using a specific skill. This message is received in the following situations:
* When the user has requested to stop using a skill
* When there is no user input for a specific amount of time (Timeout)
* When an error has occurred

<div class="note">
  <p><strong>Note!</strong></p>
  <p>If the extension first declares the end of the session using the <code>shouldEndSession</code> field of <a href="#CustomExtResponseMessage">response message</a>, this message will not be received.</p>
</div>


The `request` object field configuration of the `SessionEndedRequest` type message is as follows:

{% raw %}
```json
{
  "type": "SessionEndedRequest"
}
```
{% endraw %}

| Field name       | Data type    | Description                     | Included |
|---------------|---------|-----------------------------|:---------:|
| `type`          | string  | The type of request message. The value is always set to `"SessionEndedRequest"`. | Always |

### Response message {#CustomExtResponseMessage}
The extension must deliver a response message after handling a request message (HTTP Response). This section explains the structure and the fields of the response message.

#### Message structure
{% raw %}
```json
{
  "response": {
    "card": {{object}},
    "directives": [
      {
        "header": {
          "messageId": {{string}},
          "name": {{string}},
          "namespace": {{string}}
        },
        "payload": {{object}}
      }
    ],
    "outputSpeech": {
      "type": {{string}},
      "values": {{SpeechInfoObject|SpeechInfoObject array}},
      "brief": {{SpeechInfoObject}},
      "verbose": {
        "type": {{string}},
        "values": {{SpeechInfoObject|SpeechInfoObject array}},
      }
    },
    "reprompt": {
      "outputSpeech": {
        "type": {{string}},
        "values": {{SpeechInfoObject|SpeechInfoObject array}},
        "brief": {{SpeechInfoObject}},
        "verbose": {
          "type": {{string}},
          "values": {{SpeechInfoObject|SpeechInfoObject array}},
        }
      }
    },
    "shouldEndSession": {{boolean}},
  },
  "sessionAttibutes": {{object}},
  "version": {{string}}
}
```
{% endraw %}

#### Message fields
| Field name       | Data type    | Description                     | Required |
|---------------|---------|-----------------------------|:---------:|
| `response`                               | object       | The object containing the response information of the extension.                            | Required |
| `response.card`                          | object       | The data is in the [content template](/CIC/References/Content_Templates.md) format and can be displayed on the client screen via this field. If data exists in this field, CIC sends the [Clova.RenderTemplate](/CIC/References/CICInterface/Clova.md#RenderTemplate) directive message to the client. If the object is empty, CIC delivers the [Clova.RenderText](/CIC/References/CICInterface/Clova.md#RenderText) directive message to the client to display the values in the `response.outputSpeech.values` field.        | Required |
| `response.directives[]`                  | object array | The directive message that the extension delivers to CEK. The `response.directives` field is normally used to provide audio content and supports the following {{ "[CIC API](/CIC/References/CIC_API.md)" if book.TargetCountryCode == "KR" else "[CIC API](#CICAPIforAudioPlayback)" }} directive messages: <ul><li><code>AudioPlayer.Play</code></li><li><code>AudioPlayer.StreamDeliver</code></li><li><code>PlaybackController.Pause</code></li><li><code>PlaybackController.Resume</code></li><li><code>PlaybackController.Stop</code></li><li><code>TemplateRuntime.RenderPlayerInfo</code></li>.</ul> | Required |
| `response.directives[].header`           | object       | The header of the directive.                                          | Required |
| `response.directives[].header.messageId` | string       | The message ID (UUID). The message ID used to distinguish individual messages.   | Required |
| `response.directives[].header.name`      | string       | The API name of directive.                                      | Required |
| `response.directives[].header.namespace` | string       | The API namespace of the directive message.                                | Required |
| `response.directives[].payload`          | object       | The object that contains information related to the directive. You can configure the payload object and the field values differently based on the directive message.         | Required |
| `response.outputSpeech`                  | object       | The object that contains the information to be synthesized as a voice. The synthesized voice information is delivered to the client via CIC.              | Required |
| `response.outputSpeech.brief`            | [SpeechInfoObject](#CustomExtSpeechInfoObject) | Summary information for voice output.                    | Optional |
| `response.outputSpeech.type`             | string       | The type of voice information to output. <ul><li><code>"SimpleSpeech"</code>: Voice information in a simple sentence format. This is the most basic type, and the <code>response.outputSpeech.values</code> field must have a <a href="#CustomExtSpeechInfoObject"><code>SpeechInfoObject</code></a> object if this value is designated.</li><li><code>"SpeechList"</code>: Voice information with a complex sentence type. This is used when outputting many sentences. If this value is designated, the <code>response.outputSpeech.values</code> field must have <a href="#CustomExtSpeechInfoObject"><code>SpeechInfoObject</code></a> object array.</li><li><code>"SpeechSet"</code>: Voice information in a combined format. This is used to deliver the summary of the voice information and detailed voice information to a client device without a display. If this value is designated, it must have the <code>response.outputSpeech.brief</code> and <code>response.outputSpeech.verbose</code> fields instead of the <code>response.outputSpeech.values</code> field.</li></ul> | Required |
| `response.outputSpeech.values[]`           | [SpeechInfoObject](#CustomExtSpeechInfoObject) or [SpeechInfoObject](#CustomExtSpeechInfoObject) array | The object or object array that contains the voice information to output from the client device. | Optional |
| `response.outputSpeech.verbose`          | object       | It is used when delivering content to a client device without a display and contains detailed voice information. | Optional |
| `response.outputSpeech.verbose.type`     | string       | The type of voice information to output. Only the voice information in simple and complex sentence formats can be entered. <ul><li><code>"SimpleSpeech"</code>: Voice information in a simple sentence format. Used when delivering the most basic voice information. If this value is designated, the <code>response.outputSpeech.verbose.values</code> field must have <a href="#CustomExtSpeechInfoObject"><code>SpeechInfoObject</code></a> object.</li><li><code>"SpeechList"</code>: Voice information in a complex sentence format. It is used when outputting many sentences. If this value is designated, the <code>response.outputSpeech.verbose.values</code> field must have <a href="#CustomExtSpeechInfoObject"><code>SpeechInfoObject</code></a> object array.</li></ul> | Required |
| `response.outputSpeech.verbose.values[]`           | [SpeechInfoObject](#CustomExtSpeechInfoObject) or [SpeechInfoObject](#CustomExtSpeechInfoObject) array | The object or object array that contains the detailed voice information to output from the client device. | Required |
| `response.reprompt`                               | object       | The object that contains voice information to encourage additional user utterances. If the `response.reprompt` field is used, the intention to continue multi-turn dialogue can be asked to the user or the user can be encouraged to enter additional mandatory information. Generally, if there is no additional utterance from the user during a multi-turn dialogue, the multi-turn dialogue exits automatically after the waiting time for input is exceeded. But if the `response.reprompt` field is used, the Clova outputs the voice written in the `response.reprompt` field after the client exceeds the waiting time for input to deliver the [`SpeechSynthesizer.Speak`](/CIC/References/CICInterface/SpeechSynthesizer.md#Speak) directive message and the [`SpeechRecognizer.ExpectSpeech`](/CIC/References/CICInterface/SpeechRecognizer.md#ExpectSpeech) directive message to the client to receive additional utterances of the user.<div class="note"><p><strong>Note!</strong></p><p><code>response.reprompt</code> The field is valid when the <code>response.shouldEndSession</code> field value is entered as <code>false</code>. It is recommended to send voice information in a short sentence format (<code>"SimpleSpeech"</code>). If the <code>response.reprompt</code> field is used, the input waiting time can be extended only once.</p></div> | Optional |
| `response.reprompt.outputSpeech`                  | object       | The object that contains the information to be synthesized as a voice. The synthesized voice information is delivered to the client via CIC.              | Required |
| `response.reprompt.outputSpeech.brief`            | [SpeechInfoObject](#CustomExtSpeechInfoObject) | Summary information for voice output.                    | Optional |
| `response.reprompt.outputSpeech.type`             | string       | The type of voice information to output. <ul><li>"SimpleSpeech": Voice information in a simple sentence format. This is the most basic type, and the <code>response.outputSpeech.values</code> field must have a <a href="#CustomExtSpeechInfoObject"><code>SpeechInfoObject</code></a> object if this value is designated.</li><li><code>"SpeechList"</code>: Voice information with a complex sentence type. This is used when outputting many sentences. If this value is designated, the <code>response.outputSpeech.values</code> field must have <a href="#CustomExtSpeechInfoObject"><code>SpeechInfoObject</code></a> object array.</li><li><code>"SpeechSet"</code>: Voice information in a combined format. This is used to deliver the summary of the voice information and detailed voice information to a client device without a display. If this value is designated, it must have the <code>response.outputSpeech.brief</code> and <code>response.outputSpeech.verbose</code> fields instead of the <code>response.outputSpeech.values</code> field.</li></ul> | Required |
| `response.reprompt.outputSpeech.values[]`           | [SpeechInfoObject](#CustomExtSpeechInfoObject) or [SpeechInfoObject](#CustomExtSpeechInfoObject) array | The object or object array that contains the voice information to output from the client device. | Optional |
| `response.reprompt.outputSpeech.verbose`          | object       | It is used when delivering content to a client device without a display and contains detailed voice information. | Optional |
| `response.reprompt.outputSpeech.verbose.type`     | string       | The type of voice information to output. Only the voice information in simple and complex sentence formats can be entered. <ul><li><code>"SimpleSpeech"</code>: Voice information in a simple sentence format. Used when delivering the most basic voice information. If this value is designated, the <code>response.outputSpeech.verbose.values</code> field must have <a href="#CustomExtSpeechInfoObject"><code>SpeechInfoObject</code></a> object.</li><li><code>"SpeechList"</code>: Voice information in a complex sentence format. It is used when outputting many sentences. If this value is designated, the <code>response.outputSpeech.verbose.values</code> field must have <a href="#CustomExtSpeechInfoObject"><code>SpeechInfoObject</code></a> object array.</li></ul> | Required |
| `response.reprompt.outputSpeech.verbose.values[]`           | [SpeechInfoObject](#CustomExtSpeechInfoObject) or [SpeechInfoObject](#CustomExtSpeechInfoObject) array | The object or object array that contains the detailed voice information to output from the client device. | Required |
| `response.shouldEndSession`              | boolean      | Session end flag A field that indicates that a user has finished using a specific extension. Used when the extension notifies the end of use first before receiving the request message of [`SessionEndedRequest`](#CustomExtSessionEndedRequest) type.<ul><li>true: End of use</li><li>false: Continue use. A multi-turn dialogue with the user is attempted.</li></ul> | Required |
| `sessionAttributes`                      | object       | The object that stores information necessary for a multi-turn dialogue with the user. A custom extension sends intermediate information to CEK using the `sessionAttributes` field and receives the corresponding information to the `session.sessionAttributes` field of the [request message](#CustomExtRequestMessage) when receiving additional user requests. `sessionAttributes` The object must be configured as a key-value pair and can be defined arbitrarily when implementing the custom extension. If there is no value to store, enter an empty object. | Required |
| `version`                                | string       | Version of message format (CEK version).                        | Required |

<div class="note">
  <p><strong>Note!</strong></p>
  <p>A prior arrangement is necessary in case of having to send an customized directive message of the extension through the <code>response.directives</code> field. Contact your Clova representative for more information.</p>
</div>

#### SpeechInfoObject {#CustomExtSpeechInfoObject}
SpeechInfoObject is an object reused in the `response.outputSpeech` of a response message. The object contains simple utterance information in the smallest unit of voice information to be outputted to the user. This object has the following fields:

| Field name        | Data type         | Description                                                                | Required |
|----------------|--------------|--------------------------------------------------------------------|:-----:|
| `lang`           | string       | Code of the language to use for voice synthesis. The current values are as follows:<ul><li><code>"en"</code>: English</li><li><code>"ja"</code>: Japanese</li><li><code>"ko"</code>: Korean</li><li><code>""</code>: If the <code>type</code> field value is <code>"URL"</code>, this field has an empty string.</li></ul>         | Required |
| `type`           | string       | Type of voice to use. The type of `value` field value varies depending on the value of this field. The current values are as follows:<ul><li><code>"PlainText"</code>: regular text</li><li><code>"URL"</code>: URI of the file that can play voice and music.</li></ul>            | Required |
| `value`          | string       | Content to synthesize voice or URI of audio file.                                    | Required |

#### Message example
{% raw %}
```json
// Example 1: Return SimpleSpeech voice information - regular text
{
  "version": "0.1.0",
  "sessionAttributes": {},
  "response": {
    "outputSpeech": {
      "type": "SimpleSpeech",
      "values": {
          "type": "PlainText",
          "lang": "en",
          "value": "Hi, nice to meet you"
      }
    },
    "card": {},
    "directives": [],
    "shouldEndSession": false
  }
}

// Example 2: Return SpeechList voice information - use regular text, URL type
{
  "version": "0.1.0",
  "sessionAttributes": {},
  "response": {
    "outputSpeech": {
      "type": "SpeechList",
      "values": [
        {
          "type": "PlainText",
          "lang": "ko",
          "value": "I will sing a song."
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

// Example 3: Return SpeechSet voice information - summary, detailed voice information
{
  "version": "0.1.0",
  "sessionAttributes": {},
  "response": {
    "outputSpeech": {
      "type": "SpeechSet",
      "brief": {
        "type": "PlainText",
        "lang": "ko",
        "value": "Here is the weather forecast."
      },
      "verbose": {
        "type": "SpeechList",
        "values": [
          {
              "type": "PlainText",
              "lang": "ko",
              "value": "Monsoon rains throughout the country until the weekend…The heat wave has died down."
          },
          {
              "type": "PlainText",
              "lang": "ko",
              "value": "Monsoon rains throughout the country tomorrow…Watch out for torrential rain in various regions."
          }
          ...
        ]
      }
    },
    "card": {},
    "directives": [],
    "shouldEndSession": true
  }
}

// Example 4: Stores intermediate information in multi-turn dialogue - use of sessionAttributes
{
  "version": "0.1.0",
  "sessionAttributes": {
    "RequestedIntent": "OrderPizza",
    "pizzaType": "Pepperoni pizza"
  },
  "response": {
    "outputSpeech": {
      "type": "SimpleSpeech",
      "values": {
          "type": "PlainText",
          "lang": "ko",
          "value": "How many boxes of pizza do you want to order?"
      }
    },
    "card": {},
    "directives": [],
    "shouldEndSession": false
  }
}

// Example 5: Encourages additional user utterances in multi-turn dialogue - use of reprompt
{
  "version": "0.1.0",
  "sessionAttributes": {
    "RequestedIntent": "OrderPizza",
    "pizzaType": "Pepperoni pizza"
  },
  "response": {
    "outputSpeech": {
      "type": "SimpleSpeech",
      "values": {
          "type": "PlainText",
          "lang": "ko",
          "value": "How many boxes of pizza do you want to order?"
      }
    },
    "card": {},
    "reprompt" : {
      "outputSpeech" : {
        "type" : "SimpleSpeech",
        "values" : {
          "type" : "PlainText",
          "lang" : "ko",
          "value" : "If you have nothing to say, would you like to cancel the order?"
        }
      }
    },
    "shouldEndSession": false
  }
}

// Example 6: Directs the client to play the audio content (uses the response.directives[] field)
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
            },
            "playBehavior": "REPLACE_ALL"
          }
        }
      }
    ],
    "outputSpeech": {},
    "shouldEndSession": true
  }
}
```
{% endraw %}

#### See also
* [Returning a custom extension response](/CEK/Guides/Build_Custom_Extension.md#ReturnCustomExtensionResponse)
* [Content template](/CIC/References/Content_Templates.md)

{% if book.TargetCountryCode == "JP" %}
## CIC API related to the audio content playback {#CICAPIforAudioPlayback}

CIC API is the message specification exchanged when the client device of a user communicates with Clova. The CIC API explained here is supported by CEK to [provide audio content](/CEK/Guides/Build_Custom_Extension.md#ProvideAudioContent) for the custom extension. CEK sends by filling out the event message the client sent to Clova in the `event` field of the [`EventRequest`](#CustomExtEventRequest) type message. Also, the custom extension must send the directive message related to the audio content playback by filling out in the `response.directives[]` field of the [`Response messages`](#CustomExtResponseMessage) to provide audio content to the user.

Therefore, if your custom extension provides audio content, you need an understanding of the following CIC API:

| Namespace   | Message name         | Type  | Description                                   |
|-------------|------------------|-----------|---------------------------------------------|
| AudioPlayer | [`Play`](#Play)                       | Directive | Instructs the client to either play or add to the playback queue the specified audio stream.                         |
| AudioPlayer | [`PlayFinished`](#PlayFinished)       | Event     | Reports to CIC that the client has finished playback with the information on the audio stream.     |
| AudioPlayer | [`PlayPaused`](#PlayPaused)           | Event     | Reports to CIC that the client has paused playback with the information on the audio stream. |
| AudioPlayer | [`PlayResumed`](#PlayResumed)         | Event     | Reports to CIC that the client has resumed playback with the information on the audio stream.         |
| AudioPlayer | [`PlayStarted`](#PlayStarted)         | Event     | Reports to CIC that the client has started playback with the information on the audio stream.    |
| AudioPlayer | [`PlayStopped`](#PlayStopped)         | Event     | Reports to CIC that the client has stopped playback with the information on the audio stream.    |
| AudioPlayer | [`ProgressReportDelayPassed`](#ProgressReportPositionPassed) | Event | Reports the current playback state to CIC after the specified time (delay) has passed playing the audio stream. |
| AudioPlayer | [`ProgressReportIntervalPassed`](#ProgressReportPositionPassed)| Event | Reports the current playback state to CIC on a regular interval while playing an audio stream. |
| AudioPlayer | [`ProgressReportPositionPassed`](#ProgressReportPositionPassed) | Event | Reports the current playback state to CIC when the client reaches a specific playback point. |
| AudioPlayer | [`StreamDeliver`](#StreamDeliver)     | Directive | Receives the audio stream information that can be played as a response to the [`AudioPlayer.StreamRequested`](#StreamRequested) event. |
| AudioPlayer | [`StreamRequested`](#StreamRequested) | Event     | Requests CIC for additional information needed for audio stream playback such as a streaming URL.               |
| PlaybackController | [`Pause`](#Pause)              | Directive | Instructs the client to pause the current audio stream.        |
| PlaybackController | [`Resume`](#Resume)            | Directive | Instructs the client to resume playing the audio stream.                |
| PlaybackController | [`Stop`](#Stop)                | Directive | Instructs the client to stop playing an audio stream.                |
| TemplateRuntime | [`RenderPlayerInfo`](#RenderPlayerInfo)        | Directive | Instructs the client to display the sent playback metadata such as a playlist, album image, and lyrics on the media player. |
| TemplateRuntime | [`RequestPlayerInfo`](#RequestPlayerInfo)      | Event     | Requests CIC for playback metadata such as a playlist, album image, and lyrics to display on the media player. |

## Play directive {#Play}
Instructs the client to either play or add to the playback queue the specified audio stream.

### Payload fields
| Field name       | Data type    | Description                     | Included |
|---------------|---------|-----------------------------|:---------:|
| `audioItem`               | object | The metadata of an audio stream to play and audio stream information required for playback.                     | Always |
| `audioItem.artImageUrl`   | string | The URL for the image on the audio (e.g. album image).                                                  | Conditional  |
| `audioItem.audioItemId`   | string | The ID of an audio stream. Use this ID to remove redundant Play directives. | Always |
| `audioItem.headerText`    | string | The text field used mainly to indicate the title of current play list.                                                | Conditional  |
| `audioItem.stream`        | [AudioStreamInfoObject](#AudioStreamInfoObject) | The audio stream information required for playback.        | Always |
| `audioItem.titleSubText1` | string | The text field used mainly to indicate the name of the artist.                                                          | Always |
| `audioItem.titleSubText2` | string | The text field used mainly to indicate the name of the album.                                                      | Conditional |
| `audioItem.titleText`     | string | The text field used mainly to indicate the title of the currently playing music.                                                         | Always  |
| `playBehavior`            | string | Indicates when to play the audio stream received from the directive. <ul><li><code>"REPLACE_ALL"</code>: Clear the playback queue and play the audio stream immediately.</li><li><code>"ENQUEUE"</code>: Clear the playback queue and add the audio stream.</li></ul> | Always |
| `source`                  | object | The information of the audio streaming service.                                                    | Always |
| `source.logoUrl`          | string | The URL for the logo of the audio streaming service. If this field is unavailable or undefined or if the logo cannot be displayed, you must at least display the name of the music service provider specified in the `source.name` field.  | Conditional |
| `source.name`             | string | The text field containing the name of the audio streaming service.                                                        | Always |

### Remarks
Based on the policy of music service providers, certain information required for playback (e.g. streaming URL) may not be shared to clients until right before playback. Whether additional information will be requested is specified in the `audioItem.stream.urlPlayable` field, as shown below:
* `urlPlayable` is `true`: No additional information is required. You can play the audio stream only with the URL specified in the `audioItem.stream.url` field.
* `urlPlayable` is `false`: Additional information is required for you to play the given audio stream. Make a request for additional information with the [`AudioPlayer.StreamRequested`](#StreamRequested) event.

### Message example
{% raw %}

```json
// Example: The audio stream that can be played only with the stream URL
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
}

// Example: The audio stream that cannot be played only with the stream URL
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
        "logoUrl": "https://img.musicproviderdomain.net/logo_180125.png"
      },
      "playBehavior": "REPLACE_ALL"
    }
  }
}
```

{% endraw %}

### See also
* [`AudioPlayer.PlayPaused`](#PlayPaused)
* [`AudioPlayer.PlayResumed`](#PlayResumed)
* [`AudioPlayer.PlayStarted`](#PlayStarted)
* [`AudioPlayer.PlayStopped`](#PlayStopped)
* [`AudioPlayer.ProgressReportDelayPassed`](#ProgressReportDelayPassed)
* [`AudioPlayer.ProgressReportIntervalPassed`](#ProgressReportIntervalPassed)
* [`AudioPlayer.ProgressReportPositionPassed`](#ProgressReportPositionPassed)
* [`AudioPlayer.StreamRequested`](#StreamRequested)

### AudioPlayer.PlayFinished event {#PlayFinished}
Reports to CIC that the client has finished playback with the information on the audio stream.

#### Payload fields

| Field name       | Data type    | Description                     | Required |
|---------------|---------|-----------------------------|:---------:|
| `token`                | string | The token of the audio stream.    | Required |
| `offsetInMilliseconds` | number | The current-time indicator of the audio playing (in milliseconds).                         | Required  |

#### Message example
{% raw %}

```json
{
  "context": [
    ...
  ],
  "event": {
    "header": {
      "namespace": "AudioPlayer",
      "name": "PlayFinished",
      "messageId": "4e4080d6-c440-498a-bb73-ae86c6312806"
    },
    "payload": {
      "token": "TR-NM-4435786",
      "offsetInMilliseconds": 183000
    }
  }
}
```

{% endraw %}

#### See also
* [`AudioPlayer.Play`](#Play)
* [`AudioPlayer.PlayStarted`](#PlayStarted)
* [`AudioPlayer.PlayStopped`](#PlayStopped)

### AudioPlayer.PlayPaused event {#PlayPaused}
Reports to CIC that the client has paused playback with the information on the audio stream.

#### Payload fields

| Field name       | Data type    | Description                     | Required |
|---------------|---------|-----------------------------|:---------:|
| `token`                | string | The token of the audio stream. | Required |
| `offsetInMilliseconds` | number | The current-time indicator of the audio playing (in milliseconds).                         | Required  |

#### Message example
{% raw %}

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

{% endraw %}

#### See also
* [`AudioPlayer.Play`](#Play)
* [`AudioPlayer.PlayResumed`](#PlayResumed)

### AudioPlayer.PlayResumed event {#PlayResumed}

Reports to CIC that the client has resumed playback with the information on the audio stream.

#### Payload fields

| Field name       | Data type    | Description                     | Required |
|---------------|---------|-----------------------------|:---------:|
| `token`                | string | The token of the audio stream. | Required |
| `offsetInMilliseconds` | number | The current-time indicator of the audio playing (in milliseconds).                         | Required  |

#### Message example
{% raw %}

```json
{
  "context": [
    ...
  ],
  "event": {
    "header": {
      "namespace": "AudioPlayer",
      "name": "PlayResumed",
      "messageId": "4e4080d6-c440-498a-bb73-ae86c6312806"
    },
    "payload": {
      "token": "TR-NM-4435786",
      "offsetInMilliseconds": 83100
    }
  }
}
```

{% endraw %}

#### See also
* [`AudioPlayer.Play`](#Play)
* [`AudioPlayer.PlayPaused`](#PlayPaused)

### AudioPlayer.PlayStarted event {#PlayStarted}
Reports to CIC that the client has started playback with the information on the audio stream.

#### Payload fields

| Field name       | Data type    | Description                     | Required |
|---------------|---------|-----------------------------|:---------:|
| `token`                | string | The token of the audio stream. | Required |
| `offsetInMilliseconds` | number | The current-time indicator of the audio playing (in milliseconds).                         | Required  |

#### Message example
{% raw %}

```json
{
  "context": [
    ...
  ],
  "event": {
    "header": {
      "namespace": "AudioPlayer",
      "name": "PlayStarted",
      "messageId": "4e4080d6-c440-498a-bb73-ae86c6312806"
    },
    "payload": {
      "token": "TR-NM-4435786",
      "offsetInMilliseconds": 0
    }
  }
}
```

{% endraw %}

#### See also
* [`AudioPlayer.Play`](#Play)
* [`AudioPlayer.PlayStopped`](#PlayStopped)

### AudioPlayer.PlayStopped event {#PlayStopped}
Reports to CIC that the client has stopped playback with the information on the audio stream.

#### Payload fields

| Field name       | Data type    | Description                     | Required |
|---------------|---------|-----------------------------|:---------:|
| `token`                | string | The token of the audio stream. | Required |
| `offsetInMilliseconds` | number | The current-time indicator of the audio playing (in milliseconds).                         | Required  |

#### Message example
{% raw %}

```json
{
  "context": [
    ...
  ],
  "event": {
    "header": {
      "namespace": "AudioPlayer",
      "name": "PlayStopped",
      "messageId": "4e4080d6-c440-498a-bb73-ae86c6312806"
    },
    "payload": {
      "token": "TR-NM-4435786",
      "offsetInMilliseconds": 83100
    }
  }
}
```

{% endraw %}

#### See also
* [`AudioPlayer.Play`](#Play)
* [`AudioPlayer.PlayStarted`](#PlayStarted)

### AudioPlayer.ProgressReportDelayPassed event {#ProgressReportDelayPassed}
Reports the current playback state to CIC after the specified time (delay) has passed playing the audio stream.

#### Payload fields

| Field name       | Data type    | Description                     | Required |
|---------------|---------|-----------------------------|:---------:|
| `token`                | string | The token of the audio stream. | Required |
| `offsetInMilliseconds` | number | The current-time indicator of the audio playing (in milliseconds).                         | Required  |

#### Message example
{% raw %}

```json
{
  "context": [
    ...
  ],
  "event": {
    "header": {
      "namespace": "AudioPlayer",
      "name": "ProgressReportDelayPassed",
      "messageId": "4e4080d6-c440-498a-bb73-ae86c6312806"
    },
    "payload": {
      "token": "TR-NM-4435786",
      "offsetInMilliseconds": 60000
    }
  }
}
```

{% endraw %}

#### See also
* [`AudioPlayer.Play`](#Play)
* [`AudioPlayer.ProgressReportIntervalPassed`](#ProgressReportIntervalPassed)
* [`AudioPlayer.ProgressReportPositionPassed`](#ProgressReportPositionPassed)

### AudioPlayer.ProgressReportIntervalPassed event {#ProgressReportIntervalPassed}
Reports the current playback state to CIC on a regular interval while playing an audio stream.

#### Payload fields

| Field name       | Data type    | Description                     | Required |
|---------------|---------|-----------------------------|:---------:|
| `token`                | string | The token of the audio stream. | Required |
| `offsetInMilliseconds` | number | The current-time indicator of the audio playing (in milliseconds).                         | Required  |

#### Message example
{% raw %}

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

{% endraw %}

#### See also
* [`AudioPlayer.Play`](#Play)
* [`AudioPlayer.ProgressReportDelayPassed`](#ProgressReportDelayPassed)
* [`AudioPlayer.ProgressReportPositionPassed`](#ProgressReportPositionPassed)

### AudioPlayer.ProgressReportPositionPassed event {#ProgressReportPositionPassed}
Reports the current playback state to CIC when the client reaches a specific playback point.

#### Payload fields

| Field name       | Data type    | Description                     | Required |
|---------------|---------|-----------------------------|:---------:|
| `token`                | string | The token of the audio stream. | Required |
| `offsetInMilliseconds` | number | The current-time indicator of the audio playing (in milliseconds).                         | Required  |

#### Message example
{% raw %}

```json
{
  "context": [
    ...
  ],
  "event": {
    "header": {
      "namespace": "AudioPlayer",
      "name": "ProgressReportPositionPassed",
      "messageId": "4e4080d6-c440-498a-bb73-ae86c6312806"
    },
    "payload": {
      "token": "TR-NM-4435786",
      "offsetInMilliseconds": 150000
    }
  }
}
```

{% endraw %}

#### See also
* [`AudioPlayer.Play`](#Play)
* [`AudioPlayer.ProgressReportDelayPassed`](#ProgressReportDelayPassed)
* [`AudioPlayer.ProgressReportIntervalPassed`](#ProgressReportIntervalPassed)

### AudioPlayer.StreamDeliver directive {#StreamDeliver}
Receives the audio stream information that can be played as a response to the [`AudioPlayer.StreamRequested`](#StreamRequested) event. The directive contains the URL for audio streaming as mandatory information so the client can play the audio.

#### Payload fields
| Field name | Data type | Description | Included |
|---------|------|--------|:---------:|
| `audioItemId` | string | The ID of the audio stream. Use this ID to remove redundant Play directives. | Always |
| `audioStream` | [AudioStreamInfoObject](#AudioStreamInfoObject) | The audio stream information required for playback.       | Always |

#### Remarks
Some contents of the `AudioStreamInfoObject` object provided by the `StreamDeliver` directive may be omitted to avoid overlapping of information with the `AudioStreamInfoObject` object provided by the [`AudioPlayer.Play`](#Play) directive. Therefore, you must combine the `payload.audioStream` information of the `StreamDeliver` directive and the received [`Play`](#Play) directive when playing the audio.

#### Message example
{% raw %}

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
        "audioItemId": "5313c879-25bb-461c-93fc-f85d95edf2a0",
        "stream": {
            "token": "b767313e-6790-4c28-ac18-5d9f8e432248",
            "url": "https://sample.musicservice.net/b767313e.mp3"
        }
    }
  }
}
```

{% endraw %}

#### See also
* [`AudioPlayer.Play`](#Play)
* [`AudioPlayer.StreamRequested`](#StreamRequested)

### AudioPlayer.StreamRequested event {#StreamRequested}
Requests CIC for additional information needed for audio stream playback such as a streaming URL.

#### Payload fields
| Field name       | Data type    | Description                     | Required |
|---------------|---------|-----------------------------|:---------:|
| `audioItemId`   | string  | The token of the audio stream.          | Required |
| `audioStream`   | [AudioStreamInfoObject](#AudioStreamInfoObject) | The `audioItem.stream` of the Play directive. | Required |

#### Remarks
Based on the policy of music service providers, certain information required for playback (e.g. streaming URL) may not be shared to clients until right before playback. This event is an interface for the cases where the stream information has to be held back. Do not send this event earlier than right before playing an audio stream.

#### Message example
{% raw %}

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
      "audioItemId": "ac192f4c-8f12-4a58-8ace-e3127eb297a4",
      "audioStream": {
        "beginAtInMilliseconds": 0,
        "progressReport": {
            "progressReportDelayInMilliseconds": null,
            "progressReportIntervalInMilliseconds": null,
            "progressReportPositionInMilliseconds": 60000
        },
        "token": "TR-NM-4435786",
        "urlPlayable": false,
        "url": "clova:TR-NM-4435786"
      }
    }
  }
}
```

{% endraw %}

#### See also
* [`AudioPlayer.Play`](#Play)

### PlaybackController.Pause directive {#Pause}
Instructs the client to pause the current audio stream. Upon receiving the directive, the client must pause playing the audio stream.

#### Payload fields
None

#### Message example
{% raw %}
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
{% endraw %}

#### See also
* [`AudioPlayer.PlayPaused`](#PlayPaused)

### PlaybackController.Resume directive {#Resume}
Instructs the client to resume playing the audio stream. Upon receiving this directive, the client must resume playing the audio stream.

#### Payload fields
None

#### Message example
{% raw %}
```json
{
  "directive": {
    "header": {
      "namespace": "PlaybackController",
      "name": "Resume",
      "dialogRequestId": "42390b12-ae91-4121-aa0a-37f74e8e422b",
      "messageId": "b1f88d7d-bbb8-44fa-a0a2-c5a7553e6f8a"
    },
    "payload": {}
  }
}
```
{% endraw %}

## PlaybackController.Stop directive {#Stop}
Instructs the client to stop playing an audio stream. Upon receiving the directive, the client must stop playing the audio stream.

### Payload fields
None

### Message example
{% raw %}
```json
{
  "directive": {
    "header": {
      "namespace": "PlaybackController",
      "name": "Stop",
      "dialogRequestId": "42390b12-ae91-4121-aa0a-37f74e8e422b",
      "messageId": "b1f88d7d-bbb8-44fa-a0a2-c5a7553e6f8a"
    },
    "payload": {}
  }
}
```
{% endraw %}

### See also
* [`AudioPlayer.PlayStopped`](/CIC/References/CICInterface/AudioPlayer.md#PlayStopped)

#### See also
* [`AudioPlayer.PlayResumed`](#PlayResumed)

### TemplateRuntime.RenderPlayerInfo directive {#RenderPlayerInfo}

Instructs the client to display the sent playback metadata such as a playlist, album image, and lyrics on the media player. If the user has requested to play music, the client plays the media by receiving the [`AudioPlayer.Play`](#Play) directive. If necessary, a client with a display may have to express information related to playback on the media player. For this process, the playback metadata can be requested to CIC using the [`TemplateRuntime.RequestPlayerInfo`](#RequestPlayerInfo) event and the `TemplateRuntime.RenderPlayerInfo` directive is returned. The `TemplateRuntime.RenderPlayerInfo` directive contains playback metadata on the media to play now and media to play later. The client is able to display metadata and play list of the currently playing media by providing the playback metadata of the `TemplateRuntime.RenderPlayerInfo` directive to the user.

#### Payload fields
| Field name       | Data type    | Description                     | Included |
|---------------|---------|-----------------------------|:---------:|
| `displayType`               | string | Display format of the media content.<ul><li><code>"list"</code>: Display a list</li><li><code>"single"</code>: Display a single item</li></ul>       | Always |
| `controls[]`                | object array | The object array that has the button information that the client must display on the media player.             | Always |
| `controls[].enabled`        | boolean      | Indicates whether the buttons specified in the `controls[].name` must be enabled from the media player.<ul><li><code>true</code>: Enable</li><li><code>false</code>: Disable</li></ul>  | Always  |
| `controls[].name`           | string       | The button name. Available values are:<ul><li><code>"NEXT"</code>: Next</li><li><code>"PLAY_PAUSE"</code>: Play/Pause</li><li><code>"PREVIOUS"</code>: Previous</li></ul>  | Always  |
| `controls[].selected`       | boolean      | Indicates whether the media content is selected. This value can be used for displaying user preferences. For example, if this value is set as `true`, the content must be expressed on the relevant UI of the media player since the user has selected it as a preference. <ul><li><code>true</code>: Selected</li><li><code>false</code>: Not selected</li></ul> | Always  |
| `controls[].type`           | string       | The type of button. Currently, only the `"BUTTON"` value is available.  | Always |
| `playableItems[]`           | object array | The object containing the list of media contents that can be played. This field can be an empty array.  | Always |
| `playableItems[].artImageUrl`  | string    | The URL of the image on the media content. This URL is the location of the album cover image or other relevant icons.      | Conditional |
| `playableItems[].controls[]`                | object array  | The object array of button information that must be displayed when playing a specific media content. This object array is omissible.  | Conditional |
| `playableItems[].controls[].enabled`        | boolean      | Indicates whether the buttons specified in the `playableItems[].controls[].name` must be enabled from the media player.<ul><li><code>true</code>: Enable</li><li><code>false</code>: Disable</li></ul>  | Always  |
| `playableItems[].controls[].name`           | string       | The button name. Available values are:<ul><li><code>"NEXT"</code>: Next</li><li><code>"PLAY_PAUSE"</code>: Play/Pause</li><li><code>"PREVIOUS"</code>: Previous</li></ul>  | Always  |
| `playableItems[].controls[].selected`       | boolean      | Indicates whether the media content is selected. This value can be used for displaying user preferences. For example, if this value is set as `true`, the content must be expressed on the relevant UI of the media player since the user has selected it as a preference. <ul><li><code>true</code>: Selected</li><li><code>false</code>: Not selected</li></ul> | Always  |
| `playableItems[].controls[].type`           | string       | The type of button. Currently, only the `"BUTTON"` value is available.  | Always |
| `playableItems[].headerText`       | string        | The text field used mainly to indicate the title of current play list.                                                | Conditional  |
| `playableItems[].isLive`           | boolean       | Whether the content is a real-time content or not.<ul><li><code>true</code>: Real-time content</li><li><code>false</code>: Not a real-time content</li></ul><div class="note"><p><strong>Note!</strong></p><p>If the content is a real-time content, an icon must be displayed to represent the real-time content state (e.g. A live icon).</p></div>  | Conditional  |
| `playableItems[].lyrics[]`         | object array  | The object array containing the lyrics information.                                                            | Conditional  |
| `playableItems[].lyrics[].data`    | string        | The lyrics data. Either this field or the `playableItems[].lyrics[].url` field exists.              | Conditional  |
| `playableItems[].lyrics[].format`  | string        | The format of the lyrics data.<ul><li><code>"LRC"</code>: <a href="https://en.wikipedia.org/wiki/LRC_(file_format)" target="_blank">LRC format</a></li><li><code>"PLAIN"</code>: Plain text format</li></ul>  | Always  |
| `playableItems[].lyrics[].url`     | string        | The URL of the lyrics data. Either this field or the `playableItems[].lyrics[].data` field exists.        | Conditional  |
| `playableItems[].showAdultIcon`    | boolean       | Indicates whether to display the icon for adult media.<ul><li><code>true</code>: Must be displayed.</li><li><code>false</code>: Must not be displayed.</li></ul>   | Always  |
| `playableItems[].titleSubText1`    | string        | The text field used mainly to indicate the name of the artist.                                                          | Always |
| `playableItems[].titleSubText2`    | string        | The text field used mainly to indicate the name of the album.                                                      | Conditional |
| `playableItems[].titleText`        | string        | The text field used mainly to indicate the title of the currently playing music.                                                         | Always  |
| `playableItems[].token`            | string        | The token of the media content.                                                                     | Always |
| `provider`                         | object        | The information of the media content provider.                                                         | Conditional |
| `provider.logoUrl`                 | string        | The logo image URL of the media content provider.                                                         | Conditional |
| `provider.name`                    | string        | The name of the media content provider.                                                                   | Always  |
| `provider.smallLogoUrl`            | string        | The URL of the small logo image of the media content provider.                                                | Conditional |

#### Message example
{% raw %}

```json
{
  "directive": {
    "header": {
      "namespace": "TemplateRuntime",
      "name": "RenderPlayerInfo",
      "dialogRequestId": "34abac3-cb46-611c-5111-47eab87b7",
      "messageId": "ad13f0d6-bb11-ca23-99aa-312a0b213805"
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
          "token": "eJyr5lIqSSyITy4tKs4vUrJSUE="
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
}
```

{% endraw %}

#### See also
* [`AudioPlayer.Play`](#Play)
* [`TemplateRuntime.RequestPlayerInfo`](#RequestPlayerInfo)

### TemplateRuntime.RequestPlayerInfo event {#RequestPlayerInfo}
Requests CIC for playback metadata such as a playlist, album image, and lyrics to display on the media player.

#### Payload fields

| Field name       | Data type    | Description                     | Required |
|---------------|---------|-----------------------------|:---------:|
| `token`        | string  | The token of the audio stream that becomes a reference point to start when importing the playback metadata. | Required |
| `range`        | object  | The scope of the playback metadata. If this field is empty, the client will receive a random number of metadata.   | Optional  |
| `range.before` | number  | Requests n number of playback metadata included in the previous playlist from the base media content.  | Optional  |
| `range.after`  | number  | Requests n number of playback metadata included in the next playlist from the existing media content. For example, if the value of `range.after` is set as `5` without specifying the value of `range.before` field, the playback metadata equivalent to a total of six media contents, including the base media content, is received. | Optional  |

#### Message example

{% raw %}

```json
{
  "context": [
    ...
  ],
  "event": {
    "header": {
      "namespace": "TemplateRuntime",
      "name": "RequestPlayerInfo",
      "messageId": "2fcb6a62-393d-46ad-a5c4-b3db9b640045"
    },
    "payload": {
      "token": "eJyr5lIqSSyITy4tKs4vUrJSUE"
    }
  }
}
```
{% endraw %}

#### See also
* [`AudioPlayer.Play`](#Play)

### AudioStreamInfoObject {#AudioStreamInfoObject}
The object containing streaming details of an audio stream. This object is used when CIC returns streaming details to a client or when the client sends the details of the currently playing audio stream to CIC.

#### Object fields
| Field name       | Data type    | Description                     | Required/Included |
|---------------|---------|-----------------------------|:-------------:|
| `beginAtInMilliseconds`  | number | The playback start point. The unit is in milliseconds. If this field is specified, play the audio stream from the specified point of the stream. If set to 0, play the audio stream from the beginning.          | Required/Always |
| `customData`             | string | The metadata on the current audio in a random format. Any streaming information that cannot be classified into a specific category or defined must be included or entered in this field. Streaming service providers can add custom values to the context of audio stream playback.<div class="danger"><p><strong>Caution!</strong></p><p>Clients must not use the value of this field, as it can cause problems. Make sure to insert these field values in the `stream` field of the <a href="/CIC/References/Context_Objects.html#PlaybackState">PlaybackState context</a> without any changes, when reporting the playback state to CIC.</p></div> | Optional/Conditional  |
| `durationInMilliseconds` | number | The length of the audio stream. The client can play and navigate audio from the playback time specified in the `beginAtInMilliseconds` field by the amount of time defined in this field. For example, if the value of `beginAtInMilliseconds` field is `10000` and the value of this field is `60000`, you can play and navigate within 10-70 seconds of the audio track. The unit is in milliseconds.   | Optional/Conditional  |
| `progressReport`         | object  | The time specified to receive the playback state after the audio starts.                                                  | Optional/Conditional |
| `progressReport.progressReportDelayInMilliseconds`    | number | The duration of time specified to receive the playback state after the audio starts. The unit is in milliseconds. This field can have a null value.  | Optional/Conditional |
| `progressReport.progressReportIntervalInMilliseconds` | number | The interval specified to receive the playback state while audio is playing. The unit is in milliseconds. This field can have a null value.        | Optional/Conditional |
| `progressReport.progressReportPositionInMilliseconds` | number | The point of time specified to receive the playback state to while audio is playing. The unit is in milliseconds. This field can have a null value.    | Optional/Conditional |
| `token`                  | string  | The token of the audio stream.                                                                                   | Required/Always |
| `url`                    | string  | The URL of the audio stream.                                                                                     | Required/Always |
| `urlPlayable`            | boolean | Indicates whether the audio stream URL in the `url` field can be played immediately. <ul><li><code>true</code>: The client can play the audio without additional information.</li><li><code>false</code>: The client requires additional information. To obtain additional information on audio streaming, send the <a href="#StreamRequested"><code>AudioPlayer.StreamRequested</code></a> event to CIC.</li></ul>        | Required/Always |

#### Remarks
* Once the audio section designated in `beginAtInMilliseconds` and `durationInMilliseconds` fields finishes playing, the client must send the [`AudioPlayer.PlayFinished`](#PlayFinished) event to CIC.

#### Object example
{% raw %}

```json
// An example of an audio stream that can be played only with the URL
{
  "beginAtInMilliseconds": 0,
  "episodeId": 22346122,
  "playType": "NONE",
  "podcastId": 12548,
  "progressReport": {
    "progressReportDelayInMilliseconds": null,
    "progressReportIntervalInMilliseconds": 60000,
    "progressReportPositionInMilliseconds": null
  },
  "url": "https://api-ex.podbbang.com/file/12548/22346122",
  "urlPlayable": true
}

// Example: The audio stream that cannot be played only with the stream URL
{
  "beginAtInMilliseconds": 0,
  "progressReport": {
      "progressReportDelayInMilliseconds": null,
      "progressReportIntervalInMilliseconds": null,
      "progressReportPositionInMilliseconds": 60000
  },
  "token": "TR-NM-4435786",
  "urlPlayable": false,
  "url": "clova:TR-NM-4435786"
}
```

{% endraw %}

#### See also
* [`AudioPlayer.Play`](#Play)
* [`AudioPlayer.PlayFinished`](#PlayFinished)
* [`AudioPlayer.StreamRequested`](#StreamRequested)

## Context information related to audio content playback {#ContextObjectforAudioPlayback}
When the client sends the [CIC API](#CICAPIforAudioPlayback) event message to the client, various types of the context information is sent. Among them, the context information related to audio content playback is [`AudioPlayer.PlaybackState`](#PlaybackState).

### AudioPlayer.PlaybackState {#PlaybackState}
`AudioPlayer.PlaybackState` is a format for reporting to CIC the details of media currently playing or the last played media.

#### Object structure
{% raw %}
```json
{
  "header": {
    "namespace": "AudioPlayer",
    "name": "PlaybackState"
  },
  "payload": {
    "offsetInMilliseconds": {{number}},
    "playerActivity": {{string}},
    "repeatMode": {{string}},
    "stream": {{AudioStreamInfoObject}},
    "totalInMilliseconds": {{number}}
  }
}
```
{% endraw %}


#### Payload fields

| Field name       | Data type    | Description                     | Required |
|---------------|---------|-----------------------------|:---------:|
| `offsetInMilliseconds` | number | The most recent playback position (offset) of the recently played media. The unit is in milliseconds. This field is omissible if the `playerActivity` field is set to `"IDLE"`.                                                  | Optional |
| `playerActivity`       | string | The value for indicating the state of player. Values are:<ul><li><code>"IDLE"</code>: Deactivated</li><li><code>"PLAYING"</code>: Playing</li><li><code>"PAUSED"</code>: Paused</li><li><code>"STOPPED"</code>: Stopped</li></ul> | Required |
| `repeatMode`           | string  | The repeat mode.<ul><li><code>"NONE"</code>: None</li><li><code>"REPEAT_ONE"</code>: Repeat one song</li></ul>                                                   | Required  |
| `stream`               | [AudioStreamInfoObject](#AudioStreamInfoObject) | The details of the currently playing media. This field is omissible if the `playerActivity` field is set as `"IDLE"`. Enter the details with the information defined in the `stream` object provided by the [`AudioPlayer.Play`](#Play) directive or [`AudioPlayer.StreamDeliver`](#StreamDeliver) directive. | Optional |
| `totalInMilliseconds`  | number | The total duration of the recently played media. If the value exists in the, `durationInMilliseconds` field of the [AudioStreamInfoObject] (#AudioStreamInfoObject) provided by the [`AudioPlayer.Play`](#Play) directive, enter the field value for this field. The unit is in milliseconds. This field is omissible if the `playerActivity` field is set to `"IDLE"`.                                                               | Optional |

#### Object example

{% raw %}

```json
// Case 1: Playing has stopped
{
  "header": {
    "namespace": "AudioPlayer",
    "name": "PlaybackState"
  },
  "payload": {
    "offsetInMilliseconds": 10000,
    "totalInMilliseconds": 300000,
    "playerActivity": "STOPPED",
    "repeatMode": "NONE",
    "stream": {
      "beginAtInMilliseconds": 0,
      "progressReport": {
        "progressReportDelayInMilliseconds": null,
        "progressReportIntervalInMilliseconds": null,
        "progressReportPositionInMilliseconds": 60000
      },
      "token": "TR-NM-17740107",
      "url": "clova:TR-NM-17740107",
      "urlPlayable": false
    }
  }
}

// Example 2: The player is deactivated
{
  "header": {
    "namespace": "AudioPlayer",
    "name": "PlaybackState"
  },
  "payload": {
    "playerActivity": "IDLE",
    "repeatMode": "NONE"
  }
}
```

{% endraw %}

#### See also
* [`AudioPlayer.Play`](#Play)
* [`AudioPlayer.StreamDeliver`](#StreamDeliver)
* [`AudioPlayer.StreamRequested`](#StreamRequested)
{% endif %}
