# 용어 및 약어

<div class="note">
  <p><strong>Note!</strong></p>
  <p>이 페이지는 계속 업데이트되고 있습니다.</p>
</div>

### CEK
[Clova Extensions Kit](#CEK)의 약어

### CIC
[Clova Interface Connect](#CIC)의 약어

### CIC API {#CICAPI}
CIC가 클라이언트에 제공하는 REST API로 클라이언트는 CIC API를 사용하여 Clova와 정보를 교환할 때 사용됩니다.

### Clova {#Clova}
[Clova](http://clova.ai)는 {{ book.TargetServiceForClientAuth }}가 개발 및 서비스하고 있는 인공지능 플랫폼입니다. Clova 사용자의 음성이나 이미지를 인식하고 이를 분석하여 사용자가 원하는 정보나 서비스를 제공합니다. 3rd party 개발자는 Clova가 가진 기술을 활용하여 인공 지능 서비스를 제공하는 기기 또는 가전 제품을 만들거나 보유하고 있는 콘텐츠나 서비스를 Clova를 통해 사용자에게 제공할 수 있습니다.

### Clova access token {#ClovaAccessToken}
클라이언트가 [Clova Interface Connect](#CIC)로 [이벤트 메시지](#Event)를 보낼 때 Clova가 클라이언트를 인증하는 수단입니다. 자세한 내용은 [Clova access token 생성하기](/CIC/Guides/Interact_with_CIC.md#CreateClovaAccessToken) 문서를 참조합니다.

### Clova developer console {#ClovaDeveloperConsole}
Clova 플랫폼과 연동하는 클라이언트 기기나 [Clova extension](#ClovaExtension)을 개발하는 개발자에게 다음과 같은 내용을 제공하는 <a target="_blank" href="{{ book.DeveloperConsoleURL }}">웹 도구</a>입니다.
* 클라이언트 기기 등록 및 클라이언트 인증 정보 제공 (추후 제공 예정)
* Clova extension [등록](/DevConsole/Guides/CEK/Register_Extension.md) 및 [배포](/DevConsole/Guides/CEK/Deploy_Extension.md)
* [Interaction 모델 등록](/DevConsole/Guides/CEK/Register_Interaction_Model.md)
* Clova 서비스 관련 통계 자료 제공 (추후 제공 예정)

### Clova extension {#ClovaExtension}
음악, 쇼핑, 금융 등과 같은 외부 서비스(3rd party service)나 집안의 IoT 기기 제어 등 사용자가 Clova를 통해 다양한 경험을 제공받을 수 있도록 Clova에게 확장된 기능을 제공하는 웹 애플리케이션입니다. 일반적으로 extension이라 부르며, Clova 플랫폼은 현재 다음과 같은 두 종류의 Clova extension을 지원 및 제공하고 있습니다. 일반 사용자에게는 "확장 서비스"라는 표현으로 제공됩니다.
* [Custom extension](#CustomExtension)
* [Clova Home extension](#ClovaHomeExtension)

### Clova Extensions Kit (CEK) {#CEK}
Clova extension을 개발 및 배포할 때 필요한 도구와 인터페이스를 제공하는 플랫폼으로 [Clova와 extension 사이의 커뮤니케이션](/CEK/CEK_Overview.md)을 지원합니다.

### Clova Home extension {#ClovaHomeExtension}
IoT 기기 제어 서비스를 제공하기 위한 extension입니다. 자세한 내용은 [Clova Home extension 만들기](/CEK/Guides/Build_Clova_Home_Extension.md) 문서를 참조합니다.

### Clova Home extension 메시지 {#ClovaHomeExtMessage}
IoT 기기를 제어하는 [Clova Home extension](#ClovaHomeExtension)이 [Clova Extensions Kit](#CEK)와 정보를 주고 받을 때 전용으로 사용하는 메시지입니다. 자세한 내용은 [Clova Home extension 메시지](/CEK/References/CEK_API.md#ClovaHomeExtMessage) 문서를 참조합니다.

### Clova Interface Connect (CIC) {#CIC}
인공 지능 비서 서비스를 제공하려는 PC/모바일용 앱, 모바일 또는 가전 기기 등의 클라이언트에게 Clova와 연동할 수 있는 인터페이스를 제공하는 플랫폼입니다. 자세한 내용은 [CIC 개요](/CIC/CIC_Overview.md) 문서를 참조합니다.

### Clova 앱 {#ClovaApp}

{{ book.OrientedService }}가 개발하여 iOS나 Android 플랫폼으로 배포한 Clova 앱입니다. Clova에 명령을 내릴 수 있을 뿐만 아니라 클라이언트 기기를 등록하고 관리할 수 있는 앱입니다.

### Clova 인증 API {#ClovaAuthAPI}
클라이언트가 [Clova access token](#ClovaAccessToken)을 획득하기 위해 사용해야 하는 API입니다. 자세한 내용은 [Clova 인증 API](/CIC/References/Clova_Auth_API.md) 문서를 참조합니다.

### Content template {#ContentTemplate}
CIC를 통해 전달되는 콘텐츠 정보를 일정 범주에 맞게 정형화한 것입니다. 자세한 내용은 [content template](/CIC/References/Content_Templates.md) 문서를 참조합니다.

### Context objects {#ContextObjects}
클라이언트의 현재 [맥락 정보](#Context)를 표현하는 객체입니다. 자세한 내용은 [맥락 정보(Context)](/CIC/References/Context_Objects.md) 문서를 참조합니다.

### Custom extension {#CustomExtension}
임의의 확장된 기능을 제공하는 [extension](#ClovaExtension)입니다. Custom extension을 사용하면 음악, 쇼핑, 금융과 같은 외부 서비스의 기능을 제공할 수 있습니다. 자세한 내용은 [Custom extension 만들기](/CEK/Guides/Build_Custom_Extension.md) 문서를 참조합니다.

### Custom extension 메시지 {#CustomExtMessage}
[Clova Extensions Kit](#CEK)와 [custom extension](#CustomExtension) 사이에서 정보를 주고 받을 때 사용하는 메시지입니다. 자세한 내용은 [Custom extension 메시지](/CEK/References/CEK_API.md#CustomExtMessage) 문서를 참조합니다.

### Discovery 기능 {#Discovery}
사용자 계정에 등록된 IoT 기기 목록을 클라이언트 기기에 제공하는 기능입니다. 자세한 내용은 [Discovery 제공하기](/CEK/Guides/Build_Clova_Home_Extension.md#ProvideDeviceDiscovery) 문서를 참조합니다.

### Downchannel {#Downchannel}
Downchannel은 클라이언트가 [Clova Interface Connect](#CIC)로부터 지시 메시지를 받을 때 사용되는 [HTTP/2](#HTTP2) 스트림입니다. 자세한 내용은 [CIC 연결하기](/CIC/Guides/Interact_with_CIC.md#ConnectToCIC) 문서를 참조합니다.

### Extension {#Extension}
[Clova extension](#ClovaExtension)의 다른 표현

### Skill 스토어 {#SkillStore}

Skill이 사용자에게 제공될 수 있도록 만든 플랫폼입니다.

### Skill 스토어 홈 {#SkillStoreHome}

Skill 스토어에 등록된 skill이 표시되는 페이지입니다. Clova 앱의 **확장 서비스 관리** 메뉴를 지칭하는 용어입니다.

### Extension 페이지 {#ExtensionPage}

Extension 스토어 홈 (**확장 서비스 관리** 메뉴)에서 특정 extension을 선택했을 때 표시되는 페이지로 extension에 대한 자세한 설명을 제공하는 페이지입니다.

### HTTP/2 {#HTTP2}
HTTP 프로토콜의 두 번째 버전이다. [SPDY](https://en.wikipedia.org/wiki/SPDY)에 기반하고 있으며, 국제 인터넷 표준화 기구(IETF)에서 개발되고 있다. 1997년 RFC 2068로 표준이 된 HTTP 1.1을 개선한 것으로, 2014년 12월 표준안 제안(Proposed Standard)으로 고려되어, 2015년 2월 17일 IESG에서 제안안으로 승인되었다. 2015년 5월, <a href="https://tools.ietf.org/html/rfc7540" target="_blank">RFC 7540</a>]로 공개되었다.

### Intent {#Intent}
Intent는 Clova extension이 처리할 사용자의 요청을 구별한 범주이며, custom intent와 built-in intent로 나뉩니다. [Custom extension](#CustomExtension)을 구현하기 전에 먼저 intent의 집합으로 구성된 [interaction 모델](#InteractionModel)을 정의해야 합니다. 자세한 내용은 [interaction 모델 정의](/Design/Design_Guideline_For_Extension.md#DefineInteractionModel)를 참조합니다.

### IntentRequest {#IntentRequest}

사용자의 요청이 분석된 결과([Intent](#Intent))를 [custom extension](#CustomExtension)으로 전달할 때 사용되는 요청 메시지 타입입니다. 자세한 내용은 [Custom extension 요청 처리하기](/CEK/Guides/Build_Custom_Extension.md#HandleCustomExtensionRequest) 문서를 참조합니다.

### Interaction 모델 {#InteractionModel}
[Custom extension](#CustomExtension)이 음성으로부터 인식된 사용자의 요청을 extension에 전달하기 위해 정형화된 포맷(JSON)으로 바꿔주는 규칙을 명세한 것입니다. 자세한 내용은 [interaction 모델 정의](/Design/Design_Guideline_For_Extension.md#DefineInteractionModel) 문서를 참조합니다.

### LaunchRequest {#LaunchRequest}
사용자가 특정 모드나 특정 [custom extension](#CustomExtension)을 사용하기로 선언한 것을 알리기 위해 보내는 요청 메시지입니다. 자세한 내용은 [Custom extension 요청 처리하기](/CEK/Guides/Build_Custom_Extension.md#HandleCustomExtensionRequest) 문서를 참조합니다.

### OAuth 2.0
접근 권한을 위임하기 위한 공개 표준으로 인터넷 사용자가 다른 웹 서비스나 응용 프로그램에 사용자 계정에 접근할 수 있는 권한을 부여하는 규약입니다. Clova 플랫폼에서는 클라이언트가 [Clova access token](#ClovaAccessToken)을 획득하거나 사용자가 특정 extension을 사용 시 자신의 [계정을 연결](/CEK/Guides/Link_User_Account.md)할 때 사용됩니다. 자세한 내용은 [https://tools.ietf.org/html/rfc6749](https://tools.ietf.org/html/rfc6749)를 참고합니다.

### SessionEndedRequest {#SessionEndedRequest}
사용자가 특정 모드나 특정 [custom extension](#CustomExtension)의 사용을 중지하기로 선언한 것을 알리기 위해 사용되며 요청 메시지에 포함됩니다. 자세한 내용은 [Custom extension 요청 처리하기](/CEK/Guides/Build_Custom_Extension.md#HandleCustomExtensionRequest) 문서를 참조합니다.

### Skill {#Skill}

Clova가 제공하는 확장 기능을 의미합니다. Skill을 사용자에게 제공하려면 [Clova extension](#ClovaExtension)을 개발해야 합니다.

### Slot {#Slot}
[Intent](#Intent)에 선언된 요청을 처리할 때 필요한 정보이며, intent를 정의할 때 함께 정의해야 합니다. Clova는 사용자 요청을 분석한 후 slot에 해당하는 정보를 추출하게 됩니다. 자세한 내용은 [interaction 모델 정의](/Design/Design_Guideline_For_Extension.md#DefineInteractionModel)를 참조합니다.

### 대화 ID {#DialogID}
대화 ID는 사용자가 새로운 발화를 시작할 때마다 생성되며, 클라이언트가 [Recognize](/CIC/References/CICInterface/SpeechRecognizer.md#Recognize) [이벤트 메시지](#Event)를 [Clova Interface Connect](#CIC)에 전달할 때 포함됩니다. 대화 ID는 서버측 응답을 내려줄 때 어떤 이벤트 메시지에 대한 응답인지 연결할 때 사용되며, [지시 메시지](#Directive)에도 포함됩니다. 클라이언트는 지시 메시지에 포함된 대화 ID를 보고 어떤 이벤트 메시지의 응답인지 판단해야 하며, 만약 클라이언트가 현재 가지고 있는 대화 ID와 지시 메시지의 대화 ID가 다르면 수신한 지시 메시지를 무시해야 합니다. 자세한 내용은 [대화 모델](/CIC/CIC_Overview.md#DialogModel) 문서를 참조합니다.

### 맥락 정보 (Context) {#Context}
맥락 정보(Context)는 클라이언트의 다양한 상태 정보를 의미하며 [context objects](#ContextObjects)로 표현됩니다. 자세한 내용은 [맥락 정보(Context)](/CIC/References/Context_Objects.md) 문서를 참조합니다.

### 메시지 ID {#MessageID}
메시지 ID는 개개의 메시지를 구분하기 위한 식별자이며, [이벤트 메시지](#Event)와 [지시 메시지](#Directive)는 모두 개개의 메시지 ID를 가집니다.

### 사용자 계정 연결 (Account Linking) {#AccountLinking}
사용자의 계정 인증(authentication)이 필요한 외부 서비스를 [extension](#ClovaExtension)이 제공해야 할 때 사용됩니다. 자세한 내용은 [사용자 계정 연결하기](/CEK/Guides/Link_User_Account.md) 문서를 참조합니다.

### 사용자 발화 예시 {#UserUtteranceExample}

사용자의 요청 발화가 어떤 식으로 입력될 수 있는지 예문을 표현한 목록입니다. [Intent](#Intent)별로 복수의 사례를 정의할 수 있으며, 예문에는 [slot](#Slot)이 표시됩니다. 자세한 내용은 [interaction 모델 정의](/Design/Design_Guideline_For_Extension.md#DefineInteractionModel)를 참조합니다.

### 세션 ID {#SessionID}
세션 ID는 [extension](#ClovaExtension)이 사용자 요청의 맥락을 구분하기 위한 세션 식별자입니다. 일반적으로 일회성의 사용자 요청은 매번 달라지는 세션 ID를 가지지만, 특정 모드나 연속되는(multi-turn) 사용자의 요청이면 같은 세션 ID를 가집니다. 이 세션 ID는 [Clova Extensions Kit](#CEK)가 extension에 사용자 요청을 전달할 때 생성됩니다. 세션 ID가 유지되는 때는 [LaunchRequest](#LaunchRequest)와 같은 요청을 받거나 extension이 필요에 의해 `response.shouldEndSession` 필드를 `false`로 설정했을 때입니다. 자세한 내용은 [Custom extension 만들기](/CEK/Guides/Build_Custom_Extension.md) 문서를 참조합니다.

### 이벤트 메시지 (Event) {#Event}
이벤트 메시지는 클라이언트에서 [Clova Interface Connect](#CIC)로 전달하는 메시지이며, 사용자 요청(음성 입력)을 전달하거나 클라이언트의 상태 값이 변경된 것을 알릴 때 이 메시지를 전송합니다.

### 지시 메시지 (Directive) {#Directive}
지시 메시지는 [Clova Interface Connect](#CIC)가 클라이언트의 행동을 제어하도록 명세한 메시지입니다. 지시 메시지는 클라이언트가 요청한 이벤트 메시지에 응답을 하거나 특정 조건에 의해 클라이언트로 정보를 전달할 때 사용됩니다.

### 클라이언트 인증 정보 {#ClientCredentialInfo}
[Clova developer console](#ClovaDeveloperConsole)를 통해 클라이언트를 등록하고 획득한 인증 정보이며, [Clova access token](#ClovaAccessToken)을 획득하는데 사용됩니다. 자세한 내용은 [Clova access token 생성하기](/CIC/Guides/Interact_with_CIC.md#CreateClovaAccessToken) 문서를 참조합니다.