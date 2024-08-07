<!-- Note! This content includes shared parts. Therefore, when you update this, you should beware of synchronization. -->

# CLOVA Home extension 테스트하기
등록한 CLOVA Home extension은 배포하기 전에 테스트해볼 수 있습니다. 다음을 항목을 수행하여 CLOVA Home extension을 테스트합니다.

* [IoT 기기 정보 가져오기](#TestDiscovery)
* [IoT 기기 제어 테스트하기](#TestControl)
* [CLOVA 앱으로 CLOVA Home extension 테스트하기](#TestOnCLOVAApp)

## IoT 기기 정보 가져오기 {#TestDiscovery}

CLOVA 앱이나 클라이언트 기기와 페어링하는 앱에서 사용자 계정에 등록된 IoT 기기 목록을 제공하는 [Discovery 기능](/Develop/Guides/Build_Clova_Home_Extension.md#ProvideDeviceDiscovery)이 올바르게 작동하고 있는지 테스트할 수 있습니다.

1. 등록한 CLOVA Home extension 목록에서 테스트하려는 CLOVA Home extension 항목의 **{{ book.DevConsole.cek_test }}** 메뉴를 누릅니다.<br />
  ![DevConsole-Clova_Home_Extension_List_After_Creation](/DevConsole/Assets/Images/DevConsole-Clova_Home_Extension_List_After_Creation.png)
2. **{{ book.DevConsole.cek_home_test_discovery_title }}** 메뉴에서 테스트하려는 계정의 액세스 토큰을 입력하십시오.
3. **{{ book.DevConsole.cek_home_test_request_test }}** 버튼을 눌러서 테스트 결과를 확인하십시오.<br />
  ![DevConsole-Clova_Home_Extension_Discovery_Test](/DevConsole/Assets/Images/DevConsole-Clova_Home_Extension_Discovery_Test.png)


다음은 테스트할 때 사용한 요청 메시지의 예입니다. `payload`에서 테스트하기 위해 입력한 액세스 토큰을 확인할 수 있습니다.

```json
{
  "header": {
    "messageId": "405a8396-fb2c-4736-8ca0-17a8b0cf1f08",
    "name": "DiscoverAppliancesRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "Vxq8eAn9i94cvVt2dhoq5jTz2RJ8"
  }
}
```

다음은 테스트 결과로 받은 응답 메시지의 예입니다. 응답 메시지 내용을 보면 테스트 대상 계정에 등록된 기기 정보를 확인할 수 있습니다. `payload`에는 기기의 ID, 기기의 타입, 제조사 이름, 사용자가 설정한 이름과 설명, 수행할 수 있는 동작과 같은 정보를 확인할 수 있습니다. 테스트하는 extension이 실제로 이 정보를 보내야 합니다.

```json
{
  "header": {
    "messageId": "405a8396-fb2c-4736-8ca0-17a8b0cf1f08",
    "name": "DiscoverAppliancesResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "discoveredAppliances": [
      {
        "applianceId": "EF:76:23:F4:E0:67:b1:2e-3a",
        "manufacturerName": "클로바 홈 리모트",
        "modelName": "Extended color light",
        "version": "1.0",
        "friendlyName": "거실",
        "friendlyDescription": "",
        "actions": [
          "TurnOn",
          "TurnOff",
          "HealthCheck",
          "SetColorTemperature",
          "SetColor",
          "SetBrightness",
          "IncrementBrightness",
          "DecrementBrightness"
        ],
        "applianceTypes": [
            "LIGHT"
        ],
        "location": "",
        "tags": null,
        "isIr": false
      },
      ...
    ]
  }
}
```

## IoT 기기 제어 테스트하기 {#TestControl}

사용자가 명령을 내렸을 때 요청한 기능이 올바르게 작동하는지 테스트할 수 있습니다. [IoT 기기 정보 가져오기](#TestDiscovery)를 하면 **{{ book.DevConsole.cek_home_test_control_title }}**의 드롭다운 메뉴가 활성화 되며, 이를 이용해 IoT 기기의 기능 제어를 테스트할 수 있습니다. 각 항목의 내용을 설정하고 테스트하는 과정은 다음과 같습니다.

<ol>
  <li><strong>applianceTypes</strong>(기기 타입) 항목에서 테스트하고자 하는 기기 타입을 선택하십시오.</li>
  <li><strong>applianceId</strong>(기기 ID) 항목에서 테스트하고자 하는 기기 ID를 선택하십시오.</li>
  <li><strong>actions</strong>(기기가 지원하는 동작) 항목에서 테스트하고자 하는 기기 동작을 선택하십시오. <strong>applianceTypes</strong> 항목에서 지정한 기기가 지원하는 동작만 선택할 수 있습니다.</li>
  <li><strong>action</strong> 항목에서 선택한 동작이 특정한 값으로 조정 가능할 경우, <strong>value</strong>(설정값) 항목에 테스트하려는 값을 입력하십시오. 동작이 요구하는 값이 날짜나 기간일 때, 입력 필드 대신 날짜를 선택할 수 있는 UI가 표시됩니다.
    <div class="tip">
      <p><strong>Tip!</strong></p>
      <p>입력 필드에 아무 내용을 입력하지 않았다면 기본값이 사용됩니다.</p>
    </div>
  </li>
  <li>테스트 설정을 마친 후, <strong>{{ book.DevConsole.cek_home_test_request_test }}</strong> 버튼을 누르십시오.<br />
    <img alt="DevConsole-Clova_Home_Extension_Control_Test" src="/DevConsole/Assets/Images/DevConsole-Clova_Home_Extension_Control_Test.png" />
  </li>
</ol>

<div class="tip">
  <p><strong>Tip!</strong></p>
  <p><code>applianceTypes</code>와 <code>actions</code>에 대한 자세한 정보는 <a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject">ApplianceInfoObject</a>를 참조합니다.</p>
</div>

다음은 스마트 전구의 밝기를 50%로 변경하도록 지시하는 요청 메시지의 예입니다. `payload`에서 테스트하기 위해 입력한 조건을 확인할 수 있습니다.

```json
{
  "header": {
    "messageId": "i42pouzk-3x6t-qsh1-jvau-a9voj71iejo3",
    "name": "SetBrightnessRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "Vxq8eAn9i94cvVt2dhoq5jTz2RJ8",
    "appliance": {
      "applianceId": "EF:76:23:F4:E0:67:b1:2e-3a",
      "additionalApplianceDetails": {
        "bridgeId": "001788fffe7ed61c",
        "index": 1,
        "userName": "82uf1ork9j6z1qjtfh2d20-g6so6rp6vjd8kxxlx"
        }
    },
    "brightness": {
      "value": 50
    }
  }
}
```

다음은 위의 요청에 대한 응답 메시지의 예입니다. 테스트하는 extension이 실제로 아래와 같이 응답 메시지를 보내야 합니다.

```json
{
  "header": {
    "messageId": "i42pouzk-3x6t-qsh1-jvau-a9voj71iejo3",
    "name": "SetBrightnessConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "brightness": {
      "value": 50
    }
  }
}
```

<!-- Start of the shared content: TestOnCLOVAApp -->

## CLOVA 앱으로 CLOVA Home extension 테스트하기 {#TestOnCLOVAApp}

CLOVA Home extension을 실제 클라이언트인 CLOVA 앱에서 테스트해볼 수 있습니다. 이를 위해 CLOVA Home extension 기본 정보를 등록하는 페이지의 **{{ book.DevConsole.cek_tester }}** 필드에 개발자 본인이나 CLOVA Home extension을 테스트할 사람의 <strong>{{ book.ServiceEnv.OrientedService }} 계정</strong>을 입력해야 합니다. 계정을 추가한 후 **{{ book.DevConsole.cek_save }}** 버튼을 누르면 입력한 계정이 인증된 CLOVA 앱에서 개발 중인 CLOVA Home extension을 테스트할 수 있습니다. CLOVA 앱에서 테스트를 중지하려면 입력한 계정 정보를 삭제하면 됩니다.

![DevConsole-Add_Tester_ID_For_Clova_Home_Extension](/DevConsole/Assets/Images/DevConsole-Add_Tester_ID_For_Clova_Home_Extension.png)

<div class="note">
  <p><strong>Note!</strong></p>
  <p>테스터 ID를 등록한 후 조금 기다리면 CLOVA Home extension을 테스트해 볼 수 있습니다. 만약, 1 시간 정도가 지나도 CLOVA Home extension을 테스트할 수 없으면 포럼이나 제휴 담당자를 통해 문의하시기 바랍니다.</p>
</div>

<!-- End of the shared content -->
