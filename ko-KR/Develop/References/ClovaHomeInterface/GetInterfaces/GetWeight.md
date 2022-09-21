## GetWeightRequest {#GetWeightRequest}

체중계 또는 저울과 같은 무게 측정 기기로부터 측정된 체중이나 무게를 CLOVA Home extension에 요청합니다. 이 요청에 대한 응답으로 [`GetWeightResponse`](#GetWeightResponse) 메시지를 사용해야 합니다.

| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | IoT 서비스의 사용자 계정의 access token. 외부 서비스의 인증 서버로부터 획득한 사용자 계정의 access token이 전달됩니다. 자세한 설명은 [사용자 계정 연결하기](/Develop/Guides/Link_User_Account.md)를 참조합니다.                          | 항상    |
| `appliance`        | [ApplianceInfoObject](/Develop/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | 대상 기기 정보를 담고 있는 객체. `applianceId` 필드는 항상 포함됩니다.     | 항상    |

### Message example

```json
{
  "header": {
    "messageId": "6145712c-1fd5-4f6d-ac3a-8188f03c8a94",
    "name": "GetWeightRequest",
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
* [`GetWeightResponse`](#GetWeightResponse)

## GetWeightResponse {#GetWeightResponse}
[`GetWeightRequest`](#GetWeightRequest) 메시지에 대한 응답으로 대상 기기가 측정한 체중이나 무게를 CLOVA에 전송합니다.

| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string | 기기에서 요청한 정보를 확인한 시간(`"YYYY-MM-DDThh:mm:ss±hh:mm"`, <a href="https://en.wikipedia.org/wiki/ISO_8601#Combined_date_and_time_representations" target="_blank">ISO 8601 Combined date and time representations</a> )     | 선택    |
| `weight`          | [WeightInfoObject](/Develop/References/ClovaHomeInterface/Shared_Objects.md#WeightInfoObject) | 기기가 측정한 체중이나 무게 정보를 담고 있는 객체   | 필수    |

### Message example

```json
{
  "header": {
    "messageId": "d06b65c1-094b-4ca9-aee0-21431302f0d7",
    "name": "GetWeightResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "weight": {
      "value": 80.9
    },
    "applianceResponseTimestamp": "2019-08-09T20:30:44+09:00"
  }
}
```

### See also
* [`GetWeightRequest`](#GetWeightRequest)
