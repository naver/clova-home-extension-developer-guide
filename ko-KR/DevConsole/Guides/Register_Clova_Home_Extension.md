<!-- Note! This content includes shared parts. Therefore, when you update this, you should beware of synchronization. -->

# CLOVA Home extension 등록하기
[CLOVA Home extension](/Develop/Guides/Build_Clova_Home_Extension.md)을 개발 중이거나 개발하고 있다면 이를 [CLOVA developer console](/DevConsole/ClovaDevConsole_Overview.md)에 등록해야 합니다. CEK 메뉴 페이지에서 페이지 하단에 있는 **{{ book.DevConsole.cek_new_home_skill }}** 버튼을 누르면 신규 CLOVA Home extension을 등록할 수 있습니다.

![DevConsole-First_Look_of_Extension_List](/DevConsole/Assets/Images/DevConsole-First_Look_of_Extension_List.png)

CLOVA Home extension을 등록할 때 일반적으로 다음 항목을 순차적으로 수행해야 합니다.

<ol>
  <li><a href="#AgreeTermsOfUse">이용 약관 및 개인 정보 수집 동의</a></li>
  <li><a href="#InputExtensionInfo">CLOVA Home extension 기본 정보 입력</a></li>
  <li><a href="#SetServerConnection">서버 연동 설정</a>
    <ul>
      <li><a href="#SetAccountLinking">계정 연결 설정</a></li>
    </ul>
  </li>
  <li><a href="#InputSupportedDevices">연동 기기 정보 입력</a></li>
</ol>

<!-- Start of the shared content: AgreeTermsOfUse -->

## 이용 약관 및 개인 정보 수집 동의 {#AgreeTermsOfUse}

CLOVA Home extension을 등록하기 전에 우선 CEK API 서비스 이용 약관과 개인 정보 수집에 동의해야 합니다. 이용 약관 및 개인 정보 수집에 대한 내용은 **최초 한 번만 표시**되며 동의한 이후에는 나타나지 않습니다.

![DevConsole-Agree_Terms_of_Use_and_Collecting_Personal_Info](/DevConsole/Assets/Images/DevConsole-Agree_Terms_of_Use_and_Collecting_Personal_Info.png)

<!-- End of the shared content -->

## CLOVA Home extension 기본 정보 입력 {#InputExtensionInfo}

CLOVA Home extension을 등록하는 과정에서 가장 먼저 할 일은 등록할 CLOVA Home extension의 기본 정보를 입력하는 것입니다. CLOVA Home extension의 기본 정보는 CLOVA developer console에 CLOVA Home extension을 생성하기 위한 필수 정보입니다. CLOVA Home extension의 기본 정보를 입력하고 나면 CEK 메뉴에서 생성한 CLOVA Home extension을 언제든지 접근 또는 수정할 수 있게 됩니다.

다음 절차에 따라 CLOVA Home extension을 등록합니다.

![DevConsole-Create_New_Clova_Home_Extension](/DevConsole/Assets/Images/DevConsole-Create_New_Clova_Home_Extension.png)

<style>
ol>li>ol {
    list-style-type: lower-alpha;
}
</style>

<ol>
  <li><strong>{{ book.DevConsole.cek_lang }}</strong> 항목에서 CLOVA Home extension에서 사용할 언어를 선택하십시오.<br />현재 <strong>{{ book.DevConsole.supported_languages }}</strong>만 지원하고 있습니다.</li>
  <li><strong>Extension의 ID</strong>, <strong>Skill 이름</strong>에 해당하는 정보를 다음 항목에 입력하십시오.
    <ol>
      <li><strong>{{ book.DevConsole.cek_id }}</strong><br />CLOVA Home extension의 고유 ID를 입력하십시오. Reverse domain name 표기 형식(예: <code>com.example.extension.homeremote</code>)으로 입력합니다.</li>
      <li><strong>{{ book.DevConsole.cek_name }}</strong><br />CLOVA Home extension의 이름을 입력하십시오. 추후 <strong>{{ book.DevConsole.ManageCLOVAHomeExtensions }}</strong>에 노출됩니다.</li>
      <li><strong>{{ book.DevConsole.cek_provider }}</strong><br />CLOVA Home extension의 제작 주체(회사나 개인)의 이름 또는 별칭을 입력합니다. 추후 <strong>{{ book.DevConsole.ManageCLOVAHomeExtensions }}</strong>에 노출되며, CLOVA Home extension 승인 과정에서 심사를 받게 됩니다.</li>
    </ol>
  </li>
  <li><strong>{{ book.DevConsole.cek_email }}</strong> 항목에 연락 가능한 이메일 주소를 입력하십시오.</li>
  <li><strong>{{ book.DevConsole.cek_tester }}</strong> 항목에 개발 중인 CLOVA Home extension을 테스트할 때 이용할 {{ book.ServiceEnv.OrientedService }} 계정을 입력하십시오. 당장 입력하지 않아도 되며 추후 <a href="/DevConsole/Guides/Test_Clova_Home_Extension.md">extension을 테스트</a>해야 할 때 이 필드에 값을 입력할 수 있습니다.</li>
  <li>CLOVA Home extension의 기본 정보를 모두 입력한 후 <strong>{{ book.DevConsole.cek_create }}</strong> 버튼을 누르십시오.</li>
</ol>

CLOVA Home extension의 기본 정보 입력이 끝나면 생성된 CLOVA Home extension의 정보를 수정하는 화면으로 전환됩니다. 이때부터 페이지 하단에 있는 **{{ book.DevConsole.cek_save }}** 버튼을 클릭하여 중간 내용을 언제든지 저장할 수 있으며, 다음과 같이 CEK 메뉴에서 등록된 CLOVA Home extension 목록을 확인할 수 있습니다.

![DevConsole-Clova_Home_Extension_List_After_Creation](/DevConsole/Assets/Images/DevConsole-Clova_Home_Extension_List_After_Creation.png)

## 서버 연동 설정 {#SetServerConnection}

CLOVA Home extension은 CEK와 HTTPS 통신을 수행하게 됩니다. 이때, CEK는 CLOVA Home extension쪽으로 HTTP 요청을 보내고, CLOVA Home extension은 HTTP 응답을 CEK에 보냅니다. CEK가 CLOVA Home extension으로 HTTP 요청을 보내려면 CLOVA developer console에서 서버 연동 설정을 수행해야 합니다. [CLOVA Home extension 기본 정보를 입력](#InputExtensionInfo)한 후 생성된 CLOVA Home extension에 대해 서버 연동 설정을 수행할 수 있습니다.

CLOVA Home extension 서버를 등록하기 전에 우선 CLOVA Home extension 서버와 통신이 되는지 확인해야 합니다. 다음 예와 같이 간단한 curl 명령으로 통신 상태를 확인할 수 있습니다.

{% raw %}
```bash
$ curl "https://example.com/homeremote" -X POST
```
{% endraw %}

다음 절차에 따라 서버 연동 설정을 수행합니다.

![DevConsole-Clova_Home_Extension_Server_Settings](/DevConsole/Assets/Images/DevConsole-Clova_Home_Extension_Server_Settings.png)

<ol>
  <li>Extension 정보 입력 UI에서 위쪽에 있는 <strong>{{ book.DevConsole.cek_configuration }}</strong> 탭을 누르십시오.</li>
  <li>CLOVA Home extension 서버 URI(endpoint) 정보를 <strong>{{ book.DevConsole.cek_service_endpoint_url }}</strong> 항목에 입력하십시오.
    <div class="note">
      <p><strong>Note!</strong></p>
      <p>테스트 단계에서는 HTTP도 가능하나 정식 서비스를 위해서는 HTTPS여야 합니다. CLOVA Home extension 서버는 HTTP일 때 80 번 포트를 HTTPS일 때 443 번 포트를 사용해야 합니다.</p>
    </div>
  </li>
  <li><strong>{{ book.DevConsole.cek_ssl_certificate }}</strong> 항목의 라디오 버튼을 누르십시오. CLOVA Home extension을 제공하는 서버는 반드시 공인된 인증 기관의 인증서를 사용해야 합니다.(Self-signed 인증서 사용 불가)</li>
  <li>서버 연동 설정과 관련된 내용을 입력한 후 <strong>{{ book.DevConsole.cek_save }}</strong> 버튼을 누르십시오.</li>
</ol>

<div class="Note">
  <p><strong>Note!</strong></p>
  <p>CLOVA Home extension이 제공하는 서비스의 사용자 계정과 CLOVA의 사용자 계정을 연결해야 합니다. 계정 연결에 대한 자세한 설명은 <a href="#SetAccountLinking">계정 연결 설정</a>을 참조합니다.</p>
</div>

### 계정 연결 설정 {#SetAccountLinking}

CLOVA Home extension으로 IoT 서비스를 제공할 때 사용자 계정이 CLOVA의 사용자 계정과 연결되어야 합니다. 이를 위해 [서버 연동 설정](#SetServerConnection) 중에 [계정 연결(account linking)](/Develop/Guides/Link_User_Account.md)에 관련된 정보를 입력해야 합니다.

다음 절차에 따라 계정 연결 설정에 [필요한 정보](/Develop/Guides/Link_User_Account.md#RegisterAccountLinkingInfo)를 입력합니다.

![DevConsole-Clova_Home_Extension_Accoun_Linking_Settings](/DevConsole/Assets/Images/DevConsole-Clova_Home_Extension_Accoun_Linking_Settings.png)

<ol>
  <li>사용자가 계정 인증을 할 수 있도록 UI를 제공하는 Authorization URI를 <strong>{{ book.DevConsole.cek_authorization_url }}</strong> 항목에 입력하십시오. 사용자가 CLOVA Home extension을 활성화하면 이 페이지로 이동됩니다.</li>
  <li>사용자 계정 인증 시 HTTP 요청에 필요한 <strong>{{ book.DevConsole.cek_client_id }}</strong>를 입력하십시오. 클라이언트 ID는 <a href="/Develop/Guides/Link_User_Account.md#BuildAuthServer">인증 서버를 구축</a>할 때 생성한 값입니다.</li>
  <li>(선택 사항) 만약, 사용자 계정 연결 시 발급되는 access token의 사용 범위(scope)를 미리 정의했다면 <strong>{{ book.DevConsole.cek_scope }}</strong> 항목에 미리 정의한 범위를 추가하십시오.</li>
  <li><strong>{{ book.DevConsole.cek_access_token_uri }}</strong> 항목에 서비스의 access token을 발급 받을 수 있는 URI를 입력하십시오. 현재 <strong>허가 승인 타입(grant type)은 code grant 방식만 지원</strong>하고 있습니다.</li>
  <li><strong>{{ book.DevConsole.cek_refresh_token_uri }}</strong> 항목에 서비스의 access token을 갱신할 수 있는 URI를 입력하십시오.</li>
  <li>서비스의 access token을 획득 시 HTTP 요청에 필요한 <strong>{{ book.DevConsole.cek_client_secret }}</strong>을 입력하십시오. 클라이언트 secret은 <a href="/Develop/Guides/Link_User_Account.md#BuildAuthServer">인증 서버를 구축</a>할 때 생성한 값입니다.</li>
  <li><strong>{{ book.DevConsole.cek_client_authentication_scheme }}</strong>은 다음 중 인증 서버의 인터페이스 구현에 맞는 값을 설정하십시오.
    <ul>
      <li><strong>HTTP Basic (Recommended)</strong>: 서비스 access token을 획득하기 위해 인증 정보(Credentials)를 헤더에 입력받을 때</li>
      <li><strong>Credentials in request body</strong>: 서비스 access token을 획득하기 위해 인증 정보를 본문(body)에 입력받을 때</li>
    </ul>
  </li>
</ol>

<div id="RedirectURI" class="note">
  <p><strong>Note!</strong></p>
  <p>계정 인증 후 클라이언트가 이동할 URI(redirect URI)은 <code>{{ book.ServiceEnv.RedirectURIforAccountLinking }}</code>이며, <strong>{{ book.DevConsole.cek_redirect_urls }}</strong> 항목에서 확인할 수 있습니다.</strong> <a href="/Develop/Guides/Link_User_Account.md#BuildAuthServer">인증 서버</a>는 클라이언트가 전달하는 <code>redirect_uri</code>의 값이 이 값과 같은지 검증해야 합니다.</p>
  <img src="/DevConsole/Assets/Images/DevConsole-Redirect_URI_for_Extension_Accoun_Linking.png" />
</div>

## 연동 기기 정보 입력 {#InputSupportedDevices}

CLOVA Home extension 등록 과정의 마지막으로 CLOVA Home extension이 지원하는 연동 기기 정보를 다음 절차에 따라 입력하십시오.

![DevConsole-Clova_Home_Extension_Input_Supported_Devices](/DevConsole/Assets/Images/DevConsole-Clova_Home_Extension_Input_Supported_Devices.png)

<ol>
  <li>Extension 정보 입력 UI에서 위쪽에 있는 <strong>{{ book.DevConsole.cek_home_appliance }}</strong> 탭을 누르십시오.</li>
  <li><strong>{{ book.DevConsole.cek_search_appliance_type }}</strong>에서 CLOVA Home extension을 통해 제공 및 지원하려는 기기 타입을 검색 또는 선택하십시오. 선택한 기기 타입은 <strong>{{ book.DevConsole.cek_appliance_type_list }}</strong>에 추가됩니다.
    <div class="note">
    <p><strong>Note!</strong></p>
    <p>연동 기기 정보를 입력할 때 실제 팔고 있거나 지원하고 있는 정확한 제품 이름을 입력해야 합니다. 연동 기기에 대한 정보도 CLOVA Home extension 승인 과정에서 심사를 받게 됩니다.</p>
   </div>
  </li>
  <li><strong>{{ book.DevConsole.cek_search_appliance_type }}</strong>에서 추가한 기기 타입의 모델명과 구매 페이지를 입력하십시오.</li>
  <li>모델 정보를 입력한 후 <img class="inlineImage" src="/DevConsole/Assets/Images/DevConsole-Plus_Button.png" /> 버튼을 누르십시오. 버튼을 누르면 모델 정보가 추가되며, 필요한 만큼 모델 정보를 추가할 수 있습니다.</li>
  <li>제공 및 지원하려는 기기 타입 및 모델 정보를 모두 입력한 후 <strong>{{ book.DevConsole.cek_save }}</strong> 버튼을 누르십시오.</li>
</ol>
