# 전환형 인터페이스

기기의 운전 모드(operation mode)나 설정을 특정하지 않고 다른 모드나 값으로 전환되도록 만드는 인터페이스입니다. 예를 들면, 리모컨의 버튼 하나로 기기의 운전 모드나 설정 값을 정해진 순서대로 계속 전환하는 동작이 수행되도록 만드는 것입니다. 요청 메시지와 응답 메시지 이름은 `Change-`과 같은 접두어(prefix)로 시작됩니다.

| 메시지 이름         | 메시지 타입  | 메시지 설명                                   |
|------------------|-----------|---------------------------------------------|
| [`ChangeFanSpeedConfirmation`](#ChangeFanSpeedConfirmation)                   | Response | [`ChangeFanSpeedRequest`](#ChangeFanSpeedRequest) 메시지에 대한 응답으로 팬 속도를 정해진 순서에 따라 다음 순서에 해당하는 속도로 변경하도록 요청한 후 그 처리 결과를 CEK에 반환합니다. |
| [`ChangeFanSpeedRequest`](#ChangeFanSpeedRequest)                             | Request  | 대상 기기의 팬 속도를 정해진 순서에 따라 다음 순서에 해당하는 속도로 변경하도록 CLOVA Home extension에 요청합니다. |
| [`ChangeInputSourceConfirmation`](#ChangeInputSourceConfirmation)             | Response | [`ChangeInputSourceRequest`](#ChangeInputSourceRequest) 메시지에 대한 응답으로 외부 입력(input source)을 정해진 순서에 따라 다음 순서에 해당하는 외부 입력으로 변경하도록 요청한 후 그 처리 결과를 CEK에 반환합니다. |
| [`ChangeInputSourceRequest`](#ChangeInputSourceRequest)                       | Request  | 대상 기기의 외부 입력(input source)을 정해진 순서에 따라 다음 순서에 해당하는 외부 입력으로 변경하도록 CLOVA Home Extension에 요청합니다. |
| [`ChangeModeConfirmation`](#ChangeModeConfirmation)                           | Response | [`ChangeModeRequest`](#ChangeModeRequest) 메시지에 대한 응답으로 운전 모드(operation mode)를 정해진 순서에 따라 다음 순서에 해당하는 모드로 변경하도록 요청한 후 그 처리 결과를 CEK에 반환합니다. |
| [`ChangeModeRequest`](#ChangeModeRequest)                                     | Request  | 대상 기기의 운전 모드(operation mode)를 정해진 순서에 따라 다음 순서에 해당하는 모드로 변경하도록 CLOVA Home Extension에 요청합니다. |
| [`ChangePowerConfirmation`](#ChangePowerConfirmation)                         | Response | [`ChangePowerRequest`](#ChangePowerRequest) 메시지에 대한 응답으로 대상 기기의 전원 상태를 변경하도록 요청한 후 처리된 결과를 CEK에 전달합니다. |
| [`ChangePowerRequest`](#ChangePowerRequest)                                   | Request  | 대상 기기의 전원 상태를 변경하도록 CLOVA Home extension에 요청합니다. |

{% include "/Develop/References/ClovaHomeInterface/SwitchingTypeInterfaces/ChangeFanSpeed.md" %}
{% include "/Develop/References/ClovaHomeInterface/SwitchingTypeInterfaces/ChangeInputSource.md" %}
{% include "/Develop/References/ClovaHomeInterface/SwitchingTypeInterfaces/ChangeMode.md" %}
{% include "/Develop/References/ClovaHomeInterface/SwitchingTypeInterfaces/ChangePower.md" %}