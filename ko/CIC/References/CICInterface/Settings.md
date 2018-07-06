# Settings

Settings 인터페이스는 Clova와 클라이언트 사이에서 클라이언트의 설정 정보를 업데이트하거나 동기화해야 할 때 필요한 지시 메시지와 이벤트 메시지를 다음과 같이 제공합니다.

| 메시지 이름         | 메시지 타입  | 메시지 설명                                 |
|------------------|-----------|-------------------------------------------|
| [`ExpectReport`](#ExpectReport) | Directive | 클라이언트에게 현재의 설정 정보를 보고하도록 지시합니다. 클라이언트는 이 지시 메시지를 받으면 [`Settings.Report`](#Report) 이벤트 메시지를 CIC로 전송해야 합니다. |
| [`Report`](#Report)             | Event     | 클라이언트가 현재의 설정 정보를 CIC에게 보고합니다. 클라이언트가 CIC로부터 [`Settings.ExpectReport`](#ExpectReport) 지시 메시지를 받은 경우 `Settings.Report` 이벤트 메시지를 CIC로 전송해야 합니다.  |
| [`Update`](#Update)             | Directive | 클라이언트에게 `payload`에 저장된 값을 설정 값으로 적용하도록 지시합니다.  |

<div class="note">
  <p><strong>Note!</strong></p>
  <p>설정 정보를 업데이트하거나 동기화하는 구조는 <a href="#WorkFlow">동작 구조</a>를 참조합니다.</p>
</div>

## 동작 구조 {#WorkFlow}

다음과 같은 상황에 Settings를 이용하여 설정 정보를 업데이트하거나 동기화해야 합니다.

* 사용자가 Clova 앱에서 클라이언트 기기의 설정 정보를 조회할 때 **설정 정보 동기화**가 필요합니다.
* 사용자가 클라이언트 기기의 **설정 정보를 Clova 앱에서 변경**했을 때 이를 기기의 설정 정보에 반영해야 합니다.
* 사용자가 클라이언트 기기에서 **직접 설정 정보를 변경**했을 때 이를 Clova 앱에 반영해야 합니다.

Settins를 이용한 설정 정보를 업데이트하거나 동기화하는 구조는 다음과 같습니다.

![](/CIC/Resources/Images/CIC_Settings_Work_Flow_ko.png)

CIC가 Clova 앱으로부터 클라이언트 기기의 **설정 정보 동기화** 요청을 받으면 CIC와 클라이언트 기기는 다음과 같은 순서로 동작하게 됩니다.

1. CIC는 `Settings.ExpectReport` 지시 메시지를 해당 클라이언트 기기에 전송합니다.
2. 클라이언트 기기는 `Settings.Report` 이벤트 메시지를 이용하여 현재 설정 정보를 CIC로 전송해야 합니다.
3. CIC는 보고 받은 설정 정보를 Clova 앱으로 전송합니다.

사용자가 클라이언트 기기의 **설정 정보를 Clova 앱에서 변경**한 경우 CIC는 해당 기기의 설정 변경에 대한 요청을 받게 됩니다. 이때, CIC와 클라이언트 기기는 다음과 같은 순서로 동작하게 됩니다.

1. CIC는 `Settings.Update` 지시 메시지를 해당 클라이언트 기기에 전송합니다.
2. 클라이언트 기기는 `Settings.Report` 이벤트 메시지를 이용하여 변경된 설정 정보를 CIC로 전송해야 합니다.
3. CIC는 보고 받은 설정 정보를 Clova 앱으로 전송합니다.

만약, 사용자가 클라이언트 기기에서 **직접 설정 정보를 변경**했을 때는 Clova 앱의 설정 정보를 갱신하는 동작을 다음과 같이 수행하게 됩니다.

1. 클라이언트 기기는 `Settings.Report` 이벤트 메시지를 이용하여 설정이 변경된 설정 정보를 CIC로 전송해야 합니다.
2. CIC는 보고 받은 설정 정보를 Clova 앱으로 전송합니다.

## ExpectReport directive {#ExpectReport}
클라이언트에게 현재의 설정 정보를 보고하도록 지시합니다. 클라이언트는 이 지시 메시지를 받으면 [`Settings.Report`](#Report) 이벤트 메시지를 CIC로 전송해야 합니다.

### Payload fields

없음

### Remarks

* 이 지시 메시지는 이벤트 메시지에 대한 응답이 아닌 [downchannel](/CIC/Guides/Interact_with_CIC.md#CreateConnection)을 통해 전달됩니다.

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

### See also
* [`Settings.Report`](#Report)

## Report event {#Report}
클라이언트가 현재의 설정 정보를 CIC에게 보고합니다. 클라이언트가 CIC로부터 [`Settings.ExpectReport`](#ExpectReport) 지시 메시지를 받은 경우 `Settings.Report` 이벤트 메시지를 CIC로 전송해야 합니다.

### Context fields

{% include "/CIC/References/CICInterface/Context_Objects_List.md" %}

### Payload fields

| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:---------:|
| `configuration` | object | 사전 정의된 클라이언트의 설정 정보를 가지는 객체. 이 객체의 하위 필드는 모두 string 타입을 가집니다.<div class="note"><p><strong>Note!</strong></p><p>클라이언트 설정 정보에 대한 사전 정의는 제휴 담당자에게 문의합니다.</p></div> | 필수   |

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

### See also
* [`Settings.ExpectReport`](#ExpectReport)

## Update directive {#Update}
클라이언트에게 `payload`에 저장된 값을 설정 값으로 적용하도록 지시합니다.

### Payload fields

| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|---------------|---------|-----------------------------|:---------:|
| `configuration` | object | 사전 정의된 클라이언트의 설정 정보를 가지는 객체. 이 객체의 하위 필드는 모두 string 타입을 가집니다.<div class="note"><p><strong>Note!</strong></p><p>클라이언트 설정 정보에 대한 사전 정의는 제휴 담당자에게 문의합니다.</p></div> | 항상   |

### Remarks

* 이 지시 메시지는 이벤트 메시지에 대한 응답이 아닌 [downchannel](/CIC/Guides/Interact_with_CIC.md#CreateConnection)을 통해 전달됩니다.

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

### See also
* [`Settings.Report`](#Report)
