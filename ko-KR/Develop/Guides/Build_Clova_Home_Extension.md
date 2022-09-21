# CLOVA Home extension 만들기

CLOVA Home extension이란 외부 IoT 서비스를 통해 가정 내 IoT 기기에 원격 제어 기능을 제공하는 extension입니다. CLOVA Home extension은 CLOVA에 사용자가 제어할 수 있는 IoT 기기가 어떤 것이 있는지 정보를 제공해야 합니다. 또한, CLOVA로부터 전달된 IoT 기기의 제어 요청을 전달받게 되며, 이에 상응하는 내용을 처리하고 그 결과를 반환해야 합니다. 다음은 CLOVA Home extension이 동작하는 구조를 나타낸 그림입니다.

![CEK_Clova_Home_Extension_Operation_Structure](/Develop/Assets/Images/CEK_Clova_Home_Extension_Operation_Structure.png)

CLOVA Home extension을 만들기 위해 사전에 준비해야 할 것이 무엇이 있고 CLOVA와 어떤 메시지를 주고 받으면서 어떻게 동작을 수행해야 하는지 설명합니다.

다음과 같은 순서로 CLOVA Home extension 개발자가 알아야 할 내용을 전달합니다.

* [사전 준비사항](#Preparation)
* [Discovery 기능 제공하기](#ProvideDeviceDiscovery)
* [CLOVA Home extension 요청 처리하기](#HandleCLOVAHomeExtensionRequest)
  * [요청 메시지 검증](#RequestMessageValidation)
* [CLOVA Home extension 응답 반환하기](#ReturnCLOVAHomeExtensionResponse)

{% include "/Develop/Guides/BuildClovaHomeExtension/Preparation.md" %}

{% include "/Develop/Guides/BuildClovaHomeExtension/Provide_Device_Discovery.md" %}

{% include "/Develop/Guides/BuildClovaHomeExtension/Handle_Clova_Home_Extension_Request.md" %}

{% include "/Develop/Guides/BuildClovaHomeExtension/Validating_Request_Message.md" %}

{% include "/Develop/Guides/BuildClovaHomeExtension/Return_Clova_Home_Extension_Response.md" %}
