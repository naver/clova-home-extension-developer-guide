# Shared objects {#SharedObjects}
[CLOVA Home extension 메시지](/Develop/References/Clova_Home_Extension_Message.md)를 보낼 때 메시지 `payload`에 다음과 같은 공유 객체(shared objects)가 사용됩니다.

| 객체 이름                 | 객체 설명                                         |
|-------------------------|------------------------------------------------|
| [ActionInfoObject](#ActionInfoObject)                     | 기기 제어 동작 정보가 담긴 객체  |
| [AirQualityInfoObject](#AirQualityInfoObject)             | 공기질 정보가 담긴 객체            |
| [ApplianceInfoObject](#ApplianceInfoObject)               | IoT 기기의 정보가 담긴 객체        |
| [BatteryInfoObject](#BatteryInfoObject)                   | 배터리 정보가 담긴 객체            |
| [BillInfoObject](#BillInfoObject)                         | 요금 정보가 담긴 객체             |
| [BrightnessInfoObject](#BrightnessInfoObject)             | 조명이나 화면의 밝기 정보가 담긴 객체 |
| [ColorInfoObject](#ColorInfoObject)                       | 대상기기의 조명이나 화면, 전등의 색 정보가 담긴 객체  |
| [ColorTemperatureInfoObject](#ColorTemperatureInfoObject) | 대상기기의 조명이나 화면, 전등의 색온도 정보가 담긴 객체  |
| [ConsumptionInfoObject](#ConsumptionInfoObject)           | 에너지 사용량 정보가 담긴 객체       |
| [CustomCommandInfoObject](#CustomCommandInfoObject)       | 사용자 정의 명령어 정보가 담긴 객체   |
| [CustomInfoObject](#CustomInfoObject)                     | 정보를 임의의 이름, 필요한 단위나 수치로 직접 입력할 때 사용되는 객체 |
| [DetectionCountInfoObject](#DetectionCountInfoObject)     | 기기가 센서나 움직임을 감지하는 카메라를 통해 대상을 감지한 횟수 정보가 담긴 객체  |
| [DirectionInfoObject](#DirectionInfoObject)               | 기기 또는 기기의 특정 부분이 향하거나 왕복하는 방향 정보가 담긴 객체   |
| [EndpointInfoObject](#EndpointInfoObject)                 | 대상 기기가 최종적으로 제어해야 하는 대상 정보가 담긴 객체  |
| [ExpendableInfoObject](#ExpendableInfoObject)             | 기기 소모품의 사용량이나 남은 수명 정보가 담긴 객체  |
| [FineDustInfoObject](#FineDustInfoObject)                 | 미세 먼지 정보가 담긴 객체          |
| [IntensityLevelInfoObject](#IntensityLevelInfoObject)     | 압력이나 수압 세기 정보가 담긴 객체   |
| [ModeInfoObject](#ModeInfoObject)                         | 운전 모드 정보가 담긴 객체          |
| [HumidityInfoObject](#HumidityInfoObject)                 | 습도 정보가 담긴 객체              |
| [PercentageInfoObject](#PercentageInfoObject)                       | 백분율 정보를 담고 있는 객체          |
| [PeriodInfoObject](#PeriodInfoObject)                     | 기간 정보를 담고 있는 객체          |
| [PhaseInfoObject](#PhaseInfoObject)                       | 기기 동작의 단계 정보가 담긴 객체     |
| [PowerStateInfoObject](#PowerStateInfoObject)             | 기기의 전원 상태 정보가 담긴 객체     |
| [ProgressiveTaxBracketInfoObject](#ProgressiveTaxBracketInfoObject)  | 누진세 단계 정보가 담긴 객체 |
| [ScoreInfoObject](#ScoreInfoObject)                       | 수면 점수 정보가 담긴 객체          |
| [SittingStateInfoObject](#SittingStateInfoObject)         | 스마트 의자와 같은 기기에 대한 사용자의 착석 정보가 담긴 객체  |
| [SpeedInfoObject](#SpeedInfoObject)                       | 속도 정보가 담긴 객체              |
| [TemperatureInfoObject](#TemperatureInfoObject)           | 온도 정보를 담고 있는 객체          |
| [TVChannelNameInfoObject](#TVChannelNameInfoObject)       | TV 채널의 이름 정보가 담긴 객체      |
| [TVChannelInfoObject](#TVChannelInfoObject)               | TV 채널 정보가 담긴 객체           |
| [UltraFineDustInfoObject](#UltraFineDustInfoObject)       | 초미세 먼지 정보가 담긴 객체         |
| [VolumeInfoObject](#VolumeInfoObject)                     | 볼륨 정보를 담고 있는 객체          |
| [WeightInfoObject](#WeightInfoObject)                     | 무게 정보를 담고 있는 객체          |

## ActionInfoObject {#ActionInfoObject}
기기 제어 동작 정보가 담긴 객체로써 하나의 기기에 하나의 동작을 수행하는 명령을 표현합니다.

### Object fields
| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:-------:|
| `applianceId` | string  | 기기 ID                      | 필수     |
| `action`      | string  | 기기 제어 동작. 동작 목록은 [ApplianceInfoObject](#ApplianceInfoObject)의 [Actions](#Actions) 항목을 참조합니다.     | 필수/항상     |

### Object Example

```json
// 예제: DiscoverAppliancesResponse 메시지에서 사용된 예
{
  "header": {
    "messageId": "99f9d8ff-9366-4cab-a90c-b4c7eca0abbe",
    "name": "DiscoverAppliancesResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "customCommands": [
      {
        "name": "좋은아침",
        "actions": [
          {
            "applianceId": "device-001",
            "action": "TurnOn"
          },
          {
            "applianceId": "device-012",
            "action": "TurnOff"
          },
          {
            "applianceId": "device-013",
            "action": "TurnOn"
          }
        ]
      },
      {
        "name": "좋은저녁",
        "actions": [
          {
            "applianceId": "device-011",
            "action": "TurnOn"
          },
          {
            "applianceId": "device-012",
            "action": "TurnOff"
          },
          {
            "applianceId": "device-013",
            "action": "TurnOn"
          }
        ]
      }
    ],
    "discoveredAppliances": [
      {
        "applianceId": "device-001",
        "manufacturerName": "device-manufacturer-name",
        "modelName": "스마트 전등",
        "version": "v1.0",
        "friendlyName": "거실 전등",
        "friendlyDescription": "스마트폰으로 제어할 수 있는 전등",
        "isIr": false,
        "actions": [
          "DecrementBrightness",
          "HealthCheck",
          "IncrementBrightness",
          "SetBrightness",
          "TurnOn",
          "TurnOff"
        ],
        "applianceTypes": ["LIGHT"],
        "additionalApplianceDetails": {}
      },
      {
        "applianceId": "device-002",
        "manufacturerName": "device-manufacturer-name",
        "modelName": "스마트 플러그",
        "version": "v1.0",
        "friendlyName": "부엌 플러그",
        "friendlyDescription": "에너지를 절약하는 플러그",
        "isIr": false,
        "actions": [
          "HealthCheck",
          "TurnOn",
          "TurnOff"
        ],
        "applianceTypes": ["SMARTPLUG"],
        "additionalApplianceDetails": {},
        "location": "LIVING_ROOM",
        "tags": ["공부", "철수방", "외출시전원해제기기"]
      }
    ]
  }
}
```

### See also
* [CustomCommandInfoObject](#CustomCommandInfoObject)
* [`DiscoverAppliancesResponse`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetDiscoverAppliancesResponse)

## AirQualityInfoObject {#AirQualityInfoObject}
공기질 정보를 담고 있는 객체입니다. 기기가 측정한 공기질 상태를 나타낼 때 사용되며 문자열로 표현됩니다.

### Object fields
| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:-------------:|
| `index`       | string  | 공기질 수준. 다음과 같은 값으로 제한되어 있습니다.<ul><li><code>"good"</code>: 좋음</li><li><code>"normal"</code>: 보통</li><li><code>"bad"</code>: 나쁨</li><li><code>"verybad"</code>: 매우 나쁨</li></ul> | 필수   |

### Object Example

```json
// 예제: GetAirQualityResponse 메시지에서 사용된 예
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetAirQualityResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "airQuality": {
        "index": "good"
    }
  }
}
```

### See also
* [`GetAirQualityRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetAirQualityRequest)
* [`GetAirQualityResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetAirQualityResponse)

## ApplianceInfoObject {#ApplianceInfoObject}
IoT 기기의 정보를 담고 있는 객체입니다. 사용자 계정에 등록된 기기 목록을 CLOVA에 전송하거나 특정 기기를 대상으로 지정하여 CLOVA Home extension에 기기 제어를 요청할 때 이 객체를 사용합니다.

### Object fields used in requests
| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|---------------|---------|-----------------------------|:-------------:|
| `additionalApplianceDetails` | object        | 제조사나 IoT 서비스에서 제공하는 추가 정보를 담고 있는 필드                                 | 조건부    |
| `applianceId`                | string        | 기기 ID                                                                         | 항상     |

### Object fields used in responses

| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:-------------:|
| `actions[]`                  | string array  | 기기가 지원하는 동작 목록. 클라이언트는 기기가 지원하는 동작 내에서 사용자가 IoT 기기를 제어하도록 제한해야 합니다. | 선택    |
| `additionalApplianceDetails` | object        | 제조사나 IoT 서비스에서 제공하는 추가 정보를 담고 있는 필드. 하위 객체 및 필드는 [additionalApplianceDetails](#additionalApplianceDetails)에서 확인합니다.                                 | 선택    |
| `applianceId`                | string        | 기기 ID                                                                        | 필수    |
| `applianceTypes[]`           | string array  | 기기 타입. `applicationType`에 따라 해당 기기가 수행할 수 있는 동작인 `actions` 필드의 값이 달라집니다. IoT 서비스에서 사용자 계정에 등록된 기기의 타입을 다음 값 중 하나로 지정해야 합니다. Remarks 항목을 참고하여 기기 타입을 입력합니다.                                                                              | 필수    |
| `friendlyName`               | string        | 사용자가 붙여준 기기의 이름                                                           | 선택    |
| `friendlyDescription`        | string        | 기기에 대한 설명                                                                  | 선택    |
| `isIr`                       | boolean       | 기기를 적외선 통신 방식으로 제어하는지 나타내는 필드<ul><li><code>true</code>: 적외선 통신 방식 사용</li><li><code>false</code>: 적외선 통신 방식 사용 안함</li></ul> <div class="note"><p><strong>Note!</strong></p><p>적외선 통신 방식으로 기기를 제어(<code>true</code>)할 때 다음과 같은 제약 사항이 있습니다.</p><ul><li>CLOVA는 사용자에게 기기 제어 결과를 전달하지 않습니다.</li><li>해당 기기 타입이 <code>HealthCheck</code> 동작을 지원하더라도 CLOVA는 <code>HealthCheck</code> 동작과 관련된 요청을 extension으로 전달하지 않습니다.</li></ul></div>  | 선택  |
| `manufacturerName`           | string        | 기기 제조사 이름                                                                  | 선택    |
| `modelName`                  | string        | 기기 모델 이름                                                                   | 선택    |
| `version`                    | string        | 제조사의 소프트웨어 버전                                                            | 선택    |
| `location`                   | string        | 기기가 설치된 장소. [Locations](#Locations) 항목에 있는 코드 값을 입력합니다. 해당 코드 값에 대응되는 한글 표현의 텍스트가 `tags` 필드에 추가됩니다.            | 선택    |
| `tags[]`                     | string array  | 사용자가 기기에 추가한 태그 목록. 사용자는 CLOVA 앱이나 IoT 서비스에서 기기의 설치 장소, 사용 목적, 제품 브랜드와 같은 다양한 속성을 태그로 기기에 추가할 수 있습니다. 같은 속성(태그)을 가지는 기기는 같은 그룹이 되며, 같은 그룹에 속한 기기 사이에 허용 동작이 같으면 동시 제어가 가능해 집니다.  | 선택  |

#### additionalApplianceDetails {#additionalApplianceDetails}

| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:-------------:|
| `actionDetails` | object array        | 기기가 지원하는 동작에 필요한 값의 제약이 있을 경우 관련 정보를 담고 있는 객체입니다. 사용자가 특정값으로 설정하는 동작을 요청했을 때 해당 정보가 있을 경우 CLOVA에서 값의 유효성을 확인하여 유효할 때만 extension에 요청합니다.                                  | 선택    |
| `actionDetails[].action`    | string  | 기기 제어 동작. 동작 목록은 [ApplianceInfoObject](#ApplianceInfoObject)의 [Actions](#Actions) 항목을 참조합니다. | 필수   |
| `actionDetails[].allowableValue` | object  | `actionDetails[].action`에 허용되는 값이나 값의 범위 정보를 담고 있는 객체 | 필수   |
| `actionDetails[].allowableValue.enumValues[]` | string array 또는 number array  | 동작에 허용되는 값을 정의하는 배열. `allowableValue.type`이 "string"일 경우 string array로, "number"일 경우 number array로 입력합니다.  | 선택   |
| `actionDetails[].allowableValue.maxValue`  | number  | 동작에 허용되는 최댓값. `allowableValue.type`이 `boundedNumber` 타입일 경우 필수 값입니다.  | 선택   |
| `actionDetails[].allowableValue.minValue`  | number  | 동작에 허용되는 최솟값. `allowableValue.type`이 `boundedNumber` 타입일 경우 필수 값입니다.  | 선택   |
| `actionDetails[].allowableValue.type` | string  | 허용 값 정의 타입 <ul><li><code>"string"</code>: 문자열 열거형. `actionDetails[].allowableValue.enumValues[]`에 입력한 문자열만 동작에 허용됩니다. </li><li><code>"number"</code>: 수 열거형. `actionDetails[].allowableValue.enumValues[]`에 열거된 숫자만 동작에 허용됩니다.</li><li><code>"boundedNumber"</code>: 수 범위형. `actionDetails[].allowableValue.minValue` 이상, `actionDetails[].allowableValue.maxValue` 이하의 숫자만 동작에 허용됩니다.</li></ul><div class="note"><p><strong>Note!</strong></p><p><code>number</code>와 <code>boundedNumber</code>에 입력된 값은 모두 실수로 취급합니다.</p></div> | 필수   |

### Remarks
[`DiscoverAppliancesRequest`](/Develop/References/ClovaHomeInterface/Discovery_Interfaces.md#DiscoverAppliancesRequest) 메시지를 통해 사용자 기기 목록을 요청하면 CLOVA Home extension은 `additionalApplianceDetails` 필드를 제외한 모든 필드의 정보를 채워서 전달해야 합니다. 이때, `actions` 필드의 값은 보통 `applianceTypes` 필드에 의해 결정되며, `applianceTypes` 필드 값에 따라 다음과 같은 값을 가질 수 있습니다.

| applianceTypes     | 설명             | 허용되는 actions                              |
|--------------------|-----------------|---------------------------------------------|
| `"AIRCONDITIONER"`  | 냉난방기 타입         | ChangeFanSpeed, ChangeMode, ChangePower, DecrementFanSpeed, DecrementTargetTemperature, GetCurrentTemperature, GetDeviceState, GetTargetTemperature, HealthCheck, IncrementFanSpeed, IncrementTargetTemperature, SetFanSpeed, SetMode, SetTargetTemperature, StartOscillation, StopOscillation, TurnOff, TurnOn       |
| `"AIRPURIFIER"`     | 공기청정기 타입        | ChangeFanSpeed, ChangeMode, ChangePower, DecrementFanSpeed, GetAirQuality, GetCurrentTemperature, GetDeviceState, GetFineDust, GetHumidity, GetUltraFineDust, HealthCheck, IncrementFanSpeed, ReleaseMode, SetFanSpeed, SetMode, TurnOff, TurnOn  |
| `"AIRSENSOR"`       | 공기질 측정기 타입     | GetAirQuality, GetCurrentTemperature, GetDeviceState, GetFineDust, GetHumidity, GetUltraFineDust, HealthCheck                                     |
| `"BIDET"`           | 비데 타입            | Close, GetDeviceState, GetExpendableState, HealthCheck, Open, TurnOff, TurnOn                                                                     |
| `"BODYWEIGHTSCALE"` | 체중계 타입           | GetBMI, GetBatteryInfo, GetDeviceState, GetBodyFat, GetHealthScore, GetMuscle, GetWeight, HealthCheck                                             |
| `"BUILDING_ELECTRIC_METER"`| 아파트 전기 타입 | GetConsumption |
| `"BUILDING_ELEVATOR_CALLER"`| 아파트 엘리베이터 타입 | CallElevator |
| `"BUILDING_GAS_METER"`     | 아파트 가스 타입 | GetConsumption |
| `"BUILDING_HEATING_METER"` | 아파트 난방 타입 | GetConsumption |
| `"BUILDING_HOTWATER_METER"`| 아파트 온수 타입 | GetConsumption |
| `"BUILDING_NOTICE_MONITOR"`| 아파트 공지사항 타입 | GetNotice |
| `"BUILDING_PACKAGE"`   | 아파트 택배 타입    | GetPackage |
| `"BUILDING_PARKING_MONITOR"`| 아파트 주차 타입 | GetVehicleLocation |
| `"BUILDING_UTILITY_BILL_MONITOR"`| 아파트 관리비 타입 | GetCurrentBill |
| `"BUILDING_WATER_METER"`   | 아파트 수도 타입 | GetConsumption |
| `"CLOTHESCAREMACHINE"` | 의류 관리기 타입    | GetDeviceState, GetPhase, GetRemainingTime, HealthCheck, TurnOff, TurnOn                                                                          |
| `"CLOTHESDRYER"`    | 의류 건조기 타입       | GetDeviceState, GetPhase, GetRemainingTime, HealthCheck, TurnOff, TurnOn                                                                          |
| `"CLOTHESWASHER"`   | 의류 세탁기 타입       | GetDeviceState, GetPhase, GetRemainingTime, HealthCheck, TurnOff, TurnOn                                                                          |
| `"DEHUMIDIFIER"`    | 제습기 타입           | GetCurrentTemperature, GetDeviceState, GetHumidity, HealthCheck, SetFanSpeed, TurnOff, TurnOn                                                     |
| `"DISHWASHER"`      | 식기 세척기 타입       | GetDeviceState, GetPhase, GetRemainingTime, HealthCheck, TurnOff, TurnOn                                                                          |
| `"ELECTRICKETTLE"`  | 전기 주전자 타입       | GetCurrentTemperature, GetDeviceState, HealthCheck, TurnOff, TurnOn                                                                               |
| `"ELECTRICTOOTHBRUSH"` | 전동 칫솔 타입     | GetDeviceState, HealthCheck                                                                                                                        |
| `"FAN"`             | 선풍기 타입           | DecrementFanSpeed, GetDeviceState, HealthCheck, IncrementFanSpeed, SetFanSpeed, SetMode, StartOscillation, StopOscillation, TurnOff, TurnOn       |
| `"HEATER"`          | 히터 타입            | DecrementTargetTemperature, GetCurrentTemperature, GetDeviceState, GetTargetTemperature, HealthCheck, IncrementTargetTemperature, SetTargetTemperature, TurnOff, TurnOn  |
| `"HOMECAM"`         | 홈캠 타입            | GetDetectionCount, HealthCheck, ReleaseMode, SetMode, StartRecording, StopRecording, TurnOff, TurnOn                                               |
| `"HUMIDIFIER"`      | 가습기 타입           | GetCurrentTemperature, GetDeviceState, GetHumidity, HealthCheck, ReleaseMode, SetFanSpeed, SetMode, TurnOff, TurnOn                               |
| `"KIMCHIREFRIGERATOR"` | 김치 냉장고 타입    | GetDeviceState, HealthCheck                                                                                                                       |
| `"LIGHT"`           | 스마트 조명 기기 타입   | DecrementBrightness, DecrementVolume HealthCheck, GetDeviceState, IncrementBrightness, IncrementVolume, ReleaseMode, SetBrightness, SetColor, SetColorTemperature, SetMode, TurnOff, TurnOn            |
| `"MASSAGECHAIR"`    | 안마 의자 타입        | DecrementIntensityLevel, GetDeviceState, HealthCheck, IncrementIntensityLevel, TurnOff, TurnOn                                                     |
| `"MICROWAVE"`       | 전자 레인지 타입      | GetDeviceState, GetRemainingTime, HealthCheck, TurnOff, TurnOn                                                                                      |
| `"MOTIONSENSOR"`    | 동작 감지 센서 타입    | GetDetectedTime, GetDeviceState, GetPowerState, HealthCheck, ReleaseMode, SetMode, TurnOff, TurnOn                                                |
| `"OPENCLOSESENSOR"` | 열림 감지 센서 타입    | GetCloseTime, GetDeviceState, GetOpenState, GetOpenTime, HealthCheck                                                                               |
| `"OVEN"`            | 오븐 타입            | GetDeviceState, GetRemainingTime, HealthCheck, Preheat                                                                                             |
| `"POWERSTRIP"`      | 멀티 탭 타입         | GetConsumption, GetDeviceState, GetEstimateBill, GetProgressiveTaxBracket, HealthCheck, TurnOff, TurnOn                                             |
| `"PURIFIER"`        | 정수기 타입          | GetConsumption, GetDeviceState, GetExpendableState, HealthCheck, ReleaseMode, SetMode, SetTargetTemperature                                         |
| `"RANGE"`           | 레인지 타입          | GetDeviceState, HealthCheck                                                                                                                         |
| `"RANGEHOOD"`       | 레인지 후드 타입      | GetDeviceState, HealthCheck, TurnOff, TurnOn                                                                                                        |
| `"REFRIGERATOR"`    | 냉장고 타입          | GetDeviceState, HealthCheck, ReleaseMode, SetMode, SetTargetTemperature                                                                             |
| `"RICECOOKER"`      | 전기 밥솥 타입        | GetCleaningCycle, GetDeviceState, GetExpendableState, GetKeepWarmTime, GetPhase, GetRemainingTime, HealthCheck, ReleaseMode, SetMode, Stop, TurnOff, TurnOn          |
| `"ROBOTVACUUM"`     | 로봇 청소기 타입       | Charge, GetBatteryInfo, GetDeviceState, HealthCheck, TurnOff, TurnOn                                                                               |
| `"SETTOPBOX"`       | TV 셋톱 박스 타입     | ChangeInputSource, ChangePower, DecrementChannel, DecrementVolume, GetDeviceState, HealthCheck, IncrementChannel, IncrementVolume, Mute, SetChannel, SetChannelByName, TurnOff, TurnOn, Unmute |
| `"SLEEPINGMONITOR"` | 수면 센서 타입        | GetAsleepDuration, GetAwakeDuration, GetDeviceState, GetSleepScore, GetSleepStartTime, HealthCheck, TurnOff, TurnOn                                |
| `"SMARTBED"`        | 스마트 침대 타입      | GetDeviceState, HealthCheck, Lower, Raise, Stop                                                                                                     |
| `"SMARTCHAIR"`      | 스마트 의자 타입      | GetCurrentSittingState, GetDeviceState, GetRightPostureRatio, GetUsageTime, HealthCheck                                                             |
| `"SMARTCURTAIN"`    | 스마트 커튼 타입      | Close, GetDeviceState, HealthCheck, Open, Stop                                                                                                      |
| `"SMARTHUB"`        | 스마트 허브 타입      | GetCurrentTemperature, GetDeviceState, GetHumidity, GetTargetTemperature, HealthCheck, SetMode                                                      |
| `"SMARTLOCK"`       | 스마트락(도어락) 타입  | GetDeviceState, GetLockState, HealthCheck, SetLockState                                                                                             |
| `"SMARTMETER"`      | 전기 계량기 타입      | GetConsumption, GetCurrentBill, GetDeviceState, GetEstimateBill, GetProgressiveTaxBracket, HealthCheck                                              |
| `"SMARTPLUG"`       | 스마트 플러그 타입     | GetConsumption, GetDeviceState, GetEstimateBill, HealthCheck, TurnOff, TurnOn                                                                       |
| `"SMARTTV"`         | 스마트 TV 타입       | ChangeInputSource, ChangePower, DecrementChannel, DecrementVolume, GetDeviceState, HealthCheck, IncrementChannel, IncrementVolume, Mute, SetChannel, SetChannelByName, TurnOff, TurnOn, Unmute |
| `"SMARTVALVE"`      | 스마트 밸브 타입      | GetDeviceState, GetLockState, SetLockState                                                                                                           |
| `"SMOKESENSOR"`     | 연기 센서 타입        | GetDeviceState, HealthCheck                                                                                                                         |
| `"SWITCH"`          | 가정 내 콘센트 전원을 제어하는 스위치 타입 | GetDeviceState, HealthCheck, TurnOff, TurnOn                                                                                          |
| `"THERMOSTAT"`      | 온도 조절 기기 타입   | DecrementTargetTemperature, GetConsumption, GetCurrentTemperature, GetDeviceState, GetEstimateConsumption, GetTargetTemperature, HealthCheck, IncrementTargetTemperature, SetMode, SetTargetTemperature TurnOff, TurnOn       |
| `"VENTILATOR"`      | 환풍기 타입          | GetAirQuality, GetCurrentTemperature, GetDeviceState, GetHumidity, GetTargetTemperature, HealthCheck, ReleaseMode, SetFanSpeed, SetMode, TurnOff, TurnOn  |
| `"WATERBOILER"`     | 온수기 타입          | GetDeviceState, HealthCheck, SetMode, TurnOff, TurnOn                                                                                                |
| `"WINECELLAR"`      | 와인 셀러 타입        | GetDeviceState, HealthCheck, ReleaseMode, SetMode, SetTargetTemperature, TurnOff, TurnOn                                                             |

<div class="note">
<p><strong>Note!</strong></p>
<p>실제 기기의 기능이 제약이나 제한이 있어 기기의 applianceTypes가 허용하는 동작(actions)보다 적은 동작을 지원한다면 지원하는 동작만 사용하도록 제한해야 합니다. 예를 들면, 사용자가 등록한 공기청정기(<code>AIRPURIFIER</code> 타입)에 팬 속도를 조절할 수 있는 기능이 없으면 해당 기기에 허용되는 actions에서 <code>IncrementFanSpeed</code>와 <code>DecrementFanSpeed</code>를 제외하고 <code>DiscoverAppliancesResponse</code> 메시지를 보내야 합니다. 참고로 사용자가 대상 기기가 지원하지 않는 동작(action)을 요청하면 CLOVA가 바로 사용자에게 허용되지 않는 범위의 요청임을 알려줍니다.</p>
</div>

### Actions {#Actions}
다음 표는 각 actions 항목과 관련이 있는 [메시지 인터페이스](/Develop/References/Message_Interfaces.md)를 나열하고 있습니다.

| actions                    | 관련된 인터페이스                            |
|----------------------------|------------------------------------------|
| CallElevator               | [`CallElevatorConfirmation`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#CallElevatorConfirmation), [`CallElevatorRequest`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#CallElevatorRequest) |
| ChangeFanSpeed             | [`ChangeFanSpeedConfirmation`](/Develop/References/ClovaHomeInterface/Switching_Type_Interfaces.md#ChangeFanSpeedConfirmation), [`ChangeFanSpeedRequest`](/Develop/References/ClovaHomeInterface/Switching_Type_Interfaces.md#ChangeFanSpeedRequest) |
| ChangeInputSource          | [`ChangeInputSourceConfirmation`](/Develop/References/ClovaHomeInterface/Switching_Type_Interfaces.md#ChangeInputSourceConfirmation), [`ChangeInputSourceRequest`](/Develop/References/ClovaHomeInterface/Switching_Type_Interfaces.md#ChangeInputSourceRequest) |
| ChangeMode                 | [`ChangeModeConfirmation`](/Develop/References/ClovaHomeInterface/Switching_Type_Interfaces.md#ChangeModeConfirmation), [`ChangeModeRequest`](/Develop/References/ClovaHomeInterface/Switching_Type_Interfaces.md#ChangeModeRequest) |
| ChangePower                | [`ChangePowerConfirmation`](/Develop/References/ClovaHomeInterface/Switching_Type_Interfaces.md#ChangePowerConfirmation), [`ChangePowerRequest`](/Develop/References/ClovaHomeInterface/Switching_Type_Interfaces.md#ChangePowerRequest) |
| Charge                     | [`ChargeConfirmation`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetChargeConfirmation), [`ChargeRequest`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetChargeRequest) |
| Close                      | [`CloseConfirmation`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetCloseConfirmation), [`CloseRequest`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetCloseRequest)  |
| DecrementBrightness        | [`DecrementBrightnessConfirmation`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#DecrementBrightnessConfirmation), [`DecrementBrightnessRequest`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#DecrementBrightnessRequest) |
| DecrementChannel           | [`DecrementChannelConfirmation`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#DecrementChannelConfirmation), [`DecrementChannelRequest`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#DecrementChannelRequest) |
| DecrementFanSpeed          | [`DecrementFanSpeedConfirmation`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#DecrementFanSpeedConfirmation), [`DecrementFanSpeedRequest`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#DecrementFanSpeedRequest) |
| DecrementIntensityLevel    | [`DecrementIntensityLevelConfirmation`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#DecrementIntensityLevelConfirmation), [`DecrementIntensityLevelRequest`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#DecrementIntensityLevelRequest)  |
| DecrementTargetTemperature | [`DecrementTargetTemperatureConfirmation`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#DecrementTargetTemperatureConfirmation), [`DecrementTargetTemperatureRequest`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#DecrementTargetTemperatureRequest) |
| DecrementVolume            | [`DecrementVolumeConfirmation`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#DecrementVolumeConfirmation), [`DecrementVolumeRequest`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#DecrementVolumeRequest) |
| GetAirQuality              | [`GetAirQualityRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetAirQualityRequest), [`GetAirQualityResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetAirQualityResponse) |
| GetAsleepDuration              | [`GetAsleepDurationRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetAsleepDurationRequest), [`GetAsleepDurationResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetAsleepDurationResponse) |
| GetAwakeDuration              | [`GetAwakeDurationRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetAwakeDurationRequest), [`GetAwakeDurationResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetAwakeDurationResponse) |
| GetBatteryInfo              | [`GetBatteryInfoRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetBatteryInfoRequest), [`GetBatteryInfoResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetBatteryInfoResponse) |
| GetBMI              | [`GetBMIRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetBMIRequest), [`GetBMIResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetBMIResponse) |
| GetBodyFat                 | [`GetBodyFatRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetBodyFatRequest), [`GetBodyFatResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetBodyFatResponse)  |
| GetCleaningCycle                | [`GetCleaningCycleRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetCleaningCycleRequest), [`GetCleaningCycleResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetCleaningCycleResponse)  |
| GetCloseTime                | [`GetCloseTimeRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetCloseTimeRequest), [`GetCloseTimeResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetCloseTimeResponse)  |
| GetConsumption              | [`GetConsumptionRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetConsumptionRequest), [`GetConsumptionResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetConsumptionResponse)  |
| GetCurrentBill              | [`GetCurrentBillRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetCurrentBillRequest), [`GetCurrentBillResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetCurrentBillResponse)  |
| GetCurrtentSittingState     | [`GetCurrentSittingStateRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetCurrentSittingStateRequest), [`GetCurrentSittingStateResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetCurrentSittingStateResponse) |
| GetCurrentTemperature       | [`GetCurrentTemperatureRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetCurrentTemperatureRequest), [`GetCurrentTemperatureResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetCurrentTemperatureResponse) |
| GetDetectionCount          | [`GetDetectionCountRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetDetectionCountRequest), [`GetDetectionCountResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetDetectionCountResponse)  |
| GetDetectedTime           | [`GetDetectedTimeRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetDetectedTimeRequest), [`GetDetectedTimeResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetDetectedTimeResponse)  |
| GetDeviceState             | [`GetDeviceStateRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetDeviceStateRequest), [`GetDeviceStateResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetDeviceStateResponse)  |
| GetEstimateBill            | [`GetEstimateBillRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetEstimateBillRequest), [`GetEstimateBillResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetEstimateBillResponse)  |
| GetEstimateConsumption     | [`GetEstimateConsumptionRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetEstimateConsumptionRequest), [`GetEstimateConsumptionResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetEstimateConsumptionResponse)  |
| GetExpendableState         | [`GetExpendableStateRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetExpendableStateRequest), [`GetExpendableStateResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetExpendableStateResponse)  |
| GetFineDust                | [`GetFineDustRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetFineDustRequest), [`GetFineDustResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetFineDustResponse) |
| GetHealthScore             | [`GetHealthScoreRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetHealthScoreRequest), [`GetHealthScoreResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetFineDustResponse) |
| GetHumidity                | [`GetHumidityRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetHumidityRequest), [`GetHumidityResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetHealthScoreResponse) |
| GetKeepWarmTime            | [`GetKeepWarmTimeRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetKeepWarmTimeRequest), [`GetKeepWarmTimeResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetKeepWarmTimeResponse) |
| GetLockState               | [`GetLockStateRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetLockStateRequest), [`GetLockStateResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetLockStateResponse) |
| GetMuscle                  | [`GetMuscleRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetMuscleRequest), [`GetMuscleResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetMuscleResponse) |
| GetNotice                  | [`GetNoticeRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetNoticeRequest), [`GetNoticeResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetNoticeResponse) |
| GetOpenState               | [`GetOpenStateRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetOpenStateRequest), [`GetOpenStateResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetOpenStateResponse)  |
| GetOpenTime                | [`GetOpenTimeRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetOpenTimeRequest), [`GetOpenTimeResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetOpenTimeResponse)  |
| GetPackage                 | [`GetPackageRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetPackageRequest), [`GetPackageResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetPackageResponse)  |
| GetPhase                   | [`GetPhaseRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetPhaseRequest), [`GetPhaseResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetPhaseResponse)  |
| GetPowerState              | [`GetPowerStateRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetPowerStateRequest), [`GetPowerStateResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetPowerStateResponse)  |
| GetProgressiveTaxBracket   | [`GetProgressiveTaxBracketRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetProgressiveTaxBracketRequest), [`GetProgressiveTaxBracketResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetProgressiveTaxBracketResponse) |
| GetRemainingTime           | [`GetRemainingTimeRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetRemainingTimeRequest), [`GetRemainingTimeResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetRemainingTimeResponse)  |
| GetRightPostureRatio       | [`GetRightPostureRatioRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetRightPostureRatioRequest), [`GetRightPostureRatioResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetRightPostureRatioResponse)  |
| GetSleepScore              | [`GetSleepScoreRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetSleepScoreRequest), [`GetSleepScoreResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetSleepScoreResponse) |
| GetSleepStartTime          | [`GetSleepStartTimeRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetSleepStartTimeRequest), [`GetSleepStartTimeResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetSleepStartTimeResponse) |
| GetTargetTemperature       | [`GetTargetTemperatureRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetTargetTemperatureRequest), [`GetTargetTemperatureResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetTargetTemperatureResponse) |
| GetUltraFineDust           | [`GetUltraFineDustRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetUltraFineDustRequest), [`GetUltraFineDustResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetUltraFineDustResponse) |
| GetUsageTime               | [`GetUsageTimeRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetUsageTimeRequest), [`GetUsageTimeResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetUsageTimeResponse)  |
| GetVehicleLocation         | [`GetVehicleLocationRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetVehicleLocationRequest), [`GetVehicleLocationResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetVehicleLocationResponse)  |
| GetWeight                  | [`GetWeightRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetWeightRequest), [`GetWeightResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetWeightResponse)  |
| HealthCheck                | [`HealthCheckRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#HealthCheckRequest), [`HealthCheckResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#HealthCheckResponse) |
| IncrementBrightness        | [`IncrementBrightnessConfirmation`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#IncrementBrightnessConfirmation), [`IncrementBrightnessRequest`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#IncrementBrightnessRequest)  |
| IncrementChannel           | [`IncrementChannelConfirmation`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#IncrementChannelConfirmation), [`IncrementChannelRequest`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#IncrementChannelRequest) |
| IncrementFanSpeed          | [`IncrementFanSpeedConfirmation`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#IncrementFanSpeedConfirmation), [`IncrementFanSpeedRequest`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#IncrementFanSpeedRequest) |
| IncrementIntensityLevel    | [`IncrementIntensityLevelConfirmation`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#IncrementIntensityLevelConfirmation), [`IncrementIntensityLevelRequest`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#IncrementIntensityLevelConfirmation)  |
| IncrementTargetTemperature | [`IncrementTargetTemperatureConfirmation`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#IncrementTargetTemperatureConfirmation), [`IncrementTargetTemperatureRequest`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#IncrementTargetTemperatureConfirmation) |
| IncrementVolume            | [`IncrementVolumeConfirmation`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#IncrementVolumeConfirmation), [`IncrementVolumeRequest`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#IncrementVolumeRequest) |
| Lower                      | [`LowerConfirmation`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetLowerConfirmation), [`LowerRequest`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetLowerRequest)  |
| Mute                       | [`MuteConfirmation`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetMuteConfirmation), [`MuteRequest`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetMuteRequest) |
| Open                       | [`OpenConfirmation`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetOpenConfirmation), [`OpenRequest`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetOpenRequest)  |
| Preheat                    | [`PreheatConfirmation`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetPreheatConfirmation), [`PreheatRequest`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetPreheatRequest)  |
| Raise                      | [`RaiseConfirmation`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetRaiseConfirmation), [`RaiseRequest`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetRaiseRequest)  |
| ReleaseMode              | [`ReleaseModeConfirmation`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetReleaseModeConfirmation), [`ReleaseModeRequest`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetReleaseModeRequest)  |
| SetBrightness              | [`SetBrightnessConfirmation`](/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md#SetBrightnessConfirmation), [`SetBrightnessRequest`](/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md#SetBrightnessRequest)  |
| SetChannel                 | [`SetChannelConfirmation`](/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md#SetChannelConfirmation), [`SetChannelRequest`](/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md#SetChannelRequest) |
| SetChannelByName           | [`SetChannelByNameConfirmation`](/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md#SetChannelByNameConfirmation), [`SetChannelByNameRequest`](/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md#SetChannelByNameRequest) |
| SetColor                   | [`SetColorConfirmation`](/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md#SetColorConfirmation), [`SetColorRequest`](/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md#SetColorRequest)  |
| SetColorTemperature        | [`SetColorTemperatureConfirmation`](/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md#SetColorTemperatureConfirmation), [`SetColorTemperatureRequest`](/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md#SetColorTemperatureRequest)  |
| SetFanSpeed                | [`SetFanSpeedConfirmation`](/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md#SetFanSpeedConfirmation), [`SetFanSpeedRequest`](/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md#SetFanSpeedRequest)  |
| SetLockState               | [`SetLockStateConfirmation`](/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md#SetLockStateConfirmation), [`SetLockStateRequest`](/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md#SetLockStateRequest)  |
| SetMode                    | [`SetModeConfirmation`](/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md#SetModeConfirmation), [`SetModeRequest`](/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md#SetModeRequest) |
| SetTargetTemperature       | [`SetTargetTemperatureConfirmation`](/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md#SetTargetTemperatureConfirmation), [`SetTargetTemperatureRequest`](/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md#SetTargetTemperatureConfirmation)  |
| StartOscillation           | [`StartOscillationConfirmation`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetStartOscillationConfirmation), [`StartOscillationRequest`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetStartOscillationRequest)  |
| StartRecording             | [`StartRecordingConfirmation`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetStartRecordingConfirmation), [`StartRecordingRequest`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetStartRecordingRequest)  |
| Stop                       | [`StopConfirmation`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetStopConfirmation), [`StopRequest`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetStopRequest)  |
| StopOscillation            | [`StopOscillationConfirmation`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetStopOscillationConfirmation), [`StopOscillationRequest`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetStopOscillationRequest)  |
| StopRecording              | [`StopRecordingConfirmation`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetStopRecordingConfirmation), [`StopRecordingRequest`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetStopRecordingRequest)  |
| TurnOff                    | [`TurnOffConfirmation`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetTurnOffConfirmation), [`TurnOffRequest`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetTurnOffRequest) |
| TurnOn                     | [`TurnOnConfirmation`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetTurnOnConfirmation), [`TurnOnRequest`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetTurnOnRequest) |
| Unmute                     | [`UnmuteConfirmation`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetUnmuteConfirmation), [`UnmuteRequest`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetUnmuteRequest) |

<div class="tip">
<p><strong>Tip!</strong></p>
<p><a href="/Develop/References/ClovaHomeInterface/Discovery_Interfaces.md#DiscoverAppliancesResponse"><code>DiscoverAppliancesResponse</code></a> 메시지를 통해 사용자가 등록한 IoT 기기 목록을 전달할 때 각 기기의 위치를 `location` 필드를 이용하여 CLOVA에 전송하면 사용자 IoT 기기의 위치가 자동으로 설정됩니다.</p>
</div>

### Locations {#Locations}

다음 표는 `location` 필드에서 지원하는 위치 정보입니다. 이 정보는 사용자의 발화를 분석하거나 사용자에게 기기를 보여줄 때 사용됩니다.

{% include "/Develop/References/ClovaHomeInterface/Location.md" %}

### Object Example

```json
// 예제 1: DiscoverAppliancesResponse 메시지에서 사용된 예
{
  "header": {
    "messageId": "99f9d8ff-9366-4cab-a90c-b4c7eca0abbe",
    "name": "DiscoverAppliancesResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "discoveredAppliances": [
      {
        "applianceId": "device-001",
        "manufacturerName": "device-manufacturer-name",
        "modelName": "스마트 전등",
        "version": "v1.0",
        "friendlyName": "거실 전등",
        "friendlyDescription": "스마트폰으로 제어할 수 있는 전등",
        "isIr": false,
        "actions": [
          "HealthCheck",
          "TurnOn",
          "TurnOff",
          "SetBrightness"
        ],
        "applianceTypes": ["LIGHT"],
        "additionalApplianceDetails": {
          "actionDetails": [
            {
              "action": "SetMode",
              "allowableValue": {
                "type": "string",
                "enumValues": ["sleep", "rest"]
              }
            },
            {
              "action": "SetBrightness",
              "allowableValue": {
                "type": "boundedNumber",
                "minValue": 30,
                "maxValue": 100
              }
            }
          ]
        },
        "location": "LIVING_ROOM"
      },
      {
        "applianceId": "device-002",
        "manufacturerName": "device-manufacturer-name",
        "modelName": "스마트 플러그",
        "version": "v1.0",
        "friendlyName": "부엌 플러그",
        "friendlyDescription": "에너지를 절약하는 플러그",
        "isIr": false,
        "actions": [
          "HealthCheck",
          "TurnOn",
          "TurnOff"
        ],
        "applianceTypes": ["SMARTPLUG"],
        "additionalApplianceDetails": {},
        "location": ""
      }
    ]
  }
}

// 예제 2: TurnOnRequest 메시지에서 사용된 예
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

### See also
* [`DiscoverAppliancesResponse`](/Develop/References/ClovaHomeInterface/Discovery_Interfaces.md#DiscoverAppliancesResponse)
* [`DiscoverAppliancesRequest`](/Develop/References/ClovaHomeInterface/Discovery_Interfaces.md#DiscoverAppliancesRequest)

## BatteryInfoObject {#BatteryInfoObject}
기기의 배터리 정보를 담고 있는 객체입니다. 배터리 정보를 나타낼 때 사용되며 백분율을 의미하는 정수(0~100)로 표현됩니다.

### Object fields
| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:-------:|
| `value`       | number  | 배터리 잔량(%)                 | 필수     |

### Object Example

```json
// 예제: GetBatteryInfoResponse 메시지에서 사용된 예
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "GetBatteryInfoResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "batteryInfo": {
      "value": 40
    }
  }
}
```

### See also
* [`GetBatteryInfoResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetBatteryInfoResponse)

## BillInfoObject {#BillInfoObject}
기기가 측정한 에너지 사용량을 기반으로 도출된 요금 정보를 담고 있는 객체입니다. 요금 정보는 액수와 통화 단위를 나누어 표시합니다.

### Object fields
| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:-------------:|
| `currency`    | string  | 통화 단위 (<a href="https://en.wikipedia.org/wiki/ISO_4217" target="_blank">ISO 4217</a>)  | 필수 |
| `value`       | number  | 요금의 액수                    | 필수   |

### Object Example

```json
// 예제: GetCurrentBillResponse 메시지에서 사용된 예
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetCurrentBillResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "currentBill": {
        "value": 29900,
        "currency": "KRW"
    },
    "applianceResponseTimestamp": "2017-11-23T20:30:54+09:00"
  }
}
```

### See also
* [`GetCurrentBillRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetCurrentBillRequest)
* [`GetCurrentBillResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetCurrentBillResponse)
* [`GetEstimateBillRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetEstimateBillRequest)
* [`GetEstimateBillResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetEstimateBillResponse)

## BrightnessInfoObject {#BrightnessInfoObject}
조명이나 화면의 밝기 정보를 담고 있는 객체입니다. 변경할 조명이나 화면의 밝기나 변경 전후의 밝기를 나타낼 때 사용되며 백분율을 의미하는 정수(0~100)로 표현됩니다.

### Object fields
| 필드 이름       | 자료형    | 필드 설명                     | 필수/포함 여부 |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | number  | 밝기(%)                      | 필수/항상     |

### Object Example

```json
// 예제 1: IncrementBrightnessRequest 메시지에서 사용된 예
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "IncrementBrightnessRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-010"
    },
    "deltaBrightness": {
      "value": 40
    }
  }
}

// 예제 2: IncrementBrightnessConfirmation 메시지에서 사용된 예
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "DecrementBrightnessConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "targetBrightness": {
      "value": 40
    },
    "previousState": {
      "targetBrightness": {
        "value": 20
      }
    }
  }
}
```

### See also
* [`DecrementBrightnessConfirmation`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#DecrementBrightnessConfirmation)
* [`DecrementBrightnessRequest`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#DecrementBrightnessRequest)
* [`IncrementBrightnessConfirmation`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#IncrementBrightnessConfirmation)
* [`IncrementBrightnessRequest`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#IncrementBrightnessRequest)
* [`SetBrightnessConfirmation`](/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md#SetBrightnessConfirmation)
* [`SetBrightnessRequest`](/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md#SetBrightnessRequest)

## ColorInfoObject {#ColorInfoObject}
대상 기기의 조명이나 화면, 전등의 색 정보를 담고 있는 객체입니다. 변경할 대상 기기의 조명이나 화면, 전등의 색이나 변경 전후의 색을 나타낼 때 사용됩니다. (<a href="https://en.wikipedia.org/wiki/HSL_and_HSV" target="_blank">HSV</a>) 방식으로 색 정보를 표현합니다.

### Object fields
| 필드 이름       | 자료형    | 필드 설명                     | 필수/포함 여부 |
|---------------|---------|-----------------------------|:-------------:|
| `brightness`  | number  | 밝기(0~100). 특정 기기의 밝기 설정에 [BrightnessInfoObject](#BrightnessInfoObject)가 사용되면 이 필드는 생략될 수 있습니다.  | 선택/조건부 |
| `hue`         | number  | 색상(0~360)                  | 필수/항상 |
| `saturation`  | number  | 채도(0~100)                  | 필수/항상 |

### Object Example

```json
// 예제 1: SetColorRequest 메시지에서 사용된 예
{
  "header": {
    "messageId": "a97dff79-5684-4535-8df3-193713c478aa",
    "name": "SetColorRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-020"
    },
    "color": {
  		"hue": 100,
      "saturation": 100,
      "brightness": 100
  	}
  }
}

// 예제 2: SetColorConfirmation 메시지에서 사용된 예
{
  "header": {
    "messageId": "0e380076-59f1-4417-9d30-895be4b34cea",
    "name": "SetColorConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
  	"color": {
  		"hue": 100,
      "saturation": 100,
      "brightness": 100
  	}
  }
}
```

### See also

* [`SetColorConfirmation`](/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md#SetColorConfirmation)
* [`SetColorRequest`](/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md#SetColorRequest)


## ColorTemperatureInfoObject {#ColorTemperatureInfoObject}
대상 기기의 조명이나 화면, 전등의 색온도 정보를 담고 있는 객체입니다. 변경할 대상 기기의 조명이나 화면, 전등의 색온도나 변경 전후의 색온도를 나타낼 때 사용되며 단위는 K(Kelvin)입니다.

### Object fields
| 필드 이름       | 자료형    | 필드 설명                     | 필수/포함 여부 |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | number  | 색온도(K, Kelvin)             | 필수/항상     |

### Object Example

```json
// 예제 1: SetColorTemperatureRequest 메시지에서 사용된 예
{
  "header": {
    "messageId": "a97dff79-5684-4535-8df3-193713c478aa",
    "name": "SetColorTemperatureRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-020"
    },
    "colorTemperature": {
      "value": 3600
    }
  }
}

// 예제 2: SetColorTemperatureConfirmation 메시지에서 사용된 예
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "SetColorTemperatureConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
  	"colorTemperature": {
  		"value": 3600
  	}
  }
}
```

### See also

* [`SetColorTemperatureConfirmation`](/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md#SetColorTemperatureConfirmation)
* [`SetColorTemperatureRequest`](/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md#SetColorTemperatureRequest)

## ConsumptionInfoObject {#ConsumptionInfoObject}
기기가 측정한 에너지 또는 자원 사용량 정보를 담고 있는 객체입니다. 에너지 사용 수치와 단위를 나누어 표시합니다.

### Object fields
| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:-------------:|
| `name`        | string  | 에너지 또는 자원 사용 항목명                   | 필수  |
| `unit`        | string  | 에너지 또는 자원 사용 단위<ul><li>전력: `KW`(`kw`), `W`</li><li>부피: `KL`(`kl`), `L`(`l`), `cc`</li></ul>        | 필수  |
| `value`       | number  | 에너지 또는 자원 사용 수치                    | 필수   |

### Object Example

```json
// 예제 1: GetConsumptionResponse 메시지에서 사용된 예 - 전력 사용량
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetConsumptionResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "consumption": [
      {
        "name": "전기사용량",
        "value": 79.7,
        "unit": "KW"
      }
    ],
    "applianceResponseTimestamp": "2017-11-23T20:30:54+09:00"
  }
}

// 예제 2: GetConsumptionResponse 메시지에서 사용된 예 - 물 사용량
{
  "header": {
    "messageId": "6a5f8139-a15b-4f55-b7ed-d92540075c61",
    "name": "GetConsumptionResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "consumption": [
      {
        "name": "마신물",
        "value": 24,
        "unit": "l"
      }
    ],
    "applianceResponseTimestamp": "2019-12-21T20:30:54+09:00"
  }
}
```

### See also
* [`GetConsumptionResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetConsumptionResponse)

## CustomCommandInfoObject {#CustomCommandInfoObject}

사용자 정의 명령의 정보를 담고 있는 객체입니다. 사용자가 CLOVA 앱을 통해 등록한 명령에 대한 정보를 담고 있으며, [`DiscoverAppliancesResponse`](/Develop/References/ClovaHomeInterface/Discovery_Interfaces.md#DiscoverAppliancesResponse) 메시지의 기기 조회 결과에 사용자 계정에 등록된 명령이 함께 반환됩니다. 이 객체에는 사용자 정의 명령 호출 시 수행하게 되는 기기 제어 동작이 포함되어 있습니다.

### Object fields

| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:-------------:|
| `name`        | string  | 사용자 정의 명령의 이름.             | 필수      |
| `actions[]`   | [ActionInfoObject](#ActionInfoObject) array | 사용자 정의 명령을 통해 수행할 기기 제어 동작 목록  | 필수  |

### Object Example

```json
// 예제: DiscoverAppliancesResponse 메시지에서 사용된 예
{
  "header": {
    "messageId": "99f9d8ff-9366-4cab-a90c-b4c7eca0abbe",
    "name": "DiscoverAppliancesResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "customCommands": [
      {
        "name": "좋은아침",
        "actions": [
          {
            "applianceId": "device-001",
            "action": "TurnOn"
          },
          {
            "applianceId": "device-012",
            "action": "TurnOff"
          },
          {
            "applianceId": "device-013",
            "action": "TurnOn"
          }
        ]
      },
      {
        "name": "좋은저녁",
        "actions": [
          {
            "applianceId": "device-011",
            "action": "TurnOn"
          },
          {
            "applianceId": "device-012",
            "action": "TurnOff"
          },
          {
            "applianceId": "device-013",
            "action": "TurnOn"
          }
        ]
      }
    ],
    "discoveredAppliances": [
      {
        "applianceId": "device-001",
        "manufacturerName": "device-manufacturer-name",
        "modelName": "스마트 전등",
        "version": "v1.0",
        "friendlyName": "거실 전등",
        "friendlyDescription": "스마트폰으로 제어할 수 있는 전등",
        "isIr": false,
        "actions": [
          "DecrementBrightness",
          "HealthCheck",
          "IncrementBrightness",
          "SetBrightness",
          "TurnOn",
          "TurnOff"
        ],
        "applianceTypes": ["LIGHT"],
        "additionalApplianceDetails": {}
      },
      {
        "applianceId": "device-002",
        "manufacturerName": "device-manufacturer-name",
        "modelName": "스마트 플러그",
        "version": "v1.0",
        "friendlyName": "부엌 플러그",
        "friendlyDescription": "에너지를 절약하는 플러그",
        "isIr": false,
        "actions": [
          "HealthCheck",
          "TurnOn",
          "TurnOff"
        ],
        "applianceTypes": ["SMARTPLUG"],
        "additionalApplianceDetails": {},
        "location": "LIVING_ROOM",
        "tags": ["공부", "철수방", "외출시전원해제기"]
      }
    ]
  }
}
```

### See also
* [ActionInfoObject](#ActionInfoObject)
* [`DiscoverAppliancesResponse`](/Develop/References/ClovaHomeInterface/Discovery_Interfaces.md#DiscoverAppliancesResponse)

## CustomInfoObject {#CustomInfoObject}

정보를 임의의 이름, 필요한 단위나 수치로 직접 입력할 때 사용되는 객체입니다. [공유 객체](/Develop/References/ClovaHomeInterface/Shared_Objects.md)가 기본으로 제공하는 객체로 정보를 표현할 수 없을 때 이 객체를 사용하거나 [`GetDeviceStateResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetDeviceStateResponse) 메시지를 통해 대상 기기가 가진 전체 정보를 제공할 때 사용됩니다.

### Object fields
| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:-------------:|
| `name`        | string            | 기기 상태 정보나 측정 대상을 가리킬 임의의 이름. 사용자에게 응답할 때 이 필드에 입력된 상태 이름이 음성으로 출력됩니다. | 필수 |
| `value`       | number 또는 string | 상태 값이나 측정 값.                                                                             | 필수 |
| `unit`        | string            | 기기 상태 값이나 측정 값의 단위 정보. `value` 필드의 자료형이 문자열이면 생략되며, 수치이면 다음과 같은 단위를 가질 수 있습니다.<ul><li><code>"celsius"</code>: 섭씨 온도</li><li><code>"percentage"</code>: 퍼센트</li></ul> | 선택 |

### Object Example

```json
// 예제: GetDeviceStateResponse 메시지에서 사용된 예
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetDeviceStateResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "states": [
      {
        "name": "냉동실온도",
        "value": -11,
        "unit": "celsius"
      },
      {
        "name": "냉장실온도",
        "value": 2,
        "unit": "celsius"
      },
      {
        "name": "냉장실습도",
        "value": 10,
        "unit": "percentage"
      },
    ],
    "applianceResponseTimestamp": "2017-11-23T20:31:18+09:00"
  }
}
```

### See also
* [`GetDeviceStateResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetDeviceStateResponse)

## DetectionCountInfoObject {#DetectionCountInfoObject}

기기가 센서나 움직임을 감지하는 카메라를 통해 대상을 감지한 횟수 정보를 담고 있는 객체입니다.

### Object fields
| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | string  | 감지 횟수를 문자열로 표현한 값. `"오늘 9건"`, `"어제 2건, 오늘 1건"`와 같은 문자열을 가질 수 있습니다. | 필수     |

### Object Example

```json
// 예제: GetDetectionCountResponse 메시지에서 사용된 예
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetDetectionCountResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "detectionCount": {
      "value": "어제 2건, 오늘 1건"
    },
    "applianceResponseTimestamp": "2019-08-16T15:18:27+09:00"
  }
}
```

### See also
* [`GetDetectionCountResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetDetectionCountResponse)

## DirectionInfoObject {#DirectionInfoObject}

기기 또는 기기의 특정 부분이 향하거나 왕복하는 방향 정보를 담고 있는 객체입니다.

### Object fields
| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | string  | 방향 정보를. 현재는 다음과 같은 값을 입력할 수 있습니다.<ul><li><code>"horizontal"</code>: 좌우/수평 방향</li><li><code>vertical</code>: 상하/수직 방향</li></ul> | 필수 |

### Object Example

```json
// 예제: StartOscillationRequest 메시지에서 사용된 예
{
  "header": {
    "messageId": "85253b03-09cd-43af-bd06-4e54855ce649",
    "name": "StartOscillationRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-025"
    },
    "direction": {
      "value": "horizontal"
    }
  }
}
```

### See also

* [`StartOscillationRequest`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetStartOscillationRequest)

## EndpointInfoObject {#EndpointInfoObject}
대상 기기가 최종적으로 제어해야 하는 대상 정보가 담긴 객체입니다. 대상 기기가 온도나 특정 설정 값을 적용할 최종 대상(endpoint)이 사용자에 의해 지정될 수 있으며, 최종 대상은 기기의 특정 부분, 구동 방식이나 이를 적용할 영역과 같은 것을 의미합니다. 희망 온도를 조정하는 것을 예로 들면 사용자는 냉장고 온도를 조절할 때 냉동실의 온도를 변경할지 냉장실의 온도를 변경할지 추가로 지정할 수 있습니다. {{ "또, 난방 기능이 있는 에어컨을 조절할 때는 냉방 모드로 동작할 때의 온도와 난방 모드로 동작할 때의 온도를 구분하여 제어할 수 있습니다." if book.L10N.TargetCountryCode == "JP" }}

### Object fields
| 필드 이름       | 자료형    | 필드 설명                     | 필수/포함 여부 |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | string  | 최종 대상을 나타내는 문자열. 자세한 내용은 [Endpoint references](#EndpointReferences)를 참조합니다.    | 필수/항상 |

### Endpoint references {#EndpointReferences}

| Endpoint 코드   | 설명                                   |
|----------------|---------------------------------------|
| coldwater      | 정수기나 온도 조절기의 냉수 온도              |
| freezer        | 냉장고의 냉동실                           |
| fridge         | 냉장고의 냉장실                           |
| hotwater       | 정수기나 온도 조절기의 온수 온도              |

<div class="tip">
  <p><strong>Tip!</strong></p>
  <p>최종 대상의 목록은 계속 추가될 수 있습니다.</p>
</div>

### Object Example

```json
// 예제 1: SetTargetTemperatureRequest 메시지에서 사용된 예
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "SetTargetTemperatureRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-001"
    },
    "targetTemperature": {
      "value": 22
    },
    "endpoint": {
      "value": "freezer"
    }
  }
}

// 예제 2: SetTargetTemperatureConfirmation 메시지에서 사용된 예
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "SetTargetTemperatureConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "targetTemperature": {
      "value": 22
    },
    "endpoint": {
      "value": "freezer"
    }
  }
}
```

### See also

* [`SetTargetTemperatureConfirmation`](/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md#SetTargetTemperatureConfirmation)
* [`SetTargetTemperatureRequest`](/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md#SetTargetTemperatureRequest)

## ExpendableInfoObject {#ExpendableInfoObject}
기기 소모품의 사용량이나 남은 수명 정보를 담고 있는 객체입니다. 대상 기기의 소모품 사용량이나 남은 수명을 나타낼 때 사용됩니다.

### Object fields
| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:-------------:|
| `name`          | string  | 소모품의 이름                  | 필수 |
| `remainingTime` | sting   | 소모품의 남은 수명(<a href="https://en.wikipedia.org/wiki/ISO_8601#Durations" target="_blank">ISO 8601 Durations</a>)    | 선택 |
| `usage`         | [CustomInfoObject](#CustomInfoObject)          | 소모품의 사용량 (회수 또는 퍼센트로 표현 가능)      | 선택 |

### Object Example

```json
// 예제: GetExpendableStateResponse 메시지에서 사용된 예
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetExpendableStateResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "expendableInfo": [
      {
        "name": "패킹",
        "remainingTime": "P0001-04-10"
      },
      {
        "name": "1 번 필터",
        "usage": {
          "value": 80,
          "unit": "percentage"
        }
      }
    ],
    "applianceResponseTimestamp": "2017-11-23T20:31:18+09:00"
  }
}
```

### See also
* [`GetExpendableStateResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetExpendableStateResponse)

## FineDustInfoObject {#FineDustInfoObject}
미세 먼지 정보를 담고 있는 객체입니다. 기기가 측정한 미세 먼지 지수나 수준을 나타낼 때 사용됩니다.

### Object fields
| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | number  | 미세 먼지 지수                  | 선택    |
| `index`       | string  | 미세 먼지 수준. 다음과 같은 값으로 제한되어 있습니다.<ul><li><code>"good"</code>: 좋음</li><li><code>"normal"</code>: 보통</li><li><code>"bad"</code>: 나쁨</li><li><code>"verybad"</code>: 매우 나쁨</li></ul> | 필수     |

### Object Example

```json
// 예제: GetFineDustResponse 메시지에서 사용된 예
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetFineDustResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "fineDust": {
        "value": 77,
        "index": "normal"
    }
  }
}
```

### See also
* [`GetFineDustResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetFineDustResponse)

## IndexInfoObject {#IndexInfoObject}

신체질량지수와 같은 지수 정보를 담고 있는 객체입니다.

### Object fields
| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | number  | 지수 값                      | 선택     |

### Object Example

```json
// 예제: GetBMIResponse 메시지에서 사용된 예
{
  "header": {
    "messageId": "5e022ef3-3ba9-471a-954f-c9e6aa2d773a",
    "name": "GetBMIResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "bmi": {
      "value": 20.5
    },
    "applianceResponseTimestamp": "2019-08-19T18:25:12+09:00"
  }
}
```

### See also
* [`GetBMIResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetBMIResponse)

## IntensityLevelInfoObject {#IntensityLevelInfoObject}
압력/수압의 세기 정보를 담고 있는 객체입니다. 각 기기가 가진 수준의 압력/수압으로 세기가 표시됩니다.

### Object fields
| 필드 이름       | 자료형    | 필드 설명                     | 필수/포함 여부 |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | number  | 압력/수압의 세기 정보            | 선택/조건부    |

### Object Example

```json
// 예제 1: IncrementIntensityLevelRequest 메시지에서 사용된 예
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "IncrementIntensityLevelRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-015"
    },
    "deltaIntensity": {
      "value": 1
    }
  }
}

// 예제 2: IncrementIntensityLevelConfirmation 메시지에서 사용된 예
{
  "header": {
    "messageId": "be3dde71-84c0-48cf-80d8-440c1ede54d8",
    "name": "IncrementIntensityLevelConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "intensityLevel": {
      "value": 1
    },
    "previousState": {
      "intensityLevel": {
        "value": 2
      }
    }
  }
}
```

### See also

* [`DecrementIntensityLevelConfirmation`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#DecrementIntensityLevelConfirmation)
* [`DecrementIntensityLevelRequest`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#DecrementIntensityLevelRequest)
* [`IncrementIntensityLevelConfirmation`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#IncrementIntensityLevelConfirmation)
* [`IncrementIntensityLevelRequest`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#IncrementIntensityLevelRequest)

## ModeInfoObject {#ModeInfoObject}
운전 모드(operation mode) 정보를 담고 있는 객체입니다. 변경할 우전 모드의 이름이나 변경 전후의 운전 모드를 나타낼 때 사용되며 문자열로 표현됩니다.

### Object fields
| 필드 이름       | 자료형    | 필드 설명                     | 필수/포함 여부 |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | string  | [운전 모드](#OperationModes)(Operation mode)    | 필수/항상     |

### Operation modes {#OperationModes}

<table>
  <thead>
    <tr>
      <th style="width:30%">기기 타입</th><th style="width:70%">운전 모드 목록 및 설명</th>
    </tr>
  </thead>
  <tdoby>
    <tr>
      <td><code>"AIRCONDITIONER"</code></td>
      <td>
        <ul>
          <li><code>"auto"</code>: 자동 모드. 주로 에어컨 기기에서 사용되는 모드입니다.</li>
          <li><code>"cool"</code>: 냉방 모드. 주로 에어컨 기기에서 사용되는 모드입니다.</li>
          <li><code>"dehumidify"</code>: 제습 모드. 주로 에어컨이나 제습기와 같은 기기에서 사용되는 모드입니다.</li>
          <li><code>"fan"</code>: 송풍 모드. 주로 에어컨 기기에서 사용되는 모드입니다.</li>
          <li><code>"heat"</code>: 난방 모드. 주로 에어컨 기기에서 사용되는 모드입니다.</li>
          <li><code>"powercool"</code>: 파워 냉방 모드. 주로 에어컨 기기에서 사용되는 모드입니다.</li>
          <li><code>"powersaving"</code>: 절전 모드</li>
          <li><code>"sleep"</code>: 취침 모드. 주로 스마트 허브와 같은 기기에서 사용되는 모드입니다.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td><code>"AIRPURIFIER"</code></td>
      <td>
        <ul>
          <li><code>"auto"</code>: 자동 모드</li>
          <li><code>"autohumidify"</code>: 자동 가습 모드</li>
          <li><code>"infant"</code>: 유아 모드</li>
          <li><code>"roomcare"</code>: 룸케어(room care) 모드</li>
          <li><code>"yellowsand"</code>: 황사 모드</li>
          <li><code>"sleep"</code>: 취침 모드</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td><code>"FAN"</code></td>
      <td>
        <ul>
          <li><code>"auto"</code>: 자동 모드</li>
          <li><code>"baby"</code>: 아기 수면용 모드</li>
          <li><code>"sleep"</code>: 취침 모드</li>
      </td>
    </tr>
    <tr>
      <td><code>"HOMECAM"</code></td>
      <td>
        <ul>
          <li><code>"privacy"</code>: 사생활 보호 모드</li>
          <li><code>"sensing"</code>: 감지 모드</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td><code>"HUMIDIFIER"</code></td>
      <td>
        <ul>
          <li><code>"light"</code>: 조명 모드</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td><code>"LIGHT"</code></td>
      <td>
        <ul>
          <li><code>"concentration"</code>: 집중 모드</li>
          <li><code>"movie"</code>: 영상 모드</li>
          <li><code>"music"</code>: 음악 모드</li>
          <li><code>"reading"</code>: 독서 모드</li>
          <li><code>"rest"</code>: 휴식 모드</li>
          <li><code>"sleep"</code>: 취침 모드</li>
          <li><code>"vitality"</code>: 활력 모드</li>
          <li><code>"wakeup"</code>: 기상 모드</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td><code>"MOTIONSENSOR"</code></td>
      <td>
        <ul>
          <li><code>"siren"</code>: 사이렌 모드</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td><code>"PURIFIER"</code></td>
      <td>
        <ul>
          <li><code>"coldwater"</code>: 냉수 모드</li>
          <li><code>"general"</code>: 일반 모드</li>
          <li><code>"hotwater"</code>: 온수 모드</li>
          <li><code>"smartchecking"</code>: 스마트 점검 모드</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td><code>"REFRIGERATOR"</code></td>
      <td>
        <ul>
          <li><code>"filter"</code>: 제균 탈취 모드</li>
          <li><code>"freeze"</code>: 특급 냉동 모드</li>
          <li><code>"powersaving"</code>: 절전 모드</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td><code>"RICECOOKER"</code></td>
      <td>
        <ul>
          <li><code>"general"</code>: 일반 모드</li>
          <li><code>"keepwarm"</code>: 보온 모드</li>
          <li><code>"powersaving"</code>: 절전 모드</li>
          <li><code>"reheating"</code>: 재가열 모드</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td><code>"SMARTHUB"</code></td>
      <td>
        <ul>
          <li><code>"away"</code>: 외출 모드</li>
          <li><code>"hotwater"</code>: 온수 모드</li>
          <li><code>"indoor"</code>: 실내 모드</li>
          <li><code>"sleep"</code>: 취침 모드</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td><code>"THERMOSTAT"</code></td>
      <td>
        <ul>
          <li><code>"away"</code>: 외출 모드</li>
          <li><code>"hotwater"</code>: 온수 모드</li>
          <li><code>"indoor"</code>: 실내 모드</li>
          <li><code>"sleep"</code>: 취침 모드</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td><code>"VENTILATOR"</code></td>
      <td>
        <ul>
          <li><code>"auto"</code>: 자동 모드</li>
          <li><code>"dehumidify"</code>: 제습 모드</li>
          <li><code>"dry"</code>: 건조 모드</li>
          <li><code>"ventilating"</code>: 환기 모드</li>
          <li><code>"warmwind"</code>: 온풍 모드</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td><code>"WATERBOILER"</code></td>
      <td>
        <ul>
          <li><code>"hotwater"</code>: 급탕 모드</li>
          <li><code>"reheating"</code>: 재가열 모드</li>
        </ul>
      </td>
    </tr>
  </tdoby>
</table>

<div class="tip">
<p><strong>Tip!</strong></p>
<p>제조사나 제품에 따라 위에서 언급한 모드가 없거나 지원하는 방식이 다를 수 있습니다. 이 경우 기기가 가지고 있는 유사한 기능이나 운전 모드를 제공할 것을 권장합니다.</p>
</div>

### Object Example

```json
// 예제 1: SetModeRequest 메시지에서 사용된 예 - 온도 조절기
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "SetModeRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
        "applianceId": "device-006"
    },
    "mode": {
        "value": "hotwater"
    }
  }
}

// 예제 2: SetModeRequest 메시지에서 사용된 예 - 스마트 허브
{
  "header": {
    "messageId": "b4151a0d-1ec5-4ed0-a39a-1538c356b93b",
    "name": "SetModeRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
        "applianceId": "device-011"
    },
    "mode": {
        "value": "indoor"
    }
  }
}

// 예제 3: SetModeConfirmation 메시지에서 사용된 예
{
  "header": {
    "messageId": "b7434bd2-c397-461d-b08d-a4a427455c8f",
    "name": "SetModeConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "mode": {
      "value": "sleep"
    }
  }
}
```

### See also

* [`ReleaseModeConfirmation`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetReleaseModeConfirmation)
* [`ReleaseModeRequest`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetReleaseModeRequest)
* [`SetModeConfirmation`](/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md#SetModeConfirmation)
* [`SetModeRequest`](/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md#SetModeRequest)

## HumidityInfoObject {#HumidityInfoObject}
습도 정보를 담고 있는 객체입니다. 기기가 측정한 습도 상태를 나타낼 때 사용되며 문자열로 표현됩니다.

### Object fields
| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | number  | 습도(%)                      | 필수     |

### Object Example

```json
// 예제: GetHumidityResponse 메시지에서 사용된 예
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetHumidityResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "fineDust": {
        "value": 40
    }
  }
}
```

### See also
* [`GetHumidityResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetHumidityResponse)

## PercentageInfoObject {#PercentageInfoObject}

백분율(percentage) 정보를 담고 있는 객체입니다.

### Object fields

| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | number  | 백분율 값. 기기에 따라 실수나 정수 형태를 가지며, 단위는 퍼센트(%)입니다. | 필수      |

### Object Example

```json
// 예제 1: GetBodyFatResponse 메시지에서 사용된 예
{
  "header": {
    "messageId": "8c5da980-9e04-479d-afb8-5213c4dfac2d",
    "name": "GetBodyFatResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "bodyFatPercentage": {
      "value": 24.0
    },
    "applianceResponseTimestamp": "2019-08-19T18:31:00+09:00"
  }
}

// 예제 2: GetRightPostureRatioResponse 메시지에서 사용된 예
{
  "header": {
    "messageId": "b502dd42-b698-4d3b-9ddb-bbdda70f254f",
    "name": "GetRightPostureRatioResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "rightPostureRatio": {
      "value": 80
    },
    "applianceResponseTimestamp": "2017-11-23T20:30:19+09:00"
  }
}
```

### See also
* [`GetBodyFatResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetBodyFatResponse)
* [`GetRightPostureRatioResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetRightPostureRatioResponse)

## PeriodInfoObject {#PeriodInfoObject}

사용량, 예상 요금과 같은 측정 데이터를 조회할 때 조회 기간이 되는 정보를 담고 있는 객체입니다. 특정 기간 동안 정보의 누적된 통계 데이터나 변화 추이와 같은 것을 사용자가 요구할 때 `period`와 같은 이름의 필드를 통해 정보가 전달됩니다. Extension은 사용자가 지정한 기간에 맞춰 정보를 수집 및 계산하여 결과를 전달해야 합니다.

### Object fields

| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|---------------|---------|-----------------------------|:-------------:|
| `end`         | string  | 기간의 종료 시점(`"YYYY-MM-DDThh:mm:ss±hh:mm"`, <a href="https://en.wikipedia.org/wiki/ISO_8601#Combined_date_and_time_representations" target="_blank">ISO 8601 Combined date and time representations</a> )    | 항상      |
| `start`       | string  | 기간의 시작 시점(`"YYYY-MM-DDThh:mm:ss±hh:mm"`, <a href="https://en.wikipedia.org/wiki/ISO_8601#Combined_date_and_time_representations" target="_blank">ISO 8601 Combined date and time representations</a> )    | 항상      |

### Remarks
"오늘", "이번 주", "이번 달"와 같은 사용자의 표현이 있는데, 이런 표현은 다음과 같은 범위로 시작 시점과 종료 시점이 지정됩니다.

* "오늘": 시작 시점은 현재 날짜의 0 시이고 종료 시점은 현재 날짜의 23 시 59 분 59 초입니다.
* "이번 주": 시작 시점은 현재 날짜가 속한 주의 {{ book.ServiceEnv.FirstDayOfWeekInCLOVAHome }} 0 시이고, 종료 시점은 현재 날짜가 속한 주의 {{ book.ServiceEnv.LastDayOfWeekInCLOVAHome }} 23 시 59 분 59 초입니다.
* "이번 달": 시작 시점은 현재 날짜가 속한 달의 1 일 0 시, 종료 시점은 현재 날짜가 속한 달의 말일 23 시 59 분 59 초입니다.

위와 같은 특수 표현의 기간 종료 시점(`end`)은 요청을 처리하는 시점 기준으로 볼 때 아직 도래하지 않는 미래의 시점일 수 있으며, 상황에 따라 처리 시점을 종료 시점으로 생각하고 데이터를 처리해야 합니다.

"내일", "다음 주", "다음 달"과 같이 시작 시점(`start`)과 종료 시점(`end`)이 모두 미래 시점일 수도 있으며, 이는 예상되는 정보를 사용자가 요구할 때 지정될 수 있습니다.

* "내일": 시작 시점은 현재 날짜 기준 내일 0 시이고 종료 시점은 현재 날짜 기준 내일 23 시 59 분 59 초입니다.
* "다음 주": 시작 시점은 현재 날짜 기준 다음 주의 {{ book.ServiceEnv.FirstDayOfWeekInCLOVAHome }} 0 시이고, 종료 시점은 현재 날짜 기준 다음 주의 {{ book.ServiceEnv.LastDayOfWeekInCLOVAHome }} 23 시 59 분 59 초입니다.
* "다음 달": 시작 시점은 현재 날짜 기준 다음 달의 1 일 0 시, 종료 시점은 현재 날짜 기준 다음 달의 말일 23 시 59 분 59 초입니다.

### Object Example

```json
// 예제 1: GetUsageTimeRequest 메시지에서 사용된 예
{
  "header": {
    "messageId": "59a3f5bc-4c38-4d4c-9b71-3a037bf9f9b0",
    "name": "GetUsageTimeRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-028"
    },
    "period": {
      "start": "2018-03-28T00:10:00+09:00",
      "end": "2018-03-28T23:59:59+09:00"
    }
  }
}
```

### See also
* [`GetAsleepDurationRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetAsleepDurationRequest)
* [`GetAwakeDurationRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetAwakeDurationRequest)
* [`GetConsumptionRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetConsumptionRequest)
* [`GetCurrentBillRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetCurrentBillRequest)
* [`GetCurrentSittingStateResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetCurrentSittingStateResponse)
* [`GetDeviceStateRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetDeviceStateRequest)
* [`GetEstimateBillRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetEstimateBillRequest)
* [`GetRightPostureRatioRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetRightPostureRatioRequest)
* [`GetSleepScoreRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetSleepScoreRequest)
* [`GetSleepStartTimeRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetSleepStartTimeRequest)
* [`GetUsageTimeRequest`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetUsageTimeRequest)

## PhaseInfoObject {#PhaseInfoObject}

기기 동작의 단계 정보를 담고 있는 객체입니다. 현재 동작 단계를 나타내거나 이전 동작 단계가 무엇이었는지 나타낼 때 사용됩니다.

### Object fields

| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | string  | 동작 단계를 설명하는 문자열        | 필수      |

### Object Example

```json
// 예제: GetPhaseResponse 메시지에서 사용된 예
{
  "header": {
    "messageId": "b502dd42-b698-4d3b-9ddb-bbdda70f254f",
    "name": "GetPhaseResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "phase": {
        "value": "탈수",
    },
    "applianceResponseTimestamp": "2017-11-23T20:30:19+09:00"
  }
}
```

### See also
* [`GetPhaseResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetPhaseResponse)
* [`StopConfirmation`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetStopConfirmation)

## PowerStateInfoObject {#PowerStateInfoObject}

기기의 전원 상태 정보를 담고 있는 객체입니다.

### Object fields

| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | string  | 전원 상태 정보를 나타내는 문자열. 기기에 따라 `"켜짐"`, `"꺼짐"`, `"충전 중"`, `"전력 부족"`과 같은 다양한 문자열을 가질 수 있습니다.        | 필수      |

### Object Example

```json
// 예제: GetPowerStateResponse 메시지에서 사용된 예
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
* [`GetPowerStateResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetPowerStateResponse)

## ProgressiveTaxBracketInfoObject {#ProgressiveTaxBracketInfoObject}
누진세 단계 정보를 담고 있는 객체입니다.

### Object fields
| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | number  | 누진세 단계                    | 필수     |

### Object Example

```json
// 예제: GetProgressiveTaxBracketResponse 메시지에서 사용된 예
{
  "header": {
    "messageId": "b502dd42-b698-4d3b-9ddb-bbdda70f254f",
    "name": "GetProgressiveTaxBracketResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "progressiveTaxBracket": {
      "value": 1
    },
    "applianceResponseTimestamp": "2017-11-23T20:30:19+09:00"
  }
}
```

### See also
* [`GetProgressiveTaxBracketResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetProgressiveTaxBracketResponse)

## ScoreInfoObject {#ScoreInfoObject}
체성분 측정기, 헬스 케어 종류의 기기가 평가한 사용자의 건강 점수, 수면 점수와 것에 대한 정보를 담고 있는 객체입니다. 기간에 대한 결과를 나타낼 때는 평균값을 의미합니다.

### Object fields
| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | number  | 기기가 측정한 점수. 기기에 따라 실수나 정수 형태를 가집니다.   | 필수     |

### Object Example

```json
// 예제 1: GetHealthScoreResponse 메시지에서 사용된 예
{
  "header": {
    "messageId": "f3c50588-9238-4cd0-9368-cade722b6d9a",
    "name": "GetHealthScoreResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "healthScore": {
      "value": 60.5
    },
    "applianceResponseTimestamp": "2019-08-09T20:30:44+09:00"
  }
}

// 예제 2: GetSleepScoreResponse 메시지에서 사용된 예
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetSleepScoreResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "sleepScore": {
      "value": 80
    },
    "applianceResponseTimestamp": "2018-03-29T14:32:13+09:00"
  }
}
```

### See also
* [`GetHealthScoreResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetHealthScoreResponse)
* [`GetSleepScoreResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetSleepScoreResponse)

## SittingStateInfoObject {#SittingStateInfoObject}
스마트 의자와 같은 기기에 대한 사용자의 착성 정보가 담긴 객체입니다.

### Object fields
| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | boolean | 착석 여부<ul><li><code>true</code>: 착석 중인 상태</li><li><code>false</code>: 착석 중이지 않은 상태</li></ul>       | 필수    |

### Object Example

```json
// 예제: GetCurrentSittingStateResponse 메시지에서 사용된 예
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetCurrentSittingStateResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "sittingState": {
      "value": true
    },
    "recentlySittingPeriod": {
      "start": "2018-03-28T00:10:00+09:00",
      "end": "2018-03-28T23:59:59+09:00"
    },
    "applianceResponseTimestamp": "2018-03-29T14:32:13+09:00"
  }
}
```

### See also
* [`GetCurrentSittingStateResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetCurrentSittingStateResponse)

## SpeedInfoObject {#SpeedInfoObject}
속도 정보를 담고 있는 객체입니다. 변경할 속도의 크기나 변경 전후의 희망 속도를 나타낼 때 사용되며 정수로 표현됩니다.

### Object fields
| 필드 이름       | 자료형    | 필드 설명                     | 필수/포함 여부 |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | number  | 속도 값                       | 필수/항상     |

### Object Example

```json
// 예제 1: IncrementFanSpeedRequest 메시지에서 사용된 예
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "IncrementFanSpeedRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-004"
    },
    "deltaFanSpeed": {
      "value": 1
    }
  }
}

// 예제 2: IncrementFanSpeedConfirmation 메시지에서 사용된 예
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "IncrementFanSpeedConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "targetFanSpeed": {
      "value": 3
    },
    "previousState": {
      "targetFanSpeed": {
        "value": 2
      }
    }
  }
}
```

### See also

* [`DecrementFanSpeedConfirmation`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#DecrementFanSpeedConfirmation)
* [`DecrementFanSpeedRequest`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#DecrementFanSpeedRequest)
* [`IncrementFanSpeedConfirmation`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#IncrementFanSpeedConfirmation)
* [`IncrementFanSpeedRequest`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#IncrementFanSpeedRequest)
* [`SetFanSpeedConfirmation`](/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md#SetFanSpeedConfirmation)
* [`SetFanSpeedRequest`](/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md#SetFanSpeedRequest)

## TemperatureInfoObject {#TemperatureInfoObject}
온도 정보를 담고 있는 객체입니다. 변경할 온도의 크기, 변경 전후의 희망 온도나 현재 설정된 희망 온도를 나타낼 때 사용되며 소수점 첫째 자리 숫자로 표현됩니다.

### Object fields
| 필드 이름       | 자료형    | 필드 설명                     | 필수/포함 여부 |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | number  | 온도 값                       | 필수/항상     |

### Object Example

```json
// 예제 1: IncrementTargetTemperatureRequest 메시지에서 사용된 예
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "IncrementTargetTemperatureRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-001"
    },
    "deltaTemperature": {
      "value": 1
    }
  }
}

// 예제 2: IncrementTargetTemperatureConfirmation 메시지에서 사용된 예
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "IncrementTargetTemperatureConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "targetTemperature": {
      "value": 25
    },
    "previousState": {
      "targetTemperature": {
        "value": 21
      }
    }
  }
}
```

### See also

* [`DecrementTargetTemperatureConfirmation`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#DecrementTargetTemperatureConfirmation)
* [`DecrementTargetTemperatureRequest`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#DecrementTargetTemperatureRequest)
* [`GetCurrentTemperatureResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetCurrentTemperatureResponse)
* [`GetTargetTemperatureResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetTargetTemperatureResponse)
* [`IncrementTargetTemperatureConfirmation`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#IncrementTargetTemperatureConfirmation)
* [`IncrementTargetTemperatureRequest`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#IncrementTargetTemperatureRequest)
* [`SetTargetTemperatureConfirmation`](/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md#SetTargetTemperatureConfirmation)
* [`SetTargetTemperatureRequest`](/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md#SetTargetTemperatureRequest)

## TVChannelNameInfoObject {#TVChannelNameInfoObject}
TV 채널의 이름 정보를 담고 있는 객체입니다. 변경할 TV 채널이나 변경 전후의 TV 채널의 이름 정보를 나타낼 때 사용되며 문자열로 표현됩니다.

### Object fields
| 필드 이름       | 자료형    | 필드 설명                     | 필수/포함 여부 |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | string  | TV 채널 이름                  | 필수/항상     |

### Object Example

```json
// 예제 1: SetChannelByNameRequest 메시지에서 사용된 예
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "SetChannelByNameRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-006"
    },
    "channelName": {
      "value": "sbs"
    }
  }
}

// 예제 2: SetChannelByNameConfirmation 메시지에서 사용된 예
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "SetChannelByNameConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
  	"channelName": {
  		"value": "sbs"
  	}
  }
}
```

### See also

* [`SetChannelByNameConfirmation`](/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md#SetChannelByNameConfirmation)
* [`SetChannelByNameRequest`](/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md#SetChannelByNameRequest)

## TVChannelInfoObject {#TVChannelInfoObject}
TV 채널의 번호 정보를 담고 있는 객체입니다. 변경할 TV 채널이나 변경 전후의 TV 채널의 번호를 나타낼 때 사용되며 숫자로 표현됩니다.

### Object fields
| 필드 이름       | 자료형    | 필드 설명                     | 필수/포함 여부 |
|---------------|---------|-----------------------------|:-------------:|
| `value`             | number  | TV 채널 번호                      | 필수/항상     |

### Object Example

```json
// 예제 1: SetChannelRequest 메시지에서 사용된 예
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "SetChannelRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
        "applianceId": "device-007"
    },
    "channel": {
      "value": 15
    },
    "subChannel": {
      "value": 1
    }
  }
}

// 예제 2: SetChannelConfirmation 메시지에서 사용된 예
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "SetChannelConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "channel": {
      "value": 15
    },
    "subChannel": {
      "value": 1
    }
  }
}
```

### See also

* [`DecrementChannelConfirmation`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#DecrementChannelConfirmation)
* [`DecrementChannelRequest`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#DecrementChannelRequest)
* [`IncrementChannelConfirmation`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#IncrementChannelConfirmation)
* [`IncrementChannelRequest`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#IncrementChannelRequest)
* [`SetChannelConfirmation`](/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md#SetChannelConfirmation)
* [`SetChannelRequest`](/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md#SetChannelRequest)

## UltraFineDustInfoObject {#UltraFineDustInfoObject}
초미세 먼지 정보를 담고 있는 객체입니다. 기기가 측정한 초미세 먼지 지수와 수준을 나타낼 때 사용됩니다.

### Object fields
| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | number  | 초미세 먼지 지수                | 선택    |
| `index`       | string  | 초미세 먼지 수준. 다음과 같은 값으로 제한되어 있습니다.<ul><li><code>"good"</code>: 좋음</li><li><code>"normal"</code>: 보통</li><li><code>"bad"</code>: 나쁨</li><li><code>"verybad"</code>: 매우 나쁨</li></ul> | 필수     |

### Object Example

```json
// 예제: GetUltraFineDustResponse 메시지에서 사용된 예
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetUltraFineDustResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "ultraFineDust": {
        "value": 44,
        "index": "good"
    }
  }
}
```

### See also
* [`GetUltraFineDustResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetUltraFineDustResponse)

## VolumeInfoObject {#VolumeInfoObject}
스피커의 볼륨 정보를 담고 있는 객체입니다. 변경할 볼륨의 크기나 변경 전후의 볼륨 정보를 나타낼 때 사용되며 정수로 표현됩니다.

### Object fields
| 필드 이름       | 자료형    | 필드 설명                     | 필수/포함 여부 |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | number  | 볼륨 값                       | 필수/항상     |

### Object Example

```json
// 예제 1: IncrementVolumeRequest 메시지에서 사용된 예
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "IncrementVolumeRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-005"
    },
    "deltaVolume": {
      "value": 10
    }
  }
}

// 예제 2: IncrementVolumeConfirmation 메시지에서 사용된 예
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "IncrementVolumeConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "targetVolume": {
      "value": 20
    },
    "previousState": {
      "targetVolume": {
        "value": 10
      }
    }
  }
}
```

### See also

* [`DecrementVolumeConfirmation`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#DecrementVolumeConfirmation)
* [`DecrementVolumeRequest`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#DecrementVolumeRequest)
* [`IncrementVolumeConfirmation`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#IncrementVolumeConfirmation)
* [`IncrementVolumeRequest`](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#IncrementVolumeRequest)

## WeightInfoObject {#WeightInfoObject}

체중과 같은 무게 정보를 담고 있는 객체입니다.

### Object fields
| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | number  | 무게. 실수 형태를 가지며, 단위는 킬로그램(Kg)입니다.    | 선택     |

### Object Example

```json
// 예제: GetWeightResponse 메시지에서 사용된 예
{
  "header": {
    "messageId": "d06b65c1-094b-4ca9-aee0-21431302f0d7",
    "name": "GetWeightResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "weight": {
      "value": 80.9
    },
    "applianceResponseTimestamp": "2019-08-09T20:30:44+09:00"
  }
}
```

### See also
* [`GetWeightResponse`](/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetWeightResponse)
