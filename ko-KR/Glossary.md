<!-- Note! This content includes shared parts. Therefore, when you update this file, you should beware of synchronization. -->

<!-- Start of the shared content: Glossary -->

# 용어 및 약어

<div class="note">
  <p><strong>Note!</strong></p>
  <p>이 페이지는 계속 업데이트되고 있습니다.</p>
</div>

### CEK
[CLOVA Extensions Kit](#CEK)의 약어

### CIC
[CLOVA Interface Connect](#CIC)의 약어

### CLOVA {#CLOVA}
[CLOVA](https://clova.ai)는 {{ book.ServiceEnv.OrientedService }}가 개발 및 서비스하고 있는 인공지능 플랫폼입니다. CLOVA 사용자의 음성이나 이미지를 인식하고 이를 분석하여 사용자가 원하는 정보나 서비스를 제공합니다. 3rd party 개발자는 CLOVA가 가진 기술을 활용하여 인공 지능 서비스를 제공하는 기기 또는 가전 제품을 만들거나 보유하고 있는 콘텐츠나 서비스를 CLOVA를 통해 사용자에게 제공할 수 있습니다.

### CLOVA developer console {#CLOVADeveloperConsole}
CLOVA 플랫폼과 연동하는 클라이언트 기기나 [CLOVA extension](#CLOVAExtension)을 개발하는 개발자에게 다음과 같은 내용을 제공하는 <a target="_blank" href="{{ book.ServiceEnv.DeveloperConsoleURI }}">웹 도구</a>입니다.
* CLOVA extension [등록](/DevConsole/Guides/Register_Clova_Home_Extension.md) 및 [배포](/DevConsole/Guides/Deploy_Clova_Home_Extension.md)
* CLOVA 서비스 관련 통계 자료 제공 (추후 제공 예정)

### CLOVA extension {#CLOVAExtension}
음악, 쇼핑, 금융 같은 외부 서비스(3rd party service)나 집 안 IoT 기기의 원격 제어와 같이 사용자가 CLOVA를 통해 더 많은 서비스와 기능을 경험할 수 있도록 CLOVA에 확장된 기능을 제공하는 애플리케이션입니다. 짧게 extension이라 부르기도 하며, CLOVA 플랫폼은 현재 다음과 같은 두 종류의 extension을 지원공하고 있습니다. 일반 사용자에게는 "Skill"이라는 이름으로 제공되고 있습니다.
* [Custom extension](#CustomExtension)
* [CLOVA Home extension](#CLOVAHomeExtension)

### CLOVA Extensions Kit (CEK) {#CEK}
CLOVA extension을 개발 및 배포할 때 필요한 도구와 인터페이스를 제공하는 플랫폼으로 [CLOVA와 extension 사이의 커뮤니케이션](/Develop/CEK_Overview.md)을 지원합니다.

### CLOVA Home extension {#CLOVAHomeExtension}
IoT 기기 제어 서비스를 제공하기 위한 extension입니다. 자세한 내용은 [CLOVA Home extension 만들기](/Develop/Guides/Build_Clova_Home_Extension.md) 문서를 참조합니다.

### CLOVA Home extension 메시지 {#CLOVAHomeExtMessage}
IoT 기기를 제어하는 [CLOVA Home extension](#CLOVAHomeExtension)이 [CLOVA Extensions Kit](#CEK)와 정보를 주고 받을 때 전용으로 사용하는 메시지입니다. 자세한 내용은 [CLOVA Home extension 메시지](/Develop/References/Clova_Home_Extension_Message.md) 문서를 참조합니다.

### CLOVA Interface Connect (CIC) {#CIC}
인공 지능 비서 서비스를 제공하려는 PC/모바일용 앱, 모바일 또는 가전 기기의 클라이언트에 CLOVA와 연동할 수 있는 인터페이스를 제공하는 플랫폼입니다. 자세한 내용은 [CIC 개요]({{ book.DocMeta.CLOVAClientDeveloperGuideBaseURI }}/Develop/CIC_Overview.{{ book.DocMeta.FileExtensionForExternalLink }}) 문서를 참조합니다.

### CLOVA 앱 {#CLOVAApp}

{{ book.ServiceEnv.OrientedService }}가 개발하여 iOS나 Android 플랫폼으로 배포한 CLOVA 앱입니다. CLOVA에 명령을 내릴 수 있을 뿐만 아니라 클라이언트 기기를 등록하고 관리할 수 있는 앱입니다.

### Custom extension {#CustomExtension}
임의의 확장된 기능을 제공하는 [extension](#CLOVAExtension)입니다. Custom extension을 사용하면 음악, 쇼핑, 금융과 같은 외부 서비스의 기능을 제공할 수 있습니다. 자세한 내용은 [CLOVA custom extension 만들기]({{ book.DocMeta.CLOVACustomExtensionDeveloperGuideBaseURI }}/Develop/Guides/Build_Custom_Extension.{{ book.DocMeta.FileExtensionForExternalLink }}) 문서를 참조합니다.

### Discovery 기능 {#Discovery}
사용자 계정에 등록된 IoT 기기 목록을 클라이언트 기기에 제공하는 기능입니다. 자세한 내용은 [Discovery 제공하기](/Develop/Guides/Build_Clova_Home_Extension.md#ProvideDeviceDiscovery) 문서를 참조합니다.

### Extension {#Extension}
[CLOVA extension](#CLOVAExtension)의 다른 표현

### OAuth 2.0
접근 권한을 위임하기 위한 공개 표준으로 인터넷 사용자가 다른 웹 서비스나 응용 프로그램에 사용자 계정에 접근할 수 있는 권한을 부여하는 규약입니다. CLOVA 플랫폼에서는 클라이언트가 [CLOVA access token](#CLOVAAccessToken)을 획득하거나 사용자가 특정 extension을 사용 시 자신의 [계정을 연결](/Develop/Guides/Link_User_Account.md)할 때 사용됩니다. 자세한 내용은 [https://tools.ietf.org/html/rfc6749](https://tools.ietf.org/html/rfc6749)를 참고합니다.

### Skill {#Skill}

CLOVA가 제공하는 사용자에게 제공하는 확장 기능이나 서비스를 의미합니다. Skill을 사용자에게 제공하려면 [CLOVA extension](#CLOVAExtension)을 개발해야 합니다.

### Skill Store {#SkillStore}

Skill이 사용자에게 제공될 수 있도록 만든 플랫폼입니다.

### Skill Store 홈 {#SkillStoreHome}

Skill Store에 등록된 skill이 표시되는 페이지입니다. CLOVA 앱의 **확장 서비스 관리** 메뉴를 지칭하는 용어입니다.

### 사용자 계정 연결 (Account Linking) {#AccountLinking}
사용자의 계정 인증(authentication)이 필요한 외부 서비스를 [extension](#CLOVAExtension)이 제공해야 할 때 사용됩니다. 자세한 내용은 [사용자 계정 연결하기](/Develop/Guides/Link_User_Account.md) 문서를 참조합니다.

<!-- End of the shared content -->
