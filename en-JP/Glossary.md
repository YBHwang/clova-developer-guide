# Terms and abbreviations

<div class="note">
  <p><strong>Note!</strong></p>
  <p>This page is updated on an ongoing basis.</p>
</div>

### CEK
The abbreviation of [Clova Extensions Kit](#CEK).

### CIC
The abbreviation of [Clova Interface Connect](#CIC).

### CIC API {#CICAPI}
The REST API that CIC provides to clients. Clients use CIC API to exchange information with Clova.

### Clova {#Clova}
[Clova](https://clova.line.me/) is an AI (artificial intelligence) platform developed and serviced by {{ book.TargetServiceForClientAuth }}. Clova recognizes user speech, analyzes them, and provides information or services that users have requested. Third-party developers, by leveraging the Clova technologies, can make a device or home appliance that provides an AI service. They can also offer their content or services to users through Clova.

### Clova access token {#ClovaAccessToken}
A means used by Clova to authorize a client when the client tries to send [events](#Event) to [Clova Interface Connect](#CIC). For more information, see [Creating Clova access tokens](/CIC/Guides/Interact_with_CIC.md#CreateClovaAccessToken).

### Clova Developer Center {#ClovaDeveloperConsole}
A <a target="_blank" href="{{ book.DeveloperConsoleURL }}">[web tool]</a> that provides the following features to the [Clova extension](#ClovaExtension) developers or to client devices that interact with the Clova platform.
* Registering a client device and obtaining client credentials for authentication (coming soon)
* [Registering](/DevConsole/Guides/CEK/Register_Extension.md) and [deploying](/DevConsole/Guides/CEK/Deploy_Extension.md) a Clova extension
* [Registering an interaction model](/DevConsole/Guides/CEK/Register_Interaction_Model.md)
* Analysis data of Clova services

### Clova Extension {#ClovaExtension}
A web application that provides extended capabilities to Clova for a more diverse user experience, including the capability of controlling IoT appliances at home or third-party services such as music, shopping, and banking. It is commonly referred to as an "extension." The Clova platform currently supports and provides two types of Clova extensions as shown below. To regular users, the extension is referred to as a "skill."
* [Custom Extension](#CustomExtension)
* [Clova Home Extension](#ClovaHomeExtension)

### Clova Extensions Kit(CEK) {#CEK}
A platform that provides tools and interfaces for development and deployment of a Clova extension. It supports [communication between Clova and extensions](/CEK/CEK_Overview.md).

### Clova Home Extension {#ClovaHomeExtension}
An extension that provides a service for controlling IoT appliances. For more information, see [Creating a Clova Home Extension](/CEK/Guides/Build_Clova_Home_Extension.md).

### Clova Home Extension messages {#ClovaHomeExtMessage}
Messages used by [Clova Home Extensions](#ClovaHomeExtension) when they exchange information with [Clova Extensions Kit](#CEK) to control IoT appliances. For more information, see [Clova Home Extension messages](/CEK/References/CEK_API.md#ClovaHomeExtMessage).

### Clova Interface Connect(CIC) {#CIC}
A platform that serves as an interface between Clova and a client aiming to provide AI assistant services such as computers, mobile apps, mobile devices, or home appliances. For more information, see [CIC overview](/CIC/CIC_Overview.md).

### Clova app {#ClovaApp}

A Clova app developed by {{ book.OrientedService }} and deployed to the iOS or Android platform. These apps can send commands to Clova and also register and manage client devices.

### Clova auth API {#ClovaAuthAPI}
An API used by clients to obtain [Clova access tokens](#ClovaAccessToken). For more information, see [Clova auth API](/CIC/References/Clova_Auth_API.md).

### Content template {#ContentTemplate}
Standardized formats for displaying content returned from CIC. For more information, see [Content template](/CIC/References/Content_Templates.md).

### Context object {#ContextObjects}
Objects that express the current [context information](#Context) of a client. For more information, see [Context](/CIC/References/Context_Objects.md).

### Custom Extension {#CustomExtension}
An [extension](#ClovaExtension) that provides tailored extended functions. A custom extension lets you provide third-party services such as music, shopping, or banking. For more information, see [Creating a custom extension](/CEK/Guides/Build_Custom_Extension.md).

### Custom extension message {#CustomExtMessage}
Messages used by [Clova Extensions Kit](#CEK) and [custom extension](#CustomExtension) to exchange information. For more information, see [Custom extension messages](/CEK/References/CEK_API.md#CustomExtMessage).

### Device discovery {#Discovery}
A feature that provides client devices with a list of IoT appliances registered to a user account. For more information, see [Providing device discovery](/CEK/Guides/Build_Clova_Home_Extension.md#ProvideDeviceDiscovery).

### Downchannel {#Downchannel}
An [HTTP/2](#HTTP2) stream through which clients receive directives from [CIC](#CIC). For more information, see [Connecting with CIC](/CIC/Guides/Interact_with_CIC.md#ConnectToCIC).

### Extension {#Extension}
An alias for [Clova extension](#ClovaExtension).

### Skill store {#ExtensionStore}

A platform designed to provide the extensions to users.

### Skill store home {#ExtensionStoreHome}

A page to display the extensions registered in the extension store. It is a term used to refer to the **extension service management** menu in the Clova app.

### Extension page {#ExtensionPage}

A page displayed when a specific extension is selected in the skill store Home (**extension service management** menu). This page provides a detailed description of the extension.

### HTTP/2 {#HTTP2}
A version of HTTP. HTTP/2 is based on <a href="https://en.wikipedia.org/wiki/SPDY" target="_blank">SPDY</a> and developed by the IETF (Internet Engineering Task Force). HTTP/2 is the enhanced version of HTTP 1.1, which was standardized in RFC 2068 in 1997 and was presented as a Proposed standard in December 2014 and approved by IESG on February 17, 2015. HTTP/2 was published as <a href="https://tools.ietf.org/html/rfc7540" target="_blank">RFC 7540</a> in May 2015.

### Intent {#Intent}
A segment that identifies the user requests for a Clova extension to handle. There are two types of intents: a custom intent and a built-in intent. Before implementing a [custom extension](#CustomExtension), an [interaction model](#InteractionModel) consisting of a set of intents must be defined. For more information, see [Defining an interaction model](/Design/Design_Guideline_For_Extension.md#DefineInteractionModel).

### IntentRequest {#IntentRequest}

A type of request message that sends the analysis details of a user request ([intent](#Intent)) to a [custom extension](#CustomExtension). For more information, see [Handling a custom extension request](/CEK/Guides/Build_Custom_Extension.md#HandleCustomExtensionRequest).

### Interaction model {#InteractionModel}
A model that defines a rule to convert to the standardized format (JSON) for a [custom extension](#CustomExtension) to pass user voice requests to an extension. For more information, see [Defining an interaction model](/Design/Design_Guideline_For_Extension.md#DefineInteractionModel).

### LaunchRequest {#LaunchRequest}
A type of request message that notifies that a user has requested to start a certain mode or [custom extension](#CustomExtension). For more information, see [Handling a custom extension request](/CEK/Guides/Build_Custom_Extension.md#HandleCustomExtensionRequest).

### OAuth 2.0
A public standard for delegation of access rights. The protocol allows internet users to grant account access rights to other web services or applications. On the Clova platform, it is used for [account linking](/CEK/Guides/Link_User_Account.md) when clients try to obtain [Clova access tokens](#ClovaAccessToken) or users try to use a certain extension. For more information, go to [https://tools.ietf.org/html/rfc6749](https://tools.ietf.org/html/rfc6749).

### SessionEndedRequest {#SessionEndedRequest}
A type of request message that notifies that a user has requested to end a certain mode or to stop the use of a certain [custom extension](#CustomExtension). For more information, see [Handling a custom extension request](/CEK/Guides/Build_Custom_Extension.md#HandleCustomExtensionRequest).

### Skill {#Skill}
An extension provided by Clova. To provide a skill to users, you must develop a [Clova extension](#ClovaExtension).

### Built-in skill {#BuiltinSkill}
A default skill on Clova devices such as LINE MUSIC, LINE: Free Calls & Messages, Weather, News, and Alarm Timer. For more information, go to [Clova > Clova Skill] (https://clova.line.me/clova-ai/).

### Slot {#Slot}
The information required to process a request declared to an [Intent](#Intent). A slot must be defined in pair with an intent. Clova analyzes a user request and extracts information specific to the slots. For more information, see [Defining an interaction model](/Design/Design_Guideline_For_Extension.md#DefineInteractionModel).

### Dialogue ID {#DialogID}
ID created every time a user initiates new speech input. Dialogue IDs are included when a client sends a [Recognize](/CIC/References/CICInterface/SpeechRecognizer.md#Recognize) [event](#Event) to [Clova Interface Connect](#CIC). Dialogue IDs are also included in a [directive](#Directive) when responses are returned from a server side to map those responses to corresponding event messages. The client must check the dialogue ID included in a directive and determine the event for which the directive is responding to. If the dialogue ID at the client side is different from that of the directive, the directive must be disregarded. For more information, see [Dialogue model](/CIC/CIC_Overview.md#DialogModel).

### Context {#Context}
The information on the state of a client. It is expressed with [context objects](#ContextObjects). For more information, see [Context](/CIC/References/Context_Objects.md).

### Message ID {#MessageID}
ID used to distinguish individual messages. All [events](#Event) and [directives](#Directive) have their own message IDs.

### Account linking {#AccountLinking}
Used when an [extension](#ClovaExtension) provides a third-party service that requires users to authenticate their account. For more information, see [Linking user account](/CEK/Guides/Link_User_Account.md).

### Sample utterance {#UserUtteranceExample}

A list of examples showing the input method of verbal user requests. You can define several example sentences for each [intent](#Intent). Example sentences are denoted with [slots](#Slot). For more information, see [Defining an interaction model](/Design/Design_Guideline_For_Extension.md#DefineInteractionModel).

### Session ID {#SessionID}
Used by [extensions](#ClovaExtension) to distinguish context of user requests. Generally, a one-time request has a unique session ID whereas a particular mode or multi-turn request has the same session ID. A session ID is created when [Clova Extensions Kit](#CEK) sends a user request to an extension. The same session ID is maintained for requests such as [LaunchRequest](#LaunchRequest) or when an extension sets the `response.shouldEndSession` field to `false`. For more information, see [Creating a custom extension](/CEK/Guides/Build_Custom_Extension.md).

### Event message {#Event}
Messages that are sent from a client to [Clova Interface Connect](#CIC). Event messages are used to send user requests (speech input) or to notify that a client state has changed.

### Directive message {#Directive}
Messages that are sent from [CIC](#CIC) to a client to control client actions. Directive messages are used when CIC returns a response to events from a client or when CIC sends information to a client under certain conditions.

### Client credentials {#ClientCredentialInfo}
Credentials obtained by registering a client in the [Clova Developer Center](#ClovaDeveloperConsole). The obtained credentials are used to generate a [Clova access token](#ClovaAccessToken). For more information, see [Creating Clova access tokens](/CIC/Guides/Interact_with_CIC.md#CreateClovaAccessToken).
