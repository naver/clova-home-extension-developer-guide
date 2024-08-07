## StopOscillationConfirmation {#StopOscillationConfirmation}
[`StopOscillationRequest`](#StopOscillationRequest) 메시지에 대한 응답으로 대상 기기가 바람의 방향을 고정하도록 요청한 후 처리된 결과를 CLOVA에 전송합니다.

### Payload fields

없음

### Message example

```json
{
  "header": {
    "messageId": "e0ce8144-038f-4b1e-a7eb-6bee027d87ea",
    "name": "StopOscillationConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
  }
}
```

### See also
* [`StopOscillationRequest`](#StopOscillationRequest)

## StopOscillationRequest {#StopOscillationRequest}
주로 선풍기와 같은 기기를 제어할 때 사용되며, 기기가 바람의 방향을 고정하도록 CLOVA Home extension에 요청합니다. 이 요청에 대한 응답으로 [`StopOscillationConfirmation`](#StopOscillationConfirmation) 메시지를 사용해야 합니다.

### Payload fields

| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | IoT 서비스의 사용자 계정의 access token. 외부 서비스의 인증 서버로부터 획득한 사용자 계정의 access token이 전달됩니다. 자세한 설명은 [사용자 계정 연결하기](/Develop/Guides/Link_User_Account.md)를 참조합니다.                          | 항상    |
| `appliance`        | [ApplianceInfoObject](/Develop/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | 대상 기기 정보를 담고 있는 객체. `applianceId` 필드는 필수입니다.     | 항상    |

### Message example

```json
{
  "header": {
    "messageId": "c3c05363-efe3-4df2-866d-799ff85e3547",
    "name": "StopOscillationRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-025"
    }
  }
}
```

### See also
* [`StopOscillationConfirmation`](#StopOscillationConfirmation)
