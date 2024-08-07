## ChangePowerConfirmation {#ChangePowerConfirmation}

[`ChangePowerRequest`](#ChangePowerRequest) 메시지에 대한 응답으로 대상 기기의 전원 상태를 변경하도록 요청한 후 처리된 결과를 CLOVA에 전송합니다.

### Payload fields
없음

### Message example

```json
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "ChangePowerConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```

### See also
* [`ChangePowerRequest`](#ChangePowerRequest)

## ChangePowerRequest {#ChangePowerRequest}
대상 기기의 전원 상태를 변경하도록 CLOVA Home extension에 요청합니다. 이 요청에 대한 응답으로 [`ChangePowerConfirmation`](#ChangePowerConfirmation) 메시지를 사용해야 합니다.

### Payload fields

| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | IoT 서비스의 사용자 계정의 access token. 외부 서비스의 인증 서버로부터 획득한 사용자 계정의 access token이 전달됩니다. 자세한 설명은 [사용자 계정 연결하기](/Develop/Guides/Link_User_Account.md)를 참조합니다.                          | 항상    |
| `appliance`        | [ApplianceInfoObject](/Develop/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | 대상 기기 정보를 담고 있는 객체. `applianceId` 필드는 필수입니다. | 항상    |

### Message example

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "ChangePowerRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-001"
    }
  }
}
```

### See also
* [`ChangePowerConfirmation`](#ChangePowerConfirmation)
