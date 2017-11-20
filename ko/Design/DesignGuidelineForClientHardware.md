# 클라이언트 기기 디자인 가이드라인

Clova가 탑재된 클라이언트 기기를 사용하는 사용자에게 일관된 UI/UX를 제공해야 사용자가 제품을 사용할 때 혼란을 느끼지 않고 편리하게 사용할 수 있습니다. 이를 위해 Clova에 접속하는 클라이언트 기기를 만들 때 다음과 같은 항목에 대해 디자인 가이드라인을 제공하고 있습니다.

* [클라이언트 상태](#ClientState)
* [버튼](#Button)
* [조명](#Light)
* [효과음](#SoundEffect)
* [화면](#Screen)

<div class="note">
  <p><strong>Note!</strong></p>
  <p>여기에서 언급되지 않은 가이드라인이나 스펙은 제조사의 재량이나 정책에 맞게 구현하시면 됩니다. 만약, 직접 판단하기 힘든 부분이 있다면 제휴 담당자에게 연락하시기 바랍니다.</p>
</div>

## 클라이언트 상태 {#ClientState}

사용자 음성 입력, Clova 음성 출력, 마이크 상태, 오류 발생(Clova 서비스 오류, 네트워크 오류 등) 등을 사용자가 쉽게 인지하거나 조작할 수 있도록 클라이언트 기기를 설계하거나 구현해야 합니다. 이를 위해 클라이언트 기기가 가지는 상태와 상태 사이의 동작 및 흐름을 이해해야 합니다. 다음은 클라이언트의 상태를 표현한 상태 다이어그램입니다.

![](/Design/Resources/Images/Clova-Client-State_Diagram.png)

각 상태에 대한 설명은 다음과 같습니다.

| 상태 이름                | 상태 설명                                                            |
|------------------------|----------------------------------------------------- --------------|
| Attending              | 클라이언트가 사용자의 음성 입력을 수신하려고 대기하는 상태                        |
| Error                  | 시스템 오류가 발생한 상태                                                |
| Hearing                | 클라이언트가 사용자의 음성 입력을 수신하는 중인 상태                            |
| Idle                   | 클라이언트가 아무런 작업도 수행하고 있지 않은 상태                             |
| Mute on                | 마이크 음소거를 설정한 상태                                               |
| Processing & reporting | Clova가 사용자의 음성 요청을 처리 중이거나 스피커를 통해 Clova 음성을 출력 중인 상태 |

위에서 언급된 상태는 [조명](#Light), [효과음](#SoundEffect), [화면](#Screen) 등을 통해 표현될 수 있으며, 상태 사이의 전이 동작은 사용자의 음성이나 [버튼](#Button) 조작, 환경 요인 등으로 실행되거나 발현될 수 있습니다.


## 버튼 {#Button}

클라이언트 기기는 사용자가 음성 대신 직접 기기를 제어할 수 있도록 버튼을 제공해야 합니다. 클라이언트가 사용자에게 어떤 버튼을 제공할 수 있는지 그리고 구현할 때 어떤 사항을 지켜야 하는지 설명합니다.

* [버튼 종류](#Bottons)
* [버튼 가이드라인](#ButtonGuideline)

### 버튼 종류 {#Buttons}

클라이언트 기기는 다음과 같은 버튼을 제공해야 합니다.

| 이름                        | 기능 설명                                                     | 필수 여부 |
|----------------------------|-------------------------------------------------------------|---------|
| 전원 버튼(Power)             | 기기 전원을 켜거나 끕니다.                                        | 필수      |
| 마이크 음소거 버튼(Mic mute)    | 마이크를 활성화하거나 비활성화합니다.                                | 필수      |
| 볼륨 업 버튼(Volume up)       | 스피커의 볼륨을 높입니다.                                         | 필수      |
| 볼륨 다운 버튼(Volume down)   | 스피커의 볼륨을 낮춥니다.                                          | 필수      |
| 재생/일시정지 버튼(Play/Pause) | 음악을 중지하거나 다시 재생합니다. 또는 진행 중인 작업을 중지합니다.         | 필수      |
| 음성 입력 수신 버튼(Wake up)   | 사용자의 음성 입력을 수신하는 모드(Attending 상태)로 전환합니다. 이는 사용자가 "클로바"라고 말하는 것과 같은 동작입니다. | 선택      |
| 무선랜 버튼 (Wi-Fi)          | 무선 네트워크를 연결하거나 해제합니다.                                 | 선택      |
| 블루투스 버튼 (Bluetooth)     | 블루투스 기기를 페어링/연결/해제 합니다.                              | 선택      |
| 초기화 버튼 (Reset)          | 기기를 초기화합니다.                                              | 선택      |

### 버튼 가이드라인 {#ButtonGuideline}

버튼을 제공할 때 다음과 같은 사항을 따라야 합니다.

* 전원 버튼과 마이크 음소거 버튼은 물리 버튼으로 제공할 것을 권고합니다.
* 전원 버튼과 마이크 음소거 버튼 이외의 버튼은 물리 버튼이나 터치 UI 형태의 버튼 등 각 제조사의 정책에 맞게 다양한 형태로 제공할 수 있습니다.
* 조작 빈도가 높은 주요 버튼은 조작이 용이하도록 전면 또는 상단에 배치하는 것을 권고합니다.
* 터치 UI 형태의 버튼을 제공하는 경우 사용자가 손을 뗄 때(touch release) 정의된 동작을 수행해야 합니다.
* (미리 정의된 버튼 조합이 없을 때) 2개 이상의 버튼 입력이 동시에 이루어지면 가장 먼저 인식된 버튼 입력의 기능만을 수행해야 합니다.
* 버튼 입력으로 이미 작업이 수행 중일 때 새로운 버튼 입력이 있으면, 이전 작업에 대한 피드백 효과를 멈추고 새로운 버튼 입력에 대한 피드백 효과를 제공해야 합니다.
* UI 화면이 제공되는 기기에 한 해 재생/일시 정지 버튼을 GUI 형태의 버튼으로 제공하는 것을 허용합니다.
* 버튼은 다음과 같은 방법으로 제공될 수 있습니다.
  - 단독의 버튼으로 기능을 제공하는 방법 (예, 블루투스 버튼 단독 제공)
  - 특정 필수 버튼의 길게 누름 동작을 활용하여 기능을 제공하는 방법 (예, 전원 버튼을 길게 눌러 초기화 기능을 제공)
  - 복수의 필수 버튼 조합을 활용하여 기능을 제공하는 방법 (예, 전원 버튼과 재생 버튼을 동시에 눌러 초기화 기능을 제공)

## 조명(LED) {#Light}

클라이언트 기기는 [클라이언트 상태](#ClientState)나 사용자 요청의 피드백 등을 표현하기 위해 조명(LED)을 제공해야 합니다. 클라이언트가 사용자에게 어떤 조명을 어떻게 제공해야 하는지 설명합니다.

* [조명 색상](#LightColor)
* [조명 효과](#LightEffect)
* [조명 가이드라인](#LightGuideline)

### 조명 색상 {#LightColor}

클라이언트는 다음과 같은 조명 색상을 사용해야 합니다.

| 조명 색상      | RGB 값             | 의미                                   | 필수 여부 |
|--------------|-------------------|---------------------------------------|--------|
| Green        | <span style="color:#32C864; font-size:150%; vertical-align:middle;">&#9724;</span> 50, 200, 100(#32C864)   | Attending 상태나                                 | 필수  |
| YellowGreen  | <span style="color:#B4FF00; font-size:150%; vertical-align:middle;">&#9724;</span> 180, 255, 0(#B4FF00)    | Clova 알림(Notification)                         | 필수  |
| Red          | <span style="color:#FF0000; font-size:150%; vertical-align:middle;">&#9724;</span> 255, 0, 0(#FF0000)      | 마이크 음소거, 네트워크 연결 오류, 배터리 부족 등의 오류 상황 | 필수  |
| warmWhite    | <span style="color:#EDE9E5; font-size:150%; vertical-align:middle;">&#9724;</span> 237, 233, 229(#EDE9E5)  | 스피커를 통한 Clova 음성 출력                        | 필수  |

다음은 Wave 기기의 조명 색상 적용 사례입니다.

| Green       | YellowGreen               | Red         | warmWhite   |
|-------------|-------------|-------------|-------------|-------------|
| ![](/Design/Resources/Images/Clova-Client-Light-Wave_Green.png) | ![](/Design/Resources/Images/Clova-Client-Light-Wave_YellowGreen.png) | ![](/Design/Resources/Images/Clova-Client-Light-Wave_Red.png) | ![](/Design/Resources/Images/Clova-Client-Light-Wave_warmWhite.png) |

### 조명 효과 {#LightEffect}

조명 효과는 [조명 색상](#LightColor)이 전달하는 의미를 바탕으로 사용자의 인지를 돕기 위해 좀 더 상세한 의미나 상태를 전달하는 용도로 사용됩니다.

다음은 Clova 기기 구현 시 조명이 나타내야 할 조명 효과와 이에 대한 Wave 적용 사례 및 설명을 제공하는 표입니다.

| 조명 효과                            | 설명                                      | Wave 적용 사례                                                      |
|------------------------------------|------------------------------------------|-------------------------------------------------------------------|
| 점등(Sustain)                       | 특별한 효과 없이 조명을 바로 켠 상태로 전환합니다.   | ![](/Design/Resources/Images/Clova-Client-Light-Wave_Sustain.png)              |
| 천천히 점멸 반복(Repeat blink slowly)  | 조명의 조도를 천천히 높였다가 낮추는 것을 반복합니다. | ![](/Design/Resources/Images/Clova-Client-Light-Wave_Repeat_Blink_Slowly.png)  |
| 천천히 소등(Fade out)                 | 조명의 조도를 천천히 낮추면서 마지막에 조명을 끕니다. | ![](/Design/Resources/Images/Clova-Client-Light-Wave_Fade_Out.png)             |

다음은 클라이언트의 [상태 및 동작](#ClientState)을 조명으로 어떻게 표현해야 하는지 나타낸 표입니다.

| 상태 설명                    | 조명 효과 적용                | 필수 여부 |
|----------------------------|----------------------------|---------|
| Attending 상태              | Green 조명 점등              | 필수     |
| End 상태                    | warmWhite 조명 천천히 소등     | 필수     |
| Error 상태                  | Red 조명 천천히 점멸 반복       | 필수     |
| Mute on 상태                | Red 조명 점등                | 필수     |
| Processing & reporting 상태 | warmWhite 조명 천천히 점멸 반복 | 필수     |
| Mute on 상태 해제            | Red 조명 천천히 소등           | 필수     |
| 대기 시간 초과한 직후           | Green 조명 천천히 소등         | 필수     |

### 조명 가이드라인 {#LightGuideline}

조명을 제공할 때 다음과 같은 사항을 따라야 합니다.
  - 1 미터 내의 거리에서 시력이 0.7인 사람이 [조명 색상](#LightColor)을 구분할 수 있어야 합니다.
  - 조명 색상에 정의된 의미 외에 다른 상태나 의미를 적용하지 않을 것을 권고합니다.
  - 사용자가 그래픽 RGB 값의 색과 조명 색상이 동일하다고 인지할 수 있도록 조명 색상을 적용해야 합니다.
  - 필수로 표현해야 하는 [조명 효과](#LightEffect) 외에도 기기 부팅, 스피커 볼륨 조절, 충전 상태, 버튼 피드백과 같이 상황에 적절하거나 제조사의 UX 정책에 따라 조명 색상과 조명 효과를 추가할 수 있습니다.
  - 하나의 조명 색상이나 효과에 너무 많은 의미나 상태를 표현하지 않을 것을 권고합니다.
  - 화면이 제공되지 않는 기기는 조명의 밝기 등을 이용하여 기기의 스피커 볼륨 수준을 표시할 것을 권고합니다.
  - 이동이 가능한 배터리 탑재 모델은 배터리 충전 상태를 조명으로 파악할 수 있게 구현할 것을 권고합니다.

## 효과음 {#SoundEffect}

클라이언트는 기기의 상태나 사용자 요청의 피드백 등을 표현하기 위해 [조명](#Light)뿐만 아니라 효과음을 함께 제공해야 합니다. 클라이언트가 사용자에게 어떤 상황에 어떤 효과음을 제공해야 하는지 설명합니다.

* [효과음 종류](#SoundEffects)
* [효과음 가이드라인](#SoundEffectGuideline)

### 효과음 종류 {#SoundEffects}

클라이언트의 [상태](#ClientState) 표현을 위해 다음과 같은 효과음을 제공해야 합니다.

| 상태 설명                   | 효과음 샘플                     | 필수 여부 |
|---------------------------|---------|------------------------------|---------|
| Attending 상태 진입         | <audio title="Attending" controls><source src="./Resources/Sounds/Clova-Client-SoundEffect-Attending.wav" type="audio/wav" /></audio> | 필수     |
| Error 상태 진입             | <audio title="Attending" controls><source src="./Resources/Sounds/Clova-Client-SoundEffect-Error.wav" type="audio/wav" /></audio>     | 필수     |
| Mute on 상태 진입           | <audio title="Attending" controls><source src="./Resources/Sounds/Clova-Client-SoundEffect-Mute_On.wav" type="audio/wav" /></audio>   | 필수     |
| Mute off 상태 해제          | <audio title="Attending" controls><source src="./Resources/Sounds/Clova-Client-SoundEffect-Mute_Off.wav" type="audio/wav" /></audio>  | 필수     |

### 효과음 가이드라인 {#SoundEffectGuideline}

효과음을 제공할 때 다음과 같은 사항을 따라야 합니다.

* 제공하는 효과음 음원을 그대로 사용할 것은 권고합니다.
* 제공하는 효과음 외에도 상황에 적절하거나 제조사의 UX 정책에 따라 효과음을 추가할 수 있습니다.
* 사용자는 각 상황을 소리로 인지할 수 있어야 합니다.
* 조명 효과나 화면의 상황에 맞게 일관성있는 효과음을 제공해야 합니다.
* 버튼 피드백에 대한 효과음을 제공하는 경우 버튼의 물성과 촉감에 어울리는 효과음을 제공해야 합니다.


## 화면 {#Screen}

클라이어언트의 디스플레이 장치를 통해 화면에 다음과 같은 UI 항목을 제공해야 합니다.

* [부팅 화면](#BootingScreen)
* [로고 표시](#DisplayingLogo)
* [Voice agent](#VoiceAgent)

### 부팅 화면 {#BootingScreen}

기기를 켠 후 부팅이 완료될 때까지 표시되는 화면입니다. 부팅 화면은 주로 로고가 표시되며 Clova의 로고를 다른 로고와 조합하지 않고 단독으로 화면에 표시합니다.

<ul>
  <li>
    <p><strong>좋은 예</strong></p>
    <img src="/Design/Resources/Images/Clova-Client-Partner_Logo_on_Loading_Screen.png" /> <img src="/Design/Resources/Images/Clova-Client-Clova_Logo_on_Loading_Screen.png" />
  </li>
  <li>
    <p><strong>나쁜 예</strong></p>
    <img src="/Design/Resources/Images/Clova-Client-_Logo_on_Loading_Screen_Bad_Example1.png" /> <img src="/Design/Resources/Images/Clova-Client-_Logo_on_Loading_Screen_Bad_Example2.png" />
  </li>
</ul>

### 로고 표시 {#DisplayingLogo}

Clova가 제공하는 UI 화면에 Clova 로고를 다음과 같은 레이아웃으로 배치할 수 있습니다.

* [로고 레이아웃 A](#LogoLayoutA)
* [로고 레이아웃 B](#LogoLayoutB)
* [로고 레이아웃 C](#LogoLayoutC)

#### 로고 레이아웃 A {#LogoLayoutA}

화면 하단의 일부나 전체를 덮는 UI 화면으로 Clova 로고가 좌측 상단에 배치되는 레이아웃입니다.

![](/Design/Resources/Images/Clova-Client-Logo_Display-Layout_A-Bottom_Overlay.png) ![](/Design/Resources/Images/Clova-Client-Logo_Display-Layout_A-Full_Screen_Overlay.png)

* Clova 로고는 좌측 상단에 배치되어야 합니다.
* Clova 로고의 투명도(Opacity)는 100%로 지정할 것을 권장합니다.

다음은 로고 레이아웃 A의 화면 예시입니다.

![](/Design/Resources/Images/Clova-Client-Logo_Display-Layout_A-Bottom_Overlay_Example.png) ![](/Design/Resources/Images/Clova-Client-Logo_Display-Layout_A-Full_Screen_Overlay_Example.png)

#### 로고 레이아웃 B {#LogoLayoutB}

[로고 레이아웃 A](#LayboutA)와 비슷하게 화면 하단의 일부나 전체를 덮는 UI 화면으로 Clova 로고가 우측 상단에 배치되는 레이아웃입니다.

![](/Design/Resources/Images/Clova-Client-Logo_Display-Layout_B-Bottom_Overlay.png) ![](/Design/Resources/Images/Clova-Client-Logo_Display-Layout_B-Full_Screen_Overlay.png)

* Clova 로고는 우측 상단에 배치되어야 합니다.
* Clova 로고의 투명도(Opacity)는 100%로 지정할 것을 권장합니다.

다음은 로고 레이아웃 B의 화면 예시입니다.

![](/Design/Resources/Images/Clova-Client-Logo_Display-Layout_B-Bottom_Overlay_Example.png) ![](/Design/Resources/Images/Clova-Client-Logo_Display-Layout_B-Full_Screen_Overlay_Example.png)

#### 로고 레이아웃 C {#LogoLayoutC}

단순 텍스트 형태의 결과를 표현하는 화면에서 Clova 로고가 상단에 배치되는 레이아웃입니다.

![](/Design/Resources/Images/Clova-Client-Logo_Display-Layout_C.png)

* Clova 로고는 상단에 배치되어야 합니다.
* 콘텐츠의 출처는 콘텐츠 하단에 표시해야 합니다.

다음은 로고 레이아웃 C의 화면 예시입니다.

![](/Design/Resources/Images/Clova-Client-Logo_Display-Layout_C_Example.png)

### Voice agent {#VoiceAgent}

Voice agent는 사용자의 음성 입력 수신, Clova 음성 출력 등 Clova 음성 동작과 관련된 상태를 표시하는 UI입니다. 화면을 가진 클라이언트 기기는 Voice agent를 표현해야 합니다. Voice agent에서 사용하는 색상이 무엇이고 voice agent의 타입에 따라 동작 및 상태를 어떻게 표현해야 하는지 설명합니다.

* [Voice agent 색상](#VoiceAgentColor)
* [Bar 타입](#BarType)
* [Icon A 타입](#IconAType)
* [Icon B 타입](#IconBType)

#### Voice agent 색상 {#VoiceAgentColor}

클라이언트는 다음과 같은 색상을 사용하여 voice agent에서 [클라이언트의 상태](#ClientState)를 표현할 수 있어야 합니다.

| 색상 이름      | RGB 값             | 의미                                   | 필수 여부 |
|--------------|-------------------|---------------------------------------|--------|
| Green1       | <span style="color:#12D5B2; font-size:150%; vertical-align:middle;">&#9724;</span> 18, 213, 178(#12D5B2)   | 사용자 음성 입력 수신                                 | 필수  |
| Green2       | <span style="color:#05D484; font-size:150%; vertical-align:middle;">&#9724;</span> 5, 212, 132 (#05D484)    | Clova 알림(Notification)                         | 필수  |
| Red          | <span style="color:#FF0000; font-size:150%; vertical-align:middle;">&#9724;</span> 255, 0, 0(#FF0000)      | 마이크 음소거, 네트워크 연결 오류, 배터리 부족 등의 오류 상황  | 필수  |
| warmWhite    | <span style="color:#EEFFFC; font-size:150%; vertical-align:middle;">&#9724;</span> 238, 255, 252(#EEFFFC)  | 스피커를 통한 Clova 음성 출력                          | 필수  |

#### Bar 타입 {#BarType}

Bar 타입의 voice agent는 아래와 같이 긴 막대 형태로 표시되며 음성 표시 텍스트, 상태 표현 색, 로고 구성되며, 상황에 따라 아이콘이 포함될 수 있습니다. 다음은 Bar 타입의 voice agent가 표시된 예입니다.

![](/Design/Resources/Images/Clova-Client-Voice_Agent-Bar_Type.png)

Bar 타입의 voice agent는 상황에 따라 다음과 같이 표현되어야 합니다.

![](/Design/Resources/Images/Clova-Client-Voice_Agent-Bar_Type_UIs.png)

| 상태 이름                | 애니메이션 효과                                                                  |
|------------------------|------------------------------------------------------------------------------|
| Attending              | Green1 색상의 bar가 1초 내로 서서히 표시되어야 합니다.                                  |
| Hearing                | 말소리 크기에 따라 중앙부터 warmWhite, Green2 색상 순으로 색상 영역이 확장되어야 합니다.      |
| Processing & reporting | warmWhite 색상 영역이 좌우로 움직여야 합니다.                                        |
| Mute on                | Red 색상의 bar와 음소거 또는 마이크 아이콘이 나타나고, 2초 후에 아이콘이 사라져야 합니다.       |
| Error                  | Red 색상의 bar와 오류 아이콘이 나타나고, 2초 후에 아이콘은 사라져야 합니다.                  |

<div class="ignoreOnPDF">
다음은 Bar 타입 voice agent가 동작하는 모습을 보여줍니다.

<ul>
  <li>
    <p><strong>Clova 사용 가능 상황(Attending, Hearing, Processing & reporting)</strong></p>
    <img src="/Design/Resources/Images/Clova-Client-Voice_Agent-Bar_Type_Example1.gif" />
  </li>
  <li>
    <p><strong>Clova 사용 불가 상황(Mute on, Error)</strong></p>
    <img src="/Design/Resources/Images/Clova-Client-Voice_Agent-Bar_Type_Example2.gif" />
  </li>
</ul>
</div>

<div class="note">
  <p><strong>Note!</strong></p>
  <p>Bar 타입 UI는 추후 내용이 업데이트 될 예정이오니 참고하시기 바랍니다.</p>
</div>

#### Icon A 타입 {#IconAType}

Icon A 타입의 voice agent는 아래와 같이 왼쪽에 아이콘 형태로 표시되며 음성 표시 텍스트, 상태 표현 색, 로고 구성되며, 상황에 따라 아이콘이 포함될 수 있습니다. 다음은 Icon A 타입의 voice agent가 표시된 예입니다.

![](/Design/Resources/Images/Clova-Client-Voice_Agent-Icon_A_Type.png)

Icon A 타입의 voice agent는 상황에 따라 다음과 같이 표현되어야 합니다.

![](/Design/Resources/Images/Clova-Client-Voice_Agent-Icon_A_Type_UIs.png)

| 상태 이름                | 애니메이션 효과                                                                 |
|------------------------|-----------------------------------------------------------------------------|
| Loading                | Green1 색상의 원을 그리며 표시되어야 합니다.  <div class="note"><p><strong>Note!</strong></p><p>Loading 상태는 사용자의 입력 수신을 받기 위해 <a href="#VoiceAgent">voice agent</a>를 준비하는 상태를 의미합니다. 화면이 있는 장치의 경우에만 적용되는 상태이며 voice agent 그래픽을 표현하기 위해 준비하는 상황을 표현해야 합니다.</p></div>                    |
| Attending              | 애니메이션 효과가 없는 Green1 색상의 원이 표시됩니다.                                               |
| Hearing                | 말소리 크기에 따라 원의 색을 아래에서 위로 warmWhite, Green2 색상 순으로 생상 영역이 확장되어야 합니다.     |
| Processing & reporting | Green2, warmWhite 색상이 원을 따라 움직여야 합니다.                                              |
| Mute on                | Red 색상의 음소거 또는 마이크 아이콘이 나타나고, "마이크 음소거 상태입니다."라는 텍스트가 표시되어야 합니다.      |
| Error                  | Red 색상의 오류 아이콘이 나타나고, 오류를 설명하는 간략한 텍스트가 표시되어야 합니다.                        |

<div class="ignoreOnPDF">

다음은 Icon A 타입 voice agent가 동작하는 모습을 보여줍니다.

<ul>
  <li>
    <p><strong>Clova 사용 가능 상황(Loading, Attending, Hearing, Processing & reporting)</strong></p>
    <img src="/Design/Resources/Images/Clova-Client-Voice_Agent-Icon_A_Type_Example1.gif" />
  </li>
  <li>
    <p><strong>마이크 음소거 상태(Mute on)</strong></p>
    <img src="/Design/Resources/Images/Clova-Client-Voice_Agent-Icon_A_Type_Example2.gif" />
  </li>
  <li>
    <p><strong>시스템 오류 상태(Error)</strong></p>
    <img src="/Design/Resources/Images/Clova-Client-Voice_Agent-Icon_A_Type_Example3.gif" />
  </li>
</ul>

</div>

#### Icon B 타입 {#IconBType}

Icon B 타입은 앱 타입의 클라이언트 즉 모바일 기기에서 voice agent를 표현할 때 사용됩니다. 다음은 Icon B 타입의 voice agent가 표시된 예입니다.

![](/Design/Resources/Images/Clova-Client-Voice_Agent-Icon_B_Type.png)

Icon B 타입의 voice agent는 상황에 따라 다음과 같이 표현되어야 합니다.

![](/Design/Resources/Images/Clova-Client-Voice_Agent-Icon_B_Type_UIs.png)

| 상태 이름                | 애니메이션 효과                                                                 |
|------------------------|-----------------------------------------------------------------------------|
| Idle                   | 애니메이션 효과가 없는 warmWhite 색상의 아이콘을 표시합니다.                             |
| Loading                | Green1 색상으로 아이콘 주변의 원을 그리며 표시되어야 합니다.  <div class="note"><p><strong>Note!</strong></p><p>Loading 상태는 사용자의 입력 수신을 받기 위해 <a href="#VoiceAgent">voice agent</a>를 준비하는 상태를 의미합니다. 화면이 있는 장치의 경우에만 적용되는 상태이며 voice agent 그래픽을 표현하기 위해 준비하는 상황을 표현해야 합니다.</p></div>                    |
| Attending              | 애니메이션 효과가 없는 Green1 색상의 아이콘을 표시합니다. 표시됩니다.                                              |
| Hearing                | warmWhite, Green2 색상 순으로 표시된 영역이 Green1 색상의 원 위에서 원을 그리며 표시되어야 합니다.                   |
| Processing & reporting | warmWhite, Green2 색상 순으로 아이콘 주변의 원을 그리며 표시되어야 합니다.                                       |
| Mute on                | Red 색상의 음소거 또는 마이크 아이콘이 표시되어야 합니다.                                                       |
| Error                  | Red 색상의 오류 아이콘이 표시되어야 합니다.                                                                  |

다음은 Icon B 타입 voice agent 상태 중 애니메이션 효과가 포함된 상태에서 voice agent가 동작하는 모습을 보여줍니다.

<div class="ignoreOnPDF">

<ul>
  <li>
    <p><strong>Clova 사용 가능 상황(Loading, Hearing, Processing & reporting)</strong></p>
    <img src="/Design/Resources/Images/Clova-Client-Voice_Agent-Icon_B_Type_Example1.gif" />
  </li>
  <li>
    <p><strong>마이크 음소거 상태(Mute on)</strong></p>
    <img src="/Design/Resources/Images/Clova-Client-Voice_Agent-Icon_B_Type_Example2.gif" />
  </li>
  <li>
    <p><strong>시스템 오류 상태(Error)</strong></p>
    <img src="/Design/Resources/Images/Clova-Client-Voice_Agent-Icon_B_Type_Example3.gif" />
  </li>
</ul>

</div>