# 값 설정형 인터페이스

기기의 특정 속성 값이나 운전 모드를 지정한 값으로 설정하는 인터페이스입니다. 요청 메시지와 응답 메시지 이름은 `Set-`과 같은 접두어(prefix)로 시작됩니다.

| 메시지 이름         | 메시지 타입  | 메시지 설명                                   |
|------------------|-----------|---------------------------------------------|
| [`SetBrightnessConfirmation`](#SetBrightnessConfirmation)                     | Response | [`SetBrightnessRequest`](#SetBrightnessRequest) 메시지에 대한 응답으로 조명 밝기를 변경하도록 요청한 후 처리된 결과를 CEK에 전달합니다. |
| [`SetBrightnessRequest`](#SetBrightnessRequest)                               | Request  | 대상 기기가 조명 밝기를 지정한 값으로 변경하도록 CLOVA Home extension에 요청합니다. |
| [`SetChannelByNameConfirmation`](#SetChannelByNameConfirmation)               | Response | [`SetChannelByNameRequest`](#SetChannelByNameRequest) 메시지에 대한 응답으로 채널 이름으로 TV 채널을 변경하도록 요청한 후 처리된 결과를 CEK에 전달합니다. |
| [`SetChannelByNameRequest`](#SetChannelByNameRequest)                         | Request  | 대상 기기가 지정한 채널 이름으로 채널을 변경하도록 CLOVA Home extension에 요청합니다. |
| [`SetChannelConfirmation`](#SetChannelConfirmation)                           | Response | [`SetChannelRequest`](#SetChannelRequest) 메시지에 대한 응답으로 채널 번호로 TV 채널을 변경하도록 요청한 후 처리된 결과를 CEK에 전달합니다. |
| [`SetChannelRequest`](#SetChannelRequest)                                     | Request  | 대상 기기가 지정한 채널 번호로 TV 채널을 변경하도록 CLOVA Home extension에 요청합니다. |
| [`SetColorConfirmation`](#SetColorConfirmation)                               | Response | [`SetColorRequest`](#SetColorRequest) 메시지에 대한 응답으로 대상기기의 조명이나 화면, 전등의 색을 변경하도록 요청한 후 처리된 결과를 CEK에 전달합니다. |
| [`SetColorRequest`](#SetColorRequest)                                         | Request  | 주로 스마트 전등과 같은 기기를 제어할 때 사용되며, 대상 기기의 조명이나 화면, 전등의 색을 변경하도록 CLOVA Home extension에 요청합니다.  |
| [`SetColorTemperatureConfirmation`](#SetColorTemperatureConfirmation)         | Response | [`SetColorTemperatureRequest`](#SetColorTemperatureRequest) 메시지에 대한 응답으로 대상기기의 조명이나 화면, 전등의 색온도를 변경하도록 요청한 후 처리된 결과를 CEK에 전달합니다.  |
| [`SetColorTemperatureRequest`](#SetColorTemperatureRequest)                   | Request  | 주로 스마트 전등과 같은 기기를 제어할 때 사용되며, 대상 기기의 조명이나 화면, 전등의 색온도를 변경하도록 CLOVA Home extension에 요청합니다.  |
| [`SetFanSpeedConfirmation`](#SetFanSpeedConfirmation)                         | Response | [`SetFanSpeedRequest`](#SetFanSpeedRequest) 메시지에 대한 응답으로 팬 속도를 변경하도록 요청한 후 처리된 결과를 CEK에 전달합니다. |
| [`SetFanSpeedRequest`](#SetFanSpeedRequest)                                   | Request  | 대상 기기가 지정한 값으로 팬 속도를 변경하도록 CLOVA Home extension에 요청합니다. |
| [`SetLockStateConfirmation`](#SetLockStateConfirmation)                       | Response | [`SetLockStateRequest`](#SetLockStateRequest) 메시지에 대한 응답으로 대상 기기가 잠기거나 열리도록 요청한 후 처리된 결과를 CEK에 전달합니다.  |
| [`SetLockStateRequest`](#SetLockStateRequest)                                 | Request  | 대상 기기를 잠그거나 열도록 CLOVA Home extension에 요청합니다.  |
| [`SetModeConfirmation`](#SetModeConfirmation)                                 | Response | [`SetModeRequest`](#SetModeRequest) 메시지에 대한 응답으로 운전 모드(operation mode)를 변경하도록 요청한 후 처리된 결과를 CEK에 전달합니다. |
| [`SetModeRequest`](#SetModeRequest)                                           | Request  | 대상 기기가 지정한 모드로 운전 모드(operation mode)를 변경하도록 CLOVA Home extension에 요청합니다. |
| [`SetTargetTemperatureConfirmation`](#SetTargetTemperatureConfirmation)       | Response | [`SetTargetTemperatureRequest`](#SetTargetTemperatureRequest) 메시지에 대한 응답으로 희망 온도를 변경하도록 요청한 후 처리된 결과를 CEK에 전달합니다. |
| [`SetTargetTemperatureRequest`](#SetTargetTemperatureRequest)                 | Request  | 대상 기기가 희망 온도를 지정한 값으로 변경하도록 CLOVA Home extension에 요청합니다. |

{% include "/Develop/References/ClovaHomeInterface/Value-SettingTypeInterfaces/SetBrightness.md" %}
{% include "/Develop/References/ClovaHomeInterface/Value-SettingTypeInterfaces/SetChannel.md" %}
{% include "/Develop/References/ClovaHomeInterface/Value-SettingTypeInterfaces/SetChannelByName.md" %}
{% include "/Develop/References/ClovaHomeInterface/Value-SettingTypeInterfaces/SetColor.md" %}
{% include "/Develop/References/ClovaHomeInterface/Value-SettingTypeInterfaces/SetColorTemperature.md" %}
{% include "/Develop/References/ClovaHomeInterface/Value-SettingTypeInterfaces/SetFanSpeed.md" %}
{% include "/Develop/References/ClovaHomeInterface/Value-SettingTypeInterfaces/SetLockState.md" %}
{% include "/Develop/References/ClovaHomeInterface/Value-SettingTypeInterfaces/SetMode.md" %}
{% include "/Develop/References/ClovaHomeInterface/Value-SettingTypeInterfaces/SetTargetTemperature.md" %}
