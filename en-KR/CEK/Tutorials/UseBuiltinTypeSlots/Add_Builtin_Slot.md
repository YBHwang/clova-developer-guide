You must modify the interaction model so that users can specify the number of dice to roll.

To do so, you must first decide on the type of slot information and declare the slot type in the interaction model. Then, add these slots to the relevant intent and help Clova recognize the slots by inputting user sample utterances that contain additional information.

### Declaring slot types to use
Depending on the type of additional information the slot is to hold, you must decide on the slot type. For example, the information type of the number of dice is number.

Commonly used information types are predefined in Clova so that it can be universally used by the extension, and this is called the [built-in slot type](/Design/Design_Guideline_For_Extension.md#BuiltinSlotType). You do not need to create a new slot type if it is already defined in the built-in slot type. For example, there is no need for you to create an information type for the number of dice as it is predefined as a `CLOVA.NUMBER` built-in slot type.

<div class="note">
  <p><strong>Note!</strong></p>
  <p>You can handle the information types unique to extension, which are not defined as built-in slot types, by defining them as <a href="/Design/Design_Guideline_For_Extension.md#CustomSlotType">custom slot types</a>.</p>
</div>

Connect to the <a href="{{ book.ServiceEnv.DeveloperConsoleURL }}/cek/#/list" target="_blank">Clova developer console</a> and declare the slot type to use in the Sample Dice extension as follows:

1. Click **{{ book.DevConsole.cek_edit }}** on the **{{ book.DevConsole.cek_interaction_model }}** item of the Sample Dice extension.
2. Click <img class="inlineImage" src="/CEK/Resources/Images/DevConsole_Plus_Button.png" /> next to **{{ book.DevConsole.cek_builder_list_title_slottype }}**.
3. Select the `CLOVA.NUMBER` checkbox in the table below **{{ book.DevConsole.cek_builder_new_slottype_builtin_title }}**.

  <img src="/CEK/Resources/Images/CEK_Tutorial_Builtin_Type_Slots_Register_Slot_Type.png" style="max-width:800px;"/>

4. Click **{{ book.DevConsole.cek_save }}** next to **{{ book.DevConsole.cek_builder_new_slottype_builtin_title }}**.

### Registering slots to an intent
The number of dice to roll is additional information required for the action of rolling dice. Since we registered the action of rolling the dice as an intent named `ThrowDiceIntent` in the first tutorial, we now need to register a slot to this intent to indicate the number of dice.
You can register the slot as follows on the same window that was previously used for declaring the slot type:

1. Select `ThrowDiceIntent`, a custom intent, below **{{ book.DevConsole.cek_builder_list_title_intent }}**.
2. Type in "diceCount" in the input field below **{{ book.DevConsole.cek_builder_intent_slot_title }}**.
3. Press Enter or click the <img class="inlineImage" src="/CEK/Resources/Images/DevConsole_Plus_Button.png" /> button next to the input field.
4. Click the **{{ book.DevConsole.cek_builder_utterance_select_slot }}** combo box next to the registered "diceCount."
5. On the displayed list, select `CLOVA.NUMBER` of the **{{ book.DevConsole.cek_builder_select_slottype_builtin }}** registered earlier.

  <img src="/CEK/Resources/Images/CEK_Tutorial_Builtin_Type_Slots_Add_Slot.png" style="max-width:800px;"/>

6. Click **{{ book.DevConsole.cek_save }}** on the top-right corner of the screen.

### Entering a sample utterance
In the first tutorial, we added a simple sample utterance for throwing a die. Now, we must enter a new sample utterance to specify the number of dice to roll using a slot.

On the same window used to register the slot, enter the sample utterance as follows:

1. Type in "Roll two dice" in the input field below **{{ book.DevConsole.cek_builder_intent_expression_title }}**.

  <img src="/CEK/Resources/Images/CEK_Tutorial_Builtin_Type_Slots_Sample_Utterance.png" style="max-width:800px;"/>

2. Press Enter click the <img class="inlineImage" src="/CEK/Resources/Images/DevConsole_Plus_Button.png" /> button.
3. Drag-and-select the text "Two" with the mouse from the list of registered sentences.
4. Select "diceCount" below **{{ book.DevConsole.cek_builder_slot_layer_select_slot }}**.

  <img src="/CEK/Resources/Images/CEK_Tutorial_Builtin_Type_Slots_Set_Slot.png" style="max-width:800px;"/>
5. Repeat steps 1-4 with sentences "Throw one" and "Roll five dice."
