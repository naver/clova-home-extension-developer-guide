## ChangeModeConfirmation {#ChangeModeConfirmation}

[`ChangeModeRequest`](#ChangeModeRequest) 메시지에 대한 응답으로 운전 모드(operation mode)를 정해진 순서에 따라 다음 순서에 해당하는 모드로 변경하도록 요청한 후 그 처리 결과를 CLOVA에 보고합니다.

### Payload fields

| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:---------:|
| `mode`               | [ModeInfoObject](/Develop/References/ClovaHomeInterface/Shared_Objects.md#ModeInfoObject)  | 현재 운전 모드 정보를 담고 있는 객체      | 선택    |
| `previousState`      | object  | 기기의 이전 상황 정보를 담고 있는 객체      | 선택    |
| `previousState.mode` | [ModeInfoObject](/Develop/References/ClovaHomeInterface/Shared_Objects.md#ModeInfoObject)  | 이전 운전 모드 정보를 담고 있는 객체      | 선택    |

### Remarks

대상 기기에서 payload에 입력할 정보를 얻어올 수 없으면 값을 입력하지 않아도 됩니다. 이때 사용자에게 구체적인 정보 없이 기기 제어 요청이 정상 처리되었음을 알려줍니다.

### Message example

```json
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "ChangeModeConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "previousState": {
      "mode": {
        "value": "sleep"
      }
    },
    "mode": {
      "value": "wakeup"
    }
  }
}
```

### See also
* [`ChangeModeRequest`](#ChangeModeRequest)

## ChangeModeRequest {#ChangeModeRequest}
기기의 운전 모드(operation mode)를 정해진 순서에 따라 다음 순서에 해당하는 모드로 변경하도록 CLOVA Home extension에 요청합니다. 이 요청에 대한 응답으로 [`ChangeModeConfirmation`](#ChangeModeConfirmation) 메시지를 사용해야 합니다.

### Payload fields

| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|---------------|---------|-----------------------------|:---------:|
| `accessToken` | string  | IoT 서비스의 사용자 계정의 access token. 외부 서비스의 인증 서버로부터 획득한 사용자 계정의 access token이 전달됩니다. 자세한 설명은 [사용자 계정 연결하기](/Develop/Guides/Link_User_Account.md)를 참조합니다. | 항상    |
| `appliance`   | [ApplianceInfoObject](/Develop/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | 대상 기기 정보를 담고 있는 객체. `applianceId` 필드는 필수입니다.   | 항상    |

### Message example

```json
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "ChangeModeRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
        "applianceId": "device-006"
    },
  }
}
```

### See also
* [`ChangeModeConfirmation`](#ChangeModeConfirmation)
