## ChangeInputSourceConfirmation {#ChangeInputSourceConfirmation}

[`ChangeInputSourceRequest`](#ChangeInputSourceRequest) 메시지에 대한 응답으로 외부 입력(input source)을 정해진 순서에 따라 다음 순서에 해당하는 외부 입력으로 변경하도록 요청한 후 그 처리 결과를 CLOVA에 보고합니다.

### Payload fields
없음

### Message example

```json
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "ChangeInputSourceConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```

### See also
* [`ChangeInputSourceRequest`](#ChangeInputSourceRequest)

## ChangeInputSourceRequest {#ChangeInputSourceRequest}
주로 TV와 같은 기기를 제어할 때 사용되며, 대상 기기의 외부 입력(input source)을 정해진 순서에 따라 다음 순서에 해당하는 외부 입력으로 변경하도록 CLOVA Home extension에 요청합니다. 이 요청에 대한 응답으로 [`ChangeInputSourceConfirmation`](#ChangeInputSourceConfirmation) 메시지를 사용해야 합니다.

### Payload fields

| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`   | string | IoT 서비스의 사용자 계정의 access token. 외부 서비스의 인증 서버로부터 획득한 사용자 계정의 access token이 전달됩니다. 자세한 설명은 [사용자 계정 연결하기](/Develop/Guides/Link_User_Account.md)를 참조합니다.                          | 항상    |
| `appliance`     | [ApplianceInfoObject](/Develop/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject) | 대상 기기 정보를 담고 있는 객체. `applianceId` 필드는 필수입니다. | 항상    |

### Message example

```json
{
  "header": {
    "messageId": "c8fb66b4-4cbe-4e15-b1b2-f5c9631bc50e",
    "name": "ChangeInputSourceRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-004"
    }
  }
}
```

### See also

* [`ChangeInputSourceConfirmation`](#ChangeInputSourceConfirmation)
