## GetRightPostureRatioRequest {#GetRightPostureRatioRequest}
사용자가 바른 자세로 대상 기기를 사용한 비율이 얼마인지 확인할 때 사용하며, 사용자가 대상 기기를 사용할 때 특정 기간이나 현재까지 바른 자세를 유지한 비율 정보를 Clova Home extension에게 요청합니다. 이 요청에 대한 응답으로 [`GetRightPostureRatioResponse`](#GetRightPostureRatioResponse) 메시지를 사용해야 합니다.

| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | IoT 서비스의 사용자 계정의 access token. CEK는 외부 서비스의 인증 서버로부터 획득한 사용자 계정의 access token을 전달합니다. 자세한 설명은 [사용자 계정 연결하기](/CEK/Guides/Link_User_Account.md)를 참조합니다.                          | 항상    |
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | 대상 기기 정보를 담고 있는 객체. `applianceId` 필드는 필수입니다.     | 항상    |
| `period`           | [PeriodInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#PeriodInfoObject)           | 기간 정보를 담고 있는 객체                                     | 항상   |

### Message example

```json
{
  "header": {
    "messageId": "59a3f5bc-4c38-4d4c-9b71-3a037bf9f9b0",
    "name": "GetRightPostureRatioRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-028"
    },
    "period": {
      "start": "2018-03-28T00:00:00+09:00",
      "end": "2018-03-28T23:59:59+09:00"
    }
  }
}
```

### See also
* [`GetRightPostureRatioResponse`](#GetRightPostureRatioResponse)

## GetRightPostureRatioResponse {#GetRightPostureRatioResponse}

[`GetRightPostureRatioRequest`](#GetRightPostureRatioRequest) 메시지에 대한 응답으로 사용자가 대상 기기를 바른 자세로 사용한 비율 정보를 CEK에게 전달합니다.

| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string | 기기에서 요청한 정보를 확인한 시간(`YYYY-MM-DDThh:mm:ss±hh:mm`<a href="https://en.wikipedia.org/wiki/ISO_8601#Combined_date_and_time_representations" target="_blank">ISO 8601</a> 형식)     | 선택    |
| `rightPostureRatio`          | [RatioInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#RatioInfoObject) | 사용자가 대상 기기르 바른 자세로 사용한 비율 정보를 가지는 객체   | 필수    |

### Message example

```json
{
  "header": {
    "messageId": "b502dd42-b698-4d3b-9ddb-bbdda70f254f",
    "name": "GetRightPostureRatioResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "rightPostureRatio": {
      "value": 80
    },
    "applianceResponseTimestamp": "2017-11-23T20:30:19+09:00"
  }
}
```

### See also
* [`GetRightPostureRatioRequest`](#GetRightPostureRatioRequest)
