## GetExpendableStateRequest {#GetExpendableStateRequest}

기기의 필터나 소모품의 사용량이나 남은 수명을 확인할 때 사용되며, 대상 기기가 보유하고 있는 소모품의 사용량이나 수명 정보를 Clova extension에게 요청합니다. 이 요청에 대한 응답으로 [`GetExpendableStateResponse`](#GetExpendableStateResponse) 메시지를 사용해야 합니다.

| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | IoT 서비스의 사용자 계정의 access token. CEK는 외부 서비스의 인증 서버로부터 획득한 사용자 계정의 access token을 전달합니다. 자세한 설명은 [사용자 계정 연결하기](/CEK/Guides/Link_User_Account.md)를 참조합니다.                          | 항상    |
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | 대상 기기 정보를 담고 있는 객체. `applianceId` 필드는 항상 포함됩니다.     | 항상    |

### Message example

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "GetExpendableStateRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-030"
    }
  }
}
```

### See also
* [`GetExpendableStateResponse`](#GetExpendableStateResponse)

## GetExpendableStateResponse {#GetExpendableStateResponse}
[`GetExpendableStateRequest`](#GetExpendableStateRequest) 메시지에 대한 응답으로 대상 기기가 제공하는 모든 소모품의 사용량이나 수명 정보를 CEK에게 전달합니다.

| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string | 기기에서 요청한 정보를 확인한 시간(`YYYY-MM-DDThh:mm:ss±hh:mm`, <a href="https://en.wikipedia.org/wiki/ISO_8601#Combined_date_and_time_representations" target="_blank">ISO 8601 Combined date and time representations</a> )     | 선택    |
| `expendableInfo[]`           | [ExpendableInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ExpendableInfoObject) array  | 기기 소모품의 사용량이나 수명 정보를 담고 있는 객체                    | 필수  |

### Message example

```json
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetExpendableStateResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "expendableInfo" : [
      {
        "name" : "패킹",
        "remainingTime": "P0001-04-10"
      },
      {
        "name" : "1번 필터",
        "usage": {
          "value" : 80,
          "unit" : "percentage"
        }
      }
    ],
    "applianceResponseTimestamp": "2017-11-23T20:31:18+09:00"
  }
}
```

### See also
* [`GetExpendableStateRequest`](#GetExpendableStateRequest)
