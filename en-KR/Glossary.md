# Terms and abbreviations

<div class="note">
  <p><strong>Note!</strong></p>
  <p>This page is updated on an ongoing basis.</p>
</div>

### CEK
The abbreviation of [Clova Extension Kit](#CEK).

### CIC
The abbreviation of [Clova Interface Connect](#CIC).

### CIC API {#CICAPI}
The REST API that CIC provides to clients. Clients use CIC API to exchange information with Clova.

### Clova {#Clova}
[Clova](http://clova.ai) is an AI (artificial intelligence) platform developed and serviced by {{ book.TargetServiceForClientAuth }}. Clova recognizes user speech or images, analyzes them, and provides information or services that users have requested. Third-party developers, by leveraging the Clova technologies, can make a device or home appliance that provides an AI service. They can also offer their content or services to users through Clova.

### Clova access token {#ClovaAccessToken}
A means used by Clova to authorize a client when the client tries to send [events](#Event) to [Clova Interface Connect](#CIC). For more information, see [Creating Clova access tokens](/CIC/Guides/Interact_with_CIC.md#CreateClovaAccessToken).

### Clova developer console {#ClovaDeveloperConsole}
A <a target="_blank" href="{{ book.DeveloperConsoleURL }}">[web tool]</a> that provides the following features to the [Clova extension](#ClovaExtension) developers or to client devices that interact with the Clova platform.
* Registering a client device and obtaining client credentials for authentication (coming soon)
* [Registering](/DevConsole/Guides/CEK/Register_Extension.md) and [deploying](/DevConsole/Guides/CEK/Deploy_Extension.md) a Clova extension
* [Registering an interaction model](/DevConsole/Guides/CEK/Register_Interaction_Model.md)
* Viewing statistics related to Clova services (coming soon)

### Clova extension {#ClovaExtension}
A web application that provides extended capabilities to Clova for a more diverse user experience, including the capability of controlling IoT appliances at home or third-party services such as music, shopping, and banking. It is commonly referred to as an "extension" and the Clova platform currently supports and provides two types of Clova extensions. To regular users, the extension is referred to as a "skill."
* [Custom extension](#CustomExtension)
* [Clova Home extension](#ClovaHomeExtension)

### Clova Extensions Kit (CEK) {#CEK}
A platform that provides tools and interfaces for development and deployment of a Clova extension. It supports [communication between Clova and extensions](/CEK/CEK_Overview.md).

### Clova Home extension {#ClovaHomeExtension}
An extension that provides a service for controlling IoT appliances. For more information, see [Building Clova Home extensions](/CEK/Guides/Build_Clova_Home_Extension.md).

### Clova Home extension messages {#ClovaHomeExtMessage}
Messages used by [Clova Home extensions](#ClovaHomeExtension) when they exchange information with [Clova Extensions Kit](#CEK) to control IoT appliances. For more information, see [Clova Home extension messages](/CEK/References/CEK_API.md#ClovaHomeExtMessage).

### Clova Interface Connect (CIC) {#CIC}
A platform that serves as an interface between Clova and a client aiming to provide AI assistant services such as PC/mobile apps, mobile devices, or home appliances. For more information, see [CIC overview](/CIC/CIC_Overview.md).

### Clova app {#ClovaApp}

A Clova app developed by {{ book.OrientedService }} and deployed to the iOS or Android platform. These apps can send commands to Clova and also register and manage client devices.

### Clova auth API {#ClovaAuthAPI}
An API used by clients to obtain [Clova access tokens](#ClovaAccessToken). For more information, see [Clova auth API](/CIC/References/Clova_Auth_API.md).

### Content template {#ContentTemplate}
Standardized formats for displaying content returned from CIC. For more information, see [Content template](/CIC/References/Content_Templates.md).

### Context objects {#ContextObjects}
Objects that express the current [context information] of a client(#Context). For more information, see [Context](/CIC/References/Context_Objects.md).

### Custom extension {#CustomExtension}
An [extension](#ClovaExtension) that provides extended capabilities. A custom extension lets you provide third-party services such as music, shopping, or banking. For more information, see [Creating a custom extension](/CEK/Guides/Build_Custom_Extension.md).

### Custom extension messages {#CustomExtMessage}
Messages used by [Clova Extensions Kit](#CEK) and [custom extension](#CustomExtension) to exchange information. For more information, see [Custom extension messages](/CEK/References/CEK_API.md#CustomExtMessage).

### Device discovery {#Discovery}
A feature that provides client devices with a list of IoT appliances registered to a user account. For more information, see [Providing device discovery](/CEK/Guides/Build_Clova_Home_Extension.md#ProvideDeviceDiscovery).

### Downchannel {#Downchannel}
An [HTTP/2](#HTTP2) stream through which clients receive directives from [CIC](#CIC). For more information, see [Connecting with CIC](/CIC/Guides/Interact_with_CIC.md#ConnectToCIC).

### Extension {#Extension}
Another name for a [Clova extension](#ClovaExtension)

### Extension page {#ExtensionPage}

A page displayed when a specific extension is selected in the skill store Home (**extension service management** menu), and it provides a detailed description of the extension.

### HTTP/2 {#HTTP2}
The second version of the HTTP protocol. HTTP/2 is based on [SPDY](https://en.wikipedia.org/wiki/SPDY) and developed by the IETF (Internet Engineering Task Force). HTTP/2 is the enhanced version of HTTP 1.1, which was standardized in RFC 2068 in 1997 and was presented as a Proposed standard in December 2014 and approved by IESG on February 17, 2015. HTTP/2 was published as [<a href="https://tools.ietf.org/html/rfc7540" target="_blank">RFC 7540</a>] in May 2015.

### Intent {#Intent}
An intent is a segment that distinguishes the user requests for a Clova extension to handle. The intent is divided into two: a custom intent and a built-in intent. Before implementing a [custom extension](#CustomExtension), an [interaction model](#InteractionModel) consisting of a set of intents has to be defined. For more information, see [Defining an interaction model](/Design/Design_Guideline_For_Extension.md#DefineInteractionModel).

### IntentRequest {#IntentRequest}

A type of request message that sends the analysis details of a user request ([Intent](#Intent)) to a [custom extension](#CustomExtension). For more information, see [Handling a custom extension request](/CEK/Guides/Build_Custom_Extension.md#HandleCustomExtensionRequest).

### Interaction model {#InteractionModel}
A model that defines a rule to convert to the standardized format (JSON) for [Custom extension](#CustomExtension) to pass user voice requests to an extension. For more information, see [Defining an interaction model](/Design/Design_Guideline_For_Extension.md#DefineInteractionModel).

### LaunchRequest {#LaunchRequest}
A type of request message that notifies that a user has requested to start a certain mode or [custom extension](#CustomExtension). For more information, see [Handling a custom extension request](/CEK/Guides/Build_Custom_Extension.md#HandleCustomExtensionRequest).

### OAuth 2.0
A public standard for delegation of access permission. The protocol allows internet users to grant account access right to other web services or applications. On the Clova platform, it is used for [account linking](/CEK/Guides/Link_User_Account.md) when clients try to obtain [Clova access tokens](#ClovaAccessToken) or users try to use a certain extension. For more information, go to [https://tools.ietf.org/html/rfc6749](https://tools.ietf.org/html/rfc6749).

### SessionEndedRequest {#SessionEndedRequest}
A type of request message that notifies that a user has requested to end a certain mode or [custom extension](#CustomExtension). For more information, see [Handling a custom extension request](/CEK/Guides/Build_Custom_Extension.md#HandleCustomExtensionRequest).

### Skill {#Skill}

An extension or service provided to users by Clova. To provide a skill to users, you must develop a [Clova extension](#ClovaExtension).

### Skill Store {#SkillStore}

A platform designed to provide skills to users.

### Skill store home {#SkillStoreHome}

A page to display skills registered in the skill store. It is a term used to refer to the **extension service management** menu in the Clova app.

### Slot {#Slot}
Information necessary for processing a request declared in an [intent](#Intent). It must be defined in pair with the intent. Clova analyzes a user request and extracts information specific to the slots. For more information, see [Defining an interaction model](/Design/Design_Guideline_For_Extension.md#DefineInteractionModel).

### Dialogue ID {#DialogID}
A dialogue ID is created every time a user initiates new speech input. It is included when clients send [Recognize](/CIC/References/CICInterface/SpeechRecognizer.md#Recognize) [event messages](#Event) to [Clova Interface Connect](#CIC). Dialogue IDs are also included in [directive messages](#Directive) when responses are returned from a server side to map those responses to corresponding event messages. Clients check the dialogue ID included in a directive message and determine which directive message is responding to which event message. If the dialogue ID at the client side is different from that of the directive message, the directive message must be disregarded. For more information, see [Dialogue model](/CIC/CIC_Overview.md#DialogModel).

### Context {#Context}
Various states of a client. It is expressed with [context objects](#ContextObjects). For more information, see [Context](/CIC/References/Context_Objects.md).

### Message ID {#MessageID}
An identifier for distinguishing individual messages. All [events](#Event) and [directives](#Directive) have their own message IDs.

### Account linking {#AccountLinking}
Used when an [extension](#ClovaExtension) provides a third-party service that requires users to authenticate their account. For more information, see [Linking user account](/CEK/Guides/Link_User_Account.md).

### Sample utterance {#UserUtteranceExample}

A list of examples showing the input method of verbal user requests. You can define several example sentences for each [intent](#Intent). Example sentences are denoted with [slots](#Slot). For more information, see [Defining an interaction model](/Design/Design_Guideline_For_Extension.md#DefineInteractionModel).

### Session ID {#SessionID}
A session identifier used by [extensions](#ClovaExtension) to distinguish context of user requests. Generally, a one-time request has a unique session ID whereas a particular mode or multi-turn request has the same session ID. A session ID is created when [Clova Extensions Kit](#CEK) sends a user request to an extension. The same session ID is maintained when requests such as [LaunchRequest](#LaunchRequest) are made or when an extension sets the `response.shouldEndSession` field to `false`. For more information, see [Creating a custom extension](/CEK/Guides/Build_Custom_Extension.md).

### Event message {#Event}
Messages that are sent from clients to [CIC](#CIC). Event messages are used to send user requests (speech input) or notify that a client state has changed.

### Directive message {#Directive}
Messages that are sent from [CIC](#CIC) to the client to control client actions. Directives are used when CIC returns responses to events from clients or when CIC sends information to clients under certain conditions.

### Client credentials {#ClientCredentialInfo}
Credentials obtained by registering a client in the [Clova developer console](#ClovaDeveloperConsole). Credentials are used to obtain [Clova access tokens](#ClovaAccessToken). For more information, see [Creating Clova access tokens](/CIC/Guides/Interact_with_CIC.md#CreateClovaAccessToken).
