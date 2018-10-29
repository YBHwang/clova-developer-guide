# 문서 정보
이 문서는 Clova가 제공하는 CIC와 CEK 플랫폼에 대한 개발 가이드 및 API 레퍼런스를 제공합니다. 대상 독자는 CIC를 사용하여 Clova 서비스와 연동되는 전자 기기, 앱을 개발하려는 클라이언트 개발자와 CEK를 사용하여 온라인 콘텐츠 및 서비스를 제공하려는 Extension 개발자입니다.

<div class="note">
  <p><strong>Note!</strong></p>
  <p>Clova는 개발이 계속 진행되고 있습니다. 따라서, 문서의 내용은 언제든지 변경될 수 있습니다.</p>
</div>

## 연락처
문서와 관련하여 궁금한 사항은 지정된 Clova 제휴 담당자나 <a href="{{ book.ServiceEnv.DeveloperCenterForumURL }}" target="_blank">{{ book.ServiceEnv.DeveloperCenterName }} 포럼</a>에 문의합니다.

## 문서 변경 이력

이 문서의 변경 이력은 다음과 같습니다.

<table>
  <thead>
    <tr>
      <th style="width:12%">신규 버전 규칙</th><th style="width:12%">이전 버전 규칙</th><th style="width:16%">배포 일자</th><th style="width:70%">이력 사항</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>v3.42.0</td><td>미적용</td><td>2018-10-20</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/CICInterface/DeviceControl.md">DeviceControl</a> 네임스페이스에 블루투스 기기를 재탐지(rescan)하거나 블루투스 기기의 제거하게 하는 <a href="/CIC/References/CICInterface/DeviceControl.md#BtDelete">DeviceControl.BtDelete</a>와 <a href="/CIC/References/CICInterface/DeviceControl.mdBtRescan">DeviceControl.BtRescan</a> 지시 메시지 추가</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/DeviceControl.md">DeviceControl</a> 네임스페이스에 블루투스 기기를 통해 음악을 재생하도록 하는 <a href="/CIC/References/CICInterface/DeviceControl.md#BtPlay">DeviceControl.BtPlay</a> 지시 메시지 추가</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/DeviceControl.md">DeviceControl</a> 네임스페이스의 <a href="/CIC/References/CICInterface/DeviceControl.md#BtConnect">DeviceControl.BtConnect</a>와 <a href="/CIC/References/CICInterface/DeviceControl.md#BtDisconnect">DeviceControl.BtDisconnect</a> 지시 메시지에 필드를 추가하여 특정 역할을 가진 기기나 특정 기기를 연결하거나 연결 해지할 수 있게 함</li>
          <li>[CIC] <a href="/CIC/References/Context_Objects.md#DeviceState">Device.DeviceState</a> 맥락 객체의 <a href="/CIC/References/Context_Objects.md#BluetoothInfoObject">BluetoothInfoObject</a>에 connecting, pairing, playerinfo, scanning 필드를 추가하여 클라이언트의 블루투스 관련 상태 정보를 추가함</li>
          <li>[CEK] Clova Home extension API <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.md">공유 객체</a> <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject">ApplianceInfoObject</a>의 Remarks에 다음의 내용을 업데이트함
            <ul>
              <li>의류 관리기 타입(CLOTHESCAREMACHINE)과 의류 건조기 타입(CLOTHESDRYER)에 GetPhase 동작 추가</li>
              <li>냉장고 타입(REFRIGERATOR)에 ReleaseMode 동작 추가</li>
              <li>Actions에 빠져있던 GetEstimateConsumption 동작 추가</li>
            </ul>
          </li>
          <li>[CEK] Clova Home extension API <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.md">공유 객체</a> <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.md#ModeInfoObject">ModeInfoObject</a>의 Operation Modes에서 환풍기(VENTILATOR) 타입 기기에 "ventilating" 모드 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.41.0</td><td>미적용</td><td>2018-10-13</td>
      <td>
        <ul>
          <li>[CEK] Clova Home extension API에 <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetEstimateConsumptionRequest">GetEstimateConsumptionRequest</a>, <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetEstimateConsumptionResponse">GetEstimateConsumptionResponse</a> 추가</li>
          <li>[CEK] Clova Home extension 메시지의 <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.md">공유 객체</a> <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.md#ModeInfoObject">ModeInfoObject</a>에 AIRPURIFIER, HUMIDIFIER, VENTILATOR 타입 기기의 모드 추가</li>
          <li>[CEK] Clova Home extension API의 <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetCurrentSittingStateRequest">GetCurrentSittingStateRequest</a>에 period 필드 추가</li>
          <li>[Dev. Console] <a href="/DevConsole/Guides/CEK/Register_Extension.md#InputExtensionInfo">Extension 기본 정보 입력</a>에 호출 이름을 한 개 이상 최대 세 개까지 등록할 수 있음을 명시</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.40.1</td><td>미적용</td><td>2018-10-05</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/CIC_API.md#Error">CIC 오류 메시지</a>의 구조 및 예제를 실제 구현에 맞게 교정</li>
          <li>[CEK] Clova Home extension API의 <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.md#DecrementFanSpeedRequest">DecrementFanSpeedRequest</a>와 <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.md#IncrementFanSpeedRequest">IncrementFanSpeedRequest</a>에서 불필요한 설명 제거</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.40.0</td><td>미적용</td><td>2018-09-21</td>
      <td>
        <ul>
          <li>[CIC] 콘텐츠의 MIME type을 명시하기 위해 <a href="/CIC/References/CICInterface/AudioPlayer.md">AudioPlayer</a> <a href="/CIC/References/CICInterface/AudioPlayer.md#AudioStreamInfoObject">AudioStreamInfoObject</a>의 payload에 format 필드를 추가</li>
          <li>[CIC] 미디어 콘텐츠 재생 시 좋아요 및 구독 기능을 처리하기 위해 <a href="/CIC/References/CICInterface/TemplateRuntime.md">TemplateRuntime</a> 네임스페이스에 SubscribeCommandIssued, UnsubscribeCommandIssued 이벤트 메시지와 UpdateLike, UpdateSubscribe 지시 메시지에 추가</li>
          <li>[CIC] 미디어 콘텐츠 재생 시 표시해야 하는 버튼이나 제어 UI의 종류를 <a href="/CIC/References/CICInterface/TemplateRuntime.md#RenderPlayerInfo">TemplateRuntime.RenderPlayerInfo</a> 지시 메시지에 추가</li>
          <li>[CEK] Clova Home extension API의 <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject">지원 기기</a> 설명 중 Actions 항목에 빠진 동작(GetCleaningCycle, GetOpenState, ReleaseMode)을 추가</li>
          <li>[CEK] Clova에서 전달하는 메시지의 검증을 위해 <a href="/CEK/References/CEK_API.md#HTTPHeader">HTTP 헤더</a>에 SignatureCEK 필드 설명을 추가하고 <a href="/CEK/Guides/Build_Custom_Extension.md">custom extension 만들기</a> 문서와 <a href="/CEK/Guides/Build_Clova_Home_Extension.md">Clova Home extension 만들기</a> 문서에 각각 요청 메시지 검증 절을 추가</li>
          <li>[CEK] Clova Home extension API의 <a href="/CEK/References/ClovaHomeInterface/Error_Interfaces.md">오류 메시지(Error)</a>에 <a href="/CEK/References/ClovaHomeInterface/Error_Interfaces.md#ActionTemporarilyBlockedError">ActionTemporarilyBlockedError</a>와 <a href="/CEK/References/ClovaHomeInterface/Error_Interfaces.md#ValueNotSupportedError">ValueNotSupportedError</a> 오류 메시지를 추가</li>
          <li>[CEK] Clova Home extension API의 <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.md">공유 객체</a>에 <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.md#RatioInfoObject">RatioInfoObject</a> 객체 추가</li>
          <li>[Common] 일부 잘못된 코드 예제를 수정</li>
          <li>[Common] 일부 잘못된 링크를 수정</li>
          <li>[Common] 일부 사용자 접점에 있는 Extension 표기를 Skill로 변경(UI 캡처 이미지 함께 업데이트)</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.39.0</td><td>미적용</td><td>2018-09-07</td>
      <td>
        <ul>
          <li>[Design] Extension 디자인 가이드라인의 <a href="/Design/Design_Guideline_For_Extension.md#SupportedAudioCompressionFormat">플랫폼 지원 오디오 압축 포맷</a>에 오디오 콘텐츠별 음질 관련 속성과 음량에 대한 권고 사항 추가</li>
          <li>[CIC] <a href="/CIC/Guides/Implement_Client_Features.md#HandleAlerts">알람 처리하기</a> 절의 링크 오류, 코드 예제 표기 오류 수정</li>
          <li>[Common] 예제 설명 중 "yourdomain.com"으로 표시된 예제를 문서 작성용 도메인 이름인 "example.com"으로 변경</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.38.0</td><td>미적용</td><td>2018-08-29</td>
      <td>
        <ul>
          <li>[Design] <a href="/Design/Design_Guideline_For_Client_Hardware.md">클라이언트 기기 디자인 가이드라인</a>에 <a href="/Design/Design_Guideline_For_Client_Hardware.md#LightColor">조명 색상</a>의 RGB 값 변경</li>
          <li>[CIC] <a href="/CIC/Guides/Implement_Client_Features.md">클라이언트 기능 구현하기</a> 절 추가</li>
          <li>[CEK] Clova Home extension API의 <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject">지원 기기</a> 중 난방기(HEATER)와 온도 조절기(THERMOSTAT) 타입에 GetTargetTemperature 동작 추가</li>
          <li>[CEK] Clova Home extension API의 <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.md">공유 객체</a> 필드 필수/포함 여부 표기 개선</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/AudioPlayer.md">AudioPlayer</a>, <a href="/CIC/References/CICInterface/TemplateRuntime.md">TemplateRuntime</a> 네임스페이스에 일부 필드 업데이트</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.37.2</td><td>미적용</td><td>2018-08-24</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/CICInterface/Alerts.md#StopAlert">Alerts.StopAlert</a> 지시 메시지의 예제에서 오류 수정</li>
          <li>[CIC] 표기에 따른 혼동을 피하기 위해 <a href="/CIC/References/CICInterface/SpeechRecognizer.md#Recognize">SpeechRecognizer.Recognize</a> 지시 메시지의 initiator.inputSource 필드의 설명을 수정</li>
          <li>[CEK] <a href="/CEK/References/CEK_API.md#CustomExtMessage">Custom extension 메시지</a> <a href="/CEK/References/CEK_API.md#CustomExtEventRequest">EventRequest</a> 요청 타입의 예제에서 오류 수정</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.37.1</td><td>미적용</td><td>2018-08-09</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/CIC_Overview.md#DialogModel">대화 모델</a>에 대한 설명을 보완</li>
          <li>[CEK] <a href="/CEK/Guides/Build_Custom_Extension.md#ProvidingMetaDataForDisplay">오디오 콘텐츠의 메타 정보 제공</a> 절에서 일부 오타 수정</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.37.0</td><td>미적용</td><td>2018-07-23</td>
      <td>
        <ul>
          <li>[Design] <a href="/Design/Design_Guideline_For_Client_Hardware.md">클라이언트 기기 디자인 가이드라인</a>의 <a href="/Design/Design_Guideline_For_Client_Hardware.md#SoundEffect">효과음</a> 중 Attending 상태 진입에 대한 효과음 업데이트</li>
          <li>[CIC] <a href="/CIC/References/Clova_Auth_API.md">CIC 인증 API</a>의 <a href="/CIC/References/Clova_Auth_API.md#RequestAuthorizationCode">Authorization code 요청</a> 설명에 423 Locked 상태 코드 추가</li>
          <li>[CEK] Clova Home extension API에서 SetFreezerTargetTemperature, SetFridgeTargetTemperature 동작을 제거하고 이와 관련된 인터페이스를 제거</li>
          <li>[CEK] Clova Home extension API의 <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetTargetTemperatureRequest">SetTargetTemperatureRequest</a>에 endpoint 필드를 추가하고 <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.md#EndpointInfoObject">EndpointInfoObject</a> 객체를 추가</li>
          <li>[CEK] Clova Home extension API의 <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject">지원 기기</a> 중 환풍기(VENTILATOR) 타입에 SetFanSpeed 동작 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.36.0</td><td>미적용</td><td>2018-07-09</td>
      <td>
        <ul>
          <li>[Design] Extension의 <a href="/Design/Design_Guideline_For_Extension.md#DefineInvocationName">이름 정의</a>에 대한 가이드라인 추가</li>
          <li>[Design] Extension의 <a href="/Design/Design_Guideline_For_Extension.md#ContentGuideline">콘텐츠 제공 시 준수 사항</a>에 대한 가이드라인 추가</li>
          <li>[CIC] 클라이언트 기기 설정 정보를 업데이트 및 동기화하기 위해 <a href="/CIC/References/CICInterface/Settings.md">Settings</a> 네임스페이스 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.35.0</td><td>v4.6</td><td>2018-06-25</td>
      <td>
        <ul>
          <li>[Design] Extension의 <a href="/Design/Design_Guideline_For_Extension.md#DecideSoundOutputType">응답 유형</a>에 대한 가이드라인 추가</li>
          <li>[CEK] Custom extension 만들기 문서에 <a href="/CEK/Guides/Build_Custom_Extension.md#ProvideAudioContent">오디오 콘텐츠 제공하기</a> 절 추가</li>
          <li>[CEK] Custom extension 메시지의 <a href="/CEK/References/CEK_API.md#CustomExtRequestType">요청 타입</a>에 <a href="/CEK/References/CEK_API.md#CustomExtEventRequest">EventRequest 타입</a> 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.34.2</td><td>v4.5</td><td>2018-06-17</td>
      <td>
        <ul>
          <li>[CIC] 실시간 방송 콘텐츠를 구분하기 위해 <a href="/CIC/References/CICInterface/TemplateRuntime.md#RenderPlayerInfo">TemplateRuntime.RenderPlayerInfo</a>에 isLive 필드 추가</li>
          <li>[CEK] <a href="/CIC/References/Content_Templates.md">Content template</a>의 <a href="/CIC/References/ContentTemplates/Common_Fields.md">공통 필드</a>에 subtitle 필드 추가</li>
          <li>[CEK] 적외선 방식으로 제어되는 기기를 위해 Clova Home extension API <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject">ApplianceInfoObject</a>에 isIr 필드 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.34.1</td><td>v4.4</td><td>2018-05-28</td>
      <td>
        <ul>
          <li>[CEK] Clova Home extension API <a href="/CEK/References/ClovaHomeInterface/Error_Interfaces.md#ConditionsNotMetError">ConditionsNotMetError</a>에 state 필드 추가</li>
          <li>[CEK] Clova Home extension API <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.md#TVChannelInfoObject">TVChannelInfoObject</a>에 서브 채널 정보 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.34.0</td><td>v4.3</td><td>2018-05-21</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/Context_Objects.md#DeviceState">Device.DeviceState</a> 맥락 객체의 <a href="/CIC/References/Context_Objects.md#BluetoothInfoObject">BluetoothInfoObject</a>에 빠진 필드(btlist[].role) 추가</li>
          <li>[CEK] Clova Home extension API에 <a href="/CEK/References/ClovaHomeInterface/Error_Interfaces.md#ValueNotFoundError">ValueNotFoundError</a> 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.33.0</td><td>v4.2</td><td>2018-05-14</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/CICInterface/Clova.md#LaunchURI">LaunchURI</a> 지시 메시지를 DeviceControl 네임스페이스에서 <a href="/CIC/References/CICInterface/Clova.md">Clova</a> 네임스페이스로 이전</li>
          <li>[CEK] HTTP 요청 메시지에 헤더(SignatureCEK, SignatureCEKCertChainUrl) 추가 및 요청 메시지 검증 절 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.32.0</td><td>v4.1</td><td>2018-05-07</td>
      <td>
        <ul>
          <li>[CIC] DeviceControl 네임스페이스에 LaunchURI 지시 메시지 추가</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/DeviceControl.md">DeviceControl</a> 네임스페이스의 <a href="/CIC/References/CICInterface/DeviceControl.md#LaunchApp">LaunchApp</a> 지시 메시지와 <a href="/CIC/References/CICInterface/DeviceControl.md#OpenScreen">OpenScreen</a> 지시 메시지의 지원을 중지(Deprecated)</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.31.0</td><td>v4.0</td><td>2018-04-30</td>
      <td>
        <ul>
          <li>[CEK] Clova Home extension API에 <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetOpenStateRequest">GetOpenStateRequest</a>, <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetOpenStateResponse">GetOpenStateResponse</a> 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.30.0</td><td>v3.9</td><td>2018-04-23</td>
      <td>
        <ul>
          <li>[CEK] Clova Home extension API에 <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.md#ReleaseModeConfirmation">ReleaseModeConfirmation</a>, <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.md#ReleaseModeRequest">ReleaseModeRequest</a> 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.29.0</td><td>v3.8</td><td>2018-04-16</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/CICInterface/SpeechRecognizer.md#Recognize">SpeechRecognizer.Recognize</a> 이벤트 메시지의 wakeWord 필드 설명 및 Audio data 설명 업데이트</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/DeviceControl.md">DeviceControl</a> 네임스페이스에 <a href="/CIC/References/CICInterface/DeviceControl.md#Open">Open</a> 지시 메시지 추가</li>
          <li>[CEK] Clova Home extension API <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetLockStateResponse">GetLockStateResponse</a>에 openState 필드 추가</li>
          <li>[CEK] Clova Home extension API에 <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetCleaningCycleRequest">GetCleaningCycleRequest</a>, <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetCleaningCycleResponse">GetCleaningCycleResponse</a> 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.28.1</td><td>v3.7</td><td>2018-04-09</td>
      <td>
        <ul>
          <li>[CIC] 클라이언트 기기 디자인 가이드라인에서 <a href="Design/Design_Guideline_For_Client_Hardware.md#BootingScreen">부팅 화면</a> 관련 설명 및 예제 이미지를 업데이트</li>
          <li>[CEK] Clova Home extension API <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.md#ColorInfoObject">ColorInfoObject</a>의 brightness 필드의 설명 및 필수/포함 여부 변경</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.28.0</td><td>v3.6</td><td>2018-04-02</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/CICInterface/AudioPlayer.md">AudioPlayer</a> 네임스페이스에 메시지 스펙 추가 및 일부 필드 업데이트
            <ul>
              <li><a href="/CIC/References/CICInterface/AudioPlayer.md#ExpectReportPlaybackState">AudioPlayer.ExpectReportPlaybackState</a> 지시 메시지, <a href="/CIC/References/CICInterface/AudioPlayer.md#ReportPlaybackState">AudioPlayer.ReportPlaybackState 이벤트 메시지</a>{% if book.DocMeta.TargetReaderType == "Internal" %}, <a href="/CIC/References/CICInterface/AudioPlayer.md#RequestPlaybackState">AudioPlayer.RequestPlaybackState</a> 이벤트 메시지, <a href="/CIC/References/CICInterface/AudioPlayer.md#SynchronizePlaybackState">SynchronizePlaybackState 지시 메시지</a>{% endif %} 추가</li>
              <li><a href="/CIC/References/CICInterface/AudioPlayer.md#Play">AudioPlayer.Play</a> 지시 메시지의 payload 필드 내용 업데이트</li>
              <li>ProgressReportXXX, PlayXXX 형식의 이름을 가진 이벤트 필드에 token 필드 값 필수로 추가</li>
            </ul>
          </li>
          <li>[CIC] <a href="/CIC/References/Context_Objects.md#PlaybackState">AudioPlayer.PlaybackState</a> 맥락 객체에 repeatMode 추가</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/PlaybackController.md">PlaybackController</a> 네임스페이스에 총 12건의 메시지 스펙 추가
            <ul>
              <li><a href="/CIC/References/CICInterface/PlaybackController.md#PauseCommandIssued">PlaybackController.PauseCommandIssued</a>, <a href="/CIC/References/CICInterface/PlaybackController.md#PlayCommandIssued">PlaybackController.PlayCommandIssued</a>, <a href="/CIC/References/CICInterface/PlaybackController.md#ResumeCommandIssued">PlaybackController.ResumeCommandIssued</a>, <a href="/CIC/References/CICInterface/PlaybackController.md#SetRepeatModeCommandIssued">PlaybackController.SetRepeatModeCommandIssued</a>, <a href="/CIC/References/CICInterface/PlaybackController.md#StopCommandIssued">PlaybackController.StopCommandIssued</a> 이벤트 메시지 추가</li>
              <li><a href="/CIC/References/CICInterface/PlaybackController.md#ExpectNextCommand">PlaybackController.ExpectNextCommand</a>, <a href="/CIC/References/CICInterface/PlaybackController.md#ExpectPauseCommand">PlaybackController.ExpectPauseCommand</a>, <a href="/CIC/References/CICInterface/PlaybackController.md#ExpectPlayCommand">PlaybackController.ExpectPlayCommand</a>, <a href="/CIC/References/CICInterface/PlaybackController.md#ExpectPreviousCommand">PlaybackController.ExpectPreviousCommand</a>,
<a href="/CIC/References/CICInterface/PlaybackController.md#ExpectResumeCommand">PlaybackController.ExpectResumeCommand</a>, <a href="/CIC/References/CICInterface/PlaybackController.md#ExpectStopCommand">PlaybackController.ExpectStopCommand</a>, <a href="/CIC/References/CICInterface/PlaybackController.md#SetRepeatMode">PlaybackController.SetRepeatMode</a> 지시 메시지 추가</li>
              <li><a href="/CIC/References/CICInterface/PlaybackController.md#TurnOnRepeatMode">PlaybackController.TurnOnRepeatMode</a> 지시 메시지와 <a href="/CIC/References/CICInterface/PlaybackController.md#TurnOffRepeatMode">PlaybackController.TurnOffRepeatMode</a>는 사라질 예정</li>
            </ul>
          </li>
          <li>[CIC] 미디어 스트림을 위한 정보와 재생 목록을 표시하기 위한 재생 메타 정보를 분리하기 위해 <a href="/CIC/References/CICInterface/TemplateRuntime.md">TemplateRuntime</a> 네임스페이스 추가</li>
          <li>[CIC] <a href="/CIC/References/Context_Objects.md#DeviceState">Device.DeviceState</a>의 <a href="/CIC/References/Context_Objects.md#BluetoothInfoObject">BluetoothInfoObject</a>에 scanlist 필드 추가</li>
          <li>[CIC] PIN 코드를 사용하는 외부 블루투스 기기와 연결할 수 있도록 <a href="/CIC/References/CICInterface/DeviceControl.md">DeviceControl</a> 네임 스페이스에 <a href="/CIC/References/CICInterface/DeviceControl.md#BtConnectByPINCode">BtConnectByPINCode</a> 지시 메시지와 <a href="/CIC/References/CICInterface/DeviceControl.md#BtRequestForPINCode">BtRequestForPINCode</a>, <a href="/CIC/References/CICInterface/DeviceControl.md#BtRequestToCancelPinCodeInput">BtRequestToCancelPinCodeInput</a> 이벤트 메시지 추가</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/DeviceControl.md">DeviceControl</a> 네임 스페이스의 <a href="/CIC/References/CICInterface/DeviceControl.md#BtConnect">BtConnect</a> 지시 메시지에 payload 추가</li>
          <li>[CEK] Clova Home extension API에 GetSleepStartTimeRequest 외 9건의 <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.md">Control API</a>와 4건의 <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.md">공유 객체</a> 추가</li>
          <li>[CEK] Clova Home extension API의 <a href="/CEK/References/ClovaHomeInterface/Discovery_Interfaces.md#DiscoverAppliancesResponse">DiscoverAppliancesResponse</a>에 <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.md#CustomCommandInfoObject">CustomCommandInfoObject</a> 추가</li>
          <li>[CEK] Clova Home extension API에서 TimeAmountInfoObject <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.md">공유 객체</a> 제거 및 이에 따른 <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.md">Control API</a>의 일부 내용 변경</li>
          <li>[CEK] Clova Home extension API의 <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject">ApplianceInfoObject</a>에 tags 필드 추가 및 location 필드 설명 변경</li>
          <li>[Dev. Console] Clova developer console의 일부 UI 업데이트 적용</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.27.0</td><td>v3.5</td><td>2018-03-19</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/Context_Objects.md#DeviceState">Device.DeviceState</a>에 <a href="/CIC/References/Context_Objects.md#SoundOutputInfoObject">SoundOutputInfoObject</a> 추가</li>
          <li>[CIC] 사용자가 설정한 임의의 명령을 실행할 수 있는 <a href="/CIC/References/CICInterface/PlaybackController.md#CustomCommandIssued">CustomCommandIssued</a> 이벤트 메시지를 <a href="/CIC/References/CICInterface/PlaybackController.md#CustomCommandIssued">PlaybackController</a> 네임스페이스에 추가</li>
          <li>[CEK] Clova Home extension API에 CloseConfirmation 외 47건의 <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.md">Control API</a>와 약 10종의 <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.md">공유 객체</a> 추가</li>
          <li>[CEK] Clova Home extension API <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject">지원 기기</a> 30종 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.26.0</td><td>v3.4</td><td>2018-03-05</td>
      <td>
        <ul>
          <li>[CIC] <a  href="/CIC/References/CICInterface/SpeechRecognizer.md#Recognize">SpeechRecognizer.Recognize</a> 이벤트 메시지 initiator 필드의 설명을 수정</li>
          <li>[CIC] <a href="/Design/Design_Guideline_For_Client_Hardware.md">클라이언트 기기 디자인 가이드라인</a>에서 클라이언트 상태 중 Hearing 상태의 이름을 Listening으로 수정</li>
          <li>[CIC] 클라이언트 기기 디자인 가이드라인의 <a href="/Design/Design_Guideline_For_Client_Hardware.md#Audio">소리</a>에서 오디오 콘텐츠 타입으로 Feedback 타입을 추가하고 설명에 관련 규칙을 추가</li>
          <li>[CEK] <a href="/CEK/Tutorials/Introduction.md">튜토리얼</a> 페이지에 <a href="/CEK/Tutorials/Use_Builtin_Type_Slots.md">사용자가 입력한 정보 활용하기</a> 페이지 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.25.0</td><td>v3.3</td><td>2018-02-26</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/CICInterface/SpeechRecognizer.md#Recognize">SpeechRecognizer.Recognize</a> 이벤트 메시지 initiator 필드에 deviceUUID 필드를 추가</li>
          <li>[CIC] 알람 동기화와 관련된 <a href="/CIC/References/CICInterface/Alerts.md#RequestSynchronizeAlert">RequestSynchronizeAlert</a> 이벤트 메시지와 <a href="/CIC/References/CICInterface/Alerts.md#SynchronizeAlert">SynchronizeAlert</a> 지시 메시지를 <a href="/CIC/References/CICInterface/Alerts.md">Alerts</a> 네임스페이스에 추가</li>
          <li>[CIC] System 네임스페이스에서 알람 동기화와 관련된 일부 필드를 제거할 예정</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.24.0</td><td>v3.2</td><td>2018-02-19</td>
      <td>
        <ul>
          <li>[CIC] 사용자의 호출을 정확히 판단하기 위해 <a href="/CIC/References/CICInterface/SpeechRecognizer.md#Recognize">SpeechRecognizer.Recognize</a> 이벤트 메시지에 initiator 필드를 추가</li>
          <li>[CIC] 리마인더 및 동작 예약의 내용을 확인하기 위해 <a href="/CIC/References/CICInterface/Alerts.md#SetAlert">Alerts.SetAlert</a> 지시 메시지에 label 필드를 추가</li>
          <li>[CIC] 리마인더 및 동작 예약의 내용을 표시하기 위해 <a href="/CIC/References/ContentTemplates/ActionTimer.md">ActionTimer</a>, <a href="/CIC/References/ContentTemplates/ActionTimerList.md">ActionTimerList</a>, <a href="/CIC/References/ContentTemplates/Reminder.md">Reminder</a>, <a href="/CIC/References/ContentTemplates/ReminderList.md">ReminderList</a> 템플릿에 label 필드를 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.23.0</td><td>v3.1</td><td>2018-02-05</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/CICInterface/AudioPlayer.md#AudioStreamInfoObject">AudioStreamInfoObject</a>의 durationInMilliseconds 필드에 대한 설명 수정</li>
          <li>[CIC] <a href="/CIC/References/ContentTemplates/Atmosphere.md">Atmosphere</a>, <a href="/CIC/References/ContentTemplates/CardList.md">CardList</a>, <a href="/CIC/References/ContentTemplates/Humidity.md">Humidity</a>, <a href="/CIC/References/ContentTemplates/TodayWeather.md">TodayWeather</a>, <a href="CIC/References/ContentTemplates/TomorrowWeather.md">TomorrowWeather</a>, <a href="/CIC/References/ContentTemplates/WeeklyWeather.md">WeeklyWeather</a>, <a href="CIC/References/ContentTemplates/WindSpeed.md">WindSpeed</a> 템플릿에 출처 관련 필드 등 내용 추가</li>
          <li>[CEK] Extension 시작 호출(<a href="CEK/Guides/Build_Custom_Extension.md#HandleLaunchRequest">LaunchRequest</a>)에 대한 설명 수정 및 <a href="/Design/Design_Guideline_For_Extension.md">Extension 디자인 가이드라인 문서 반영</a></li>
          <li>[CEK] CEK와 extension간 통신에 사용되는 <a href="/CEK/CEK_Overview.md#WhatisCEK">HTTP 프로토콜 버전</a> 명시</li>
          <li>[CEK] <a href="/CEK/Tutorials/Introduction.md">튜토리얼</a> 페이지에 <a href="/CEK/Tutorials/Handle_Builtin_Intents.md">기본적인 의사 표현 처리하기</a> 페이지 추가</li>
          <li>[Dev. Console] Extension 서버에서 사용해야 할 <a href="/DevConsole/Guides/CEK/Register_Extension.md#SetServerConnection">포트</a>를 명시</li>
          <li>[Common] 일부 문서 오류 교정</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.22.0</td><td>v3.0</td><td>2018-01-29</td>
      <td>
        <ul>
          <li>[Design] <a href="/Design/Design_Guideline_For_Client_Hardware.md">클라이언트 기기 디자인 가이드라인</a>에 <a href="/Design/Design_Guideline_For_Client_Hardware.md#SoundEffect">Reminder용 효과음</a> 추가</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/Notifier.md">Notifier</a> 네임스페이스에 <a href="/CIC/References/CICInterface/Notifier.md#Notify">Notifier.Notify</a> 이벤트 메시지 추가 및 해당 네임스페이스 메시지의 payload 필드 업데이트</li>
          <li>[CIC] <a href="/CIC/References/Context_Objects.md#SpeechState">SpeechSynthesizer.SpeechState</a> 및 <a href="/CIC/References/CICInterface/SpeechSynthesizer.md">SpeechSynthesizer</a> 네임스페이스에 <a href="/CIC/References/CICInterface/SpeechSynthesizer.md#SpeechFinished">SpeechFinished</a>, <a href="/CIC/References/CICInterface/SpeechSynthesizer.md#SpeechStarted">SpeechStarted</a>, <a href="/CIC/References/CICInterface/SpeechSynthesizer.md#SpeechStopped">SpeechStopped</a> 이벤트 메시지 추가</li>
          <li>[CIC] Multi-turn 대화를 위해 <a href="/CIC/References/CICInterface/TextRecognizer.md">TextRecognizer.Recognize</a> 이벤트 메시지에 speechId, explicit 필드 추가</li>
          <li>[CEK] Clova Home extension 메시지 레퍼런스 중 <a href="/CEK/References/ClovaHomeInterface/Error_Interfaces.md">Error 인터페이스</a>에 <a href="/CEK/References/ClovaHomeInterface/Error_Interfaces.md#NoSuchTargetError">NoSuchTargetError</a>, <a href="/CEK/References/ClovaHomeInterface/Error_Interfaces.md#NotSupportedInCurrentModeError">NotSupportedInCurrentModeError</a>, <a href="/CEK/References/ClovaHomeInterface/Error_Interfaces.md#UnsupportedOperationError">UnsupportedOperationError</a> 그리고 <a href="/CEK/References/ClovaHomeInterface/Error_Interfaces.md#ValueOutOfRangeError">ValueOutOfRangeError</a> 추가</li>
          <li>[Dev. Console] <a href="/DevConsole/Guides/CEK/Register_Extension.md#SetServerConnection">Extension 서버 연동 설정</a> 전 연결 확인하는 방법 추가 및 <a href="/DevConsole/Guides/CEK/Test_Extension.md#TestOnClovaApp">테스터 ID 적용 자동화</a>에 대한 안내 추가</li>
          <li>[Dev. Console] Clova developer console의 일부 UI 업데이트 적용</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.21.0</td><td>v2.9</td><td>2018-01-22</td>
      <td>
        <ul>
          <li>[Design] 플랫폼 지원 오디오 압축 포맷 내용을 <a href="/Design/Design_Guideline_For_Client_Hardware.md#SupportedAudioCompressionFormat">클라이언트 기기 디자인 가이드라인</a>과 <a href="/Design/Design_Guideline_For_Extension.md#SupportedAudioCompressionFormat">extension 디자인 가이드라인</a>에 각각 추가</li>
          <li>[CEK] <a href="/CEK/Tutorials/Introduction.md">튜토리얼</a> 페이지와 <a href="/CEK/Tutorials/Build_Simple_Extension.md">기초적인 extension 만들기</a> 페이지 추가</li>
          <li>[Dev. Console] <a href="/DevConsole/Guides/CEK/Register_Interaction_Model.md#AddCustomSlotType">Built-in intent 목록 표시</a>, <a href="/DevConsole/Guides/CEK/Deploy_Extension.md#InputComplianceInfo">심사 신청</a> 시 심사 요청 메시지 작성을 위한 UI 추가</li>
          <li>[Common] UML 다이어그램의 이미지 포맷 변경</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.20.0</td><td>v2.8</td><td>2018-01-15</td>
      <td>
        <ul>
          <li>[Design] <a href="/Design/Design_Guideline_For_Client_Hardware.md">클라이언트 기기 디자인 가이드라인</a>에 알람, 리마인더, 타이머에 대한 조명 효과 및 효과음 가이드라인 설명 추가 </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.19.0</td><td>v2.7</td><td>2018-01-08</td>
      <td>
        <ul>
          <li>[Design] 플랫폼 구현 상황에 맞게 <a href="/Design/Design_Guideline_For_Extension.md#DefineInteractionModel">built-in intent</a>에 대한 설명 수정</li>
          <li>[CIC] <a href="/CIC/Guides/Implement_Client_Features.md#HandleDelegation">위임된 사용자 요청 처리하기</a> 절 추가 및 <a href="/CIC/References/CICInterface/Clova.md#HandleDelegatedEvent">Clova.HandleDelegatedEvent</a> 지시 메시지와 <a href="/CIC/References/CICInterface/Clova.md#ProcessDelegatedEvent">Clova.ProcessDelegatedEvent</a> 이벤트 메시지 추가</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/PlaybackController.md#NextCommandIssued">PlaybackController.NextCommandIssued</a>와 <a href="/CIC/References/CICInterface/PlaybackController.md#PreviousCommandIssued">PlaybackController.PreviousCommandIssued</a> 이벤트 메시지에 <a href="/CIC/References/Context_Objects.md#PlaybackState">AudioPlayer.PlaybackState</a> 맥락 정보를 포함하도록 설명 추가</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/Alerts.md">Alerts</a> API의 동작 구조에 대한 설명 개선</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/DeviceControl.md">DeviceControl</a> API의 <a href="/CIC/References/CICInterface/DeviceControl.md#DeviceControlWorkFlow">동작 구조</a>에 대한 설명 추가</li>
          <li>[CIC] 일부 content template 및 공유 객체에 대한 오류 교정 내용 수정</li>
          <li>[CEK] <a href="/CEK/Examples/Extension_Examples.md">Extension 예제</a> 페이지 추가</li>
          <li>[Dev. Console] <strong>테스터 ID</strong> 필드 추가에 따른 <a href="/DevConsole/Guides/CEK/Test_Extension.md">Extension 테스트하기</a> 설명 업데이트</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.18.1</td><td>v2.6</td><td>2018-01-02</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/CIC_API.md#EstablishDownchannel">Downchannel 구성</a>절 내용에 429 오류 코드 및 관련 설명 Remarks 항목에 추가</li>
          <li>[CIC] 길찾기 템플릿(CarRoute, TransportationRoute) 제거, 길찾기에 대한 UI 표현이 ImageText 템플릿으로 대체됨.</li>
          <li>[Common] 일부 문서 오류, 오타 수정</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.18.0</td><td>v2.5</td><td>2017-12-18</td>
      <td>
        <ul>
          <li>[Design] <a href="/DevConsole/Guides/CEK/Register_Interaction_Model.md">Interaction 모델 등록하기</a>에서 <a href="/Design/Design_Guideline_For_Extension.md#DefineInteractionModel">interaction 모델 정의</a> 절 내용을 <a href="/Design/Design_Guideline_For_Extension.md">Extension 디자인 가이드라인</a> 문서로 이동</li>
          <li>[Design] <a href="/Design/Design_Guideline_For_Extension.md#DefineInteractionModel">Interaction 모델 정의</a> 절 내용에 <a href="/Design/Design_Guideline_For_Extension.md#UtteranceExample">발화 예시</a>문 작성 가이드라인 추가</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/SpeechRecognizer.md">SpeechRecognizer</a> 인터페이스에서 ExpectSpeechTimedOut 이벤트 메시지 제거</li>
          <li>[CIC] <a href="/CIC/References/Context_Objects.md">맥락 정보(context)</a>에서 Clova.FreetalkState 개체 제거</li>
          <li>[Dev. console] <a href="/DevConsole/Guides/CEK/Test_Extension.md">Extension 테스트하기</a>에 테스트 모드 사용하기 추가</li>
          <li>[Dev. console] UI 개선에 따른 이미지 및 설명 수정</li>
          <li>[Dev. console] <a href="/DevConsole/Guides/CEK/Update_Extension.md">Extension 업데이트하기</a>, <a href="/DevConsole/Guides/CEK/Remove_Extension.md">Extension 중지 및 삭제하기</a> 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.17.0</td><td>v2.4</td><td>2017-12-11</td>
      <td>
        <ul>
          <li>[Design] <a href="/Design/Design_Guideline_For_Extension.md">Extension 디자인 가이드라인</a> 추가</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/AudioPlayer.md">AudioPlayer</a> 인터페이스에 <a href="/CIC/References/CICInterface/AudioPlayer.md#ClearQueue">ClearQueue</a> 지시 메시지 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.16.0</td><td>v2.3</td><td>2017-12-04</td>
      <td>
        <ul>
          <li>[Design] <a href="/Design/Design_Guideline_For_Client_Hardware.md#AudioInterruptionRule">오디오 재생 규칙(audio interruption rule)</a>을 <a href="/Design/Design_Guideline_For_Client_Hardware.md">클라이언트 기기 디자인 가이드라인</a>에 추가</li>
          <li>[Design] <a href="/Design/Design_Guideline_For_Client_Hardware.md">클라이언트 기기 디자인 가이드라인</a>의 이미지 개선</li>
          <li>[CIC] CIC 연동하기의 사전 준비사항에 <a href="/CIC/Guides/Interact_with_CIC.md#UserAgentString">User-Agent string</a>을 추가</li>
          <li>[CIC] <a href="/CIC/References/CIC_API.md">CIC API 레퍼런스</a>의 <a href="/CIC/References/CIC_API.md#SendEvent">이벤트 메시지 전송</a> 절에 412 Precondition Failed 상태 코드 설명 추가</li>
          <li>[CEK] 사용자 multi-turn 대화를 위해 reprompt 필드를 <a href="/CEK/References/CEK_API.md#CustomExtResponseMessage">응답 메시지</a>에 추가</li>
          <li>[CEK] 일부 문서 오류 수정</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.15.0</td><td>v2.2</td><td>2017-11-20</td>
      <td>
        <ul>
          <li>[Design] <a href="/Design/Design_Guideline_For_Client_Hardware.md">클라이언트 기기 디자인 가이드라인</a> 추가</li>
          <li>[CIC] 오디오 콘텐츠 및 이미지 썸네일 표시를 위해 <a href="/CIC/References/ContentTemplates/CardList.md">CardList 템플릿</a>의 subType 값에 Type5, Type6를 추가</li>
          <li>[CEK] Clova Home extension 메시지의 <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.md">공유 객체</a> HeatingModeInfoObject를 <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.md#ModeInfoObject">ModeInfoObject</a>로 이름을 변경하고 범용적인 기기의 운전 모드를 나타내는데 사용하는 객체로 설명을 수정</li>
          <li>[CEK] Clova Home extension 메시지의 <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.md">Control</a> 인터페이스에 <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetCurrentTemperatureRequest">GetCurrentTemperatureRequest</a> 메시지와 <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetCurrentTemperatureResponse">GetCurrentTemperatureResponse</a> 메시지 추가</li>
          <li>[CEK] Clova Home extension 메시지의 <a href="/CEK/References/ClovaHomeInterface/Error_Interfaces.md">Error</a> 인터페이스에 <a href="/CEK/References/ClovaHomeInterface/Error_Interfaces.md#UnsupportedOperationError">UnsupportedOperationError</a> 메시지 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.14.0</td><td>v2.1</td><td>2017-11-13</td>
      <td>
        <ul>
          <li>[CIC] 볼륨 제어 관련 지시 메시지(<a href="/CIC/References/CICInterface/DeviceControl.md#Decrease">DeviceControl.Decrease</a>, <a href="/CIC/References/CICInterface/DeviceControl.md#Increase">DeviceControl.Increase</a>, <a href="/CIC/References/CICInterface/DeviceControl.md#SetValue">DeviceControl.SetValue</a>, <a href="/CIC/References/CICInterface/PlaybackController.md#Mute">PlaybackController.Mute</a>, <a href="/CIC/References/CICInterface/PlaybackController.md#Unmute">PlaybackController.Unmute</a>)의 Remarks 항목에 UX 관련 내용 추가</li>
          <li>[CEK] <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject">ApplianceInfoObject</a>에서 에어컨 타입(AIRCONDITIONER)에 DecrementFanSpeed, IncrementFanSpeed, SetFanSpeed, SetMode actioin을 가습기 타입(HUMIDIFIER)에 SetFanSpeed를 추가 </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.13.0</td><td>v2.0</td><td>2017-11-06</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/CICInterface/SpeechRecognizer.md#KeepRecording">SpeechRecognizer.KeepRecording</a> 지시 메시지 추가</li>
          <li>[CIC] <a href="/CIC/References/Context_Objects.md#Display">Device.Display</a> 맥락 정보 추가</li>
          <li>[CIC] <a href="/CIC/References/ContentTemplates/ActionTimer.md">ActionTimer</a>, <a href="/CIC/References/ContentTemplates/ActionTimerList.md">ActionTimerList</a>, <a href="/CIC/References/ContentTemplates/Alarm.md">Alarm</a>, <a href="/CIC/References/ContentTemplates/AlarmList.md">AlarmList</a>, <a href="/CIC/References/ContentTemplates/Memo.md">Memo</a>, <a href="/CIC/References/ContentTemplates/MemoList.md">MemoList</a>, <a href="/CIC/References/ContentTemplates/Reminder.md">Reminder</a>, <a href="/CIC/References/ContentTemplates/ReminderList.md">ReminderList</a>, <a href="/CIC/References/ContentTemplates/Schedule.md">Schedule</a>, <a href="/CIC/References/ContentTemplates/ScheduleList.md">ScheduleList</a>, <a href="/CIC/References/ContentTemplates/Timer.md">Timer</a>, <a href="/CIC/References/ContentTemplates/TimerList.md">TimerList</a> 템플릿에 token 필드 추가</li>
          <li>[CEK] <a href="/CEK/References/CEK_API.md#CustomExtMessage">Custom extension 메시지</a> 중 요청 메시지에서 context.System.device.displayType 필드의 이름을 context.System.device.display로 바꾸고 하위 필드 구성을 변경</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.12.0</td><td>v1.9</td><td>2017-10-30</td>
      <td>
        <ul>
          <li>[Dev. console] <a href="/DevConsole/ClovaDevConsole_Overview.md">Clova developer console 개요</a> 설명 추가</li>
          <li>[Dev. console] <a href="/DevConsole/Guides/CEK/Register_Extension.md">Extension 등록하기</a> 가이드 추가</li>
          <li>[Dev. console] <a href="/DevConsole/Guides/CEK/Register_Interaction_Model.md">Interaction 모델 등록하기</a> 가이드 추가</li>
          <li>[Dev. console] <a href="/DevConsole/Guides/CEK/Deploy_Extension.md">Extension 배포하기</a> 가이드 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.11.0</td><td>v1.8</td><td>2017-10-23</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/ContentTemplates/Text.md">Text</a> 템플릿에 emotionCode 필드와 motionCode 필드를 추가</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/Alerts.md#SetAlert">Alerts.SetAlert</a> 지시 메시지의 assets[].url 필드 내용 변경</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/AudioPlayer.md#StreamRequested">AudioPlayer.StreamRequested</a> 이벤트 메시지의 예제 오류 수정</li>
          <li>[CEK] <a href="/CEK/References/CEK_API.md#CustomExtMessage">Custom extension 메시지</a> 중 요청 메시지에 context.System.device.displayType 필드 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.10.0</td><td>v1.7</td><td>2017-10-16</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/CICInterface/PlaybackController.md">PlaybackController</a> 네임스페이스에 <a href="/CIC/References/CICInterface/PlaybackController.md#Replay">Replay</a> 지시 메시지 추가</li>
          <li>[CIC] 알람 동기화에 대한 보충 설명을 알람 동작 구조 절에 추가</li>
          <li>[CIC] content 필드를 <a href="/CIC/References/Context_Objects.md#AlertsState">Alert.AlertsState</a> 문맥 정보의 <a href="/CIC/References/Context_Objects.md#AlertInfoObject">AlertInfoObject</a>에서 제거</li>
          <li>[공통] 일부 문서 이미지 수정 및 문서 오류 교정</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.9.0</td><td>v1.6</td><td>2017-10-02</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/CICInterface/Alerts.md">Alerts</a> 네임스페이스 및 알람 관련 인터페이스 추가</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/System.md">System</a> 네임스페이스 및 알람 관련 인터페이스 추가</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/SpeechRecognizer.md#ExpectSpeech">SpeechRecognizer.ExpectSpeech</a> 지시 메시지에 expectContentType 필드 추가</li>
          <li>[CIC] <a href="/CIC/References/Context_Objects.md#DeviceState">Device.DeviceState</a>의 <a href="/CIC/References/Context_Objects.md#VolumeInfoObject">VolumeInfoObject</a>에 warning 필드 추가</li>
          <li>[CIC] <a href="/CIC/References/ContentTemplates/ActionTimer.md">ActionTimer</a>, <a href="/CIC/References/ContentTemplates/ActionTimerList.md">ActionTimerList</a>, <a href="/CIC/References/ContentTemplates/Alarm.md">Alarm</a>, <a href="/CIC/References/ContentTemplates/AlarmList.md">AlarmList</a>, <a href="/CIC/References/ContentTemplates/Memo.md">Memo</a>, <a href="/CIC/References/ContentTemplates/MemoList.md">MemoList</a>, <a href="/CIC/References/ContentTemplates/Reminder.md">Reminder</a>, <a href="/CIC/References/ContentTemplates/ReminderList.md">ReminderList</a>, <a href="/CIC/References/ContentTemplates/Schedule.md">Schedule</a>, <a href="/CIC/References/ContentTemplates/ScheduleList.md">ScheduleList</a>, <a href="/CIC/References/ContentTemplates/Timer.md">Timer</a>, <a href="/CIC/References/ContentTemplates/TimerList.md">TimerList</a> 템플릿 추가</li>
          <li>[CIC] <a href="/CIC/References/ContentTemplates/ImageText.md">ImageText</a> 템플릿의 일부 코드 예제 수정</li>
          <li>[CIC] <a href="/CIC/References/ContentTemplates/Popup.md">Popup 템플릿</a> 일부 필드 수정</li>
          <li>[CIC] <a href="/CIC/Guides/Interact_with_CIC.md#CreateClovaAccessToken">Clova access token 생성하기</a>와 <a href="/CIC/References/Clova_Auth_API.md#RequestAuthorizationCode">Authorization code 요청</a>에 서비스 이용 약관에 대한 내용 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.8.0</td><td>v1.5</td><td>2017-09-25</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/CICInterface/PlaybackController.md">PlaybackController API</a>에 음악 재생 제어용 <a href="/CIC/References/CICInterface/PlaybackController.md#NextCommandIssued">PlaybackController.NextCommandIssued</a> 이벤트 메시지와 <a href="/CIC/References/CICInterface/PlaybackController.md#PreviousCommandIssued">PlaybackController.PreviousCommandIssued</a> 이벤트 메시지 추가</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/SpeechRecognizer.md#ExpectSpeech">SpeechRecognizer.ExpectSpeech</a> 지시 메시지에 expectSpeechId 필드를 <a href="/CIC/References/CICInterface/SpeechRecognizer.md#Recognize">SpeechRecognizer.Recognize</a> 이벤트 메시지에 speechId와 explicit 필드를 각각 추가</li>
          <li>[CIC] <a href="/CIC/References/ContentTemplates/Popup.md">Popup 템플릿</a> 추가</li>
          <li>[CEK] Clova Home extension API에 ChargeConfirmation 외 33건의 <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.md">Control API</a> 추가</li>
          <li>[CEK] Clova Home extension API <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject">지원 기기</a> 6종 추가 및 location 필드 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.7.0</td><td>v1.4</td><td>2017-09-18</td>
      <td>
        <ul>
          <li>[CIC] DeviceControl API에 <a href="/CIC/References/CICInterface/DeviceControl.md#ExpectReportState">DeviceControl.ExpectReportState</a> 지시 메시지, <a href="/CIC/References/CICInterface/DeviceControl.md#ReportState">DeviceControl.ReportState</a> 이벤트 메시지, <a href="/CIC/References/CICInterface/DeviceControl.md#RequestStateSynchronization">DeviceControl.RequestStateSynchronization</a> 이벤트 메시지 추가 및 DeviceControl.UpdateDeviceState 지시 메시지를 <a href="/CIC/References/CICInterface/DeviceControl.md#SynchronizeState">DeviceControl.SynchronizeState</a>로 이름 변경</li>
          <li>[CIC] <a href="/CIC/References/ContentTemplates/Text.md">Text</a> 템플릿에 item3 필드 추가</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/AudioPlayer.md#Play">AudioPlayer.Play</a> 지시 메시지에 출처 정보 관련 source 필드 추가</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/AudioPlayer.md#AudioStreamInfoObject">AudioStreamInfoObject</a>에 durationInMilliseconds 필드 추가 </li>
          <li>[CIC] Notifier 네임스페이스 및 <a href="/CIC/References/CICInterface/Notifier.md#ClearIndicator">ClearIndicator</a>, <a href="/CIC/References/CICInterface/Notifier.md#SetIndicator">SetIndicator</a> 지시 메시지 추가</li>
          <li>[CIC] <a href="/CIC/References/ContentTemplates/Atmosphere.md">대기 정보(Atmosphere) 템플릿</a> 추가</li>
          <li>[CIC] 라이선스 이슈에 따른 날씨 템플릿의 bgClipURL 필드 사용 불가 문구 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.6.0</td><td>v1.3</td><td>2017-09-11</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/CICInterface/SpeechRecognizer.md#ExpectSpeech">SpeechRecognizer.ExpectSpeech</a> 지시 메시지에 explicit 필드 추가</li>
          <li>[CIC] <a href="/CIC/References/Content_Templates.md">Content template</a>에 <a href="/CIC/References/ContentTemplates/Common_Fields.md">공통 필드</a> 스펙 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.5.0</td><td>v1.2</td><td>2017-09-04</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/CICInterface/Clova.md#Help">Clova.Help</a> 지시 메시지 추가</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/DeviceControl.md#LaunchApp">DeviceControl.LaunchApp</a> 지시 메시지 추가</li>
          <li>[CIC] TextRecognizer 네임스페이스 및 <a href="/CIC/References/CICInterface/TextRecognizer.md">TextRecognizer.Recognize</a> 이벤트 메시지 추가</li>
          <li>[CIC] <a href="/CIC/References/CIC_API.md">CIC API</a>, <a href="/CEK/References/CEK_API.md">CEK API</a>의 목차, 설명 재작성</li>
          <li>[CIC] CIC API 내용 업데이트: 요청/응답 헤더의 Status code 추가, REST API reference 문서 포맷 적용</li>
          <li>[기타] 일부 문서 오류 수정</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.4.0</td><td>v1.1</td><td>2017-08-28</td>
      <td>
        <ul>
          <li>[CIC] 셋톱박스용 TV 채널 정보 스펙과 전원 상태 정보 스펙을 <a href="/CIC/References/Context_Objects.md#DeviceState">Device.DeviceState</a>와 <a href="/CIC/References/CICInterface/DeviceControl.md">DeviceControl API</a>에 추가</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/DeviceControl.md">DeviceControl API</a>에서 target으로 사용되는 값 일부 추가 및 변경: power, energysave, screenbrightness</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/DeviceControl.md">DeviceControl API</a>의 SetPoint를 <a href="/CIC/References/CICInterface/DeviceControl.md#SetValue">SetValue</a>로 이름 변경</li>
          <li>[CIC] <a href="/CIC/References/Clova_Auth_API.md">Clova 인증 API</a> 내용 업데이트 - 요청/응답 헤더와 Status code 추가, REST API reference 문서 포맷 적용</li>
          <li>[CEK] <a href="/CEK/References/ClovaHomeInterface/Error_Interfaces.md#ValueOutOfRangeError">ValueOutOfRangeError</a>를 Clova Home의 Error 인터페이스에 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.3.0</td><td>v1.0</td><td>2017-08-21</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/Guides/Interact_with_CIC.md#ManageConnection">Access token 갱신</a>절 추가 및 /token API 내용 업데이트</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.2.0</td><td>v0.9</td><td>2017-08-14</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/CIC_Overview.md#DialogModel">대화 모델</a> 설명 추가</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/DeviceControl.md">DeviceControl</a> API 추가</li>
          <li>[CIC] <a href="/CIC/References/Context_Objects.md">Device.DeviceState</a> payload 필드 추가: airplane, battery, bluetooth, brightness, flashLight, gps, powerSavingMode, soundMode, volume, wifi</li>
          <li>[CEK] <a href="/CEK/Guides/Build_Custom_Extension.md#DoMultiturnDialog">Multi-turn 대화 수행하기</a>절 추가 및 sessionAttributes 필드 설명 업데이트</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.1.0</td><td>v0.8</td><td>2017-08-04</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/CICInterface/Clova.md#Hello">Clova.Hello</a> 지시 메시지 추가</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/AudioPlayer.md#Play">AudioPlayer.Play</a> 지시 메시지의 AudioItem 객체에 type 필드 추가</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/AudioPlayer.md#AudioStreamInfoObject">AudioStreamInfoObject</a> 객체에 urlPlayable 필드 추가</li>
          <li>[CIC] <a href="/CIC/References/CIC_API.md#Error">CIC 오류 메시지</a> 스펙 추가</li>
          <li>[CIC] <a href="/CIC/References/CIC_API.md#MultipartMessage">Multipart 메시지</a> 내용 재작성</li>
          <li>[CEK] Clova Home <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject">지원 기기</a> 추가: 공기청정기, 가습기, 셋톱박스, 난방기기</li>
          <li>[CEK] Clova Home <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject">지원 기기</a> 제외: 도어락</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.0.0</td><td>v0.7</td><td>2017-07-28</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/CICInterface/AudioPlayer.md">AudioPlayer</a>의 PlayNext, Stop 제거 (<a href="/CIC/References/CICInterface/PlaybackController.md">PlaybackController</a>에 병합)</li>
          <li>[CIC]  <a href="/CIC/References/CICInterface/PlaybackController.md">PlaybackController</a>의 메시지 이름 변경(Mute, Next, Pause, Previous, Resume, Stop, Unmute, VolumeDown, VolumeUp </li>
          <li>[CIC] 길찾기 템플릿 추가: CarRoute, TransportationRoute</li>
          <li>[CIC] 날씨 템플릿 추가: <a href="/CIC/References/ContentTemplates/Humidity.md">Humidity</a>, <a href="/CIC/References/ContentTemplates/TodayWeather.md">TodayWeather</a>, <a href="/CIC/References/ContentTemplates/TomorrowWeather.md">TomorrowWeather</a>, <a href="/CIC/References/ContentTemplates/WeeklyWeather.md">WeeklyWeather</a>, <a href="/CIC/References/ContentTemplates/WindSpeed.md">WindSpeed</a></li>
          <li>[CEK] <a href="/CEK/Guides/Build_Clova_Home_Extension.md">Clova Home extension 문서</a> 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v2.2.1</td><td>v0.6</td><td>2017-07-14</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/CICInterface/AudioPlayer.md#AudioStreamInfoObject">AudioStreamInfoObject</a> 객체 beginAtInMilliseconds 필드 내용 추가</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v2.2.0</td><td>v0.5</td><td>2017-07-07</td>
      <td>
        <ul>
          <li>[CEK] <a href="/CEK/References/CEK_API.md#CustomExtResponseMessage">Custom extension 응답 메시지</a>의 <a href="/CEK/References/CEK_API.md#CustomExtResponseMessage">outputSpeech</a> 객체 구성 업데이트 반영</li>
          <li>[공통] <a href="/Glossary.md">용어집 추가</a></li>
          <li>CEK 메시지 포맷 파트의 목차 업데이트</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v2.1.0</td><td>v0.4</td><td>2017-07-03</td>
      <td>
        <ul>
          <li>[CEK] CEK 문서 이미지 내용 업데이트</li>
          <li>[공통] 문서 리뷰 결과 반영</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v2.0.0</td><td>v0.3</td><td>2017-06-19</td>
      <td>
        <ul>
          <li>[CEK] CEK 문서 파트 작성</li>
          <li>[CIC] <a href="/CIC/Guides/Interact_with_CIC.md#ManageConnection">연결 관리하기</a> 업데이트 (HTTP Ping 프레임을 사용할 수 없을 때)</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v1.1.0</td><td>v0.2</td><td>2017-06-08</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/Guides/Interact_with_CIC.md">CIC 연동하기</a>에 <a href="/CIC/Guides/Interact_with_CIC.md#ManageConnection">연결 관리하기</a> 추가 (HTTP Ping)</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v1.0.0</td><td>v0.1</td><td>2017-05-29</td>
      <td>
        <ul>
          <li>[CIC] CIC 문서 파트 작성</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>
