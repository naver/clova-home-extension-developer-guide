## CLOVA Home extension 요청 처리하기 {#HandleCLOVAHomeExtensionRequest}

사용자는 "전등 켜줘"와 같이 IoT 기기를 제어하도록 CLOVA에 요청합니다(HTTP Request). 클라이언트는 [Discovery 기능](#ProvideDeviceDiscovery)을 통해 확보된 기기 목록과 각 기기별 허용 동작을 보고 사용자의 IoT 기기 제어 요청이 수행 가능한 요청인지 검증합니다. 검증된 사용자 요청은 CLOVA Home extension에 전송되며 이때, [CLOVA Home extension 메시지](/Develop/References/Clova_Home_Extension_Message.md)를 이용합니다.

"전등 켜줘"와 같은 요청은 다음과 같이 [`TurnOnRequest`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetTurnOnRequest) 메시지로 전달됩니다.

{% raw %}
```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "TurnOnRequest",
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
{% endraw %}

요청 받은 메시지를 분석하여 IoT 서비스가 제공하는 URI로 사용자의 IoT 기기 제어 요청을 전달하면 됩니다. 이때 함께 전달받은 access token을 사용하여 요청합니다.
