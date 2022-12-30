---
layout: post
title: [Python] 입문 week-01
---

# Coding Test by Python

## Contents


---

# Basic

## Python에서 캐스팅하는 방법

---

---

## enumerate()

---

# List

## init list()


---

# Data Structure

## depue()

---

# function

## split()

_문자열을 특정 구분자(String) 기준으로 List로 변환하는 함수_

```py
str1 = "Hello, python"

str2 = str1.split(", ")
```

> 출력결과
> ['Hello', 'python']


## join()

_List를 특정 구분자(char))를 포함해 문자열로 변환하는 함수_

```py
list1 = ['Hello', 'python']

list2 = ', '.join(list1)
```
> 출력결과
> Hello, pyrthon

_split() != join()_

## map()

_map(func, iterable) 반복 가능한 자료형의 각 요소에 func을 적용해 결과를 묶어서 반환하는 함수_


```py
list1 = [1, 2, 3, 4]

list2 = list(map(str, list1))
```

> 출력결과
> ['1', '2', '3', '4']