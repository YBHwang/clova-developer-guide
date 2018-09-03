# Utilizing user-input information
This tutorial will guide on how to make the Sample Dice extension created in [Building a basic extension](/CEK/Tutorials/Build_Simple_Extension.md) to roll more than one die depending on the user request. 

Voice commands of users can contain the action that needs to be performed by an extension and also additional information for the action. But first, let us recap on how to use the Sample Dice extension as described in [Tutorial introduction](/CEK/Tutorials/Introduction.md).

{% include "/CEK/Tutorials/BasicInformation/DICE_Sample_Dialog.md" %}

In the second dialogue, the user requested "Throw **2** dice." Here, "2" is the additional information required for an action called "throwing dice".

In an interaction, such additional information is called a [slot](/Design/Design_Guideline_For_Extension.md#Slot). For the extension to use the additional information, you must first identify the type of additional information that could be used and register corresponding slots when defining the interaction model. Clova can use these registered slots to recognize additional information in user requests.

The methods for handling additional information are as follows:
* Step 1. Registering slots to the interaction model (on the Clova developer console)
* Step 2. Implementing slot processing (on the extension server)
* Step 3. Testing the slot operation (on the Clova developer console)

## Step 1. Adding a slot to the interaction model {#Step1}
{% include "/CEK/Tutorials/UseBuiltinTypeSlots/Add_Builtin_Slot.md" %}

## Step 2. Implementing slot processing {#Step2}
{% include "/CEK/Tutorials/UseBuiltinTypeSlots/Implement_Slot_Handler.md" %}

## Step 3. Testing the slot action {#Step3}
{% include "/CEK/Tutorials/UseBuiltinTypeSlots/Test_Builtin_Type_Slots.md" %}

Now your Sample Dice extension can throw more than one die.
You can either have the extension throw a die multiple times in the same method or throw non-numeric dice.
