# README
This document is a developer guide and API reference for CIC and CEK platforms. The target audiences of this document are client developers using CIC to develop electronic devices and apps that link with Clova services and extension developers using CEK to provide online content and services.

<div class="note">
  <p><strong>Note!</strong></p>
  <p>Clova is under continuous development. Thus, the information in this document is subject to change at any time.</p>
</div>

## Contacts
For any inquiries about this document, contact the Clova partnership team or put your query in our <a href="{{ book.ServiceEnv.DeveloperCenterForumURL }}" target="_blank">{{ book.ServiceEnv.DeveloperCenterName }}forum</a>.

## Document revision history

The revision history of this document is as follows:

<table>
  <thead>
    <tr>
      <th style="width:10%">New version rules</th><th style="width:10%">Previous version rules</th><th style="width:15%">Release date</th><th style="width:75%">History</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>v3.41.0</td><td>Not applied</td><td>10/13/2018</td>
      <td>
        <ul>
          <li>[CEK] Added <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.html#GetEstimateConsumptionRequest">GetEstimateConsumptionRequest</a> and <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.html#GetEstimateConsumptionResponse">GetEstimateConsumptionResponse</a> to the Clova Home extension API</li>
          <li>[CEK] Added the modes of AIRPURIFIER, HUMIDIFIER and VENTILATOR type appliance to <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html#ModeInfoObject">ModeInfoObject</a> that is a <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html">shared object</a> of the Clova Home extension message</li>
          <li>[CEK] Added a period field to <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.html#GetCurrentSittingStateRequest">GetCurrentSittingStateRequest</a> of the Clova Home extension API</li>
          <li>[Dev. Console] Specified that at least one and up to three invocation names can be registered when <a href="/DevConsole/Guides/CEK/Register_Extension.html#InputExtensionInfo">entering basic extension information</a></li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.40.1</td><td>Not applied</td><td>2018-10-05</td>
      <td>
        <ul>
          <li>[CIC] Emended the structure and examples of <a href="/CIC/References/CIC_API.html#Error">CIC error messages</a> according to the actual implementation</li>
          <li>[CEK] Removed unnecessary description in the <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.html#DecrementFanSpeedRequest">DecrementFanSpeedRequest</a> and the <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.html#IncrementFanSpeedRequest">IncrementFanSpeedRequest</a> of Clova Home extension API</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.40.0</td><td>Not applied</td><td>2018-09-21</td>
      <td>
        <ul>
          <li>[CIC] Added the format field to the payload of <a href="/CIC/References/CICInterface/AudioPlayer.html">AudioPlayer</a> <a href="/CIC/References/CICInterface/AudioPlayer.html#AudioStreamInfoObject">AudioStreamInfoObject</a> to specify the MIME type of contents</li>
          <li>[CIC] Added SubscribeCommandIssued and UnsubscribeCommandIssued events, and UpdateLike and UpdateSubscribe directives to the <a href="/CIC/References/CICInterface/TemplateRuntime.html">TemplateRuntime</a> namespace to handle Like and Subscribe features when playing media contents</li>
          <li>[CIC] Added the button information that must be displayed when playing media contents or the type of UI control to the <a href="/CIC/References/CICInterface/TemplateRuntime.html#RenderPlayerInfo">TemplateRuntime.RenderPlayerInfo</a> directive</li>
          <li>[CEK] Added the actions missing in the Actions items under the description of <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html#ApplianceInfoObject">appliances that are supported</a> by the Clova Home extension API</li>
          <li>[CEK] Added the description of the SignatureCEK field added in the <a href="/CEK/References/CEK_API.html#HTTPHeader">HTTP header</a> to verify that the messages sent from Clova, and added a section on verifying each request message to <a href="/CEK/Guides/Build_Custom_Extension.html">Creating a custom extension</a> and <a href="/CEK/Guides/Build_Clova_Home_Extension.html">Creating a Clova Home extension</a></li>
          <li>[CEK] Added the <a href="/CEK/References/ClovaHomeInterface/Error_Interfaces.html#ActionTemporarilyBlockedError">ActionTemporarilyBlockedError</a> and <a href="/CEK/References/ClovaHomeInterface/Error_Interfaces.html#ValueNotSupportedError">ValueNotSupportedError</a> messages to the <a href="/CEK/References/ClovaHomeInterface/Error_Interfaces.html">error messages</a> of the Clova Home extension API</li>
          <li>[CEK] Added <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html#RatioInfoObject">RatioInfoObject</a> to the <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html">shared objects</a> of the Clova Home extension API</li>
          <li>[Common] Revised some wrong code examples</li>
          <li>[Common] Revised some incorrect links</li>
          <li>[Common] Changed some notations of the word Extension that is at the point of interaction with the end user, to Skill (Also updated the UI capture images)</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.39.0</td><td>Not applied</td><td>2018-09-07</td>
      <td>
        <ul>
          <li>[Design] Added recommendations on attributes and loudness for sound quality by audio content type in the <a href="/Design/Design_Guideline_For_Extension.html#SupportedAudioCompressionFormat">Supported audio compression formats</a> section of Design guidelines for extensions</li>
          <li>[CIC] Revised errors in links and mistakes in code examples in the <a href="/CIC/Guides/Implement_Client_Features.html#HandleAlerts">Handling alerts</a> section</li>
          <li>[Common] Changed "yourdomain.com" used in examples to "example.com," which is the domain name for document preparation</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.38.0</td><td>Not applied</td><td>2018-08-29</td>
      <td>
        <ul>
          <li>[Design] Changed the RGB value of the <a href="/Design/Design_Guideline_For_Client_Hardware.html#LightColor">light colors</a> in the <a href="/Design/Design_Guideline_For_Client_Hardware.html">Design guidelines for client devices</a></li>
          <li>[CIC] Added a section on <a href="/CIC/Guides/Implement_Client_Features.html">Implementing client features</a></li>
          <li>[CEK] Added the GetTargetTemperature action to the heater and thermostat type of <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html#ApplianceInfoObject">appliances that are supported</a> by the Clova Home extension API</li>
          <li>[CEK] Improved the required/included state indicators of <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html">shared objects</a> in the Clova Home extension API</li>
          <li>[CIC] Updated some fields in the <a href="/CIC/References/CICInterface/AudioPlayer.html">AudioPlayer</a> and <a href="/CIC/References/CICInterface/TemplateRuntime.html">TemplateRuntime</a> namespaces</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.37.2</td><td>Not applied</td><td>2018-08-24</td>
      <td>
        <ul>
          <li>[CIC] Revised an error in the example for the <a href="/CIC/References/CICInterface/Alerts.html#StopAlert">Alerts.StopAlert</a> directive</li>
          <li>[CIC] Revised the description on the initiator.inputSource field of the <a href="/CIC/References/CICInterface/SpeechRecognizer.html#Recognize">SpeechRecognizer.Recognize</a> directive to avoid confusion</li>
          <li>[CEK] Revised an error in the example of an <a href="/CEK/References/CEK_API.html#CustomExtEventRequest">EventRequest</a> type of a <a href="/CEK/References/CEK_API.html#CustomExtMessage">custom extension</a></li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.37.1</td><td>Not applied</td><td>2018-08-09</td>
      <td>
        <ul>
          <li>[CIC] Supplemented the description of the <a href="/CIC/CIC_Overview.html#DialogModel">dialogue model</a></li>
          <li>[CEK] Emended typos in the section on <a href="/CEK/Guides/Build_Custom_Extension.html#ProvidingMetaDataForDisplay">Providing audio content metadata for display</a></li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.37.0</td><td>Not applied</td><td>2018-07-23</td>
      <td>
        <ul>
          <li>[Design] Updated the sound effect of entering the attending state among the <a href="/Design/Design_Guideline_For_Client_Hardware.html#SoundEffect">sound effects</a> of the <a href="/Design/Design_Guideline_For_Client_Hardware.html">Design guidelines for client devices</a></li>
          <li>[CIC] Added 423 Locked status code to the section on <a href="/CIC/References/Clova_Auth_API.html#RequestAuthorizationCode">Requesting an authorization code</a> under <a href="/CIC/References/Clova_Auth_API.html">CIC auth API</a></li>
          <li>[CEK] Removed SetFreezerTargetTemperature and SetFridgeTargetTemperature actions in the Clova Home extension API, and the related interfaces</li>
          <li>[CEK] Added the endpoint field to <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.html#SetTargetTemperatureRequest">SetTargetTemperatureRequest</a> of the Clova Home extension API and added <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html#EndpointInfoObject">EndpointInfoObject</a></li>
          <li>[CEK] Added the SetFanSpeed action to the ventilator type of appliance in the <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html#ApplianceInfoObject">appliances supported by the </a>Clova Home extension API</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.36.0</td><td>Not applied</td><td>2018-07-09</td>
      <td>
        <ul>
          <li>[Design] Added a guideline for <a href="/Design/Design_Guideline_For_Extension.html#DefineInvocationName">defining the name</a> of the extension</li>
          <li>[Design] Added a guideline for <a href="/Design/Design_Guideline_For_Extension.html#ContentGuideline">providing contents</a> of the extension</li>
          <li>[CIC] Added the <a href="/CIC/References/CICInterface/Settings.html">Settings</a> namespace to update and synchronize the settings information of the client device</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.35.0</td><td>v4.6</td><td>2018-06-25</td>
      <td>
        <ul>
          <li>[Design] Added a guideline for the <a href="/Design/Design_Guideline_For_Extension.html#DecideSoundOutputType">response types</a> of the extension</li>
          <li>[CEK] Added a section on <a href="/CEK/Guides/Build_Custom_Extension.html#ProvideAudioContent">Providing audio content</a> in Creating a custom extension</li>
          <li>[CEK] Added the <a href="/CEK/References/CEK_API.html#CustomExtEventRequest">EventRequest type</a> to the <a href="/CEK/References/CEK_API.html#CustomExtRequestType">request types</a> of custom extension messages</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.34.2</td><td>v4.5</td><td>2018-06-17</td>
      <td>
        <ul>
          <li>[CIC] Added the isLive field to <a href="/CIC/References/CICInterface/TemplateRuntime.html#RenderPlayerInfo">TemplateRuntime.RenderPlayerInfo</a> to distinguish real-time broadcasting content</li>
          <li>[CEK] Added a subtitle field to the <a href="/CIC/References/ContentTemplates/Common_Fields.html">common field</a> of <a href="/CIC/References/Content_Templates.html">Content template</a></li>
          <li>[CEK] Added the isIr field to <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html#ApplianceInfoObject">ApplianceInfoObject</a> of the Clova Home extension API for appliances controlled by infrared communication</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.34.1</td><td>v4.4</td><td>2018-05-28</td>
      <td>
        <ul>
          <li>[CEK] Added a state field to <a href="/CEK/References/ClovaHomeInterface/Error_Interfaces.html#ConditionsNotMetError">ConditionsNotMetError</a> of the Clova Home extension API</li>
          <li>[CEK] Added subchannel information to <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html#TVChannelInfoObject">TVChannelInfoObject</a> of the Clova Home extension API</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.34.0</td><td>v4.3</td><td>2018-05-21</td>
      <td>
        <ul>
          <li>[CIC] Added the missing field (btlist[].role) in <a href="/CIC/References/Context_Objects.html#BluetoothInfoObject">BluetoothInfoObject</a> of the <a href="/CIC/References/Context_Objects.html#DeviceState">Device.DeviceState</a> context object</li>
          <li>[CEK] Added <a href="/CEK/References/ClovaHomeInterface/Error_Interfaces.html#ValueNotFoundError">ValueNotFoundError</a> to the Clova Home extension API</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.33.0</td><td>v4.2</td><td>2018-05-14</td>
      <td>
        <ul>
          <li>[CIC] Moved the <a href="/CIC/References/CICInterface/Clova.html#LaunchURI">LaunchURI</a> directive from the DeviceControl namespace to the <a href="/CIC/References/CICInterface/Clova.html">Clova</a> namespace</li>
          <li>[CEK] Added HTTP request message headers (SignatureCEK, SignatureCEKCertChainUrl) and a section on Validating a request message</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.32.0</td><td>v4.1</td><td>2018-05-07</td>
      <td>
        <ul>
          <li>[CIC] Added the LaunchURI directive to the DeviceControl namespace</li>
          <li>[CIC] Deprecated the <a href="/CIC/References/CICInterface/DeviceControl.html#LaunchApp">LaunchApp</a> directive and the <a href="/CIC/References/CICInterface/DeviceControl.html#OpenScreen">OpenScreen</a> directive of the <a href="/CIC/References/CICInterface/DeviceControl.html">DeviceControl</a> namespace</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.31.0</td><td>v4.0</td><td>2018-04-30</td>
      <td>
        <ul>
          <li>[CEK] Added <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.html#GetOpenStateRequest">GetOpenStateRequest</a> and <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.html#GetOpenStateResponse">GetOpenStateResponse</a> to the Clova Home extension API</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.30.0</td><td>v3.9</td><td>2018-04-23</td>
      <td>
        <ul>
          <li>[CEK] Added <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.html#ReleaseModeConfirmation">ReleaseModeConfirmation</a> and <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.html#ReleaseModeRequest">ReleaseModeRequest</a> to the Clova Home extension API</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.29.0</td><td>v3.8</td><td>2018-04-16</td>
      <td>
        <ul>
          <li>[CIC] Updated the description of the wakeWord field and audio data of the <a href="/CIC/References/CICInterface/SpeechRecognizer.html#Recognize">SpeechRecognizer.Recognize</a> event</li>
          <li>[CIC] Added the <a href="/CIC/References/CICInterface/DeviceControl.html#Open">Open</a> directive to the <a href="/CIC/References/CICInterface/DeviceControl.html">DeviceControl</a> namespace</li>
          <li>[CEK] Added the openState field description to <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.html#GetLockStateResponse">GetLockStateResponse</a> of the Clova Home extension API</li>
          <li>[CEK] Added <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.html#GetCleaningCycleRequest">GetCleaningCycleRequest</a> and <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.html#GetCleaningCycleResponse">GetCleaningCycleResponse</a> to the Clova Home extension API</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.28.1</td><td>v3.7</td><td>2018-04-09</td>
      <td>
        <ul>
          <li>[CIC] Updated the description and example image for the <a href="Design/Design_Guideline_For_Client_Hardware.html#BootingScreen">bootscreen</a> in the Design guidelines for client devices</li>
          <li>[CEK] Changed the description of the brightness field and required/included state of <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html#ColorInfoObject">ColorInfoObject</a> in the Clova Home extension API</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.28.0</td><td>v3.6</td><td>2018-04-02</td>
      <td>
        <ul>
          <li>[CIC] Added message specifications to the <a href="/CIC/References/CICInterface/AudioPlayer.html">AudioPlayer</a> namespace and updated some fields
            <ul>
              <li>Added the <a href="/CIC/References/CICInterface/AudioPlayer.html#ExpectReportPlaybackState">AudioPlayer.ExpectReportPlaybackState</a> directive, <a href="/CIC/References/CICInterface/AudioPlayer.html#ReportPlaybackState">AudioPlayer.ReportPlaybackState event</a> {% if book.DocMeta.TargetReaderType == "Internal" %}, <a href="/CIC/References/CICInterface/AudioPlayer.html#RequestPlaybackState">AudioPlayer.RequestPlaybackState</a> event, and <a href="/CIC/References/CICInterface/AudioPlayer.html#SynchronizePlaybackState">SynchronizePlaybackState directive</a> {% endif %}</li>
              <li>Updated the payload field of the <a href="/CIC/References/CICInterface/AudioPlayer.html#Play">AudioPlayer.Play</a> directive</li>
              <li>Added a mandatory token field value to the event fields with name formats ProgressReportXXX and PlayXXX</li>
            </ul>
          </li>
          <li>[CIC] Added repeatMode to the <a href="/CIC/References/Context_Objects.html#PlaybackState">AudioPlayer.PlaybackState</a> context object</li>
          <li>[CIC] Added a total of 12 message specifications to the <a href="/CIC/References/CICInterface/PlaybackController.html">PlaybackController</a> namespace
            <ul>
              <li>Added the <a href="/CIC/References/CICInterface/PlaybackController.html#PauseCommandIssued">PlaybackController.PauseCommandIssued</a>, <a href="/CIC/References/CICInterface/PlaybackController.html#PlayCommandIssued">PlaybackController.PlayCommandIssued</a>, <a href="/CIC/References/CICInterface/PlaybackController.html#ResumeCommandIssued">PlaybackController.ResumeCommandIssued</a>, <a href="/CIC/References/CICInterface/PlaybackController.html#SetRepeatModeCommandIssued">PlaybackController.SetRepeatModeCommandIssued</a>, and <a href="/CIC/References/CICInterface/PlaybackController.html#StopCommandIssued">PlaybackController.StopCommandIssued</a> events</li>
              <li><a href="/CIC/References/CICInterface/PlaybackController.html#ExpectNextCommand">PlaybackController.ExpectNextCommand</a>, <a href="/CIC/References/CICInterface/PlaybackController.html#ExpectPauseCommand">PlaybackController.ExpectPauseCommand</a>, <a href="/CIC/References/CICInterface/PlaybackController.html#ExpectPlayCommand">PlaybackController.ExpectPlayCommand</a>, <a href="/CIC/References/CICInterface/PlaybackController.html#ExpectPreviousCommand">PlaybackController.ExpectPreviousCommand</a>,
<a href="/CIC/References/CICInterface/PlaybackController.html#ExpectResumeCommand">PlaybackController.ExpectResumeCommand</a>, <a href="/CIC/References/CICInterface/PlaybackController.html#ExpectStopCommand">PlaybackController.ExpectStopCommand</a>, and <a href="/CIC/References/CICInterface/PlaybackController.html#SetRepeatMode">PlaybackController.SetRepeatMode</a> directives</li>
              The <li><a href="/CIC/References/CICInterface/PlaybackController.html#TurnOnRepeatMode">PlaybackController.TurnOnRepeatMode</a> and <a href="/CIC/References/CICInterface/PlaybackController.html#TurnOffRepeatMode">PlaybackController.TurnOffRepeatMode</a> directives are scheduled to be removed</li>
            </ul>
          </li>
          <li>[CIC] Added the <a href="/CIC/References/CICInterface/TemplateRuntime.html">TemplateRuntime</a> namespace to separate the information for streaming media and metadata for displaying the play list</li>
          <li>[CIC] Added the scanlist field to <a href="/CIC/References/Context_Objects.html#BluetoothInfoObject">BluetoothInfoObject</a> of <a href="/CIC/References/Context_Objects.html#DeviceState">Device.DeviceState</a></li>
          <li>[CIC] Added the <a href="/CIC/References/CICInterface/DeviceControl.html#BtConnectByPINCode">BtConnectByPINCode</a> directive, <a href="/CIC/References/CICInterface/DeviceControl.html#BtRequestForPINCode">BtRequestForPINCode</a> event, and <a href="/CIC/References/CICInterface/DeviceControl.html#BtRequestToCancelPinCodeInput">BtRequestToCancelPinCodeInput</a> event to the <a href="/CIC/References/CICInterface/DeviceControl.html">DeviceControl</a> namespace to connect with third-party Bluetooth devices that use PIN codes</li>
          <li>[CIC] Added a payload to the <a href="/CIC/References/CICInterface/DeviceControl.html#BtConnect">BtConnect</a> directive of the <a href="/CIC/References/CICInterface/DeviceControl.html">DeviceControl</a> namespace</li>
          <li>[CEK] Added 10 <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.html">Control APIs</a>, including GetSleepStartTimeRequest and 4 <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html">shared objects</a> in the Clova Home extension API</li>
          <li>[CEK] Added <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html#CustomCommandInfoObject">CustomCommandInfoObject</a> to <a href="/CEK/References/ClovaHomeInterface/Discovery_Interfaces.html#DiscoverAppliancesResponse">DiscoverAppliancesResponse</a> of the Clova Home extension API</li>
          <li>[CEK] Removed the TimeAmountInfoObject <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html">shared object</a> from the Clova Home extension API and revised corresponding contents of the <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.html">Control API</a></li>
          <li>[CEK] Added the tags field and changed the description of the location field in <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html#ApplianceInfoObject">ApplianceInfoObject</a> of the Clova Home extension API</li>
          <li>[Dev. console] Updated some UIs on the Clova developer console</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.27.0</td><td>v3.5</td><td>2018-03-19</td>
      <td>
        <ul>
          <li>[CIC] Added <a href="/CIC/References/Context_Objects.html#SoundOutputInfoObject">SoundOutputInfoObject</a> to <a href="/CIC/References/Context_Objects.html#DeviceState">Device.DeviceState</a></li>
          <li>[CIC] Added the <a href="/CIC/References/CICInterface/PlaybackController.html#CustomCommandIssued">CustomCommandIssued</a> event, which can execute customized commands of a user, to the <a href="/CIC/References/CICInterface/PlaybackController.html#CustomCommandIssued">PlaybackController</a> namespace</li>
          <li>[CEK] Added 48 <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.html">Control APIs</a>, including CloseConfirmation and 10 types of <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html">shared objects</a> in the Clova Home extension API</li>
          <li>[CEK] Added 30 more <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html#ApplianceInfoObject">appliances supported by</a> the Clova Home extension API</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.26.0</td><td>v3.4</td><td>2018-03-05</td>
      <td>
        <ul>
          <li>[CIC] Modified the description of the initiator field of the <a  href="/CIC/References/CICInterface/SpeechRecognizer.html#Recognize">SpeechRecognizer.Recognize</a> event</li>
          <li>[CIC] Changed the name of the hearing state to listening state in the client states of the <a href="/Design/Design_Guideline_For_Client_Hardware.html">Design guidelines for client devices</a></li>
          <li>[CIC] Added Feedback type in the audio content type and explanation on rules in the <a href="/Design/Design_Guideline_For_Client_Hardware.html#Audio">Audio</a> section of the Design guidelines for client devices</li>
          <li>[CEK] Added the <a href="/CEK/Tutorials/Use_Builtin_Type_Slots.html">Utilizing user-input information</a> page in the <a href="/CEK/Tutorials/Introduction.html">tutorial</a></li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.25.0</td><td>v3.3</td><td>2018-02-26</td>
      <td>
        <ul>
          <li>[CIC] Added the deviceUUID field to the initiator field of the <a href="/CIC/References/CICInterface/SpeechRecognizer.html#Recognize">SpeechRecognizer.Recognize</a> event</li>
          <li>[CIC] Added the <a href="/CIC/References/CICInterface/Alerts.html#RequestSynchronizeAlert">RequestSynchronizeAlert</a> event and the <a href="/CIC/References/CICInterface/Alerts.html#SynchronizeAlert">SynchronizeAlert</a> directive related to alarm synchronization to the <a href="/CIC/References/CICInterface/Alerts.html">Alerts</a> namespace</li>
          <li>[CIC] Scheduled to remove some fields related to alarm synchronization from the System namespace</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.24.0</td><td>v3.2</td><td>2018-02-19</td>
      <td>
        <ul>
          <li>[CIC] Added the initiator field to the <a href="/CIC/References/CICInterface/SpeechRecognizer.html#Recognize">SpeechRecognizer.Recognize</a> event to accurately identify the user invocation</li>
          <li>[CIC] Added the label field to the <a href="/CIC/References/CICInterface/Alerts.html#SetAlert">Alerts.SetAlert</a> directive to check details of reminders and scheduled actions</li>
          <li>[CIC] Added the label field to the <a href="/CIC/References/ContentTemplates/ActionTimer.html">ActionTimer</a>, <a href="/CIC/References/ContentTemplates/ActionTimerList.html">ActionTimerList</a>, <a href="/CIC/References/ContentTemplates/Reminder.html">Reminder</a>, and <a href="/CIC/References/ContentTemplates/ReminderList.html">ReminderList</a> templates to display the details of reminders and scheduled actions</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.23.0</td><td>v3.1</td><td>2018-02-05</td>
      <td>
        <ul>
          <li>[CIC] Modified the description of the durationInMilliseconds field of <a href="/CIC/References/CICInterface/AudioPlayer.html#AudioStreamInfoObject">AudioStreamInfoObject</a></li>
          <li>[CIC] Added new information such as a field to state the source on the following templates: <a href="/CIC/References/ContentTemplates/Atmosphere.html">Atmosphere</a>, <a href="/CIC/References/ContentTemplates/CardList.html">CardList</a>, <a href="/CIC/References/ContentTemplates/Humidity.html">Humidity</a>, <a href="/CIC/References/ContentTemplates/TodayWeather.html">TodayWeather</a>, <a href="CIC/References/ContentTemplates/TomorrowWeather.html">TomorrowWeather</a>, <a href="/CIC/References/ContentTemplates/WeeklyWeather.html">WeeklyWeather</a>, and <a href="CIC/References/ContentTemplates/WindSpeed.html">WindSpeed</a></li>
          <li>[CEK] Modified the description of the request (<a href="CEK/Guides/Build_Custom_Extension.html#HandleLaunchRequest">LaunchRequest</a>) to invoke extension and applied the changed contents to the <a href="/Design/Design_Guideline_For_Extension.html">Design guidelines for extensions</a></li>
          <li>[CEK] Added a list of <a href="/CEK/CEK_Overview.html#WhatisCEK">HTTP versions</a> used for communicating between CEK and extensions</li>
          <li>[CEK] Added the <a href="/CEK/Tutorials/Handle_Builtin_Intents.html">Handling built-in intents</a> page to the <a href="/CEK/Tutorials/Introduction.html">tutorial</a></li>
          <li>[Dev. console] Specified the <a href="/DevConsole/Guides/CEK/Register_Extension.html#SetServerConnection">port</a> to be used by the extension server</li>
          <li>[Common] Emended some errors in the document</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.22.0</td><td>v3.0</td><td>2018-01-29</td>
      <td>
        <ul>
          <li>[Design] Added <a href="/Design/Design_Guideline_For_Client_Hardware.html#SoundEffect">sound effects for reminders</a> in the <a href="/Design/Design_Guideline_For_Client_Hardware.html">Design guidelines for client devices</a></li>
          <li>[CIC] Added the <a href="/CIC/References/CICInterface/Notifier.html#Notify">Notifier.Notify</a> event to the <a href="/CIC/References/CICInterface/Notifier.html">Notifier</a> namespace and updated the payload field of the namespace</li>
          <li>[CIC] Added <a href="/CIC/References/CICInterface/SpeechSynthesizer.html#SpeechFinished">SpeechFinished</a>, <a href="/CIC/References/CICInterface/SpeechSynthesizer.html#SpeechStarted">SpeechStarted</a>, and <a href="/CIC/References/CICInterface/SpeechSynthesizer.html#SpeechStopped">SpeechStopped</a> event messages to the <a href="/CIC/References/Context_Objects.html#SpeechState">SpeechSynthesizer.SpeechState</a> and <a href="/CIC/References/CICInterface/SpeechSynthesizer.html">SpeechSynthesizer</a> namespaces</li>
          <li>[CIC] Added speechId and explicit fields to the <a href="/CIC/References/CICInterface/TextRecognizer.html">TextRecognizer.Recognize</a> event for multi-turn dialogues</li>
          <li>[CEK] Added <a href="/CEK/References/ClovaHomeInterface/Error_Interfaces.html#NoSuchTargetError">NoSuchTargetError</a>, <a href="/CEK/References/ClovaHomeInterface/Error_Interfaces.html#NotSupportedInCurrentModeError">NotSupportedInCurrentModeError</a>, <a href="/CEK/References/ClovaHomeInterface/Error_Interfaces.html#UnsupportedOperationError">UnsupportedOperationError</a>, and <a href="/CEK/References/ClovaHomeInterface/Error_Interfaces.html#ValueOutOfRangeError">ValueOutOfRangeError</a> to the <a href="/CEK/References/ClovaHomeInterface/Error_Interfaces.html">error interface</a> of the Clova Home extension message references</li>
          <li>[Dev. console] Added the method to check the connection before <a href="/DevConsole/Guides/CEK/Register_Extension.html#SetServerConnection">setting an extension server connection</a> and added a guide on the <a href="/DevConsole/Guides/CEK/Test_Extension.html#TestOnClovaApp">automated application of tester IDs</a></li>
          <li>[Dev. console] Updated some UIs on the Clova developer console</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.21.0</td><td>v2.9</td><td>2018-01-22</td>
      <td>
        <ul>
          <li>[Design] Added a section on supported audio compression formats in the <a href="/Design/Design_Guideline_For_Client_Hardware.html#SupportedAudioCompressionFormat">Design guidelines for client devices</a> and <a href="/Design/Design_Guideline_For_Extension.html#SupportedAudioCompressionFormat">Design guidelines for extensions</a></li>
          <li>[CEK] Added the <a href="/CEK/Tutorials/Introduction.html">Tutorial</a> page and the <a href="/CEK/Tutorials/Build_Simple_Extension.html">Building a basic extension</a> page</li>
          <li>[Dev. console] Displayed the <a href="/DevConsole/Guides/CEK/Register_Interaction_Model.html#AddCustomSlotType">list of built-in intents</a> and added UI for writing messages for a <a href="/DevConsole/Guides/CEK/Deploy_Extension.html#InputComplianceInfo">review request</a></li>
          <li>[Common] Changed the image format of the UML diagram</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.20.0</td><td>v2.8</td><td>2018-01-15</td>
      <td>
        <ul>
          <li>[Design] Added guideline descriptions on light and sound effects for alarms, reminders, and timers to the <a href="/Design/Design_Guideline_For_Client_Hardware.html">Design guidelines for client devices</a></li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.19.0</td><td>v2.7</td><td>2018-01-08</td>
      <td>
        <ul>
          <li>[Design] Modified the description of the <a href="/Design/Design_Guideline_For_Extension.html#DefineInteractionModel">built-in intent</a> based on platform implementation</li>
          <li>[CIC] Added a section on <a href="/CIC/Guides/Implement_Client_Features.html#HandleDelegation">Handling delegated user requests</a> and added the <a href="/CIC/References/CICInterface/Clova.html#HandleDelegatedEvent">Clova.HandleDelegatedEvent</a> directive and the <a href="/CIC/References/CICInterface/Clova.html#ProcessDelegatedEvent">Clova.ProcessDelegatedEvent</a> event</li>
          <li>[CIC] Added a description to include the <a href="/CIC/References/Context_Objects.html#PlaybackState">AudioPlayer.PlaybackState</a> context information in <a href="/CIC/References/CICInterface/PlaybackController.html#NextCommandIssued">PlaybackController.NextCommandIssued</a> and <a href="/CIC/References/CICInterface/PlaybackController.html#PreviousCommandIssued">PlaybackController.PreviousCommandIssued</a> event messages</li>
          <li>[CIC] Revised the description of the interaction structure of the <a href="/CIC/References/CICInterface/Alerts.html">Alerts</a> API</li>
          <li>[CIC] Added the description of the <a href="/CIC/References/CICInterface/DeviceControl.html#DeviceControlWorkFlow">interaction structure</a> of the <a href="/CIC/References/CICInterface/DeviceControl.html">DeviceControl</a> API</li>
          <li>[CIC] Emended errors on some content templates and shared objects</li>
          <li>[CEK] Added the <a href="/CEK/Examples/Extension_Examples.html">Extension examples</a> page</li>
          <li>[Dev. console] Updated the description on <a href="/DevConsole/Guides/CEK/Test_Extension.html">testing an extension</a> due to the added <strong>tester ID</strong> field</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.18.1</td><td>v2.6</td><td>2018-01-02</td>
      <td>
        <ul>
          <li>[CIC] Added error code 429 and its description in the Remarks of the section <a href="/CIC/References/CIC_API.html#EstablishDownchannel">Establishing a downchannel</a></li>
          <li>[CIC] Removed route-finding templates (CarRoute, TransportationRoute) and the UI for route-finder was replaced with an ImageText template</li>
          <li>[Common] Emended some errors and typos in the document</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.18.0</td><td>v2.5</td><td>2017-12-18</td>
      <td>
        <ul>
          <li>[Design] Moved the section on <a href="/Design/Design_Guideline_For_Extension.html#DefineInteractionModel">Defining an interaction model</a> in <a href="/DevConsole/Guides/CEK/Register_Interaction_Model.html">Registering interaction model</a> to <a href="/Design/Design_Guideline_For_Extension.html">Design guidelines for extensions</a></li>
          <li>[Design] Added a guideline to prepare <a href="/Design/Design_Guideline_For_Extension.html#UtteranceExample">sample utterances</a> in the section on <a href="/Design/Design_Guideline_For_Extension.html#DefineInteractionModel">Defining an interaction model</a></li>
          <li>[CIC] Removed the ExpectSpeechTimedOut event from the <a href="/CIC/References/CICInterface/SpeechRecognizer.html">SpeechRecognizer</a> interface</li>
          <li>[CIC] Removed the Clova.FreetalkState object from the <a href="/CIC/References/Context_Objects.html">context information</a></li>
          <li>[Dev. console] Added a description on how to use the test mode in <a href="/DevConsole/Guides/CEK/Test_Extension.html">Testing an extension</a></li>
          <li>[Dev. console] Modified image and description due to UI improvements</li>
          <li>[Dev. console] Added sections <a href="/DevConsole/Guides/CEK/Update_Extension.html">Updating an extension</a> and <a href="/DevConsole/Guides/CEK/Remove_Extension.html">Disabling and deleting an extension</a></li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.17.0</td><td>v2.4</td><td>2017-12-11</td>
      <td>
        <ul>
          <li>[Design] Added <a href="/Design/Design_Guideline_For_Extension.html">Design guidelines for extensions</a></li>
          <li>[CIC] Added the <a href="/CIC/References/CICInterface/AudioPlayer.html#ClearQueue">ClearQueue</a> directive to the <a href="/CIC/References/CICInterface/AudioPlayer.html">AudioPlayer</a> interface</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.16.0</td><td>v2.3</td><td>2017-12-04</td>
      <td>
        <ul>
          <li>[Design] Added <a href="/Design/Design_Guideline_For_Client_Hardware.html#AudioInterruptionRule">audio interruption rules</a> to the <a href="/Design/Design_Guideline_For_Client_Hardware.html">Design guidelines for client devices</a></li>
          <li>[Design] Improved the images in <a href="/Design/Design_Guideline_For_Client_Hardware.html">Design guidelines for client devices</a></li>
          <li>[CIC] Added the section on <a href="/CIC/Guides/Interact_with_CIC.html#UserAgentString">user-agent strings</a> for prerequisites before interacting with CIC</li>
          <li>[CIC] Added the description of the 412 Precondition failed code in the <a href="/CIC/References/CIC_API.html#SendEvent">Sending events</a> section of the <a href="/CIC/References/CIC_API.html">CIC API reference</a></li>
          <li>[CEK] Added a reprompt field in the <a href="/CEK/References/CEK_API.html#CustomExtResponseMessage">response message</a> to encourage multi-turn dialogues with the user</li>
          <li>[CEK] Emended errors in the document</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.15.0</td><td>v2.2</td><td>2017-11-20</td>
      <td>
        <ul>
          <li>[Design] Added <a href="/Design/Design_Guideline_For_Client_Hardware.html">Design guidelines for client devices</a></li>
          <li>[CIC] Added Type5 and Type6 to the subType value of the <a href="/CIC/References/ContentTemplates/CardList.html">CardList template</a> to display audio content and image thumbnails</li>
          <li>[CEK] Changed the name of a <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html">shared object</a>, HeatingModeInfoObject of the Clova Home extension message to <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html#ModeInfoObject">ModeInfoObject</a> and modified the description as an object indicating the operation mode of universal devices</li>
          <li>[CEK] Added the <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.html#GetCurrentTemperatureRequest">GetCurrentTemperatureRequest</a> message and the <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.html#GetCurrentTemperatureResponse">GetCurrentTemperatureResponse</a> message to the <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.html">Control</a> interface of the Clova Home extension message</li>
          <li>[CEK] Added the <a href="/CEK/References/ClovaHomeInterface/Error_Interfaces.html#UnsupportedOperationError">UnsupportedOperationError</a> message to the <a href="/CEK/References/ClovaHomeInterface/Error_Interfaces.html">error</a> interface of the Clova Home extension message</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.14.0</td><td>v2.1</td><td>2017-11-13</td>
      <td>
        <ul>
          <li>[CIC] Added UX details in the Remarks of directive messages for volume control (<a href="/CIC/References/CICInterface/DeviceControl.html#Decrease">DeviceControl.Decrease</a>, <a href="/CIC/References/CICInterface/DeviceControl.html#Increase">DeviceControl.Increase</a>, <a href="/CIC/References/CICInterface/DeviceControl.html#SetValue">DeviceControl.SetValue</a>, <a href="/CIC/References/CICInterface/PlaybackController.html#Mute">PlaybackController.Mute</a>, and <a href="/CIC/References/CICInterface/PlaybackController.html#Unmute">PlaybackController.Unmute</a>)</li>
          <li>[CEK] Added DecrementFanSpeed, IncrementFanSpeed, SetFanSpeed, and SetMode actions to the AIRCONDITIONER type, and added SetFanSpeed to the HUMIDIFIER type in the <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html#ApplianceInfoObject">ApplianceInfoObject</a></li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.13.0</td><td>v2.0</td><td>2017-11-06</td>
      <td>
        <ul>
          <li>[CIC] Added the <a href="/CIC/References/CICInterface/SpeechRecognizer.html#KeepRecording">SpeechRecognizer.KeepRecording</a> directive</li>
          <li>[CIC] Added <a href="/CIC/References/Context_Objects.html#Display">Device.Display</a> context information</li>
          <li>[CIC] Added a token field to the <a href="/CIC/References/ContentTemplates/ActionTimer.html">ActionTimer</a>, <a href="/CIC/References/ContentTemplates/ActionTimerList.html">ActionTimerList</a>, <a href="/CIC/References/ContentTemplates/Alarm.html">Alarm</a>, <a href="/CIC/References/ContentTemplates/AlarmList.html">AlarmList</a>, <a href="/CIC/References/ContentTemplates/Memo.html">Memo</a>, <a href="/CIC/References/ContentTemplates/MemoList.html">MemoList</a>, <a href="/CIC/References/ContentTemplates/Reminder.html">Reminder</a>, <a href="/CIC/References/ContentTemplates/ReminderList.html">ReminderList</a>, <a href="/CIC/References/ContentTemplates/Schedule.html">Schedule</a>, <a href="/CIC/References/ContentTemplates/ScheduleList.html">ScheduleList</a>, <a href="/CIC/References/ContentTemplates/Timer.html">Timer</a>, and <a href="/CIC/References/ContentTemplates/TimerList.html">TimerList</a> templates</li>
          <li>[CEK] Changed the name of the context.System.device.displayType to context.System.device.display from the request messages of <a href="/CEK/References/CEK_API.html#CustomExtMessage">custom extension messages</a> and changed the sub-field configuration</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.12.0</td><td>v1.9</td><td>2017-10-30</td>
      <td>
        <ul>
          <li>[Dev. console] Added the description for the <a href="/DevConsole/ClovaDevConsole_Overview.html">Clova developer console overview</a></li>
          <li>[Dev. console] Added the guide for <a href="/DevConsole/Guides/CEK/Register_Extension.html">Registering an extension</a></li>
          <li>[Dev. console] Added the guide for <a href="/DevConsole/Guides/CEK/Register_Interaction_Model.html">Registering an interaction model</a></li>
          <li>[Dev. console] Added the guide for <a href="/DevConsole/Guides/CEK/Deploy_Extension.html">Deploying an extension</a></li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.11.0</td><td>v1.8</td><td>2017-10-23</td>
      <td>
        <ul>
          <li>[CIC] Added emotionCode and motionCode fields to the <a href="/CIC/References/ContentTemplates/Text.html">Text</a> template</li>
          <li>[CIC] Changed assets[].url field contents of <a href="/CIC/References/CICInterface/Alerts.html#SetAlert">Alerts.SetAlert</a> directive message</li>
          <li>[CIC] Revised an error in the example of the <a href="/CIC/References/CICInterface/AudioPlayer.html#StreamRequested">AudioPlayer.StreamRequested</a> event</li>
          <li>[CEK] Added context.System.device.displayType field to the request message in the request message of <a href="/CEK/References/CEK_API.html#CustomExtMessage">custom extension messages</a></li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.10.0</td><td>v1.7</td><td>2017-10-16</td>
      <td>
        <ul>
          <li>[CIC] Added <a href="/CIC/References/CICInterface/PlaybackController.html#Replay">Replay</a> directive message to the <a href="/CIC/References/CICInterface/PlaybackController.html">PlaybackController</a> namespace</li>
          <li>[CIC] Added supplementary information on alarm synchronization in the Overall process section</li>
          <li>[CIC] Removed the content field from the <a href="/CIC/References/Context_Objects.html#AlertsState">Alert.AlertsState</a> of <a href="/CIC/References/Context_Objects.html#AlertInfoObject">AlertInfoObject</a> context information</li>
          <li>[Common] Modified images and emended errors in the document</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.9.0</td><td>v1.6</td><td>2017-10-02</td>
      <td>
        <ul>
          <li>[CIC] Added the <a href="/CIC/References/CICInterface/Alerts.html">Alerts</a> namespace and alarm related interface</li>
          <li>[CIC] Added the <a href="/CIC/References/CICInterface/System.html">System</a> namespace and alarm related interface</li>
          <li>[CIC] Added the expectContentType field to the <a href="/CIC/References/CICInterface/SpeechRecognizer.html#ExpectSpeech">SpeechRecognizer.ExpectSpeech</a> directive</li>
          <li>[CIC] Added a warning field to the <a href="/CIC/References/Context_Objects.html#VolumeInfoObject">VolumeInfoObject</a> of <a href="/CIC/References/Context_Objects.html#DeviceState">Device.DeviceState</a></li>
          <li>[CIC] Added templates: <a href="/CIC/References/ContentTemplates/ActionTimer.html">ActionTimer</a>, <a href="/CIC/References/ContentTemplates/ActionTimerList.html">ActionTimerList</a>, <a href="/CIC/References/ContentTemplates/Alarm.html">Alarm</a>, <a href="/CIC/References/ContentTemplates/AlarmList.html">AlarmList</a>, <a href="/CIC/References/ContentTemplates/Memo.html">Memo</a>, <a href="/CIC/References/ContentTemplates/MemoList.html">MemoList</a>, <a href="/CIC/References/ContentTemplates/Reminder.html">Reminder</a>, <a href="/CIC/References/ContentTemplates/ReminderList.html">ReminderList</a>, <a href="/CIC/References/ContentTemplates/Schedule.html">Schedule</a>, <a href="/CIC/References/ContentTemplates/ScheduleList.html">ScheduleList</a>, <a href="/CIC/References/ContentTemplates/Timer.html">Timer</a>, and <a href="/CIC/References/ContentTemplates/TimerList.html">TimerList</a></li>
          <li>[CIC] Modified some code examples of the <a href="/CIC/References/ContentTemplates/ImageText.html">ImageText</a> template</li>
          <li>[CIC] Modified some fields of the <a href="/CIC/References/ContentTemplates/Popup.html">Popup</a> template</li>
          <li>[CIC] Added the Terms and Conditions of Service on <a href="/CIC/Guides/Interact_with_CIC.html#CreateClovaAccessToken">Creating Clova access tokens</a> and <a href="/CIC/References/Clova_Auth_API.html#RequestAuthorizationCode">Requesting an authorization code</a></li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.8.0</td><td>v1.5</td><td>2017-09-25</td>
      <td>
        <ul>
          <li>[CIC] Added the <a href="/CIC/References/CICInterface/PlaybackController.html#NextCommandIssued">PlaybackController.NextCommandIssued</a> and <a href="/CIC/References/CICInterface/PlaybackController.html#PreviousCommandIssued">PlaybackController.PreviousCommandIssued</a> events for music playback control to the <a href="/CIC/References/CICInterface/PlaybackController.html">PlaybackController API</a></li>
          <li>[CIC] Added the expectSpeechId field to the <a href="/CIC/References/CICInterface/SpeechRecognizer.html#ExpectSpeech">SpeechRecognizer.ExpectSpeech</a> directive, and added speechId and explicit fields to the <a href="/CIC/References/CICInterface/SpeechRecognizer.html#Recognize">SpeechRecognizer.Recognize</a> event</li>
          <li>[CIC] Added the <a href="/CIC/References/ContentTemplates/Popup.html">Popup template</a></li>
          <li>[CEK] Added 34 <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.html">Control APIs</a>, including ChargeConfirmation in the Clova Home extension API</li>
          <li>[CEK] Added 6 more Clova Home extension API <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html#ApplianceInfoObject">supported appliances</a> and added a location field</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.7.0</td><td>v1.4</td><td>2017-09-18</td>
      <td>
        <ul>
          <li>[CIC] Added the <a href="/CIC/References/CICInterface/DeviceControl.html#ExpectReportState">DeviceControl.ExpectReportState</a> directive, <a href="/CIC/References/CICInterface/DeviceControl.html#ReportState">DeviceControl.ReportState</a> event, and <a href="/CIC/References/CICInterface/DeviceControl.html#RequestStateSynchronization">DeviceControl.RequestStateSynchronization</a> event to DeviceControl API and changed the name of the DeviceControl.UpdateDeviceState directive to <a href="/CIC/References/CICInterface/DeviceControl.html#SynchronizeState">DeviceControl.SynchronizeState</a></li>
          <li>[CIC] Added the item3 field to the <a href="/CIC/References/ContentTemplates/Text.html">Text</a> template</li>
          <li>[CIC] Added a source field in the <a href="/CIC/References/CICInterface/AudioPlayer.html#Play">AudioPlayer.Play</a> directive message</li>
          <li>[CIC] Added the durationInMilliseconds field in <a href="/CIC/References/CICInterface/AudioPlayer.html#AudioStreamInfoObject">AudioStreamInfoObject</a> </li>
          <li>[CIC] Added the Notifier namespace. Added <a href="/CIC/References/CICInterface/Notifier.html#ClearIndicator">ClearIndicator</a> and <a href="/CIC/References/CICInterface/Notifier.html#SetIndicator">SetIndicator</a> directive messages</li>
          <li>[CIC] Added the <a href="/CIC/References/ContentTemplates/Atmosphere.html">Atmosphere</a> template</li>
          <li>[CIC] Added a guide text on prohibited use for the bgClipURL field of weather templates due to license issues</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.6.0</td><td>v1.3</td><td>2017-09-11</td>
      <td>
        <ul>
          <li>[CIC] Added the explicit field to the <a href="/CIC/References/CICInterface/SpeechRecognizer.html#ExpectSpeech">SpeechRecognizer.ExpectSpeech</a> directive message</li>
          <li>[CIC] Added <a href="/CIC/References/ContentTemplates/Common_Fields.html">common fields</a> specification to the <a href="/CIC/References/Content_Templates.html">Content</a> template</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.5.0</td><td>v1.2</td><td>2017-09-04</td>
      <td>
        <ul>
          <li>[CIC] Added the <a href="/CIC/References/CICInterface/Clova.html#Help">Clova.Help</a> directive</li>
          <li>[CIC] Added the <a href="/CIC/References/CICInterface/DeviceControl.html#LaunchApp">DeviceControl.LaunchApp</a> directive message</li>
          <li>[CIC] Added the TextRecognizer namespace and the <a href="/CIC/References/CICInterface/TextRecognizer.html">TextRecognizer.Recognize</a> event</li>
          <li>[CIC] Rewrote the table of contents and descriptions of the <a href="/CIC/References/CIC_API.html">CIC API</a> and <a href="/CEK/References/CEK_API.html">CEK API</a></li>
          <li>[CIC] Updated content on CIC API: Added status codes for the request and response header, and applied the format of the REST API reference to the document</li>
          <li>[Other] Emended errors in the document</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.4.0</td><td>v1.1</td><td>2017-08-28</td>
      <td>
        <ul>
          <li>[CIC] Added the set-top box specification on TV channels and specifications for the power state to <a href="/CIC/References/Context_Objects.html#DeviceState">Device.DeviceState</a> and <a href="/CIC/References/CICInterface/DeviceControl.html">DeviceControl API</a></li>
          <li>[CIC] Added and changed some target values in the <a href="/CIC/References/CICInterface/DeviceControl.html">DeviceControl API</a>: power, energysave, screenbrightness</li>
          <li>[CIC] Changed the name SetPoint of the <a href="/CIC/References/CICInterface/DeviceControl.html">DeviceControl API</a> to <a href="/CIC/References/CICInterface/DeviceControl.html#SetValue">SetValue</a></li>
          <li>[CIC] Updated <a href="/CIC/References/Clova_Auth_API.html">Clova auth API</a>: Added request and response headers, and status codes. Applied the format of the REST API reference to the document</li>
          <li>[CEK] Added <a href="/CEK/References/ClovaHomeInterface/Error_Interfaces.html#ValueOutOfRangeError">ValueOutOfRangeError</a> to the error interface of the Clova Home</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.3.0</td><td>v1.0</td><td>2017-08-21</td>
      <td>
        <ul>
          <li>[CIC] Added the section on <a href="/CIC/Guides/Interact_with_CIC.html#ManageConnection">Renewing a Clova access token</a> and updated content on token APIs</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.2.0</td><td>v0.9</td><td>2017-08-14</td>
      <td>
        <ul>
          <li>[CIC] Added description on the <a href="/CIC/CIC_Overview.html#DialogModel">dialogue model</a> </li>
          <li>[CIC] Added <a href="/CIC/References/CICInterface/DeviceControl.html">DeviceControl</a> API</li>
          <li>[CIC] Added payload fields in <a href="/CIC/References/Context_Objects.html">Device.DeviceState</a>: airplane, battery, bluetooth, brightness, flashLight, gps, powerSavingMode, soundMode, volume, and wifi</li>
          <li>[CEK] Added the section on <a href="/CEK/Guides/Build_Custom_Extension.html#DoMultiturnDialog">Engaging in multi-turn dialogues</a> and updated the description on the sessionAttributes field</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.1.0</td><td>v0.8</td><td>2017-08-04</td>
      <td>
        <ul>
          <li>[CIC] Added the <a href="/CIC/References/CICInterface/Clova.html#Hello">Clova.Hello</a> directive message</li>
          <li>[CIC] Added the type field to the AudioItem object of the <a href="/CIC/References/CICInterface/AudioPlayer.html#Play">AudioPlayer.Play</a> directive message</li>
          <li>[CIC] Added the urlPlayable field to the <a href="/CIC/References/CICInterface/AudioPlayer.html#AudioStreamInfoObject">AudioStreamInfoObject</a></li>
          <li>[CIC] Added specification on <a href="/CIC/References/CIC_API.html#Error">CIC error messages</a></li>
          <li>[CIC] Rewrote the contents of <a href="/CIC/References/CIC_API.html#MultipartMessage">multipart message</a></li>
          <li>[CEK] Added new Clova Home <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html#ApplianceInfoObject">supported appliances</a>: air purifier, humidifier, set-top box, and heater</li>
          <li>[CEK] Removed an existing Clova Home <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html#ApplianceInfoObject">supported appliance</a>: door lock</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.0.0</td><td>v0.7</td><td>2017-07-28</td>
      <td>
        <ul>
          <li>[CIC] Removed PlayNext and Stop from <a href="/CIC/References/CICInterface/AudioPlayer.html">AudioPlayer</a> (merged into <a href="/CIC/References/CICInterface/PlaybackController.html">PlaybackController</a>)</li>
          <li>[CIC] Changed the message names of <a href="/CIC/References/CICInterface/PlaybackController.html">PlaybackController</a> (Mute, Next, Pause, Previous, Resume, Stop, Unmute, VolumeDown, and VolumeUp</li>
          <li>[CIC] Added route-finding templates: CarRoute and TransportationRoute</li>
          <li>[CIC] Added weather templates: <a href="/CIC/References/ContentTemplates/Humidity.html">Humidity</a>, <a href="/CIC/References/ContentTemplates/TodayWeather.html">TodayWeather</a>, <a href="/CIC/References/ContentTemplates/TomorrowWeather.html">TomorrowWeather</a>, <a href="/CIC/References/ContentTemplates/WeeklyWeather.html">WeeklyWeather</a>, and <a href="/CIC/References/ContentTemplates/WindSpeed.html">WindSpeed</a></li>
          <li>[CEK] Added the <a href="/CEK/Guides/Build_Clova_Home_Extension.html">Clova Home extension document</a></li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v2.2.1</td><td>v0.6</td><td>2017-07-14</td>
      <td>
        <ul>
          <li>[CIC] Added beginAtInMilliseconds field contents of <a href="/CIC/References/CICInterface/AudioPlayer.html#AudioStreamInfoObject">AudioStreamInfoObject</a></li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v2.2.0</td><td>v0.5</td><td>2017-07-07</td>
      <td>
        <ul>
          <li>[CEK] Updated the <a href="/CEK/References/CEK_API.html#CustomExtResponseMessage">outputSpeech</a> object configuration in the <a href="/CEK/References/CEK_API.html#CustomExtResponseMessage">response message of custom extensions</a></li>
          <li>[Common] Added the <a href="/Glossary.html">Glossary</a></li>
          <li>Updated the table of contents for the section on CEK message formats</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v2.1.0</td><td>v0.4</td><td>2017-07-03</td>
      <td>
        <ul>
          <li>[CEK] Updated images in the CEK document</li>
          <li>[Common] Applied changes according to the document review results</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v2.0.0</td><td>v0.3</td><td>2017-06-19</td>
      <td>
        <ul>
          <li>[CEK] Completed the first draft of the CEK document</li>
          <li>[CIC] Updated <a href="/CIC/Guides/Interact_with_CIC.html#ManageConnection">Managing connections</a> (for when HTTP PING frame is unavailable)</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v1.1.0</td><td>v0.2</td><td>2017-06-08</td>
      <td>
        <ul>
          <li>[CIC] Added the section on <a href="/CIC/Guides/Interact_with_CIC.html#ManageConnection">Managing connections</a> (HTTP PING) to <a href="/CIC/Guides/Interact_with_CIC.html">Interacting with CIC</a></li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v1.0.0</td><td>v0.1</td><td>2017-05-29</td>
      <td>
        <ul>
          <li>[CIC] Completed the first draft of the CIC document</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>
