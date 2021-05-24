# 문서 정보
이 문서는 CLOVA Home extension을 개발할 수 있도록 CEK 플랫폼에 대한 개발 가이드 및 API 레퍼런스 그리고 CLOVA developer console에 대한 가이드를 제공합니다. 대상 독자는 CEK를 사용하여 IoT 허브 서비스를 제공하려는 CLOVA Home extension 개발자입니다.

<div class="note">
  <p><strong>Note!</strong></p>
  <p>CLOVA는 개발이 계속 진행되고 있습니다. 따라서, 문서의 내용은 언제든지 변경될 수 있습니다.</p>
</div>

## 연락처
문서와 관련하여 궁금한 사항은 지정된 CLOVA 제휴 담당자나 <a href="{{ book.ServiceEnv.DeveloperCenterForumURI }}" target="_blank">{{ book.ServiceEnv.DeveloperCenterName }} 포럼</a>에 문의합니다.

## 문서 변경 이력

이 문서의 변경 이력은 다음과 같습니다.

<table>
  <thead>
    <tr>
      <th style="width:12%">배포 일자</th><th style="width:88%">이력 사항</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>2020-12-01</td>
      <td>
        <ul>
          <li><a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject">ApplianceInfoObject</a> 공유 객체에서 isReachable 필드가 폐기됨</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2020-11-10</td>
      <td>
        <ul>
          <li>Heater 타입 기기에 온도 설정(SetTargetTemperature) 동작 지원 추가함</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2020-09-23</td>
      <td>
        <ul>
          <li>아파트나 오피스텔의 스마트 홈 시스템을 지원하기 위해 다음과 같이 규격을 추가함.
            <ul>
              <li>기기 제어 인터페이스의 액션형 인터페이스에 엘리베이터 호출 동작(CallElevator)을 추가함</li>
              <li>정보 조회 인터페이스에 공지 조회(GetNotice), 택배 조회(GetPackage), 차량 주차 위치 조회(GetVehicleLocation) 동작을 추가함</li>
              <li><code>applyanceTypes</code> 필드에 관련 <code>BUILDING_</code>으로 시작하는 관련 기기 타입을 추가</li>
            </ul>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2020-06-24</td>
      <td>
        <ul>
          <li>Clova의 표기를 CLOVA로 수정</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2020-05-08</td>
      <td>
        <ul>
          <li>기기가 지원하는 동작에 필요한 값의 제약이 있을 경우 관련 정보를 알려주기 위해 <a href="Develop/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject">ApplianceInfoObject</a> 중 <a href="Develop/References/ClovaHomeInterface/Shared_Objects.md#additionalApplianceDetails">additionalApplianceDetails</a>에 세부 내용 추가함</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2020-01-29</td>
      <td>
        <ul>
          <li>적외선 리모컨과 같이 버튼 제약이 심한 기기 제어를 위해 <a href="/Develop/References/ClovaHomeInterface/Switching_Type_Interfaces.md">전환형 인터페이스</a>를 추가함</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2020-01-13</td>
      <td>
        <ul>
          <li><a href="/Develop/References/ClovaHomeInterface/Control_Interfaces.md">기기 제어 인터페이스</a>를 세분화하여 <a href="/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md">값 설정형 인터페이스</a>, <a href="/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md">값 증감형 인터페이스</a>, <a href="/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md">액션형 인터페이스</a>로 나눔</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2019-11-05</td>
      <td>
        <ul>
          <li>잘못 작성된 <a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md#UltraFineDustInfoObject">UltraFineDustInfoObject</a> index 필드 자료형을 string으로 수정함</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2019-09-30</td>
      <td>
        <ul>
          <li><a href="/DevConsole/Guides/Configure_Push_Settings.md">CLOVA Home extension 푸시 알림 설정하기</a>를 추가함</li>
          <li><a href="/Develop/References/Clova_Push_API.md">CLOVA Push API 레퍼런스</a>를 추가함</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2019-08-19</td>
      <td>
        <ul>
          <li>홈캠, 모션 센서, 헬스 케어 장비(체성분 측정기), 선풍기 기기 지원을 위해 <a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject">CLOVA Home extension API</a>가 업데이트됨
            <ul>
              <li>홈캠(HOMECAM) 기기 타입 추가 </li>
              <li>모션센터(MOTIONSENSOR)에 지원 동작 추가</li>
              <li>체중계(BODYWEIGHTSCALE) 기기타입에 지원 동작 추가</li>
              <li>선풍기(FAN)에 지원 동작 추가</li>
            </ul>
          </li>
          <li>CLOVA Home extension API에서 제어 동작과 관련된 API만 따로 모아 <a href="/Develop/References/ClovaHomeInterface/Control_Interfaces.md">기기 제어 인터페이스</a>라고 분류하고 동작을 추가함
            <ul>
              <li>StartOscillationConfirmation, StartOscillationRequest</li>
              <li>StartRecordingConfirmation, StartRecordingRequest</li>
              <li>StopOscillationConfirmation, StopOscillationRequest</li>
              <li>StopRecordingConfirmation, StopRecordingRequest</li>
            </ul>
          </li>
          <li>CLOVA Home extension API에서 정보 조회와 관련된 API만 따로 모아 <a href="/Develop/References/ClovaHomeInterface/Get_Interfaces.md">정보 조회 인터페이스</a>라고 분류하고 동작을 추가함
            <ul>
              <li>GetBMIRequest, GetBMIResponse</li>
              <li>GetBodyFatRequest, GetBodyFatResponse</li>
              <li>GetDetectedTimeRequest, GetDetectedTimeResponse</li>
              <li>GetDetectionCountRequest, GetDetectionCountResponse</li>
              <li>GetHealthScoreRequest, GetHealthScoreResponse</li>
              <li>GetMuscleRequest, GetMuscleResponse</li>
              <li>GetPowerStateRequest, GetPowerStateResponse</li>
              <li>GetWeightRequest, GetWeightResponse</li>
            </ul>
          </li>
          <li>기기 제어 실시 전 준비 단계에서 발생한 오류를 알리기 위한 <a href="/Develop/References/ClovaHomeInterface/Error_Interfaces.md#ActionFailedError">ActionFailedError</a> 메시지를 <a href="/Develop/References/ClovaHomeInterface/Error_Interfaces.md">오류 응답 인터페이스</a>에 추가</li>
          <li>API 레퍼런스와 developer console 가이드의 목차 수준을 한 단계씩 올림</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2019-07-31</td>
      <td>
        <ul>
          <li>CLOVA developer guide에서 CLOVA Home extension guide 문서로 분리됨</li>
          <li>일부 링크 오류 수정 및 오탈자 교정</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2019-07-02</td>
      <td>
        <ul>
          <li>일부 예제 오탈자 교정 및 노트 상자 수준 조정</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2019-05-20</td>
      <td>
        <ul>
          <li>CLOVA Home extension API의 <a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject">지원 기기</a> 설명 중 FAN 타입의 Action 항목에 빠진 동작(DecrementFanSpeed, IncrementFanSpeed, SetFanSpeed)을 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2019-04-08</td>
      <td>
        <ul>
          <li>CLOVA Home extension API의 <a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject">지원 기기</a> 설명 중 PURIFIER 타입의 Action 항목에 빠진 동작(GetConsumption)을 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2019-03-25</td>
      <td>
        <ul>
          <li>CLOVA Home extension API의 <a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md#ConsumptionInfoObject">ConsumptionInfoObject</a>에서 액체류 자원을 위한 부피 단위를 지원함</li>
          <li>일부 링크 오류 및 예제 수정</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2019-03-13</td>
      <td>
        <ul>
          <li>일부 레퍼런스 문서의 내용 순서 수정</li>
          <li>내외부 피드백을 문서에 반영</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2019-02-26</td>
      <td>
        <ul>
          <li>Extension이라는 표현이 custom extension과 CLOVA Home extension을 포괄하고 있어, 문서에서 extension만 단독으로 사용된 부분에서 둘 중 어느 것을 뜻하는지 명시함</li>
          <li>CLOVA Home extension 관리하기 가이드 추가
            <ul>
              <li><a href="/DevConsole/Guides/Register_Clova_Home_Extension.md">CLOVA Home extension 등록하기</a> 절 추가</li>
              <li><a href="/DevConsole/Guides/Test_Clova_Home_Extension.md">CLOVA Home extension 테스트하기</a> 절 추가</li>
              <li><a href="/DevConsole/Guides/Deploy_Clova_Home_Extension.md">CLOVA Home extension 배포하기</a> 절 추가</li>
              <li><a href="/DevConsole/Guides/Update_Clova_Home_Extension.md">CLOVA Home extension 업데이트하기</a> 절 추가</li>
              <li><a href="/DevConsole/Guides/Remove_Clova_Home_Extension.md">CLOVA Home extension 중지 및 삭제하기</a> 절 추가</li>
            </ul>
          <li>UI 요소를 제외한 것에 대해 URL이라는 표현 대신 URI로 수정함</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2019-01-25</td>
      <td>
        <ul>
          <li>CLOVA Home extension API의 <a href="/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetConsumptionRequest">GetConsumptionRequest</a>, <a href="/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetCurrentBillRequest">GetCurrentBillRequest</a>, <a href="/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetEstimateBillRequest">GetEstimateBillRequest</a> 메시지에 period 필드 추가</li>
          <li>다이어그램 일부 스타일 수정 및 표의 열 간격 조정</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2019-01-07</td>
      <td>
        <ul>
          <li>문서에 사용되 일부 UML 다이어그램의 스타일 통일</li>
          <li>문서 이력의 일부 표기 오류 수정</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2019-01-04</td>
      <td>
        <ul>
          <li>CLOVA Home extension 명세 중 <a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md#ModeInfoObject">ModeInfoObject</a>에 AIRCONDITIONER 타입 기기의 모드에 난방 모드(heat)와 송풍 모드(fan)를 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2018-12-22</td>
      <td>
        <ul>
          <li><a href="/Develop/Guides/Link_User_Account.md">사용자 계정 연결하기</a> 가이드의 <a href="/Develop/Guides/Link_User_Account.md#BuildAuthServer">인증 서버 구축</a> 설명에서 redirect_uri 파라미터 중 잘못 명시된 vendorId 필드를 제거함</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2018-11-30</td>
      <td>
        <ul>
          <li>CLOVA Home extension API에 <a href="/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetPreheatConfirmation">PreheatConfirmation</a>, <a href="/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetPreheatRequest">PreheatRequest</a> 추가</li>
          <li>CLOVA Home extension API <a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md">공유 객체</a> <a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject">ApplianceInfoObject</a>의 Remarks에 다음의 내용을 업데이트함
            <ul>
              <li>스마트락(SMARTLOCK) 기기 타입 추가</li>
              <li>와인 셀러(WINECELLAR) 기기 타입 추가</li>
              <li>공기청정기(AIRPURIFIER) 타입에 GetCurrentTemperature, GetHumidity 동작 추가</li>
              <li>스마트 조명 기기(LIGHT) 타입에 ReleaseMode 동작 추가</li>
              <li>오븐(OVEN) 타입에 SetPreheat 동작 추가</li>
              <li>환풍기(VENTILATOR) 타입에 GetCurrentTemperature 동작 추가</li>
            </ul>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2018-11-16</td>
      <td>
        <ul>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2018-11-09</td>
      <td>
        <ul>
          <li>CLOVA Home extension API <a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md">공유 객체</a> <a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject">ApplianceInfoObject</a>의 Remarks에 다음의 내용을 업데이트함
            <ul>
              <li>모든 기기 타입에 GetDeviceState 동작 추가</li>
              <li>오븐(OVEN) 타입에 GetRemainingTime 동작 추가</li>
              <li>의류 건조기(CLOTHESDRYER) 타입에 빠져있던 GetRemainingTime 동작 추가</li>
            </ul>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2018-10-20</td>
      <td>
        <ul>
          <li>CLOVA Home extension API <a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md">공유 객체</a> <a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject">ApplianceInfoObject</a>의 Remarks에 다음의 내용을 업데이트함
            <ul>
              <li>의류 관리기 타입(CLOTHESCAREMACHINE)과 의류 건조기 타입(CLOTHESDRYER)에 GetPhase 동작 추가</li>
              <li>냉장고 타입(REFRIGERATOR)에 ReleaseMode 동작 추가</li>
              <li>Actions에 빠져있던 GetEstimateConsumption 동작 추가</li>
            </ul>
          </li>
          <li>CLOVA Home extension API <a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md">공유 객체</a> <a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md#ModeInfoObject">ModeInfoObject</a>의 Operation Modes에서 환풍기(VENTILATOR) 타입 기기에 "ventilating" 모드 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2018-10-13</td>
      <td>
        <ul>
          <li>CLOVA Home extension API에 <a href="/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetEstimateConsumptionRequest">GetEstimateConsumptionRequest</a>, <a href="/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetEstimateConsumptionResponse">GetEstimateConsumptionResponse</a> 추가</li>
          <li>CLOVA Home extension 메시지의 <a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md">공유 객체</a> <a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md#ModeInfoObject">ModeInfoObject</a>에 AIRPURIFIER, HUMIDIFIER, VENTILATOR 타입 기기의 모드 추가</li>
          <li>CLOVA Home extension API의 <a href="/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetCurrentSittingStateRequest">GetCurrentSittingStateRequest</a>에 period 필드 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2018-10-05</td>
      <td>
        <ul>
          <li>CLOVA Home extension API의 <a href="/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#DecrementFanSpeedRequest">DecrementFanSpeedRequest</a>와 <a href="/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md#IncrementFanSpeedRequest">IncrementFanSpeedRequest</a>에서 불필요한 설명 제거</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2018-09-21</td>
      <td>
        <ul>
          <li>CLOVA Home extension API의 <a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject">지원 기기</a> 설명 중 Actions 항목에 빠진 동작(GetCleaningCycle, GetOpenState, ReleaseMode)을 추가</li>
          <li>CLOVA에서 전달하는 메시지의 검증을 위해 <a href="/Develop/References/HTTP_Message.md#HTTPHeader">HTTP 헤더</a>에 SignatureCEK 필드 설명을 추가하고 <a href="/Develop/Guides/Build_Clova_Home_Extension.md">CLOVA Home extension 만들기</a> 문서에 요청 메시지 검증 절을 추가</li>
          <li>CLOVA Home extension API의 <a href="/Develop/References/ClovaHomeInterface/Error_Interfaces.md">오류 메시지(Error)</a>에 <a href="/Develop/References/ClovaHomeInterface/Error_Interfaces.md#ActionTemporarilyBlockedError">ActionTemporarilyBlockedError</a>와 <a href="/Develop/References/ClovaHomeInterface/Error_Interfaces.md#ValueNotSupportedError">ValueNotSupportedError</a> 오류 메시지를 추가</li>
          <li>CLOVA Home extension API의 <a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md">공유 객체</a>에 <a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md#PercentageInfoObject">PercentageInfoObject</a> 객체 추가</li>
          <li>일부 잘못된 코드 예제를 수정</li>
          <li>일부 잘못된 링크를 수정</li>
          <li>일부 사용자 접점에 있는 Extension 표기를 Skill로 변경(UI 캡처 이미지 함께 업데이트)</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2018-09-07</td>
      <td>
        <ul>
          <li>예제 설명 중 "yourdomain.com"으로 표시된 예제를 문서 작성용 도메인 이름인 "example.com"으로 변경</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2018-08-29</td>
      <td>
        <ul>
          <li>CLOVA Home extension API의 <a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject">지원 기기</a> 중 난방기(HEATER)와 온도 조절기(THERMOSTAT) 타입에 GetTargetTemperature 동작 추가</li>
          <li>CLOVA Home extension API의 <a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md">공유 객체</a> 필드 필수/포함 여부 표기 개선</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2018-07-23</td>
      <td>
        <ul>
          <li>CLOVA Home extension API에서 SetFreezerTargetTemperature, SetFridgeTargetTemperature 동작을 제거하고 이와 관련된 인터페이스를 제거</li>
          <li>CLOVA Home extension API의 <a href="/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md#SetTargetTemperatureRequest">SetTargetTemperatureRequest</a>에 endpoint 필드를 추가하고 <a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md#EndpointInfoObject">EndpointInfoObject</a> 객체를 추가</li>
          <li>CLOVA Home extension API의 <a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject">지원 기기</a> 중 환풍기(VENTILATOR) 타입에 SetFanSpeed 동작 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2018-06-17</td>
      <td>
        <ul>
          <li>적외선 방식으로 제어되는 기기를 위해 CLOVA Home extension API <a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject">ApplianceInfoObject</a>에 isIr 필드 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2018-05-28</td>
      <td>
        <ul>
          <li>CLOVA Home extension API <a href="/Develop/References/ClovaHomeInterface/Error_Interfaces.md#ConditionsNotMetError">ConditionsNotMetError</a>에 state 필드 추가</li>
          <li>CLOVA Home extension API <a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md#TVChannelInfoObject">TVChannelInfoObject</a>에 서브 채널 정보 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2018-05-21</td>
      <td>
        <ul>
          <li>CLOVA Home extension API에 <a href="/Develop/References/ClovaHomeInterface/Error_Interfaces.md#ValueNotFoundError">ValueNotFoundError</a> 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2018-05-14</td>
      <td>
        <ul>
          <li>HTTP 요청 메시지에 헤더(SignatureCEK, SignatureCEKCertChainUrl) 추가 및 요청 메시지 검증 절 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2018-04-30</td>
      <td>
        <ul>
          <li>CLOVA Home extension API에 <a href="/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetOpenStateRequest">GetOpenStateRequest</a>, <a href="/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetOpenStateResponse">GetOpenStateResponse</a> 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2018-04-23</td>
      <td>
        <ul>
          <li>CLOVA Home extension API에 <a href="/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetReleaseModeConfirmation">ReleaseModeConfirmation</a>, <a href="/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetReleaseModeRequest">ReleaseModeRequest</a> 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2018-04-16</td>
      <td>
        <ul>
          <li>CLOVA Home extension API <a href="/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetLockStateResponse">GetLockStateResponse</a>에 openState 필드 추가</li>
          <li>CLOVA Home extension API에 <a href="/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetCleaningCycleRequest">GetCleaningCycleRequest</a>, <a href="/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetCleaningCycleResponse">GetCleaningCycleResponse</a> 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2018-04-09</td>
      <td>
        <ul>
          <li>CLOVA Home extension API <a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md#ColorInfoObject">ColorInfoObject</a>의 brightness 필드의 설명 및 필수/포함 여부 변경</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2018-04-02</td>
      <td>
        <ul>
          <li>CLOVA Home extension API에 GetSleepStartTimeRequest 외 9 건의 <a href="/Develop/References/ClovaHomeInterface/Control_Interfaces.md">Control API</a>와 4 건의 <a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md">공유 객체</a> 추가</li>
          <li>CLOVA Home extension API의 <a href="/Develop/References/ClovaHomeInterface/Discovery_Interfaces.md#DiscoverAppliancesResponse">DiscoverAppliancesResponse</a>에 <a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md#CustomCommandInfoObject">CustomCommandInfoObject</a> 추가</li>
          <li>CLOVA Home extension API에서 TimeAmountInfoObject <a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md">공유 객체</a> 제거 및 이에 따른 <a href="/Develop/References/ClovaHomeInterface/Control_Interfaces.md">Control API</a>의 일부 내용 변경</li>
          <li>CLOVA Home extension API의 <a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject">ApplianceInfoObject</a>에 tags 필드 추가 및 location 필드 설명 변경</li>
          <li>CLOVA developer console의 일부 UI 업데이트 적용</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2018-03-19</td>
      <td>
        <ul>
          <li>CLOVA Home extension API에 CloseConfirmation 외 47 건의 <a href="/Develop/References/ClovaHomeInterface/Control_Interfaces.md">Control API</a>와 약 10 종의 <a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md">공유 객체</a> 추가</li>
          <li>CLOVA Home extension API <a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject">지원 기기</a> 30 종 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2018-01-29</td>
      <td>
        <ul>
          <li>CLOVA Home extension 메시지 레퍼런스 중 <a href="/Develop/References/ClovaHomeInterface/Error_Interfaces.md">오류 응답 인터페이스</a>에 <a href="/Develop/References/ClovaHomeInterface/Error_Interfaces.md#NoSuchTargetError">NoSuchTargetError</a>, <a href="/Develop/References/ClovaHomeInterface/Error_Interfaces.md#NotSupportedInCurrentModeError">NotSupportedInCurrentModeError</a>, <a href="/Develop/References/ClovaHomeInterface/Error_Interfaces.md#UnsupportedOperationError">UnsupportedOperationError</a> 그리고 <a href="/Develop/References/ClovaHomeInterface/Error_Interfaces.md#ValueOutOfRangeError">ValueOutOfRangeError</a> 추가</li>
          <li>CLOVA developer console의 일부 UI 업데이트 적용</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2018-01-22</td>
      <td>
        <ul>
          <li>UML 다이어그램의 이미지 포맷 변경</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2018-01-02</td>
      <td>
        <ul>
          <li>일부 문서 오류, 오타 수정</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2017-11-20</td>
      <td>
        <ul>
          <li>CLOVA Home extension 메시지의 <a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md">공유 객체</a> HeatingModeInfoObject를 <a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md#ModeInfoObject">ModeInfoObject</a>로 이름을 변경하고 범용적인 기기의 운전 모드를 나타내는데 사용하는 객체로 설명을 수정</li>
          <li>CLOVA Home extension 메시지의 <a href="/Develop/References/ClovaHomeInterface/Control_Interfaces.md">Control</a> 인터페이스에 <a href="/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetCurrentTemperatureRequest">GetCurrentTemperatureRequest</a> 메시지와 <a href="/Develop/References/ClovaHomeInterface/Get_Interfaces.md#GetCurrentTemperatureResponse">GetCurrentTemperatureResponse</a> 메시지 추가</li>
          <li>CLOVA Home extension 메시지의 <a href="/Develop/References/ClovaHomeInterface/Error_Interfaces.md">Error</a> 인터페이스에 <a href="/Develop/References/ClovaHomeInterface/Error_Interfaces.md#UnsupportedOperationError">UnsupportedOperationError</a> 메시지 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2017-11-13</td>
      <td>
        <ul>
          <li><a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject">ApplianceInfoObject</a>에서 에어컨 타입(AIRCONDITIONER)에 DecrementFanSpeed, IncrementFanSpeed, SetFanSpeed, SetMode actioin을 가습기 타입(HUMIDIFIER)에 SetFanSpeed를 추가 </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2017-10-30</td>
      <td>
        <ul>
          <li><a href="/DevConsole/ClovaDevConsole_Overview.md">CLOVA developer console 개요</a> 설명 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2017-10-16</td>
      <td>
        <ul>
          <li>일부 문서 이미지 수정 및 문서 오류 교정</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2017-09-25</td>
      <td>
        <ul>
          <li>CLOVA Home extension API에 ChargeConfirmation 외 33 건의 <a href="/Develop/References/ClovaHomeInterface/Control_Interfaces.md">Control API</a> 추가</li>
          <li>CLOVA Home extension API <a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject">지원 기기</a> 6 종 추가 및 location 필드 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2017-09-04</td>
      <td>
        <ul>
          <li>일부 문서 오류 수정</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2017-08-28</td>
      <td>
        <ul>
          <li><a href="/Develop/References/ClovaHomeInterface/Error_Interfaces.md#ValueOutOfRangeError">ValueOutOfRangeError</a>를 CLOVA Home의 오류 응답 인터페이스에 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2017-08-04</td>
      <td>
        <ul>
          <li>CLOVA Home <a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject">지원 기기</a> 추가: 공기청정기, 가습기, 셋톱박스, 난방기기</li>
          <li>CLOVA Home <a href="/Develop/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject">지원 기기</a> 제외: 도어락</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2017-07-28</td>
      <td>
        <ul>
          <li><a href="/Develop/Guides/Build_Clova_Home_Extension.md">CLOVA Home extension 문서</a> 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2017-07-07</td>
      <td>
        <ul>
          <li><a href="/Glossary.md">용어집 추가</a></li>
          <li>CEK 메시지 포맷 파트의 목차 업데이트</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2017-07-03</td>
      <td>
        <ul>
          <li>CEK 문서 이미지 내용 업데이트</li>
          <li>문서 리뷰 결과 반영</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>2017-06-19</td>
      <td>
        <ul>
          <li>CEK 문서 파트 작성</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>
