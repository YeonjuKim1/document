---
title: Slot 노드 
tags: [chatflow, basic]
keywords: Basic Conversation
summary: Slot 노드에 대한 이해와 설정 방법을 설명합니다.
sidebar: danbee_doc_sidebar
permalink: chatflow_slot.html
folder: danbeeDoc
previous: {
    title: Speak 노드, 
    url: chatflow_speak.html
}
next: {
    title: Split 노드,
    url: chatflow_split.html
}
---

{% include callout.html content="화면 위치 : 챗봇 만들기 > 챗봇 제작 > 주요 대화 > 대화 흐름" type="default" %}

## 개요 

Slot 노드는 Slot-filling 노드의 줄임말로 챗봇이 사용자의 의도를 파악하여 명령을 수행하는데 있어, 필수적으로 얻어야 하는 정보를 되물어볼 수 있는 노드입니다.

예를 들어 회의실 예약하는 의도라고 한다면 회의실 장소와 일자, 시간, 참여자 정보가 필요 것입니다. 그런데 챗봇에게 “일정 잡아줘” 라고만 요청한다면 챗봇 입장에서는 요청 내용만 가지고는 회의실을 예약할 수 없습니다. 
이런 경우 챗봇은 회의실을 예약하기 위한 기본적인 정보 (일자, 시간, 참여자, 장소)를 되물어봐야 하는데 이때, Slot 노드가 그러한 역할을 수행합니다.

만약 사용자가 “내일 A회의실 예약해줘” 라고 묻는다면, 챗봇이 회의실 예약하는데 필요한 기본 정보 일자, 시간, 참여자, 장소를 다시 되물어봐야 할까요?
Slot 노드에서는 사용자가 물어본 문장에서 ‘내일’ 이라는 일자와 ‘A회의실’ 이라는 장소 정보가 있기 때문에 굳이 ‘일자’ 와 ‘장소’ 정보를 되물을 필요가 없기 때문에 Slot 노드에서는 부족한 정보 참여자, 시간 정보만을 되묻게 됩니다. 

{% include image.html file="chatflow/Chatflow_slot_canvas.png"  caption="Slot 노드" %}

## 질문 설정
 
질문을 물어볼 경우에는 질문 대상과 대상에 대한 메시지가 있어야 합니다. 
질문설정 탭에서는 질문 대상을 파라미터로 지정할 수 있으며, 사용자가 질문에 대한 답변을 할 경우에 지정된 파라미터에 값이 저장되게 됩니다. 

Slot 노드는 질문하고자하는 항목 변수의 값이 이미 있는 경우에는 해당 질문을 하지 않습니다. 
변수의 값이 없는 경우에만 질문을 하여 중복 질문을 하지 않도록 설계되어 있습니다. 
그러나 변수 값이 있는 경우라도 재확인 차원에서도 질문을 해야하는 경우가 필요할 때는 '무조건 물어보기' 설정을 체크하면 됩니다. 

{% include image.html file="chatflow/Chatflow_slot_question.png"  caption="질문 설정" %}

### 변수값 물어보기

Slot 노드에서는 Listen 노드에 선언된 단어항목(parameter)들에 한해 값을 물어보기 위한 설정을 할 수 있습니다.
해당 시나리오는 'name' 변수값에 이름을 입력 받고 입력 받은 값을 메시지에 표시합니다.

{% include image.html file="chatflow/Chatflow_slot_sampleTest.png"  caption="변수값 물어보기 시나리오" %}

## 시간 설정

챗봇이 메시지를 대답하는 시간은 1초가 기본값으로 설정되어 있습니다. 챗봇이 바로 대답하기를 원하지 않을 경우, 얼마만큼 지연시킬것인지
시간을 밀리초(millisecond, ms) 단위로 설정할 수도 있습니다. (1초는 1000ms입니다.)

{% include image.html file="chatflow/chatflow_timedelay.png"  caption="메시지 시간 설정" %}


<!-- 
#### [의도파악] Listen 노드 설정

Listen 노드에 'name' 변수를 다음과 같이 선언합니다.

{% include image.html file="chatflow/Chatflow_slot_sampleListen.png"  caption="Listen 노드 설정" %}

#### [변수값 물어보기] Slot 노드 설정

Slot 노드에서는 'name' 값을 입력 받기 위해 다음과 변수를 지정하고 질문 메시지를 등록합니다. 

{% include image.html file="chatflow/Chatflow_slot_sampleSlot.png"  caption="Slot 노드 설정" %}

#### [변수값 표시] Speak 노드 설정

Speak 노드에서는 답변 메시지를 입력할때 변수 값을 표시하고 싶은 경우 #{변수명} 과 같이 표시하면 됩니다. 
해당 시나리오 실행시에는 #{변수명} 은 변수값으로 치환되어 보여지게 됩니다.

{% include image.html file="chatflow/Chatflow_slot_sampleSpeak.png"  caption="Speak 노드 설정" %}

#### 테스트

'변수값 표시' 시나리오를 테스트해 보면 Speak 노드에 입력된 메시시 중에 변수처리 된 부분은 #{name} 은 입력 받은 값이 치환되어 다음과 같은 결과가 나오게 됩니다. 

{% include image.html file="chatflow/Chatflow_slot_sampleTest.png"  caption="변수값 표시 테스트" %}
 -->


{% include bottom.html %}
