# 액션형 인터페이스

기기가 특정 동작을 수행하도록 만드는 인터페이스입니다. 동작과 관련된 명령형 동사가 요청 메시지와 응답 메시지 이름에서 접두어(prefix)로 정의되어 있습니다. 

| 메시지 이름         | 메시지 타입  | 메시지 설명                                   |
|------------------|-----------|---------------------------------------------|
| [`CallElevatorConfirmation`](#CallElevatorConfirmation)                       | Response | [`CallElevatorRequest`](#CallElevatorRequest) 메시지에 대한 응답으로 엘리베이터를 호출하도록 요청한 후 처리된 결과를 CLOVA에 전송합니다. |
| [`CallElevatorRequest`](#CallElevatorRequest)                                 | Request  | 건물의 엘리베이터가 호출되도록 Clova Home extension에게 요청합니다.  |
| [`ChargeConfirmation`](#ChargeConfirmation)                                   | Response | [`ChargeRequest`](#ChargeRequest) 메시지에 대한 응답으로 대상 기기가 스스로 충전하도록 요청한 후 처리된 결과를 CLOVA에 전송합니다. |
| [`ChargeRequest`](#ChargeRequest)                                             | Request  | 대상 기기가 스스로를 충전하도록 CLOVA Home extension에 요청합니다. |
| [`CloseConfirmation`](#CloseConfirmation)                                     | Response | [`CloseRequest`](#CloseRequest) 메시지에 대한 응답으로 스마트 커튼이 일광 차단하거나, 비데의 뚜껑을 닫도록 요청한 후 처리된 결과를 CLOVA에 전송합니다. |
| [`CloseRequest`](#CloseRequest)                                               | Request  | 스마트 커튼이나 비데와 같은 제품을 제어할 때 사용되며, 스마트 커튼이 일광 차단하거나, 비데의 뚜껑을 닫도록 CLOVA Home extension에 요청합니다.  |
| [`LowerConfirmation`](#LowerConfirmation)                                     | Response | [`LowerRequest`](#LowerRequest) 메시지에 대한 응답으로 대상 기기의 높낮이를 낮추도록 요청한 후 처리된 결과를 CLOVA에 전송합니다.  |
| [`LowerRequest`](#LowerRequest)                                               | Request  | 주로 커튼이나 블라인드, 침대 같은 기기를 제어할 때 사용되며, 대상 기기의 높낮이를 내리도록 CLOVA Home extension에 요청합니다.  |
| [`MuteConfirmation`](#MuteConfirmation)                                       | Response | [`MuteRequest`](#MuteRequest) 메시지에 대한 응답으로 대상 기기의 소리를 끄도록 설정(음소거)한 결과를 CLOVA에 전송합니다. |
| [`MuteRequest`](#MuteRequest)                                                 | Request  | 대상 기기의 소리를 끄도록(음소거) CLOVA Home extension에 요청합니다. |
| [`OpenConfirmation`](#OpenConfirmation)                                       | Response | [`OpenRequest`](#OpenRequest) 메시지에 대한 응답으로 스마트 커튼이 일광 차단을 해제하거나, 비데의 뚜껑을 열도록 요청한 후 처리된 결과를 CLOVA에 전송합니다. |
| [`OpenRequest`](#OpenRequest)                                                 | Request  | 스마트 커튼이나 비데와 같은 제품을 제어할 때 사용되며, 스마트 커튼이 일광 차단을 해제하거나, 비데의 뚜껑을 열도록 CLOVA Home extension에 요청합니다.  |
| [`PreheatConfirmation`](#PreheatConfirmation)                                 | Response | [`PreheatRequest`](#PreheatRequest) 메시지에 대한 응답으로 예열 요청을 처리한 후 그 결과를 CLOVA에 전송합니다.  |
| [`PreheatRequest`](#PreheatRequest)                                           | Response | 주로 오븐과 같은 기기를 제어할 때 사용되며, 대상 기기가 예열하도록 CLOVA Home extension에 요청합니다.                        |
| [`RaiseConfirmation`](#RaiseConfirmation)                                     | Response | [`RaiseRequest`](#RaiseRequest) 메시지에 대한 응답으로 대상 기기의 높낮이를 높이도록 요청한 후 처리된 결과를 CLOVA에 전송합니다.  |
| [`RaiseRequest`](#RaiseRequest)                                               | Request  | 주로 커튼이나 블라인드, 침대 같은 기기를 제어할 때 사용되며, 대상 기기의 높낮이를 높이도록 CLOVA Home extension에 요청합니다.  |
| [`ReleaseModeConfirmation`](#ReleaseModeConfirmation)                         | Response | [`ReleaseModeRequest`](#ReleaseModeRequest) 메시지에 대한 응답으로 현재 기기의 운전 모드(operation mode)를 해제하도록 요청한 후 처리된 결과를 CLOVA에 전송합니다.  |
| [`ReleaseModeRequest`](#ReleaseModeRequest)                                   | Request  | 현재 기기에 설정된 운전 모드(operation mode)를 해제할 때 사용되며, 기기의 운전 모드를 해제하여 이전 운전 모드나 기본 운전 모드로 돌아가도록 CLOVA Home extension에 요청합니다.  |
| [`StartOscillationConfirmation`](#StartOscillationConfirmation)       | Response | [`StartOscillationRequest`](#StartOscillationRequest) 메시지에 대한 응답으로 바람의 방향을 바꾸기 위해 대상 기기에 동작을 요청한 결과를 CLOVA에 전송합니다. |
| [`StartOscillationRequest`](#StartOscillationRequest)                 | Request  | 주로 선풍기와 같은 기기를 제어할 때 사용되며, 기기가 바람의 방향을 상하 또는 좌우로 왕복하여 바꾸도록 CLOVA Home extension에 요청합니다. |
| [`StartRecordingConfirmation`](#StartRecordingConfirmation)       | Response | [`StartRecordingRequest`](#StartRecordingRequest) 메시지에 대한 응답으로 대상 기기가 녹화를 시작하도록 요청한 후 처리된 결과를 CLOVA에 전송합니다. |
| [`StartRecordingRequest`](#StartRecordingRequest)                 | Request  | 주로 홈캠과 같이 카메라가 있는 기기를 제어할 때 사용되며, 기기가 녹화를 시작하도록 CLOVA Home extension에 요청합니다. |
| [`StopConfirmation`](#StopConfirmation)                                       | Response | [`StopRequest`](#StopRequest) 메시지에 대한 응답으로 대상 기기에 동작 중지를 요청한 결과를 CLOVA에 전송합니다.  |
| [`StopRequest`](#StopRequest)                                                 | Request  | 기기의 현재 동작을 중지하도록 CLOVA Home extension에 요청합니다.  |
| [`StopOscillationConfirmation`](#StopOscillationConfirmation)       | Response | [`StopOscillationRequest`](#StopOscillationRequest) 메시지에 대한 응답으로 바람의 방향을 고정하기 위해 대상 기기에 동작을 요청한 결과를 CLOVA에 전송합니다. |
| [`StopOscillationRequest`](#StopOscillationRequest)                 | Request  | 주로 선풍기와 같은 기기를 제어할 때 사용되며, 기기가 바람의 방향을 고정하도록 CLOVA Home extension에 요청합니다. |
| [`StopRecordingConfirmation`](#StopRecordingConfirmation)       | Response | [`StopRecordingRequest`](#StopRecordingRequest) 메시지에 대한 응답으로 대상 기기가 녹화를 중지하도록 요청한 후 처리된 결과를 CLOVA에 전송합니다. |
| [`StopRecordingRequest`](#StopRecordingRequest)                 | Request  | 주로 선풍기와 같은 기기를 제어할 때 사용되며, 기기가 바람의 방향을 고정하도록 CLOVA Home extension에 요청합니다. |
| [`TurnOffConfirmation`](#TurnOffConfirmation)                                 | Response | [`TurnOffRequest`](#TurnOffRequest) 메시지에 대한 응답으로 대상 기기를 끄도록 요청한 후 처리된 결과를 CLOVA에 전송합니다. |
| [`TurnOffRequest`](#TurnOffRequest)                                           | Request  | 대상 기기를 끄도록 CLOVA Home extension에 요청합니다.                        |
| [`TurnOnConfirmation`](#TurnOnConfirmation)                                   | Response | [`TurnOnRequest`](#TurnOnRequest) 메시지에 대한 응답으로 대상 기기를 켜도록 요청한 후 처리된 결과를 CLOVA에 전송합니다. |
| [`TurnOnRequest`](#TurnOnRequest)                                             | Request  | 대상 기기를 켜도록 CLOVA Home extension에 요청합니다.                        |
| [`UnmuteConfirmation`](#UnmuteConfirmation)                                   | Response | [`UnmuteRequest`](#UnmuteRequest) 메시지에 대한 응답으로 대상 기기의 소리를 켜도록 설정(음소거 해제)한 결과를 CLOVA에 전송합니다. |
| [`UnmuteRequest`](#UnmuteRequest)                                             | Request  | 대상 기기의 소리를 켜도록(음소거 해제) CLOVA Home extension에 요청합니다. |

{% include "/Develop/References/ClovaHomeInterface/ActionTypeInterfaces/CallElevator.md" %}
{% include "/Develop/References/ClovaHomeInterface/ActionTypeInterfaces/Charge.md" %}
{% include "/Develop/References/ClovaHomeInterface/ActionTypeInterfaces/Close.md" %}
{% include "/Develop/References/ClovaHomeInterface/ActionTypeInterfaces/Close.md" %}
{% include "/Develop/References/ClovaHomeInterface/ActionTypeInterfaces/Lower.md" %}
{% include "/Develop/References/ClovaHomeInterface/ActionTypeInterfaces/Mute.md" %}
{% include "/Develop/References/ClovaHomeInterface/ActionTypeInterfaces/Open.md" %}
{% include "/Develop/References/ClovaHomeInterface/ActionTypeInterfaces/Preheat.md" %}
{% include "/Develop/References/ClovaHomeInterface/ActionTypeInterfaces/Raise.md" %}
{% include "/Develop/References/ClovaHomeInterface/ActionTypeInterfaces/ReleaseMode.md" %}
{% include "/Develop/References/ClovaHomeInterface/ActionTypeInterfaces/StartOscillation.md" %}
{% include "/Develop/References/ClovaHomeInterface/ActionTypeInterfaces/StartRecording.md" %}
{% include "/Develop/References/ClovaHomeInterface/ActionTypeInterfaces/Stop.md" %}
{% include "/Develop/References/ClovaHomeInterface/ActionTypeInterfaces/StopOscillation.md" %}
{% include "/Develop/References/ClovaHomeInterface/ActionTypeInterfaces/StopRecording.md" %}
{% include "/Develop/References/ClovaHomeInterface/ActionTypeInterfaces/TurnOff.md" %}
{% include "/Develop/References/ClovaHomeInterface/ActionTypeInterfaces/TurnOn.md" %}
{% include "/Develop/References/ClovaHomeInterface/ActionTypeInterfaces/Unmute.md" %}
