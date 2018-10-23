You must test whether the Sample Dice extension handles the the help request built-in intent from the extension via an appropriate method.

There are two test methods shown in the [first tutorial](/CEK/Tutorials/Build_Simple_Extension.md). One method is checking the operation of the interaction model on the Clova developer console and the other is checking the actual operation of the Clova app by registering a tester ID.
This tutorial checks the operation of the interaction model only.

<div class="note">
  <p><strong>Note!</strong></p>
  <p>Built-in intents work by default even if not specified in the interaction model.
  We are planning to allow selective registration of built-in intents for extensions in the future.</p>
</div>

Follow the steps below to check whether the help request of the Sample Dice extension is operating properly:
1. Access the <a href="{{ book.ServiceEnv.DeveloperConsoleURL }}/cek/#/list" target="_blank">Clova developer console</a>.
2. Click **{{ book.DevConsole.cek_edit}}** on the **{{ book.DevConsole.cek_interaction_model }}** item of the Sample Dice extension.
3. Click **{{ book.DevConsole.cek_builder_menu_build }}** on the top left section of the screen to build the interaction model.
4. Once the build is complete, click the **{{ book.DevConsole.cek_test }}** menu from the menu list on the left.
5. Enter the sentence to request help in **{{ book.DevConsole.cek_builder_test_expression_title }}**. For example, enter "Give me the instructions."
6. Press Enter or click **{{ book.DevConsole.cek_builder_test_request_test }}**.
7. Check whether "Clova.GuideIntent" appears in the **{{ book.DevConsole.cek_builder_test_intent_result }}** field under the **{{ book.DevConsole.cek_builder_test_result_title }}**.

	<img src="/CEK/Resources/Images/CEK_Tutorial_Builtin_Intent_Test.png" style="max-width:800px;"/>

  <div class="note">
	<p><strong>Note!</strong></p>
	<p>If you have not registered an extension server that can be accessed externally, a "{{ book.DevConsole.cek_builder_test_no_response }}" message is displayed as a <strong>{{ book.DevConsole.cek_builder_test_service_response }}</strong>.</p>
	</div>
