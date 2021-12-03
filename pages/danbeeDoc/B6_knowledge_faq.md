---
title: FAQ
tags: [nlu, advanced]
keywords: 지식 라이브러리, Knowledge Library, FAQ+, FAQ, 엑셀, 스프레드시트
summary: 단답형 대화컨텐츠를 엑셀형태로 쉽게 관리할 수 있습니다.
sidebar: danbee_doc_sidebar
permalink: knowledge_faq.html
folder: danbeeDoc
previous: {
    title: FAQ+,
    url: knowledge_faq2.html
}
next: {
    title: Sheet,
    url: knowledge_sheet.html
}
---

{% include callout.html content="위치 : 챗봇 만들기 > 그룹내 챗봇 공통 > 지식 라이브러리" type="default" %}

## 보다 더 쉬운 대화콘텐츠 관리
지식 라이브러리는 빠르게 검색형 챗봇을 만들고, 엑셀처럼 쉽게 대화컨텐츠를 관리할 수 있는 단비의 새로운 챗봇 제작 도구입니다. 엑셀과 같은 스프레드시트에 잘 정리해놓으면 챗봇이 정리된 정보를 가져가 답변에 활용합니다. 단비Ai에서는 4가지 모델을 구상하고 있습니다. 그 중 FAQ기능이 먼저 오픈되었습니다. 지속적으로 업데이트 될 예정이니 많은 관심과 응원 부탁드립니다.

## FAQ 타입의 지식
FAQ(Frequently Asked Questions)는 가장 빈번하게 물어보는 질문들을 의미합니다. 기업들은 보통 엑셀로 질문과 답을 정리합니다. 챗봇을 담당하는 사람은 여러 부서에서 FAQ로 정리할 수 있는 내용을 취합하기도 하는데 이때도 엑셀이 활용됩니다. 엑셀로 잘 정리만 되어 있다면 단답형 FAQ챗봇을 빠르게 만들 수 있습니다.

{% include image.html file="knowledge/knowledge_library00.png" alt="엑셀만 할 줄 알면, 챗봇을 만들 수 있다." caption="엑셀만 할 줄 알면, 챗봇을 만들 수 있다." %}
  
  
  
### 빠르게 FAQ 지식 라이브러리 경험하는 방법
[FAQ챗봇 튜토리얼](/tutorial_faq.html)에서 FAQ위자드, 셀라몬을 이용하면 쉽게 FAQ지식을 활용한 챗봇을 만들어 보실 수 있습니다.

### FAQ 지식 만드는 방법
1. [그룹 관린 > 그룹 챗봇 > 지식 라이브러리] 메뉴에 들어갑니다. 
2. [+지식 생성]버튼을 클릭합니다.
3. 지식 유형을 선택하는 화면에서 FAQ를 선택합니다. 샘플파일을 다운로드하여 FAQ정보를 취합, 정리하는데 활용하실 수 있습니다.
4. 컨텐츠 관리에서 [직접 입력]하거나 [업로드]할 수 있습니다.
5. 직접입력은 웹화면에서 제공되는 스프레드 시트에 직접 입력하는 방식이며, 다른 스프레드시트 파일에서 여러 셀을 복사/붙여넣기를 할 수 있습니다.
6. 업로드는 엑셀파일(확장자 xls, xlsx)을 지원합니다.
7. 정보가 모두 등록되고 나면 [생성]을 클릭합니다.
8. 생성된 데이터는 언제든 수정이 가능합니다.

{% include image.html file="knowledge/knowledge_library01.png" alt="스프레드 시트 형태로 정리된 FAQ지식" caption="스프레드 시트 형태로 정리된 FAQ지식" %}


### FAQ 지식을 챗봇에 연결하는 방법
1. 연결하고자 하는 챗봇이 선택된 상태에서, [챗봇 만들기 > 고급 설정 > 지식 답변 설정] 메뉴로 이동합니다.
2. 지식 답변 관리의 FAQ유형탭에 지식 라이브러리 연결관리의 [사용안함] 버튼을 클릭하여 [사용함]으로 변환합니다.
3. [사용함]으로 활성화된 버튼 아래 [FAQ지식을 선택해주세요]를 클릭합니다.
4. 앞서 FAQ 지식 만드는 방법을 통해 등록한 지식을 선택합니다.
5. [변경내용 저장]을 클릭하여 연결을 마칩니다.
6. 연결을 마치고 나면 [대화 의도]로 추론되지 않은 경우, 지식 라이브러리의 FAQ지식에 있는 정보에서 응답할 수 있는 정보를 확인하고 답변하게 됩니다.

{% include image.html file="knowledge/knowledge_library02.png" alt="대화 의도/흐름을 만들지 않아도 동작하는 FAQ챗봇" caption="대화 의도/흐름을 만들지 않아도 동작하는 FAQ챗봇" %}

예시처럼 FAQ 데이터를 습득한 챗봇은 따로 시나리오를 등록하지 않았음에도 알고있는 지식을 바탕으로 알맞은 답변을 해줍니다.

## 빠르게 FAQ 챗봇을 만들어 보기
단비Ai에서 제공하는 위자드 템플릿을 이용하면, 빠르게 FAQ챗봇을 만들어 볼 수 있습니다. 튜토리얼을 참고하세요.
[FAQ챗봇 만들기 튜토리얼](https://doc.danbee.ai/tutorial_faq.html)

{% include bottom.html %}
