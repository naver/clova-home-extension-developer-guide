<!-- Note! This content includes shared parts. Therefore, when you update this, you should beware of synchronization. -->

# CLOVA Home extension 배포하기
CLOVA Home extension을 [CLOVA developer console에 등록](/DevConsole/Guides/Register_Clova_Home_Extension.md)했다면 등록한 CLOVA Home extension을 CLOVA 서비스에 배포할 수 있습니다. 배포하면 일반 사용자들이 **{{ book.DevConsole.ManageCLOVAHomeExtensions }}**에서 배포된 CLOVA Home extension을 사용할 수 있게 됩니다.

CLOVA Home extension을 배포할 때 일반적으로 다음 항목을 수행해야 합니다.

* [배포 정보 입력](#InputDeploymentInfo)
* [개인 정보 및 규정 준수 정보 입력](#InputComplianceInfo)
* [심사 신청하기](#RequestExtensionSubmission)

## 배포 정보 입력 {#InputDeploymentInfo}

CLOVA developer console에서 [CLOVA Home extension을 등록](/DevConsole/Guides/Register_Clova_Home_Extension.md)한 후 배포 정보를 입력할 수 있습니다. CLOVA Home extension 등록 메뉴에서 **{{ book.DevConsole.cek_home_publishing }}**를 선택합니다.

![DevConsole-Clova_Home_Extension_Deployment_Info_Menu](/DevConsole/Assets/Images/DevConsole-Clova_Home_Extension_Deployment_Info_Menu.png)

다음과 같이 CLOVA Home extension의 배포 정보를 입력합니다.

![DevConsole-Input_Clova_Home_Extension_Deployment_Info](/DevConsole/Assets/Images/DevConsole-Input_Clova_Home_Extension_Deployment_Info.png)

**{{ book.DevConsole.ManageCLOVAHomeExtensions }}**을 통해 CLOVA Home extension을 표시하기 위한 정보입니다. 다음과 같은 정보들이 입력됩니다.

{% if book.L10N.TargetCountryCode == "KR" %}
* **{{ book.DevConsole.cek_icon }}**: CLOVA Home extension 아이콘 파일(250px X 250px)입니다. **{{ book.DevConsole.ManageCLOVAHomeExtensions }}**에 표시됩니다.
* **{{ book.DevConsole.cek_banner_img }}**: CLOVA Home extension용 배너 이미지(750px X 500px)로 사용자 계정 연결이 완료된 후 페이지 상단에 배너 형태로 표시됩니다.
* **{{ book.DevConsole.cek_home_publish_website }}**: 제공하는 IoT 서비스의 대표 사이트 URI를 입력합니다. 배너 아래 쪽에 대표 사이트로 이동하는 링크가 제공됩니다.
{% elif book.L10N.TargetCountryCode == "JP" %}
* **{{ book.DevConsole.cek_icon }}**: CLOVA Home extension 아이콘 파일(460px X 460px)입니다. **{{ book.DevConsole.ManageCLOVAHomeExtensions }}**에 표시됩니다.
* **{{ book.DevConsole.cek_banner_img }}**: CLOVA Home extension용 배너 이미지(1080px X 692px)로 사용자 계정 연결이 완료된 후 페이지 상단에 배너 형태로 표시됩니다.
* **{{ book.DevConsole.cek_home_publish_website }}**: 제공하는 IoT 서비스의 대표 사이트 URI를 입력합니다. 배너 아래 쪽에 대표 사이트로 이동하는 링크가 제공됩니다.
{% endif %}

이렇게 입력된 정보는 **{{ book.DevConsole.ManageCLOVAHomeExtensions }}**에서 다음과 같이 표시됩니다.

| {{ book.DevConsole.CLOVAHomeExtensionMenu }} | {{ book.DevConsole.ExtensionPage }}   |
|-------------------|-------------------|
| ![CLOVA Home extension List](/DevConsole/Assets/Images/DevConsole-SmartHome_UI_Example-Clova_Home_Extension_Main.png) | ![CLOVA Home extension Details](/DevConsole/Assets/Images/DevConsole-SmartHome_UI_Example-Clova_Home_Extension_Page.png) |

<div class="tip">
  <p><strong>Tip!</strong></p>
  <p><strong>{{ book.DevConsole.ExtensionPage }}</strong>에 표시되는 일부 정보는 <a href="/DevConsole/Guides/Register_Clova_Home_Extension.md#InputExtensionInfo">Extension 기본 정보를 등록</a>할 때 입력된 정보를 활용합니다.</p>
</div>

## 개인 정보 보호 및 규정 준수 정보 입력 {#InputComplianceInfo}

CLOVA Home extension 배포에 필요한 정보를 입력하는 마지막 단계로서 개인 정보 관리 및 규정 준수에 관련된 내용을 입력해야 합니다. Extension 등록 메뉴에서 **{{ book.DevConsole.cek_privacy }}**를 선택합니다.

![DevConsole-Clova_Home_Extension_Policy_Menu](/DevConsole/Assets/Images/DevConsole-Clova_Home_Extension_Policy_Menu.png)

다음과 같이 정보를 입력합니다.

![DevConsole-Input_Clova_Home_Extension_Policy](/DevConsole/Assets/Images/DevConsole-Input_Clova_Home_Extension_Policy.png)

* **{{ book.DevConsole.cek_use_personal_info }}**: CLOVA Home extension이 사용자의 개인 정보를 수집한다면 **{{ book.DevConsole.cek_yes }}**를 선택합니다.

<!-- Start of the shared content: RequestExtensionSubmission -->

## 심사 신청하기 {#RequestExtensionSubmission}

CLOVA Home extension의 [배포 정보](#InputDeploymentInfo)와 [개인 정보 보호 및 규정 준수 정보](#InputComplianceInfo)까지 입력이 완료되었다면 마지막 단계로 등록한 extension에 대해 extension 심사를 신청할 수 있습니다. CLOVA의 운영자는 등록한 extension의 정보와 실제 실행 여부 및 적합성을 심사하게 됩니다.

* Extension이 정상 동작하고 검수 시 특별한 문제 사항이 없다면 extension은 심사를 통과하게 될 것이며, 심사를 통과하면 즉시 extension을 배포할 수 있게 됩니다.
* 만약, 심사 과정에서 실행 오류가 있거나 사용자 시나리오 상의 심각한 문제가 발견되면 운영자에 의해 배포 요청이 거절되며 심사 신청하기 전 단계로 돌아가게 됩니다.

![DevConsole-Extension_Submission_Process](/DevConsole/Assets/Images/DevConsole-Extension_Submission_Process.png)

등록한 extension 목록에서 **{{ book.DevConsole.cek_request_submit }}** 메뉴를 클릭하여 extension 심사를 신청할 수 있습니다.

![DevConsole-Submit_Extension_1](/DevConsole/Assets/Images/DevConsole-Submit_Extension_1.png)

또는 [개인 정보 보호 및 규정 준수 정보](#InputComplianceInfo)를 입력하는 화면 마지막에 있는 **{{ book.DevConsole.cek_request_submit }}** 버튼을 클릭해도 됩니다.

![DevConsole-Submit_Extension_2](/DevConsole/Assets/Images/DevConsole-Submit_Extension_2.png)

**{{ book.DevConsole.cek_request_submit }}**을 누르면 다음과 같이 운영자에게 해당 심사 신청에 대한 정보를 남길 수 있습니다. Extension의 첫 번째 심사 신청이라면 최초 심사 요청이라는 메시지와 어떤 extension인지 설명하는 메시지를 남기면 됩니다. Extension을 수정하여 재심사를 요청할 때는 개선된 사항이나 반려 의견 반영 여부를 입력하면 됩니다.

![DevConsole-Submission_Request_Message](/DevConsole/Assets/Images/DevConsole-Submission_Request_Message.png)

<div class="note">
  <p><strong>Note!</strong></p>
  <p>심사 중에는 extension의 정보를 수정할 수 없습니다.</p>
</div>

Skill 심사는 **{{ book.DevConsole.ManageCLOVAHomeExtensions }}**에 반영하기 전에 진행되며 심사를 위한 별도 환경에서 진행됩니다. [배포 정보를 입력](#InputDeploymentInfo)할 때 테스트를 위한 계정 정보를 **{{ book.DevConsole.cek_test_instructions }}** 항목에 입력해야 합니다.

심사할 때 다음과 같은 항목을 평가합니다.

* 동작 검증
  * 사용자 계정 연결이 잘 되는지 확인합니다.
  * 등록된 모든 제품에 대해 요청 동작이 제대로 지원되는지 확인합니다.
* 배포 정보 검증
  * 지원하는 기기 타입과 모델 명과 같은 것이 제대로 입력되었는지 확인합니다.
  * 제품의 로고나 배너 이미지가 제대로 입력되었는지 확인합니다.

심사 중에 **{{ book.DevConsole.cek_cancel_review }}** 메뉴를 누르면 언제든지 심사 신청을 취소할 수 있습니다. 심사 신청을 취소하면 이전 상태로 돌아갑니다.

![DevConsole-Cancel_Submission](/DevConsole/Assets/Images/DevConsole-Cancel_Submission.png)

심사에 통과하지 못하면 extension의 **{{ book.DevConsole.cek_status }}**가 **{{ book.DevConsole.cek_status_rejected }}**으로 변경됩니다. 이 상태는 **{{ book.DevConsole.cek_status_dev }}**인 상태와 같은 상태이며 다시 심사를 신청할 수 있습니다.

![DevConsole-Extension_Submission_Rejected](/DevConsole/Assets/Images/DevConsole-Extension_Submission_Rejected.png)

이때, **{{ book.DevConsole.cek_message }}**의 **{{ book.DevConsole.cek_view }}** 메뉴를 누르면 심사에 대한 피드백을 확인할 수 있습니다.

![DevConsole-Show_Submission_Feedback](/DevConsole/Assets/Images/DevConsole-Show_Submission_Feedback.png)

<!-- End of the shared content -->
