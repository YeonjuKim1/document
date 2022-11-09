---
title: 시작 메시지
tags: [nlu, advanced]
keywords: Chatbot Management
summary: 챗봇이 사용자를 반기는 가장 첫 메시지를 설정합니다.
sidebar: danbee_doc_sidebar
permalink: welcome.html
folder: danbeeDoc
previous: {
    title: 챗봇 생성,
    url: chatbot_create.html
}
next: {
    title: 대화 의도,
    url: intent.html
}
---

{% include callout.html content="화면 위치 : 챗봇 만들기 > 챗봇 제작 > 시작 메시지" type="default" %}
{% include image.html file="welcome/01_welcome.png" %}

## 시작 메시지의 중요성
{% include image.html file="welcome/02_welcome.png" %}
시작 메시지를 상황에 맞게 설정하는 것이 **챗봇 만들기의 가장 중요한 첫단계**입니다.

시작 메시지는 챗봇에 대해 함축적으로 설명하고, 사용자의 흥미를 끌어내는 첫인상에 영향을 크게 미치기 때문입니다.


## 시작 메시지 만들기
시작 메시지는 [기본 시작 메시지], [캐로셀 시작 메시지], [대화 흐름 연결]중 필요에 따라 설정할 수 있습니다.

{% include image.html file="welcome/03_welcome.png" %}

### 기본 시작 메시지
간단한 문장을 이용해 시작 메시지를 작성합니다.

### 캐로셀 시작 메시지
캐로셀이라는 용어가 생소하실 텐데요. 카드뉴스 이미지를 생각하시면 됩니다. 단비에서는 챗봇 답변을 캐로셀형으로 나타내줄 수 있습니다. 이미지나 버튼없이도 캐로셀 답변을 제작할 수 있습니다.
{% include image.html file="welcome/04_welcome.png" %}
(단, 캐로셀 메시지는 채널별로 제약이 있을 수 있습니다.)

| 컴포넌트 | 제약사항 | 비고 |
|--------|-------|-------|
| 카드 갯수 | 최대 10개 |  |
| 선택지 버튼 | 최대 5개 | ※메신저 채널에 따라 다를 수 있음 |
| 퀵 리플라이 | 최대 10개 | ※메신저 채널에 따라 다를 수 있음 |
{: .table .table-striped}

### 캐로셀 엑셀 샘플 템플릿
1․ 엑셀로 작업을 하시려면 [샘플파일]을 내려받아 업로드해주세요.
{% include image.html file="welcome/05_welcome.png" %}

2․ 샘플파일을 참고하여, 각 칸에 알맞은 값을 써넣어 업로드하세요.
{% include image.html file="welcome/06_welcome.png" %}
  
<table class="table table-bordered">
    <colgroup>
        <col width="15%" />
        <col width="85%" />
    </colgroup>
    <tr>
        <th>ID<span style="color:red">(필수)</span></th>
        <td>(추후 지원예정)<br>다른 지식에서 해당하는 열의 답변을 불러올때 쓰는 호출값입니다. 자유롭게 변경가능합니다.<br>(예시) ID가 간편답변1일 때 → 🗣답변01 or #간편답변_캐로셀1</td>
    </tr>
    <tr>
        <th>이미지 URL</th>
        <td>답변과 함께 이미지를 내보냅니다. <br>URL 형태로만 넣을 수 있습니다.</td>
    </tr>
    <tr>    
        <th>버튼 값</th>
        <td>
            ▶ 버튼값 작성법 <br><br>
            1.웹 링크 버튼웹 링크 호출코드와 주소를 입력합니다.<br>(예시) 🔗https://www.naver.com or #링크_https://www.naver.com <br><br>
            2.내부 App 링크내부 App 링크 호출코드와 주소를 입력합니다.<br>(예시) 😀https://NMXWArA or #내부앱_https://NMXWArA <br><br>
            3.외부 App 링크외부 App 링크 호출코드와 주소를 입력합니다.<br>(예시)😎https://N347ccc or #외부앱_https://N347ccc <br><br>
            4. 전화걸기전화걸기 호출코드와 주소를 입력합니다.<br>(예시)📞01012345678 or #전화_01012345678 <br><br>            
            <b style="font-size: 4px">●</b> 캐로셀 일때 퀵리플라이 버튼의 값은 선택지문구와 전화걸기만 지원합니다.
        </td>
    </tr>
</table>

3․ [다운로드]를 클릭하시면 내가 작업한 캐로셀 답변을 엑셀(.xlsx)로 내려받으실 수 있습니다.
{% include image.html file="welcome/07_welcome.png" %}

### 대화 흐름 연결
대화 흐름을 이용해서 여러 상황에 적합한 시작 메시지를 만들어냅니다.
{% include image.html file="welcome/08_welcome.png" %}

{% include bottom.html %}
