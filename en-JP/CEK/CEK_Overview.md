# CEK Overview
This document provides details on Clova Extensions Kit (hereinafter referred to as "CEK"). This document will help you understand what CEK is and how it operates and includes CEK guides and references.

## What is CEK? {#WhatisCEK}
CEK is a platform that provides tools and interfaces for developing and deploying a Clova extension (hereafter referred to as "extension"). CEK supports communication between Clova and extensions. An extension is a web application that provides extended capabilities to Clova for a more diverse user experience, including the capability to control IoT appliances at home, or third-party services such as music, shopping and banking.

![](/CEK/Resources/Images/CEK_Concept_Diagram.png)

CEK provides the following features:
* [Interaction model](/Design/Design_Guideline_For_Extension.md#DefineInteractionModel) management (provided by the [Clova developer console](/DevConsole/ClovaDevConsole_Overview.md))
* Interface between Clova and extensions

## CEK interaction structure {#CEKInteractionStructure}
Clova recognizes user utterances inputted through CIC and analyzes it by referring to the [interaction model](/DevConsole/Guides/CEK/Register_Interaction_Model.md) registered in CEK. CEK delivers the analyzed user utterance information to the extension, and the extension must return the processed result of user request as a response. During this process, the exchanged messages follow the predefined message format. CEK and the extensions communicate via the <a href="https://tools.ietf.org/html/rfc2616" target="_blank">HTTP/1.1</a> protocol.

The diagram below shows the operating structure between the Clova platform and extension.

![](/CEK/Resources/Images/CEK_Interaction_Structure.png)


## Extension types {#ExtensionType}
The Clova platform currently supports and provides two types of extensions as follows:

* [Custom extension](/CEK/Guides/Build_Custom_Extension.md): An extension that provides tailored extended functions. A custom extension lets you provide third-party services such as music, shopping, or banking services.
* [Clova Home extension](/CEK/Guides/Build_Clova_Home_Extension.md): An extension that provides a service for controlling IoT appliances.
