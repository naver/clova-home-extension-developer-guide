## GetBMIRequest {#GetBMIRequest}

체성분 측정기나 헬스 케어 종류의 기기로부터 측정된 신체질량지수(BMI, Body Mass Index)를 CLOVA Home extension에 요청합니다. 이 요청에 대한 응답으로 [`GetBMIResponse`](#GetBMIResponse) 메시지를 사용해야 합니다.

| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | IoT 서비스의 사용자 계정의 access token. CEK는 외부 서비스의 인증 서버로부터 획득한 사용자 계정의 access token을 전달합니다. 자세한 설명은 [사용자 계정 연결하기](/Develop/Guides/Link_User_Account.md)를 참조합니다.                          | 항상    |
| `appliance`        | [ApplianceInfoObject](/Develop/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | 대상 기기 정보를 담고 있는 객체. `applianceId` 필드는 항상 포함됩니다.     | 항상    |

### Message example

```json
{
  "header": {
    "messageId": "a9d64261-913f-4fcf-bce5-4544b4519413",
    "name": "GetBMIRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-021"
    }
  }
}
```

### See also
* [`GetBMIResponse`](#GetBMIResponse)

## GetBMIResponse {#GetBMIResponse}
[`GetBMIRequest`](#GetBMIRequest) 메시지에 대한 응답으로 대상 기기가 측정한 신체질량지수(BMI, Body Mass Index)를 CEK에 전달합니다.

| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string | 기기에서 요청한 정보를 확인한 시간(`"YYYY-MM-DDThh:mm:ss±hh:mm"`, <a href="https://en.wikipedia.org/wiki/ISO_8601#Combined_date_and_time_representations" target="_blank">ISO 8601 Combined date and time representations</a> )     | 선택    |
| `bmi`             | [IndexInfoObject](/Develop/References/ClovaHomeInterface/Shared_Objects.md#IndexInfoObject) | 기기가 측정한 신체질량지수 정보를 담고 있는 객체   | 필수    |

### Message example

```json
{
  "header": {
    "messageId": "c46be915-7fdc-4a0e-a409-9e029dff186b",
    "name": "GetBMIResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "bmi": {
      "value": 20.5
    },
    "applianceResponseTimestamp": "2019-08-09T20:30:44+09:00"
  }
}
```

### See also
* [`GetBMIRequest`](#GetBMIRequest)
