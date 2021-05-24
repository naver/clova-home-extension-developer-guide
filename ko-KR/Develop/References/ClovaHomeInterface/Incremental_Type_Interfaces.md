# 값 증감형 인터페이스 

수치나 단계로 표현되는 기기의 특정 속성 값이나 설정 값을 올리거나 내리는 인터페이스입니다. 요청 메시지와 응답 메시지 이름은 `Increment-` 또는 `Decrement-`와 같은 접두어(prefix)로 시작됩니다.

| 메시지 이름         | 메시지 타입  | 메시지 설명                                   |
|------------------|-----------|---------------------------------------------|
| [`DecrementBrightnessConfirmation`](#DecrementBrightnessConfirmation)         | Response | [`DecrementBrightnessRequest`](#DecrementBrightnessRequest) 메시지에 대한 응답으로 대상 기기가 조명 밝기를 낮추도록 요청한 후 처리된 결과를 CEK에 전달합니다. |
| [`DecrementBrightnessRequest`](#DecrementBrightnessRequest)                   | Request  | 대상 기기가 지정한 수준만큼 조명의 밝기를 낮추도록 CLOVA Home extension에 요청합니다. |
| [`DecrementChannelConfirmation`](#DecrementChannelConfirmation)               | Response | [`DecrementChannelRequest`](#DecrementChannelRequest) 메시지에 대한 응답으로 대상 기기가 TV 채널을 낮추도록 요청한 후 처리된 결과를 CEK에 전달합니다. |
| [`DecrementChannelRequest`](#DecrementChannelRequest)                         | Request  | 대상 기기가 지정한 수준만큼 TV 채널을 낮추도록 CLOVA Home extension에 요청합니다. |
| [`DecrementFanSpeedConfirmation`](#DecrementFanSpeedConfirmation)             | Response | [`DecrementFanSpeedRequest`](#DecrementFanSpeedRequest) 메시지에 대한 응답으로 대상 기기가 팬 속도를 낮추도록 요청한 후 처리된 결과를 CEK에 전달합니다. |
| [`DecrementFanSpeedRequest`](#DecrementFanSpeedRequest)                       | Request  | 대상 기기가 지정한 값만큼 팬 속도를 낮추도록 CLOVA Home extension에 요청합니다. |
| [`DecrementIntensityLevelConfirmation`](#DecrementIntensityLevelConfirmation) | Response | [`DecrementIntensityLevelRequest`](#DecrementIntensityLevelRequest) 메시지에 대한 응답으로 대상 기기가 압력이나 수압의 세기를 낮추도록 요청한 후 처리된 결과를 CEK에 전달합니다.  |
| [`DecrementIntensityLevelRequest`](#DecrementIntensityLevelRequest)           | Request  | 주로 에어컨이나 온도 조절 장치와 같은 기기를 제어할 때 사용되며, 대상 기기가 지정한 값만큼 압력이나 수압의 세기를 낮추도록 CLOVA Home extension에 요청합니다.  |
| [`DecrementTargetTemperatureConfirmation`](#DecrementTargetTemperatureConfirmation) | Response | [`DecrementTargetTemperatureRequest`](#DecrementTargetTemperatureRequest) 메시지에 대한 응답으로 대상 기기가 온도를 낮추도록 요청한 후 처리된 결과를 CEK에 전달합니다. |
| [`DecrementTargetTemperatureRequest`](#DecrementTargetTemperatureRequest)     | Request  | 대상 기기가 지정한 값만큼 온도를 낮추도록 CLOVA Home extension에 요청합니다.      |
| [`DecrementVolumeConfirmation`](#DecrementVolumeConfirmation)                 | Response | [`DecrementVolumeRequest`](#DecrementVolumeRequest) 메시지에 대한 응답으로 대상 기기가 스피커 볼륨 크기를 낮추도록 요청한 후 처리된 결과를 CEK에 전달합니다. |
| [`DecrementVolumeRequest`](#DecrementVolumeRequest)                           | Request  | 대상 기기가 지정한 값만큼 볼륨 크기를 낮추도록 CLOVA home extension에 요청합니다. |
| [`IncrementBrightnessConfirmation`](#IncrementBrightnessConfirmation)         | Response | [`IncrementBrightnessRequest`](#IncrementBrightnessRequest) 메시지에 대한 응답으로 대상 기기가 조명 밝기를 높이도록 요청한 후 처리된 결과를 CEK에 전달합니다. |
| [`IncrementBrightnessRequest`](#IncrementBrightnessRequest)                   | Request  | 대상 기기가 지정한 수준만큼 조명의 밝기를 높이도록 CLOVA Home extension에 요청합니다. |
| [`IncrementChannelConfirmation`](#IncrementChannelConfirmation)               | Response | [`IncrementChannelRequest`](#IncrementChannelRequest) 메시지에 대한 응답으로 대상 기기가 TV 채널을 높이도록 요청한 후 처리된 결과를 CEK에 전달합니다. |
| [`IncrementChannelRequest`](#IncrementChannelRequest)                         | Request  | 대상 기기가 지정한 수준만큼 TV 채널을 높이도록 CLOVA Home extension에 요청합니다. |
| [`IncrementFanSpeedConfirmation`](#IncrementFanSpeedConfirmation)             | Response | [`IncrementFanSpeedRequest`](#IncrementFanSpeedRequest) 메시지에 대한 응답으로 대상 기기가 팬의 속도를 높이도록 요청한 후 처리된 결과를 CEK에 전달합니다. |
| [`IncrementFanSpeedRequest`](#IncrementFanSpeedRequest)                       | Request | 대상 기기가 지정한 값만큼 팬 속도를 높이도록 CLOVA Home extension에 요청합니다. |
| [`IncrementIntensityLevelConfirmation`](#IncrementIntensityLevelConfirmation) | Response | [`IncrementIntensityLevelRequest`](#IncrementIntensityLevelRequest) 메시지에 대한 응답으로 대상 기기가 압력이나 수압 세기를 높이도록 요청한 후 처리된 결과를 CEK에 전달합니다.  |
| [`IncrementIntensityLevelRequest`](#IncrementIntensityLevelRequest)           | Request  | 대상 기기가 지정한 값만큼 압력이나 수압의 세기를 높이도록 CLOVA Home extension에 요청합니다. |
| [`IncrementTargetTemperatureConfirmation`](#IncrementTargetTemperatureConfirmation) | Response | [`IncrementTargetTemperatureRequest`](#IncrementTargetTemperatureRequest) 메시지에 대한 응답으로 대상 기기가 온도를 높이도록 요청한 후 처리된 결과를 CEK에 전달합니다. |
| [`IncrementTargetTemperatureRequest`](#IncrementTargetTemperatureRequest)     | Request  | 대상 기기가 지정한 값만큼 온도를 높이도록 CLOVA Home extension에 요청합니다.     |
| [`IncrementVolumeConfirmation`](#IncrementVolumeConfirmation)                 | Response | [`IncrementVolumeRequest`](#IncrementVolumeRequest) 메시지에 대한 응답으로 대상 기기가 스피커 볼륨을 높이도록 요청한 후 처리된 결과를 CEK에 전달합니다. |
| [`IncrementVolumeRequest`](#IncrementVolumeRequest)                           | Request | 대상 기기가 지정한 값만큼 볼륨 크기를 높이도록 CLOVA Home extension에 요청합니다. |

{% include "/Develop/References/ClovaHomeInterface/IncrementalTypeInterfaces/DecrementBrightness.md" %}
{% include "/Develop/References/ClovaHomeInterface/IncrementalTypeInterfaces/DecrementFanSpeed.md" %}
{% include "/Develop/References/ClovaHomeInterface/IncrementalTypeInterfaces/DecrementIntensityLevel.md" %}
{% include "/Develop/References/ClovaHomeInterface/IncrementalTypeInterfaces/DecrementTargetTemperature.md" %}
{% include "/Develop/References/ClovaHomeInterface/IncrementalTypeInterfaces/DecrementVolume.md" %}
{% include "/Develop/References/ClovaHomeInterface/IncrementalTypeInterfaces/IncrementBrightness.md" %}
{% include "/Develop/References/ClovaHomeInterface/IncrementalTypeInterfaces/IncrementChannel.md" %}
{% include "/Develop/References/ClovaHomeInterface/IncrementalTypeInterfaces/IncrementFanSpeed.md" %}
{% include "/Develop/References/ClovaHomeInterface/IncrementalTypeInterfaces/IncrementIntensityLevel.md" %}
{% include "/Develop/References/ClovaHomeInterface/IncrementalTypeInterfaces/IncrementTargetTemperature.md" %}
{% include "/Develop/References/ClovaHomeInterface/IncrementalTypeInterfaces/IncrementVolume.md" %}