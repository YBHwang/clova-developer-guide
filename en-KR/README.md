# Before getting started

<a target="_blank" href="http://clova.ai">Clova</a> is an artificial intelligence platform developed and serviced by NAVER. Clova recognizes user speech or images, analyzes them, and provides information or services that users have requested. Third-party developers who use the Clova platform can be divided into the following two groups.

* [CIC platform](/CIC/CIC_Overview.md#WhatisCIC) users: Client developers who are developing an electronic appliance or an app that provides Clova AI service.
* [CEK platform](/CEK/CEK_Overview.md#WhatisCEK) users: Extension developers who are developing an extension that provides private online content or services through Clova.

<div class="note">
  <p><strong>Note!</strong></p>
  <p>A company or individual trying to develop an extension or client that includes monetary transactions or payments, or an extension or client that provides an IoT service, is required to be in a partnership with NAVER by visiting the <a target="_blank" href="https://www.navercorp.com/ko/company/proposalRegister.nhn">NAVER partnership suggestions</a> page in advance.</p>
</div>

For client and extension developers, Clova platform provides Clova interface connection (CIC), Clova extension kit (CEK), and Clova developer console. Developers can use the following documents when necessary:

<table>
  <thead>
    <tr>
      <th width="12%">Type</th>
      <th width="44%">Client developer</th>
      <th width="44%">Extension developer</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align: center;">Understanding the concept</td>
      <td>
        <ul>
          <li><a href="/CIC/CIC_Overview.md#WhatisCIC">What is CIC?</a></li>
          <li><a href="/CIC/CIC_Overview.md#DialogModel">Dialogue model</a></li>
        </ul>
      </td>
      <td>
        <ul>
          <li><a href="/CEK/CEK_Overview.md#WhatisCEK">What is CEK?</a></li>
          <li><a href="/Design/Design_Guideline_For_Extension.md#DefineInteractionModel">Understanding the interaction model</a></li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align: center;">Design</td>
      <td>
        <ul>
          <li><a href="/Design/Design_Guideline_For_Client_Hardware.md">Design guidelines for client devices</a></li>
        </ul>
      </td>
      <td>
        <ul>
          <li><a href="/Design/Design_Guideline_For_Extension.md">Design guidelines for extensions</a></li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align: center;">Development</td>
      <td>
        <ul>
          <li>Guide</li>
          <ul>
            <li><a href="/CIC/Guides/Interact_with_CIC.md">Interacting with CIC</a></li>
          </ul>
          <li>Reference</li>
          <ul>
            <li><a href="/CIC/References/CIC_API.md">CIC API</a></li>
            <li><a href="/CIC/References/CIC_API.md#CICInterface">CIC interface</a></li>
            <li><a href="/CIC/References/Content_Templates.md">Content template</a></li>
            <li><a href="/CIC/References/Clova_Auth_API.md">CIC auth API</a></li>
          </ul>
        </ul>
      </td>
      <td>
        <ul>
          <li>Tutorial</li>
          <ul>
            <li><a href="/CEK/Tutorials/Build_Simple_Extension.md">Building a basic extension</a></li>
            <li><a href="/CEK/Tutorials/Handle_Builtin_Intents.md">Handling basic built-in intents</a></li>
            <li><a href="/CEK/Tutorials/Use_Builtin_Type_Slots.md">Utilizing user-input information</a></li>
          </ul>
          <li>Guide</li>
          <ul>
            <li><a href="/CEK/Guides/Build_Custom_Extension.md">Creating a custom extension</a></li>
            <li><a href="/CEK/Guides/Build_Clova_Home_Extension.md">Creating a Clova Home extension</a></li>
            <li><a href="/CEK/Guides/Link_User_Account.md">Linking user accounts</a></li>
            <li><a href="/DevConsole/Guides/CEK/Register_Extension.md">Registering an extension</a></li>
            <li><a href="/DevConsole/Guides/CEK/Register_Interaction_Model.md">Registering an interaction model</a></li>
          </ul>
          <li>Reference</li>
          <ul>
            <li><a href="/CEK/References/CEK_API.md#CustomExtMessage">Custom extension messages</a></li>
            <li><a href="/CEK/References/CEK_API.md#ClovaHomeExtMessage">Clova Home extension messages</a></li>
          </ul>
          <li>Example extensions</li>
          <ul>
            <li><a href="/CEK/Examples/Extension_Examples.md#MagicBall">MagicBall</a></li>
            <li><a href="/CEK/Examples/Extension_Examples.md#RainSound">RainSound</a></li>
            <li><a href="/CEK/Examples/Extension_Examples.md#DiceDrawer">DiceDrawer</a></li>
            <li><a href="/CEK/Examples/Extension_Examples.md#CoinHelper">CoinHelper</a></li>
          </ul>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align: center;">Deployment</td>
      <td>
        <ul>
          <li>Registering a client (coming soon)</li>
        </ul>
      </td>
      <td>
        <ul>
          <li><a href="/DevConsole/Guides/CEK/Deploy_Extension.md">Deploying an extension</a></li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

<div class="note">
  <p><strong>Note!</strong></p>
  <p>Clova is currently under continuous development. Thus, the information in this document is subject to change at any time.</p>
</div>
