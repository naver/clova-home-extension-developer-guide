## GetDetectedTimeRequest {#GetDetectedTimeRequest}

센서가 있는 기기에서 센서가 움직임과 같은 것을 감지한 시각을 CLOVA Home extension에 요청합니다. 이 요청에 대한 응답으로 [`GetDetectedTimeResponse`](#GetDetectedTimeResponse) 메시지를 사용해야 합니다.

| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | IoT 서비스의 사용자 계정의 access token. CEK는 외부 서비스의 인증 서버로부터 획득한 사용자 계정의 access token을 전달합니다. 자세한 설명은 [사용자 계정 연결하기](/Develop/Guides/Link_User_Account.md)를 참조합니다.                          | 항상    |
| `appliance`        | [ApplianceInfoObject](/Develop/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | 대상 기기 정보를 담고 있는 객체. `applianceId` 필드는 항상 포함됩니다.     | 항상    |

### Message example

```json
{
  "header": {
    "messageId": "db608484-afdf-4df6-91b9-a6227b46942a",
    "name": "GetDetectedTimeRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-011"
    }
  }
}
```

### See also
* [`GetDetectedTimeResponse`](#GetDetectedTimeResponse)

## GetDetectedTimeResponse {#GetDetectedTimeResponse}
[`GetDetectedTimeRequest`](#GetDetectedTimeRequest) 메시지에 대한 응답으로 대상 기기가 움직임을 감지한 시각 정보를 CEK에 전달합니다.

| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string | 기기에서 요청한 정보를 확인한 시간(`"YYYY-MM-DDThh:mm:ss±hh:mm"`, <a href="https://en.wikipedia.org/wiki/ISO_8601#Combined_date_and_time_representations" target="_blank">ISO 8601 Combined date and time representations</a> )     | 선택    |
| `detectedTime`             | string | 기기가 대상을 감지한 시간(`"YYYY-MM-DDThh:mm:ss±hh:mm"`, <a href="https://en.wikipedia.org/wiki/ISO_8601#Combined_date_and_time_representations" target="_blank">ISO 8601 Combined date and time representations</a> )     | 필수    |

### Message example

```json
{
  "header": {
    "messageId": "3d4446644-950e-4162-a4d9-9d563f63e81b",
    "name": "GetDetectedTimeResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "detectedTime": {
      "value": "어제 오후 10시"
    },
    "applianceResponseTimestamp": "2019-08-19T11:18:10+09:00"
  }
}
```

### See also
* [`GetDetectedTimeRequest`](#GetDetectedTimeRequest)
