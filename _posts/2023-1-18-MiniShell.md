---
layout: post
title: (42Seoul) MiniShell
subtitle: "Minishell에 대한 회고를 정리합니다"
type: "TIL"
published: true
---

42seoul의 첫 팀 프로젝트, MiniShell에 대한 회고를 작성합니다

# MiniShell

_기간: '23.01.10. ~ '23.01.31. (3주)_

**history**

- '23.01.10. ~ '23.01.17.   허용 함수 및 과제 이해 학습
- '23.01.18. ~ '23.01.20.   bash 학습
- '23.01.20. ~ '23.01.31.   코드 구현

우연히 복도에서 마주친 ilhna 님과 minishell 과제를 시작하게 되었습니다

현재 spring 개인 공부와 웹 백엔드 프로젝트를 진행하고 있어 42과제를 함께 하는 부분에 고민을 많이 했지만,

조금 더 욕심 내보자는 마음으로 과제를 임해보자 다짐했습니다

저는 minitalk을, ilhna님은 pipex 과제를 진행했습니다

함께하는 과제가 처음이었기에 과제 진행 방향에 대해 함께 논의가 필요했고 우리의 방향은 다음과 같습니다

- 허용함수 숙지
- bash 학습
- 대략적인 로직 설게
- 병렬적 코드 구현
  - parsing
  - executing


'23.01.17.

pipex 과제를 진행하신 ilhna 님께서 좀더 익숙하겠다는 생각으로 executing을 진행해주시기로 했고

해당 부분이 비교적 강도가 높을 것으로 판단되어 얼른 parsing을 구현하고 동참 해야겠습니다

'23.01.18.

bash 학습을 시작합니다

- [bash reference](https://www.gnu.org/savannah-checkouts/gnu/bash/manual/bash.html)


**쉘 작동**

인수로 제공된 문자열을 읽는다

quoting 규칙을 지키며 입력을 단어와 연산자로 나눈다

이것을 토큰이라고 하는데 이는 `metacharacters` 에 의해 분리된다

```
metacharacter

A character that, when unquoted, separates words. A metacharacter is a space, tab, newline, or one of the following characters: ‘|’, ‘&’, ‘;’, ‘(’, ‘)’, ‘<’, or ‘>’.
```

토큰을 명령으로 구문 분석한다

다양한 셸 확장( 셸 확장 참조 )을 수행하여 확장된 토큰을 파일 이름 목록( 파일 이름 확장 참조 )과 명령 및 인수로 나눈다

필요한 리디렉션을 수행하고( 리디렉션 참조 ) 리디렉션 연산자와 해당 피연산자를 인수 목록에서 제거한다

명령을 실행한다

선택적으로 명령이 완료될 때까지 기다렸다가 종료 상태를 수집합니다( 종료 상태 참조 )

init

prompt

parse





동기 비동기 병렬처리


