---
layout: post
title: (Spring) Entity
subtitle: "김영한 Spring Core 강의 내용을 정리합니다"
type: "TIL"
published: true
---

Entity 란 무엇일까요

김영한님 강의를 듣다가 엔티라는 개념이 나왔습니다

### 엔티티

_Entity_

엔티티는 데이터의 집합을 의미합니다

저장되고 관리되어야하는 데이터입니다

개념, 장소, 사건 등을 가리키며 유형 또는 무형의 대상을 가리팁니다

클라이언트가 회원 서비스를 통해 회원 가입을 하고 그 데이터가 회원 저장소에 저장이 됩니다

따라서 회원이라는 대상은 엔티티입니다

### 엔티티의 특징

◎ 식별자 - 유일한 식별자를 갖고 있어야 합니다 ex) 주민번호, ID 등...

◎ 인스턴스 집합 - 2개 이상의 인스턴스가 있어야 합니다

◎ 속성 - 반드시 속성을 가지고 있어야 합니다 ex) 학생에 학번, 이름, 주소 등...

◎ 관계 - 다른 엔티티와 최소 한 개 이상 관계가 있어야 합니다 ex) 학생은 이름을 갖고 있음

◎ 업무 - 업무에서 관리되어야 하는 집합입니다 ex) 학생, 성적