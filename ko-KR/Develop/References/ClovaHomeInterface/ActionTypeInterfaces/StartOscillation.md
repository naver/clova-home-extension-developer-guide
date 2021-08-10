## StartOscillationConfirmation {#StartOscillationConfirmation}
[`StartOscillationRequest`](#StartOscillationRequest) 메시지에 대한 응답으로 대상 기기가 바람의 방향을 바꾸도록 요청한 후 처리된 결과를 CEK에 전달합니다.

### Payload fields

없음

### Message example

```json
{
  "header": {
    "messageId": "b927f3ec-6e24-4975-840d-f28033b8474c",
    "name": "StartOscillationConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
  }
}
```

### See also
* [`StartOscillationRequest`](#StartOscillationRequest)

## StartOscillationRequest {#StartOscillationRequest}
주로 선풍기와 같은 기기를 제어할 때 사용되며, 기기가 바람의 방향을 상하 또는 좌우로 왕복하여 바꾸도록 CLOVA Home extension에 요청합니다. 이 요청에 대한 응답으로 [`StartOscillationConfirmation`](#StartOscillationConfirmation) 메시지를 사용해야 합니다.

### Payload fields

| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | IoT 서비스의 사용자 계정의 access token. CEK는 외부 서비스의 인증 서버로부터 획득한 사용자 계정의 access token을 전달합니다. 자세한 설명은 [사용자 계정 연결하기](/Develop/Guides/Link_User_Account.md)를 참조합니다.                          | 항상    |
| `appliance`        | [ApplianceInfoObject](/Develop/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | 대상 기기 정보를 담고 있는 객체. `applianceId` 필드는 필수입니다.     | 항상    |
| `direction`        | [DirectionInfoObject](/Develop/References/ClovaHomeInterface/Shared_Objects.md#DirectionInfoObject)  | 왕복할 바람의 방향 정보를 담고 있는 객체.  | 조건부 |

### Message example

```json
{
  "header": {
    "messageId": "85253b03-09cd-43af-bd06-4e54855ce649",
    "name": "StartOscillationRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-025"
    },
    "direction": {
      "value": "horizontal"
    }
  }
}
```

### See also
* [`StartOscillationConfirmation`](#StartOscillationConfirmation)
