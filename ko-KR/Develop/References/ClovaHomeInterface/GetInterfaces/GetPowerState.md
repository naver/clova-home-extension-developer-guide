## GetPowerStateRequest {#GetPowerStateRequest}
기기 자체의 전원 상태를 확인할 수 있는 기기에서 현재 기기의 전원 상태를 CLOVA Home extension에 요청합니다. 이 요청에 대한 응답으로 [`GetPowerStateResponse`](#GetPowerStateResponse) 메시지를 사용해야 합니다.

| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | IoT 서비스의 사용자 계정의 access token. 외부 서비스의 인증 서버로부터 획득한 사용자 계정의 access token이 전달됩니다. 자세한 설명은 [사용자 계정 연결하기](/Develop/Guides/Link_User_Account.md)를 참조합니다.                          | 항상    |
| `appliance`        | [ApplianceInfoObject](/Develop/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | 대상 기기 정보를 담고 있는 객체. `applianceId` 필드는 항상 포함됩니다.     | 항상    |

### Message example

```json
{
  "header": {
    "messageId": "8204b9dd-96e3-4810-90e7-819aff373a9b",
    "name": "GetPowerStateRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-022"
    }
  }
}
```

### See also
* [`GetPowerStateResponse`](#GetPowerStateResponse)

## GetPowerStateResponse {#GetPowerStateResponse}
[`GetPowerStateRequest`](#GetPowerStateRequest) 메시지에 대한 응답으로 대상 기기의 현재 전원 상태 정보를 CLOVA에 전송합니다.

| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string | 기기에서 요청한 정보를 확인한 시간(`"YYYY-MM-DDThh:mm:ss±hh:mm"`, <a href="https://en.wikipedia.org/wiki/ISO_8601#Combined_date_and_time_representations" target="_blank">ISO 8601 Combined date and time representations</a> )     | 선택    |
| `powerState`                 | [PowerStateInfoObject](/Develop/References/ClovaHomeInterface/Shared_Objects.md#PowerStateInfoObject) | 기기의 현재 전원 상태 정보를 담고 있는 객체 | 필수    |


### Message example

```json
{
  "header": {
    "messageId": "5fb7a9c0-9a02-43bb-b4dd-0f325acdfb66",
    "name": "GetPowerStateResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "powerState": {
      "value": "꺼짐"
    },
    "applianceResponseTimestamp": "2019-08-19T20:04:26+09:00"
  }
}
```

### See also
* [`GetPowerStateRequest`](#GetPowerStateRequest)
