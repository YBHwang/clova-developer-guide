## IncrementChannelConfirmation {#IncrementChannelConfirmation}
[`IncrementChannelRequest`](#IncrementChannelRequest) 메시지에 대한 응답으로 대상 기기가 TV 채널을 높이도록 요청한 후 처리된 결과를 CEK에게 전달합니다.

### Payload fields

| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:---------:|
| `channel`               | [TVChannelInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TVChannelInfoObject) | 현재 TV 채널 정보를 담고 있는 객체                                | 선택    |
| `subChannel`            | [TVChannelInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TVChannelInfoObject) | 현재 TV 채널의 서브 채널 정보를 가지는 객체                         | 선택    |
| `previousState`            | object | 기기의 이전 상황 정보를 담고 있는 객체                           | 선택    |
| `previousState.channel`    | [TVChannelInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TVChannelInfoObject) | 이전 TV 채널 정보를 담고 있는 객체                                | 선택    |
| `previousState.subChannel` | [TVChannelInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TVChannelInfoObject) | 이전 TV 채널의 서브 채널 정보를 가지는 객체                         | 선택    |

### Remarks

대상 기기에서 payload에 입력할 정보를 얻어올 수 없으면 값을 입력하지 않아도 됩니다. 이때 사용자에게 구체적인 정보 없이 기기 제어 요청이 정상 처리되었음을 알려줍니다.

### Message example

```json
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "IncrementChannelConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "channel": {
      "value": 14
    },
    "subChannel": {
      "value": 1
    }
    "previousState": {
      "channel": {
        "value": 15
      },
      "subChannel": {
        "value": 1
      }
    }
  }
}
```

### See also
* [`IncrementChannelRequest`](#IncrementChannelRequest)

## IncrementChannelRequest {#IncrementChannelRequest}
주로 TV나 셋톱박스를 제어할 때 사용되며, 대상 기기가 지정한 수준만큼 TV 채널을 높이도록 Clova Home extension에게 요청합니다. 이 요청에 대한 응답으로 [`IncrementChannelConfirmation`](#IncrementChannelConfirmation) 메시지를 사용해야 합니다.

### Payload fields

| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | IoT 서비스의 사용자 계정의 access token. CEK는 외부 서비스의 인증 서버로부터 획득한 사용자 계정의 access token을 전달합니다. 자세한 설명은 [사용자 계정 연결하기](/CEK/Guides/Link_User_Account.md)를 참조합니다.                          | 항상    |
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | 대상 기기 정보를 담고 있는 객체. `applianceId` 필드는 필수입니다.     | 항상    |
| `deltaChannel`       | [TVChannelInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TVChannelInfoObject)             | 변경할 TV 채널의 크기 정보를 담고 있는 객체                              | 항상    |

### Message example

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "IncrementChannelRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-011"
    },
    "deltaChannel": {
      "value": 1
    }
  }
}
```

### See also
* [`IncrementChannelConfirmation`](#IncrementChannelConfirmation)
