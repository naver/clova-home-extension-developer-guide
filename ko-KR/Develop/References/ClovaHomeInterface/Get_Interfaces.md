# 정보 조회 인터페이스

IoT 기기의 상태 정보나 IoT 기기가 측정한 정보를 확인하는 요청 및 응답을 수행할 때 사용되는 메시지 인터페이스입니다. 요청 메시지는 `XxxxRequest`, 응답 메시지는  `XxxxResponse`와 같은 이름을 가집니다.

| 메시지 이름         | 메시지 타입  | 메시지 설명                                   |
|------------------|-----------|---------------------------------------------|
| [`GetAirQualityRequest`](#GetAirQualityRequest)                               | Request  | 대상 기기가 측정한 공기질 정보를 CLOVA Home extension에 요청합니다. |
| [`GetAirQualityResponse`](#GetAirQualityResponse)                             | Response | [`GetAirQualityRequest`](#GetAirQualityRequest) 메시지에 대한 응답으로 대상 기기가 측정한 공기질 정보를 CEK에 전달합니다. |
| [`GetAsleepDurationRequest`](#GetAsleepDurationRequest)                       | Request  | 주로 수면 센서에서 측정된 정보를 확인할 때 사용되며, 대상 기기가 측정한 사용자의 수면 시간을 CLOVA Home extension에 요청합니다.  |
| [`GetAsleepDurationResponse`](#GetAsleepDurationResponse)                     | Response | [`GetAsleepDurationRequest`](#GetAsleepDurationRequest) 메시지에 대한 응답으로 대상 기기가 측정한 사용자의 수면 시간을 CEK에 전달합니다.  |
| [`GetAwakeDurationRequest`](#GetAwakeDurationRequest)                         | Request  | 주로 수면 센서에서 측정된 정보를 확인할 때 사용되며, 대상 기기가 측정한 사용자의 취침 후 비수면 시간, 즉 사용자가 취침을 시작한 순간부터 수면에 진입한 순간까지의 시간을 CLOVA Home extension에 요청합니다.  |
| [`GetAwakeDurationResponse`](#GetAwakeDurationResponse)                       | Response | [`GetAwakeDurationRequest`](#GetAwakeDurationRequest) 메시지에 대한 응답으로 대상 기기가 측정한 사용자의 취침 후 비수면 시간, 즉 사용자가 취침을 시작한 순간부터 수면에 진입한 순간까지의 시간을 CEK에 전달합니다.  |
| [`GetBMIRequest`](#GetBMIRequest)                             | Request  | 대상 기기로부터 측정된 신체질량지수(BMI, Body Mass Index)를 CLOVA Home extension에 요청합니다. |
| [`GetBMIResponse`](#GetBMIResponse)                           | Response | [`GetBMIRequest`](#GetBMIRequest) 메시지에 대한 응답으로 대상 기기가 측정한 신체질량지수(BMI, Body Mass Index)를 CEK에 전달합니다. |
| [`GetBatteryInfoRequest`](#GetBatteryInfoRequest)                             | Request  | 대상 기기의 배터리 정보를 CLOVA Home extension에 요청합니다. |
| [`GetBatteryInfoResponse`](#GetBatteryInfoResponse)                           | Response | [`GetBatteryInfoRequest`](#GetBatteryInfoRequest) 메시지에 대한 응답으로 대상 기기의 배터리 정보를 CEK에 전달합니다. |
| [`GetBodyFatRequest`](#GetBodyFatRequest)                      | Request  | 대상 기기로부터 측정된 체지방율을 CLOVA Home extension에 요청합니다. |
| [`GetBodyFatResponse`](#GetBodyFatResponse)                           | Response | [`GetBodyFatRequest`](#GetBodyFatRequest) 메시지에 대한 응답으로 대상 기기가 측정한 체지방율을 CEK에 전달합니다. |
| [`GetCleaningCycleRequest`](#GetCleaningCycleRequest)                         | Request  | 기기의 세척 주기를 확인할 때 사용되며, 대상 기기의 다음 세척 주기까지 남은 시간에 대한 정보를 CLOVA Home extension에 요청합니다.  |
| [`GetCleaningCycleResponse`](#GetCleaningCycleResponse)                       | Response | [`GetCleaningCycleRequest`](#GetCleaningCycleRequest) 메시지에 대한 응답으로 대상 기기의 다음 세척 주기까지 남은 시간을 CEK에 전달합니다.  |
| [`GetCloseTimeRequest`](#GetCloseTimeRequest)                                 | Request  | 주로 열림 감지 센서가 감지한 내용 중 감지 대상이 마지막으로 닫혔던 시점의 시간 정보를 CLOVA Home extension에 요청합니다. |
| [`GetCloseTimeResponse`](#GetCloseTimeResponse)                               | Response | [`GetCloseTimeRequest`](#GetCloseTimeRequest) 메시지에 대한 응답으로 대상 기기가 감지한 내용 중 감지 대상이 마지막으로 닫혔던 시점의 시간 정보를 CEK에 전달합니다.  |
| [`GetConsumptionRequest`](#GetConsumptionRequest)                             | Request  | 주로 스마트 플러그나 스마트 멀티탭과 같은 기기에서 현재까지 측정된 에너지 또는 자원 사용량을 확인할 때 사용되며, 대상 기기가 측정한 에너지 또는 자원 사용량 정보를 CLOVA Home extension에 요청합니다.  |
| [`GetConsumptionResponse`](#GetConsumptionResponse)                           | Response | [`GetConsumptionRequest`](#GetConsumptionRequest) 메시지에 대한 응답으로 대상 기기가 현재까지 측정한 에너지 또는 자원 사용량 정보를 CEK에 전달합니다.  |
| [`GetCurrentBillRequest`](#GetCurrentBillRequest)                             | Request  | 주로 스마트 플러그나 스마트 멀티탭과 같은 기기에서 측정된 현재까지의 사용량의 기반으로 요금을 확인할 때 사용되며, 대상 기기가 측정한 요금 정보를 CLOVA Home extension에 요청합니다.  |
| [`GetCurrentBillResponse`](#GetCurrentBillResponse)                           | Response | [`GetCurrentBillRequest`](#GetCurrentBillRequest) 메시지에 대한 응답으로 대상 기기가 현재까지 측정한 요금 정보를 CEK에 전달합니다.   |
| [`GetCurrentSittingStateRequest`](#GetCurrentSittingStateRequest)             | Request  | 스마트 의자와 같은 기기에서 사용자의 사용 상태를 확인할 때 사용되며, 대상 기기가 사용자 착석 여부를 감지한 정보와 최근 사용자가 사용한 시간 정보를 CLOVA Home extension에 요청합니다.  |
| [`GetCurrentSittingStateResponse`](#GetCurrentSittingStateResponse)           | Response | [`GetCurrentSittingStateRequest`](#GetCurrentSittingStateRequest) 메시지에 대한 응답으로 대상 기기가 사용자 착석 여부를 감지한 정보와 최근 사용자가 사용한 시간 정보를 CEK에 전달합니다.  |
| [`GetCurrentTemperatureRequest`](#GetCurrentTemperatureRequest)               | Request  | 대상 기기가 측정한 현재 온도 정보를 CLOVA Home extension에 요청합니다. |
| [`GetCurrentTemperatureResponse`](#GetCurrentTemperatureResponse)             | Response | [`GetCurrentTemperatureRequest`](#GetCurrentTemperatureRequest) 메시지에 대한 응답으로 대상 기기가 측정한 현재 온도 정보를 CEK에 전달합니다. |
| [`GetDetectedTimeRequest`](#GetDetectedTimeRequest)                       | Request  | 센서나 움직임을 인식하는 카메라가 있는 기기에서 센서나 카메라가 움직임을 감지한 횟수를 CLOVA Home extension에 요청합니다. |
| [`GetDetectedTimeResponse`](#GetDetectedTimeResponse)                      | Response | [`GetDetectedTimeRequest`](#GetDetectedTimeRequest) 메시지에 대한 응답으로 대상 기기가 측정한 사용자의 수면 시작 시간을 CEK에 전달합니다.  |
| [`GetDetectionCountRequest`](#GetDetectionCountRequest)                             | Request  | 센서나 움직임을 인식하는 카메라가 있는 기기에서 센서나 카메라가 움직임을 감지한 횟수를 CLOVA Home extension에 요청합니다.  |
| [`GetDetectionCountResponse`](#GetDetectionCountResponse)                           | Response | [`GetDetectionCountRequest`](#GetDetectionCountRequest) 메시지에 대한 응답으로 대상 기기가 제공하는 모든 상태 정보를 CEK에 전달합니다.  |
| [`GetDeviceStateRequest`](#GetDeviceStateRequest)                             | Request  | 대상 기기가 제공하는 모든 상태 정보를 확인할 때 사용됩니다.  |
| [`GetDeviceStateResponse`](#GetDeviceStateResponse)                           | Response | [`GetDeviceStateRequest`](#GetDeviceStateRequest) 메시지에 대한 응답으로 대상 기기가 제공하는 모든 상태 정보를 CEK에 전달합니다.  |
| [`GetEstimateBillRequest`](#GetEstimateBillRequest)                           | Request  | 주로 스마트 플러그나 스마트 멀티탭과 같은 기기에서 측정된 사용량의 기반으로 예상 요금을 확인할 때 사용되며, 대상 기기가 예측한 요금 정보를 CLOVA Home extension에 요청합니다.  |
| [`GetEstimateBillResponse`](#GetEstimateBillResponse)                         | Response | [`GetEstimateBillRequest`](#GetEstimateBillRequest) 메시지에 대한 응답으로 대상 기기가 예측한 요금 정보를 CEK에 전달합니다.  |
| [`GetEstimateConsumptionRequest`](#GetEstimateConsumptionRequest)             | Request  | 주로 스마트 플러그나 스마트 멀티탭과 같은 기기에서 예상되는 에너지 또는 자원 사용량을 확인할 때 사용되며, 대상 기기가 예측한 에너지 또는 자원 사용량 정보를 CLOVA Home extension에 요청합니다.  |
| [`GetEstimateConsumptionResponse`](#GetEstimateConsumptionResponse)           | Response | [`GetEstimateConsumptionRequest`](#GetEstimateConsumptionRequest) 메시지에 대한 응답으로 대상 기기가 현재까지 측정한 에너지 또는 자원 정보를 CEK에 전달합니다.  |
| [`GetExpendableStateRequest`](#GetExpendableStateRequest)                     | Request  | 기기의 필터나 소모품의 사용량이나 남은 수명을 확인할 때 사용되며, 대상 기기가 보유하고 있는 소모품의 사용량이나 수명 정보를 CLOVA extension에 요청합니다.  |
| [`GetExpendableStateResponse`](#GetExpendableStateResponse)                   | Response | [`GetExpendableStateRequest`](#GetExpendableStateRequest) 메시지에 대한 응답으로 대상 기기가 제공하는 모든 소모품의 사용량이나 수명 정보를 CEK에 전달합니다. |
| [`GetFineDustRequest`](#GetFineDustRequest)                                   | Request  | 대상 기기가 측정한 미세 먼지(PM10) 정보를 CLOVA Home extension에 요청합니다. |
| [`GetFineDustResponse`](#GetFineDustResponse)                                 | Response | [`GetFineDustRequest`](#GetFineDustRequest) 메시지에 대한 응답으로 대상 기기가 측정한 미세 먼지(PM10) 정보를 CEK에 전달합니다. |
| [`GetHealthScoreRequest`](#GetHealthScoreRequest)                             | Request  | 체성분 측정기나 헬스 케어 종류의 기기에서 사용자 건강과 관련된 점수 정보를 확인할 때 사용되며, 대상 기기가 평가한 사용자의 건강 점수를 CLOVA Home extension에 요청합니다. |
| [`GetHealthScoreResponse`](#GetHealthScoreResponse)                           | Response | [`GetHealthScoreRequest`](#GetHealthScoreRequest) 메시지에 대한 응답으로 대상 기기가 평가한 사용자의 건강 점수를 CEK에 전달합니다. |
| [`GetHumidityRequest`](#GetHumidityRequest)                                   | Request  | 대상 기기가 측정한 습도 정보를 CLOVA Home extension에 요청합니다. |
| [`GetHumidityResponse`](#GetHumidityResponse)                                 | Response | [`GetHumidityRequest`](#GetHumidityRequest) 메시지에 대한 응답으로 대상 기기가 측정한 습도 정보를 CEK에 전달합니다. |
| [`GetKeepWarmTimeRequest`](#GetKeepWarmTimeRequest)                           | Request  | 밥솥과 같은 기기에서 음식의 보온에 사용된 시간을 확인할 때 사용되며, 대상 기기가 보온 모드를 유지한 시간 정보를 CLOVA Home extension에 요청합니다.  |
| [`GetKeepWarmTimeResponse`](#GetKeepWarmTimeResponse)                         | Response | [`GetKeepWarmTimeRequest`](#GetKeepWarmTimeRequest) 메시지에 대한 응답으로 대상 기기가 보온 모드를 유지한 시간 정보를 CEK에 전달합니다.  |
| [`GetLockStateRequest`](#GetLockStateRequest)                                 | Request  | 주로 스마트 밸브와 같은 기기의 상태를 확인할 때 사용되며, 대상 기기가 가진 잠금 장치의 현재 잠금 상태 정보를 CLOVA Home extension에 요청합니다.  |
| [`GetLockStateResponse`](#GetLockStateResponse)                               | Response | [`GetLockStateRequest`](#GetLockStateRequest) 메시지에 대한 응답으로 대상 기기가 가진 잠금 장치의 현재 잠금 상태를 CEK에 전달합니다.  |
| [`GetMuscleRequest`](#GetMuscleRequest)                                 | Request  | 체성분 측정기나 헬스 케어 종류의 기기로부터 측정된 근육량을 CLOVA Home extension에 요청합니다.  |
| [`GetMuscleResponse`](#GetMuscleResponse)                               | Response | [`GetMuscleRequest`](#GetMuscleRequest) 메시지에 대한 응답으로 대상 기기가 측정한 근육량을 백분율 형태로 CEK에 전달합니다.  |
| [`GetNoticeRequest`](#GetNoticeRequest)                                  | Request  | 아파트나 오피스텔 관리 사무소의 공지 사항을 확인할 때 사용되며 대상 기기의 현재 상태 정보를 Clova Home extension에게 요청합니다. |
| [`GetNoticeResponse`](#GetNoticeResponse)                                | Response | [`GetNoticeRequest`](#GetNoticeRequest) 메시지에 대한 응답으로 아파트나 오피스텔 관리 사무소의 공지 사항을 CEK에게 전달합니다. |
| [`GetOpenStateRequest`](#GetOpenStateRequest)                                 | Request  | 주로 열림 감지 센서가 감지한 내용 중 감지 대상의 현재 상태 정보(열림 또는 닫힘)를 CLOVA Home extension에 요청합니다.  |
| [`GetOpenStateResponse`](#GetOpenStateResponse)                               | Response | [`GetOpenStateRequest`](#GetOpenStateRequest) 메시지에 대한 응답으로 주로 감지 대상의 현재 상태 정보(열림 또는 닫힘)를 CEK에 전달합니다.  |
| [`GetOpenTimeRequest`](#GetOpenTimeRequest)                                   | Request  | 주로 열림 감지 센서가 감지한 내용 중 감지 대상이 마지막으로 열렸던 시점의 시간 정보를 CLOVA Home extension에 요청합니다.   |
| [`GetOpenTimeResponse`](#GetOpenTimeResponse)                                 | Response | [`GetOpenTimeRequest`](#GetOpenTimeRequest) 메시지에 대한 응답으로 대상 기기가 감지한 내용 중 감지 대상이 마지막으로 열렸던 시점의 시간 정보를 CEK에 전달합니다.  |
| [`GetPackageRequest`](#GetPackageRequest)                                     | Request | 아파트나 오피스텔 택배함을 확인할 때 사용되며 대상 기기의 현재 상태 정보를 Clova Home extension에게 요청합니다. |
| [`GetPackageResponse`](#GetPackageResponse)                                   | Response | [`GetPackageRequest`](#GetPackageRequest) 메시지에 대한 응답으로 택배함 정보를 CEK에게 전달합니다.  |
| [`GetPhaseRequest`](#GetPhaseRequest)                                         | Request  | 주로 밥솥이나 세탁기와 같이 동작 단계가 있는 기기에서 현재 동작 단계 정보를 확인할 때 사용되며, 대상 기기의 현재 동작 단계 정보를 CLOVA Home extension에 요청합니다.  |
| [`GetPhaseResponse`](#GetPhaseResponse)                                       | Response | [`GetPhaseRequest`](#GetPhaseRequest) 메시지에 대한 응답으로 대상 기기의 현재 동작 단계 정보를 CEK에 전달합니다.  |
| [`GetPowerStateRequest`](#GetPowerStateRequest)                               | Request  | 기기 자체의 전원 상태를 확인할 수 있는 기기에서 현재 기기의 전원 상태를 CLOVA Home extension에 요청합니다.  |
| [`GetPowerStateResponse`](#GetPowerStateResponse)                                | Response | [`GetPowerStateRequest`](#GetPowerStateRequest) 메시지에 대한 응답으로 대상 기기의 현재 전원 상태 정보를 CEK에 전달합니다.  |
| [`GetProgressiveTaxBracketRequest`](#GetProgressiveTaxBracketRequest)         | Request  | 주로 전기 계량기나 스마트 플러그와 같은 기기에서 누진세 단계를 확인할 때 사용되며, 대상 기기가 판단한 누진세 단계 정보를 CLOVA Home extension에 요청합니다.  |
| [`GetProgressiveTaxBracketResponse`](#GetProgressiveTaxBracketResponse)         | Response | [`GetProgressiveTaxBracketRequest`](#GetProgressiveTaxBracketRequest) 메시지에 대한 응답으로 대상 기기가 판단한 누진세 단계 정보를 CEK에 전달합니다. |
| [`GetRemainingTimeRequest`](#GetRemainingTimeRequest)                         | Request  | 주로 밥솥이나 세탁기와 같은 기기에서 동작 종료까지 남은 시간을 확인할 때 사용되며, 대상 기기의 동작 종료까지 남은 시간에 대한 정보를 CLOVA Home extension에 요청합니다.  |
| [`GetRemainingTimeResponse`](#GetRemainingTimeResponse)                       | Response | [`GetRemainingTimeRequest`](#GetRemainingTimeRequest) 메시지에 대한 응답으로 대상 기기가 동작 종료하기까지 남은 시간을 CEK에 전달합니다. |
| [`GetRightPostureRatioRequest`](#GetRightPostureRatioRequest)                 | Request  | 사용자가 바른 자세로 대상 기기를 사용한 비율이 얼마인지 확인할 때 사용하며, 사용자가 대상 기기를 사용할 때 특정 기간이나 현재까지 바른 자세를 유지한 비율 정보를 CLOVA Home extension에 요청합니다.  |
| [`GetRightPostureRatioResponse`](#GetRightPostureRatioResponse)               | Response | [`GetRightPostureRatioRequest`](#GetRightPostureRatioRequest) 메시지에 대한 응답으로 사용자가 대상 기기를 바른 자세로 사용한 비율 정보를 CEK에 전달합니다.  |
| [`GetSleepScoreRequest`](#GetSleepScoreRequest)                               | Request  | 수면 센서와 같은 기기에서 사용자 수면 점수 정보를 확인할 때 사용되며, 대상 기기가 평가한 사용자의 수면 점수를 CLOVA Home extension에 요청합니다.  |
| [`GetSleepScoreResponse`](#GetSleepScoreResponse)                             | Response | [`GetSleepScoreRequest`](#GetSleepScoreRequest) 메시지에 대한 응답으로 대상 기기가 평가한 사용자의 수면 점수를 CEK에 전달합니다.  |
| [`GetSleepStartTimeRequest`](#GetSleepStartTimeRequest)                       | Request  | 수면 센서와 같은 기기에서 사용자 수면 점수 정보를 확인할 때 사용되며, 대상 기기가 측정한 사용자의 수면 시작 시간을 CLOVA Home extension에 요청합니다.  |
| [`GetSleepStartTimeResponse`](#GetSleepStartTimeRequest)                      | Response | [`GetSleepStartTimeRequest`](#GetSleepStartTimeRequest) 메시지에 대한 응답으로 대상 기기가 측정한 사용자의 수면 시작 시간을 CEK에 전달합니다.  |
| [`GetTargetTemperatureRequest`](#GetTargetTemperatureRequest)                 | Request  | 대상 기기가 설정한 희망 온도 정보를 CLOVA Home extension에 요청합니다. |
| [`GetTargetTemperatureResponse`](#GetTargetTemperatureResponse)               | Response | [`GetTargetTemperatureRequest`](#GetTargetTemperatureRequest) 메시지에 대한 응답으로 대상 기기가 설정한 희망 온도 정보를 CEK에 전달합니다. |
| [`GetUltraFineDustRequest`](#GetUltraFineDustRequest)                         | Request  | 대상 기기가 측정한 초미세 먼지(PM2.5) 정보를 CLOVA Home extension에 요청합니다. |
| [`GetUltraFineDustResponse`](#GetUltraFineDustResponse)                       | Response | [`GetUltraFineDustRequest`](#GetUltraFineDustRequest) 메시지에 대한 응답으로 대상 기기가 측정한 초미세 먼지(PM2.5) 정보를 CEK에 전달합니다. |
| [`GetUsageTimeRequest`](#GetUsageTimeRequest)                                 | Request | 사용자가 대상 기기를 얼마나 사용했는지 확인할 때 사용하며, 대상 기기가 특정 기간이나 현재까지 누적 사용된 시간 정보를 CLOVA Home extension에 요청합니다.  |
| [`GetUsageTimeResponse`](#GetUsageTimeResponse)                               | Response | [`GetUsageTimeRequest`](#GetUsageTimeRequest) 메시지에 대한 응답으로 대상 기기가 사용된 시간 정보를 CEK에 전달합니다.  |
| [`GetVehicleLocationRequest`](#GetVehicleLocationRequest)                     | Request | 아파트나 오피스텔 주차장에서 등록된 차량의 주차 위치를 확인할 때 사용되며, 대상 차량의 주차 정보를 Clova Home extension에게 요청합니다.  |
| [`GetVehicleLocationResponse`](#GetVehicleLocationResponse)                   | Response | [`GetVehicleLocationRequest`](#GetVehicleLocationRequest) 메시지에 대한 응답으로 대상 차량의 주차 정보를 CEK에게 전달합니다. |
| [`GetWeightRequest`](#GetWeightRequest)                                 | Request | 체중계 또는 저울과 같은 무게 측정 기기로부터 측정된 체중이나 무게를 CLOVA Home extension에 요청합니다.  |
| [`GetWeightResponse`](#GetWeightResponse)                               | Response | [`GetWeightRequest`](#GetWeightRequest) 메시지에 대한 응답으로 대상 기기가 측정한 체중이나 무게를 CEK에 전달합니다.  |
| [`HealthCheckRequest`](#HealthCheckRequest)                                   | Request  | 지정한 기기의 상태를 파악할 때 사용되며, 대상 기기의 상태 정보를 CLOVA Home extension에 요청합니다. |
| [`HealthCheckResponse`](#HealthCheckResponse)                                 | Response | [`HealthCheckRequest`](#HealthCheckRequest) 메시지에 대한 응답으로 지정한 기기의 상태 정보를 CEK에 전달합니다. |

{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetAirQuality.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetAsleepDuration.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetAwakeDuration.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetBMI.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetBatteryInfo.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetBodyFat.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetCleaningCycle.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetCloseTime.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetConsumption.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetCurrentBill.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetCurrentSittingState.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetCurrentTemperature.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetDetectedTime.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetDetectionCount.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetDeviceState.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetEstimateBill.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetEstimateConsumption.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetExpendableState.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetFineDust.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetHealthScore.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetHumidity.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetKeepWarmTime.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetLockState.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetMuscle.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetNotice.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetOpenState.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetOpenTime.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetPackage.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetPhase.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetPowerState.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetProgressiveTaxBracket.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetRemainingTime.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetRightPostureRatio.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetSleepScore.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetSleepStartTime.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetTargetTemperature.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetUltraFineDust.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetUsageTime.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetVehicleLocation.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/GetWeight.md" %}
{% include "/Develop/References/ClovaHomeInterface/GetInterfaces/HealthCheck.md" %}
