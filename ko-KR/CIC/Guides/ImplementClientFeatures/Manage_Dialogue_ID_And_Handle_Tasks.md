# 대화 ID 관리 및 작업 처리하기

[간접 대화 구조](/CIC/CIC_Overview.md#IndirectDialogue)의 이슈를 해결하기 위해 **대화 ID**라는 개념을 사용합니다. 클라이언트는 대화 ID와 관련하여 다음과 같은 내용을 수행해야 합니다.

* [대화 ID 생성하기](#CreatingDialogueID)
* [대화 ID에 따라 지시 메시지 처리하기](#HandleDirectivesByDialogueID)

## 대화 ID 생성하기 {#CreatingDialogueID}

**대화 ID**는 사용자의 요청을 식별하기 위해 사용자가 발화를 시작할 때마다 생성하는 식별자입니다. 클라이언트는 CIC에 전달한 사용자의 요청을 CIC로 보낼 때마다 마지막에 보낸 사용자 요청의 대화 ID를 기억해야하며, 이를 **마지막 대화 ID**로 부릅니다. **마지막 대화 ID**란 클라이언트가 CIC에게 마지막으로 보낸 [SpeechRecognizer.Recognize](/CIC/References/CICInterface/SpeechRecognizer.md#Recognize) 이벤트 메시지나 [TextRecognizer.Recognize](/CIC/References/CICInterface/TextRecognizer.md#Recognize) 이벤트 메시지에 포함된 대화 ID이며, 클라이언트는 이 마지막 대화 ID를 잘 저장해 두어야 하며, CIC로 사용자의 요청을 전달할 때마다 갱신해야 합니다.

클라이언트는 다음과 같이 동작을 수행해야 합니다.

![](/CIC/Assets/Images/CIC_Dialogue_ID_Creation.svg)

<ol>
  <li>사용자가 새로운 대화를 시작할 때마다 <strong>새로운 대화 ID를 생성</strong>(UUID 포맷 권장)합니다.</li>
  <li><a href="/CIC/References/CICInterface/SpeechRecognizer.md#Recognize">SpeechRecognizer.Recognize</a> 이벤트 메시지로 사용자의 요청을 CIC로 전달합니다. (텍스트 명령이면, <a href="/CIC/References/CICInterface/TextRecognizer.md#Recognize">TextRecognizer.Recognize</a> 이벤트 메시지)
    <ul>
      <li>이때 <a href="/CIC/References/CIC_API.md#Event">이벤트 메시지의 헤더</a>의 <code>dialogRequestId</code>에 새로 생성한 대화 ID를 포함시킵니다.</li>
    </ul>
  </li>
  <li>이벤트 메시지를 전송한 후 생성한 대화 ID를 <strong>마지막 대화 ID</strong>로 기록해 두어야 합니다.</li>
</ol>

<div class="danger">
<p><strong>Caution!</strong></p>
<p>마지막 대화 ID는 <strong>반드시 <a href="/CIC/References/CICInterface/SpeechRecognizer.md#Recognize">SpeechRecognizer.Recognize</a> 이벤트 메시지나 <a href="/CIC/References/CICInterface/TextRecognizer.md#Recognize">TextRecognizer.Recognize</a> 이벤트 메시지 전송을 완료한 후 갱신</strong>되어야 합니다. 마지막 대화 ID를 기억 또는 갱신하지 않으면 사용자의 갑작스런 요청 변경에 대응할 수 없게 됩니다. 이에 대한 자세한 설명은 <a href="/CIC/CIC_Overview.md#IndirectDialogue">간접 대화 구조</a>를 참조합니다.</p>
</div>

마지막 대화 ID를 업데이트했으면 클라이언트는 새 [대화 ID를 가진 지시 메시지를 처리하기](#HandleDirectivesByDialogueID) 위해 다음과 같은 것을 수행해야 합니다.

* 이전 대화 ID를 가진 지시 메시지의 내용을 사용자에게 제공하고 있다면 [기본 오디오 재생 규칙](/Design/Design_Guideline_For_Client_Hardware.md#AudioInterruptionRule)이나 [사용자 발화 시 오디오 재생 규칙](/Design/Design_Guideline_For_Client_Hardware.md#AudioInterruptionRuleForUserUtterance)을 참고하여 이를 중단해야 합니다.
* [메시지 큐](/CIC/Guides/Interact_with_CIC.md#ManageMessageQ)에서 이전 대화 ID를 가진 지시 메시지를 모두 폐기해야 합니다.

## 대화 ID에 따라 지시 메시지 처리하기 {#HandleDirectivesByDialogueID}

일반적으로 CIC는 사용자 요청에 대한 응답으로 지시 메시지를 클라이언트에게 보내며, 이 지시 메시지에 [클라이언트가 생성한 대화 ID](#CreatingDialogueID)를 포함시킵니다. 따라서, 대화 ID를 이용하면 CIC로부터 전달된 결과가 현재 사용자의 요청에 부합하는 응답인지 확인할 수 있습니다. 클라이언트는 대화 ID에 따라 지시 메시지를 다음과 같이 처리해야 합니다.

![](/CIC/Assets/Images/CIC_Handle_Directives_By_Dialogue_ID.svg)

우선, 클라이언트는 CIC로부터 수신한 지시 메시지가 [지시 메시지의 헤더](/CIC/References/CIC_API.md#Directive)에에 대화 ID를 포함하고 있는지 확인해야 합니다. 대화 ID가 포함된 지시 메시지를 수신했다면 **마지막 대화 ID**와 비교하고 그 결과에 따라 다음과 같이 처리합니다.

* **두 대화 ID가 서로 같으면**, 수신한 메시지를 [메시지 큐](/CIC/Guides/Interact_with_CIC.md#ManageMessageQ)에 추가하고 순서에 맞게 내용을 사용자에게 제공하면 됩니다.
* **두 대화 ID가 서로 다르면**, 수신한 지시 메시지를 폐기하면 됩니다.

만약, **지시 메시지가 대화 ID를 포함하고 있지 않으면**, 클라이언트는 **즉시** 수신한 지시 메시지를 처리해야 합니다. 대화 ID가 없는 지시 메시지는 주로 [downchannel](/CIC/References/CIC_API.md#EstablishDownchannel)을 통해 전달되며 대화를 방해하지 않는 백그라운드 서비스 동작을 요구합니다.
