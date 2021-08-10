## GetPhaseRequest {#GetPhaseRequest}
주로 밥솥이나 세탁기와 같이 동작 단계가 있는 기기에서 현재 동작 단계 정보를 확인할 때 사용되며, 대상 기기의 현재 동작 단계 정보를 CLOVA Home extension에 요청합니다. 이 요청에 대한 응답으로 [`GetPhaseResponse`](#GetPhaseResponse) 메시지를 사용해야 합니다.

| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | IoT 서비스의 사용자 계정의 access token. CEK는 외부 서비스의 인증 서버로부터 획득한 사용자 계정의 access token을 전달합니다. 자세한 설명은 [사용자 계정 연결하기](/Develop/Guides/Link_User_Account.md)를 참조합니다.                          | 항상    |
| `appliance`        | [ApplianceInfoObject](/Develop/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | 대상 기기 정보를 담고 있는 객체. `applianceId` 필드는 필수입니다.     | 항상    |

### Message example

```json
{
  "header": {
    "messageId": "0e25429d-b7c2-4588-aa85-3c46168e8776",
    "name": "GetPhaseRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-017"
    }
  }
}
```

### See also
* [`GetPhaseResponse`](#GetPhaseResponse)

## GetPhaseResponse {#GetPhaseResponse}
[`GetPhaseRequest`](#GetPhaseRequest) 메시지에 대한 응답으로 대상 기기의 현재 동작 단계 정보를 CEK에 전달합니다.

| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string | 기기에서 요청한 정보를 확인한 시간(`"YYYY-MM-DDThh:mm:ss±hh:mm"`, <a href="https://en.wikipedia.org/wiki/ISO_8601#Combined_date_and_time_representations" target="_blank">ISO 8601 Combined date and time representations</a> )     | 선택    |
| `phase`                 | [PhaseInfoObject](/Develop/References/ClovaHomeInterface/Shared_Objects.md#PhaseInfoObject) | 기기의 현재 동작 단계 정보를 담고 있는 객체   | 필수    |

### Message example

```json
{
  "header": {
    "messageId": "b502dd42-b698-4d3b-9ddb-bbdda70f254f",
    "name": "GetPhaseResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "phase": {
        "value": "wash"
    },
    "applianceResponseTimestamp": "2017-11-23T20:30:19+09:00"
  }
}
```

### See also
* [`GetPhaseRequest`](#GetPhaseRequest)
