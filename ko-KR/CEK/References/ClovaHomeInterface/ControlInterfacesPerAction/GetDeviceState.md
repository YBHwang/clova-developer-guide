## GetDeviceStateRequest {#GetDeviceStateRequest}

대상 기기가 제공하는 모든 상태 정보와 측정 정보를 확인할 때 사용됩니다. 예를 들면, 공기 청정기로부터 공기질, 습도, 미세 먼지, 초미세 먼지 정보를 각각 [`GetAirQualityRequest`](#GetAirQualityRequest), [`GetHumidityRequest`](#GetHumidityRequest), [`GetFineDustRequest`](#GetFineDustRequest), [`GetUltraFineDustRequest`](#GetUltraFineDustRequest) 메시지를 이용하여 확인할 수도 있지만 `GetDeviceStateRequest` 메시지를 이용하여 해당 정보를 한번에 확인할 수도 있습니다. 일부 측정 정보는 기간 정보가 필요한데 이때 `period` 필드를 통해 정보가 전달됩니다. 이 요청에 대한 응답으로 [`GetDeviceStateResponse`](#GetDeviceStateResponse) 메시지를 사용해야 합니다.

| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | IoT 서비스의 사용자 계정의 access token. CEK는 외부 서비스의 인증 서버로부터 획득한 사용자 계정의 access token을 전달합니다. 자세한 설명은 [사용자 계정 연결하기](/CEK/Guides/Link_User_Account.md)를 참조합니다.                          | 항상    |
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | 대상 기기 정보를 담고 있는 객체. `applianceId` 필드는 항상 포함됩니다.     | 항상    |
| `period`           | [PeriodInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#PeriodInfoObject)           | 기간 정보를 담고 있는 객체. 이 필드가 요청에 포함되어 있으면 지정된 기간에 관련된 데이터를 제공해야 합니다.        | 조건부   |

### Message example

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "GetDeviceStateRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-012"
    },
    "period": {
      "start": "2018-03-28T00:00:00+09:00",
      "end": "2018-03-28T23:59:59+09:00"
    }
  }
}
```

### See also
* [`GetDeviceStateResponse`](#GetDeviceStateResponse)

## GetDeviceStateResponse {#GetDeviceStateResponse}
[`GetDeviceStateRequest`](#GetDeviceStateRequest) 메시지에 대한 응답으로 대상 기기가 제공하는 모든 상태 정보를 CEK에게 전달합니다.

| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string | 기기에서 요청한 정보를 확인한 시간(`YYYY-MM-DDThh:mm:ss±hh:mm`, <a href="https://en.wikipedia.org/wiki/ISO_8601#Combined_date_and_time_representations" target="_blank">ISO 8601 Combined date and time representations</a> )     | 선택    |
| `states[]`                   | [CustomInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#CustomInfoObject) array  | 기기가 제공하는 모든 상태 정보를 담고 있는 객체                    | 필수  |

### Message example

```json
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetDeviceStateResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "states" : [
      {
        "name" : "냉동실온도",
        "value" : -11,
        "unit" : "celsius"
      },
      {
        "name" : "냉장실온도",
        "value" : 2,
        "unit" : "celsius"
      },
      {
        "name" : "냉장실습도",
        "value" : 10,
        "unit" : "percentage"
      }
    ],
    "applianceResponseTimestamp": "2017-11-23T20:31:18+09:00"
  }
}
```

### See also
* [`GetDeviceStateRequest`](#GetDeviceStateRequest)
