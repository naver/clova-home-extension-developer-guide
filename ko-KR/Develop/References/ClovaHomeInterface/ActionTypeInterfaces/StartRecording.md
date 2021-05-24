## StartRecordingConfirmation {#StartRecordingConfirmation}
[`StartRecordingRequest`](#StartRecordingRequest) 메시지에 대한 응답으로 대상 기기가 녹화를 시작하도록 요청한 후 처리된 결과를 CEK에 전달합니다.

### Payload fields

없음

### Remarks

녹화 준비 중 오류가 발생하면, [ActionFailedError](/Develop/References/ClovaHomeInterface/Error_Interfaces.md#ActionFailedError) 메시지를 CEK에 전달해야 합니다.

### Message example

```json
{
  "header": {
    "messageId": "9d6b0a2b-8348-4055-9a80-86d2829f2147",
    "name": "StartRecordingConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
  }
}
```

### See also
* [`StartRecordingRequest`](#StartRecordingRequest)

## StartRecordingRequest {#StartRecordingRequest}
주로 홈캠과 같이 카메라가 있는 기기를 제어할 때 사용되며, 기기가 녹화를 시작하도록 CLOVA Home extension에 요청합니다. 이 요청에 대한 응답으로 [`StartRecordingConfirmation`](#StartRecordingConfirmation) 메시지를 사용해야 합니다.

### Payload fields

| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | IoT 서비스의 사용자 계정의 access token. CEK는 외부 서비스의 인증 서버로부터 획득한 사용자 계정의 access token을 전달합니다. 자세한 설명은 [사용자 계정 연결하기](/Develop/Guides/Link_User_Account.md)를 참조합니다.                          | 항상    |
| `appliance`        | [ApplianceInfoObject](/Develop/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | 대상 기기 정보를 담고 있는 객체. `applianceId` 필드는 필수입니다.     | 항상    |

### Message example

```json
{
  "header": {
    "messageId": "51ace666-8c8d-43c5-977c-27e8248d0356",
    "name": "StartRecordingRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-027"
    }
  }
}
```

### See also
* [`StartRecordingConfirmation`](#StartRecordingConfirmation)
