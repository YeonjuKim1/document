---
title: API for Your App (이전버전)
tags: [api,channel, advanced]
keywords: Basic Conversation
summary:  단비Ai의 API를 활용하여 직접만든 대화채널에 연결할 수 있습니다. (이전버전)
sidebar: danbee_doc_sidebar
permalink: channel_native_app_old.html
folder: danbeeDoc
previous: {
    title: Frogue(챗봇전용 채팅창)오픈소스,
    url: channel_frogu_open.html
}
next: {
    title: 페이스북,
    url: channel_facebook.html
}
---

{% include important_developer.html content="이전 버전의 API 입니다. <br /> 새로운 버전의 API를 사용하세요." type="default" %}

## API for Your App (이전버전)
채널에서 danbee.Ai 와 연계하기 위해 제공되는 API들과 각 이벤트시에 처리되고 활용되는 데이터 항목에 대해 설명드리겠습니다.
{% include callout.html content="화면 위치 : [챗봇 만들기] > [챗봇 배포] > [메신저 연결]" type="default" %}
최신 버전의 API 는 [여기](channel_native_app.html)에서 확인하십시오.

## Welcome 메시지 API
대화 채널이 처음 사용자와 대화가 시작될때 챗봇이 먼저 인사를 하거나 메뉴 선택지를 제공하고자 할 경우 사용하는 API입니다.

### 기본 정보

| Field | Infomation |
|--------|--------|
| URL | https://danbee.ai/chatflow/welcome.do |
| METHOD | POST |
| HEADER | "Content-Type" : "application/json;charset=UTF-8" |
{: .table .table-striped}

### REQUEST BODY 정보 

| KEY | TYPE | Required | VALUE |
|--------|--------|--------|--------|
| chatbot_id | String | Yes | 챗봇아이디 |
| session_id | Number | No | 대화 세션 아이디(기존대화이력과 연결하여 시작메시지를 사용할 경우 전달) |
| parameters | JSON | No | 전체 파라미터 정보 (전달할 파라미터가 있는 경우 key, value 값을 전달해야 합니다.) |
{: .table .table-striped}

### RESPONSE 정보

| KEY | TYPE | Required | Description |
|--------|--------|--------|--------|
| version | String | No | 버전 |
| chatbot_id | String | No | 챗봇 아이디 |
| user_id | String | No | 사용자 아이디 |
| input_sentence | String | No | 사용자 대화 문장 |
| session_id | String | Yes | 대화 세션 아이디(대화창이 오픈되어 끝날 때까지의 대화이력을 식별할 수 있는 정보) |
| ins_id | String | Yes | 대화 흐름 인스턴스 아이디 (대화 흐름 단위의 대화가 진행될 때 마다 채번되는 인스턴스 아이디) |
| intent_id | String | Yes | 대화 의도 아이디 (Slot 노드, Carousel 노드에서 사용함) |
| node_id | String | Yes | 노드 아이디 |
| param_id | String | Yes | 파라미터 아이디 (Slot 노드, Carousel 노드 경우 사용됨) |
| ref_intent_id | String | No | 대화 의도 아이디 (참조) |
| chatflow_id | String | No | 대화 흐름 아이디 |
| another_result | JSON Array  | No | NLU 에서 파악한 다른 의도 결과 |
| result | JSON Array | No | 답변 메시지 결과 정보 |
| parameters | JSON | No | 파라미터 정보 (내부 파라미터 정보가 표시됩니다)|
| evaluate_setting | String | No | 채널 사용자 평가 문장 사용 여부 (제휴기능) |
| emotions | JSON | No | 감정 정보 (감성정보 설정시에만 값이 표시됩니다)|
| debugCode | String | No | 디버그 코드정보|
| debugMsg | String | No | 디버그 메시지|
| resultStatus | JSON | No | 결과 상태정보|
{: .table .table-striped}

#### RESPONSE Object 정보
* another_result Object

| KEY | Description |
|--------|--------|
| object_match_rate | 대화 의도 매칭률 |
| intent_name | 대화 의도 명 |
| intent_id | 대화 의도 아이디 |
| intent_alias | 대화 의도 별명 |
{: .table .table-striped}

 * result Object

| KEY | Description |
|--------|--------|
| message | 노드에 설정된 메시지를 표시합니다. |
| imgRoute | 메시지에 표시될 이미지 정보가 표시됩니다. |
| optionList | 버튼, 팝업, 전화연결과 같은 설정정보가 표시됩니다. |
| carouselList | 캐로셀 노드의 카드 정보가 표시됩니다 |
{: .table .table-striped}

 * parameters Object

| KEY | Description |
|--------|--------|
| 대화 의도에 정의된 파라미터 Key | 대화 흐름 시 전달된 파라미터 Value |
{: .table .table-striped}

 * emotions Object

| KEY | Description |
|--------|--------|
| positive | 긍정 확률 |
| neutral | 중립 확률 |
| negative | 부정 확률 |
{: .table .table-striped}

 * resultStatus Object
 
| KEY | Description |
|--------|--------|
| resultCmt | 결과 코멘트 |
| resultCode | 결과 코드 |
| resultMsg | 결과 메시지 |
{: .table .table-striped}

## 대화 엔진 API 
대화 채널에서 주고받는 대화를 처리하는 API. 사용자의 질문의 의도를 파악하고 그에 따른 대화 흐름을 관리하는 대화 흐름를 사용하는 API입니다.

### 기본 정보

| Field | Infomation |
|--------|--------|
| URL | https://danbee.ai/chatflow/engine.do |
| METHOD | POST |
| HEADER | "Content-Type" : "application/json;charset=UTF-8" |
{: .table .table-striped}

### REQUEST BODY 정보 

| KEY | TYPE | Required | VALUE |
|--------|--------|--------|--------|
| chatbot_id | String | Yes | 챗봇아이디 |
| input_sentence | String | Yes | 사용자 대화 문장 |
| user_id | String | No | 사용자 아이디 |
| session_id | String | No | 대화 세션 아이디(대화창이 오픈되어 끝날 때까지의 대화이력을 식별할 수 있는 정보) |
| ins_id | String | No | 대화 흐름 인스턴스 아이디 (대화 흐름 단위의 대화가 진행될 때 마다 채번되는 인스턴스 아이디) |
| intent_id | String | No | 대화 의도 아이디 (Slot 노드, Carousel 노드에서 사용함) |
| node_id | String | No | 노드 아이디 |
| param_id | String | No | 파라미터 아이디 (Slot 노드, Carousel 노드 경우 사용됨) |
| chatflow_id | String | No | 대화 흐름 아이디 |
| parameters | JSON | No | 전체 파라미터 정보 (전달할 파라미터가 있는 경우 key, value 값을 전달해야 합니다.) |
{: .table .table-striped}

#### REQUEST Object 정보

 * parameters Object

| KEY | Description |
|--------|--------|
| 대화 의도에 정의된 파라미터 Key | 대화 흐름 시 전달된 파라미터 Value |
{: .table .table-striped}

### RESPONSE 정보

| KEY | TYPE | Required | Description |
|--------|--------|--------|--------|
| version | String | No | 버전 |
| chatbot_id | String | No | 챗봇 아이디 |
| user_id | String | No | 사용자 아이디 |
| input_sentence | String | No | 사용자 대화 문장 |
| session_id | String | Yes | 대화 세션 아이디(대화창이 오픈되어 끝날 때까지의 대화이력을 식별할 수 있는 정보) |
| log_id | int | Yes | 챗봇 대화의 로그 아이디 ( 사용자 평가 시 사용 )  |
| ins_id | String | Yes | 대화 흐름 인스턴스 아이디 (대화 흐름 단위의 대화가 진행될 때 마다 채번되는 인스턴스 아이디) |
| intent_id | String | Yes | 대화 의도 아이디 (Slot 노드, Carousel 노드에서 사용함) |
| node_id | String | Yes | 노드 아이디 |
| param_id | String | Yes | 파라미터 아이디 (Slot 노드, Carousel 노드 경우 사용됨) |
| ref_intent_id | String | No | 대화 의도 아이디 (참조) |
| chatflow_id | String | No | 대화 흐름 아이디 |
| another_result | JSON Array | No | NLU 에서 파악한 다른 의도 결과 |
| result | JSON Array | No | 답변 메시지 결과 정보 |
| parameters | JSON | No | 파라미터 정보 (내부 파라미터 정보가 표시됩니다)|
| emotions | JSON | No | 감정 정보 (감성정보 설정시에만 값이 표시됩니다)|
| evaluate_setting | String | No | 채널 사용자 평가 문장 사용 여부 (제휴기능) |
| debugCode | String | No | 디버그 코드정보|
| debugMsg | String | No | 디버그 메시지|
| resultStatus | JSON | No | 결과 상태정보|
{: .table .table-striped}

#### RESPONSE Object 정보
* another_result Object

| KEY | Description |
|--------|--------|
| object_match_rate | 대화 의도 매칭률 |
| intent_name | 대화 의도 명 |
| intent_id | 대화 의도 아이디 |
| intent_alias | 대화 의도 별명 |

 * result Object

| KEY | Description |
|--------|--------|
| message | 노드에 설정된 메시지를 표시합니다. |
| imgRoute | 메시지에 표시될 이미지 정보가 표시됩니다. |
| optionList | 버튼, 팝업, 전화연결과 같은 설정정보가 표시됩니다. |
| carouselList | 캐로셀 노드의 카드 정보가 표시됩니다 |
{: .table .table-striped}

 * parameters Object

| KEY | Description |
|--------|--------|
| 대화 의도에 정의된 파라미터 Key | 대화 흐름 시 전달된 파라미터 Value |
{: .table .table-striped}

 * emotions Object

| KEY | Description |
|--------|--------|
| positive | 긍정 확률 |
| neutral | 중립 확률 |
| negative | 부정 확률 |
{: .table .table-striped}

 * resultStatus Object
 
| KEY | Description |
|--------|--------|
| resultCmt | 결과 코멘트 |
| resultCode | 결과 코드 |
| resultMsg | 결과 메시지 |
{: .table .table-striped}

## 노드 Option Object
노드 옵션 기능은 챗봇의 답변을 표시하는 speak 노드, slot 노드, carousel 노드에서 설정할 수 있습니다. <figure><img class="docimage" src="images/channel/nptive/nptive_app_node_option.png" alt="Frogue 셋팅" style="max-width: 800px"></figure>

 * 노드 옵션의 정보는 아래와 같습니다. 
 
| 구분 | 속성 설명 |
|--------|--------|
| id | 옵션 아이디가 순서대로 설정됩니다. |
| type | 6 가지의 옵션 구분값이 표시됩니다. |
| label | 채널 화면에서 보여질 명칭이 표시됩니다. |
| value | 채널에서 옵션에 따라 처리할 정보가 표시됩니다. |
{: .table .table-striped}

 * 노드 옵션의 유형에는 아래와 같습니다.
 
| 구분 | 유형값 | 기능설명 |
|--------|--------|--------|
| 선택지 | btn | 사용자의 답변을 선택지로 받기 위한 정보를 설정합니다. |
| Web Link | link | 웹 팝업을 호출하기위 위한 정보를 설정합니다. |
| 내부 App 실행 | inApp | 스마트폰에서 내부 App 실행을 하기 위한 정보를 설정합니다. |
| 외부 App 실행 | outApp | 스마트폰에서 외부 App 실행을 하기 위한 정보를 설정합니다. |
| Call (전화연결) | call | 스마트폰에서 전화연결을 하기 위한 정보를 설정합니다. |
| 대화 흐름 호출 | callFlow | 다른 대화 흐름 를 진행하기 위한 정보를 설정합니다. |
{: .table .table-striped}

## 사용자 대화 평가 API 
대화 채널에서 챗봇 대화에 대해서 사용자 평가를 처리하는 API. 챗봇에 대답에 대해 약 7가지의 평가를 진행할 수 있습니다.
 * like : 좋아요
 * love : 사랑해요
 * haha : 빵터짐
 * yay : 흐믓해요
 * wow : 놀라워요
 * sad : 슬퍼요
 * angry : 화나요
 * bad   : 싫어요

### 기본 정보

| Field | Infomation |
|--------|--------|
| URL | https://danbee.ai/chatflow/evaluateMsg.do |
| METHOD | POST |
| HEADER | "Content-Type" : "application/json;charset=UTF-8" |
{: .table .table-striped}

### REQUEST 정보 

| KEY | TYPE | Required | VALUE |
|--------|--------|--------|--------|
| log_id | int | Yes | 로그아이디 |
| evaluate_flag | String | Yes | 평가 |
{: .table .table-striped}

### RESPONSE 정보

| KEY | TYPE | Required | Description |
|--------|--------|--------|--------|
| code | String | Yes | 결과코드  |
| result | JSON | No | 결과 |
{: .table .table-striped}

#### RESPONSE Object 정보
* result Object

| KEY | Description |
|--------|--------|
| log_id | 로그아이디 |
| evaluate_flag | 평가 |
{: .table .table-striped}


#### RESPONSE resultStatus 유형

| Code | Description |
|--------|--------------------------|
| 200 | 정상코드 |
| 201 | 여러가지 의도로 해석되는 경우 |
| 400 | [NLU] 의도 파악이 안되었을 경우, EngineHandler 예외상황 |
| 404 | [Chatflow] 대화 의도에 해당하는 flow를 찾지 못할 경우, 노드가 10번이상 진행될 경우, EngineService 예외상황 |
| 405 | [Chatflow] flow 설정 문제 (답변 메시지를 못 찾았을 때, 분기 오류인 경우) |
{: .table .table-striped}

## 의도추론이력 조회 API
의도추론이력을 일자별로 조회 가능한 API. 제휴회원만 사용가능.

의도추론이력 다운로드 KEY 발급은 [의도추론 이력 관리-다운로드-api-key-관리](log.html#다운로드-api-key-관리) 에서 확인 가능합니다.

### 기본 정보

| Field | Infomation |
|--------|--------|
| URL | https://danbee.ai/chatbot/chatbotlog/nlu/retrieve |
| METHOD | GET |
| HEADER | "Content-Type" : "application/json;charset=UTF-8" |
{: .table .table-striped}

### REQUEST 정보 

| KEY | TYPE | Required | VALUE |
|--------|--------|--------|--------|
| chatbotId | String | Yes | 챗봇아이디 |
| baseDate | String | Yes | 기준일자 ( YYYYMMDD : 예 - 20180101 ) |
| apiKey | String | Yes | 챗봇 이력 다운로드 키 ( 의도추론이력 화면에서 생성 및 조회 가능 ) |
{: .table .table-striped}

### REQUEST 브라우저 테스트
아래의 예시로 브라우저에서 간단히 테스트가 가능함.

https://danbee.ai/chatbot/chatbotlog/nlu/retrieve?chatbotId=챗봇아이디&baseDate=년월일&apiKey=XXXXXXXXXXXXXXXXX

### RESPONSE 정보

| KEY | TYPE | Required | Description |
|--------|--------|--------|--------|
| logId | String | Yes | 의도추론이력 로그 아이디 |
| logSdatetime | Date | Yes | 의도추론 이력 시작일시 |
| logDatetime | Date | Yes | 의도추론 이력 일시 |
| inputSentence | String | Yes | 사용자 입력 문장 |
| intentId | String | No | 의도추론 아이디 |
| intentName | String | No | 의도추론 명 |
| resultScore | Number | No | 의도 추론율 |
| opIntentId | String | No | 의도추론 아이디 ( 의도추론 상세화면에서 설정된 값 ) |
| userId | String | Yes | 사용자 아이디 ( 채널별로 형식이 상이함 ) |
| chatSessionId | Number | Yes | 챗봇과 사용자 대화 세션 아이디 |
{: .table .table-striped}

## 대화이력 조회 API
대화 이력을 일자별로 조회 가능한 API. 제휴회원만 사용가능.

대화이력 다운로드 KEY 발급은 [대화 이력 관리-다운로드-api-key-관리](log.html#다운로드-api-key-관리) 에서 확인 가능합니다.

### 기본 정보

| Field | Infomation |
|--------|--------|
| URL | https://danbee.ai/chatbot/chatbotlog/chatflow/retrieve |
| METHOD | GET |
| HEADER | "Content-Type" : "application/json;charset=UTF-8" |
{: .table .table-striped}

### REQUEST 정보 

| KEY | TYPE | Required | VALUE |
|--------|--------|--------|--------|
| chatbotId | String | Yes | 챗봇아이디 |
| baseDate | String | Yes | 기준일자 ( YYYYMMDD : 예 - 20180101 ) |
| apiKey | String | Yes | 챗봇 이력 다운로드 키 ( 대화이력 화면에서 생성 및 조회 가능 ) |
{: .table .table-striped}

### REQUEST 브라우저 테스트
아래의 예시로 브라우저에서 간단히 테스트가 가능함.

https://danbee.ai/chatbot/chatbotlog/chatflow/retrieve?chatbotId=챗봇아이디&baseDate=년월일&apiKey=XXXXXXXXXXXXXXXXX

### RESPONSE 정보

| KEY | TYPE | Required | Description |
|--------|--------|--------|--------|
| logId | Number | Yes | 대화이력 로그 아이디 |
| sessionId | Number | Yes | 챗봇과 사용자 대화 세션 아이디 |
| flowId | String | Yes | 대화 흐름 아이디 |
| flowName | String | Yes | 대화 흐름 명 |
| nodeName | String | No | 노드 명 |
| nodeType | String | No | 노드 유형 |
| userId | String | No | 사용자 아이디 ( 채널별로 형식이 상이함 ) |
| message | String | No | 사용자 또는 챗봇의 대화내용 |
| createDate | String | Yes | 로그 생성 일시 |
| updateDate | String | Yes | 로그 수정 일시 |
| neg | Number | No | 대화내용 감정 부정 수치 |
| neu | Number  | No | 대화내용 감정 중립 수치 |
| pos | Number | No | 대화내용 감정 긍정 수치 |
{: .table .table-striped}


{% include bottom.html %}
