You must test whether the Sample Dice extension properly handles the registered slot.

There are two test methods shown in the [first tutorial](/CEK/Tutorials/Build_Simple_Extension.md). One method is checking the operation of the interaction model on the Clova developer console and the other is checking the actual operation of the Clova app by registering a tester ID.
This tutorial checks the operation of the interaction model only.

Connect to the <a href="{{ book.DeveloperConsoleURL }}/cek/#/list" target="_blank">Clova developer console</a> and check that the Sample Dice extension correctly recognizes the number of dice by completing the following steps:
1. Click **{{ book.DevConsole.cek_edit}}** on the **{{ book.DevConsole.cek_interaction_model }}** items of the Sample Dice extension.
2. Click **{{ book.DevConsole.cek_builder_menu_build }}** on the top left section of the screen to build the interaction model.
3. Once the build is complete, select the **{{ book.DevConsole.cek_test }}** menu from the menu list on the left.
4. In **{{ book.DevConsole.cek_builder_test_expression_title }}**, type in a sentence to roll multiple dice. For example, type in "Roll two dice."
5. Press the Enter key or click **{{ book.DevConsole.cek_builder_test_request_test }}**.
6. Check that `ThrowDiceIntent` appears in the **{{ book.DevConsole.cek_builder_test_intent_result }}** field under the **{{ book.DevConsole.cek_builder_test_result_title }}** , `diceCount` appears in the **{{ book.DevConsole.cek_builder_test_slot_result }}** field, and that the correct number of dice appears in the **{{ book.DevConsole.cek_builder_test_slot_data}}** field.

	<img src="/CEK/Resources/Images/CEK_Tutorial_Builtin_Type_Slot_Test.png" style="max-width:800px;"/>

  <div class="note">
	<p><strong>Note!</strong></p>
	<p>If you have not registered an extension server that can be accessed externally, a "{{ book.DevConsole.cek_builder_test_no_response }}" message is displayed as a <strong>{{ book.DevConsole.cek_builder_test_service_response }}</strong>.</p>
	</div>

7. Repeat steps 4-6 with sentences such as "Roll ten dice" or "Throw four dice."

If the speech recognition is unsatisfactory, you can increase the probability of recognition by adding further types of sample utterances.
