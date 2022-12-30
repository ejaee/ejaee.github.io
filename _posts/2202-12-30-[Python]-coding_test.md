---
layout: post
title: [Python] 입문 week-01
---

# Coding Test by Python

## Contents
- [basic](#basic)
    - [casting](#casting)
- [list](#list)
- [date structure](#data-structure)
    - [deque](#depue)
- [function](#function)
    - [split()](#split)
    - [join()](#join)
    - [map()](#map)


---

# Basic

## Casting

Python에서 캐스팅하는 방법
```py

float(3) -> 3.0

int(3.0) -> 3

hex(12) -> 0xa

a = 0b0010 -> 2
# 자동으로 바뀐다


# 진수 값이 문자열이면 int() 함수를 사용한다
int('0xc', 16) -> 12
int(input())
```

---

---

## enumerate()

반복문을 사용할 때 리스트를 인덱싱 합니다

```py
item = ["First", "Second", "Third"] 
data = enumerate(item) 

print(data, type(data))  
```

> (0, 'First') 
> (1, 'Second') 
> (2, 'Third') 

enumerate함수를 사용하여 for문을 돌려보면 리스트의 원소와 인덱스가 튜플형태로 담겨 있습니다

```py
item = ["First", "Second", "Third"] 

for i, val in enumerate(item): 
    print("{} 번쨰 값은 {}입니다".format(i, val)) 
```

> 0 번쨰 값은 First입니다 
> 1 번쨰 값은 Second입니다 
> 2 번쨰 값은 Third입니다 


### Reference

- [enumerate](https://devpouch.tistory.com/74)


---

## List

리스트 내부에 넣는 자료를 요소(element)라고 부른다

### init list()

```py
# 초기화는 쉼표로 구분해서 입력한다
array = [273, 32, 103, "문자열", True, False]

print(array)
```
> 출력결과
> [273, 32, 103, '문자열', True, False]

인덱스는 1부터 시작한다

```py
list_a = [273, 32, 103, "문자열", True, False]
list_a[0] = "변경"

print(list_a)
> 출력결과
> ['변경', 32, 103, '문자열', True, False]
```

### 리스트 연산자

- 연결(+)
- 반복(*)
- len()

```py
list_a = [1, 2, 3]
list_b = [4, 5, 6]

print("list_a + list_b = ", list_a + list_b)
# list_a + list_b =  [1, 2, 3, 4, 5, 6]

print("list * 3 = ", list_a * 3)
# list * 3 =  [1, 2, 3, 1, 2, 3, 1, 2, 3]

print("len(list_a) = ", len(list_a))
# len(list_a) =  3
```

### 리스트 함수

**추가**
- 리스트명.append(요소)
- 리스트명.insert(위치, 요소)
- 한번에 여러 요소를 추가하는 extend()
    ```py
    list_a = [1, 2, 3]
    list_a.extend([4, 5, 6])
    
    print(list_a)
    ```
    > 출력 결과
    > [1, 2, 3, 4, 5, 6]

append 와 extend의 차이를 실습을 통해 알아보겠습니다

```py

x = ['1', '2', '3' ]
y = ['a', 'b']

# 1
x.append(y)

print(x)
```
> ['1', '2', '3', ['4', '5']]

```py
# 2
x.extend(y)

print(x)
```
> ['1', '2', '3', '4', '5']

**제거**
- 인덱스로 제거
    ```py
    del 리스트명[index]

    또는

    리스트명.pop(index)
    ```
- 값으로 제거
    ```py
    리스트.remove(value)
    # 제일 먼저 발견되는 하나만 제거
    ```

- 모두 제거
    ```py
    리스트.clear()
    ```

### Reference

- [List](https://codesyun.tistory.com/174)
- [List func](https://m.blog.naver.com/wideeyed/221541104629)


---



# Data Structure

## depue()
_데크_

양방향 큐를 말합니다

앞, 뒤 양쪽 방향에서 요소를 추가, 제거할 수 있습니다

일반적인 list는 양끝 요소를 다룰 때 O(n)인 반면에

deque는 O(1)로 접근이 가능합니다

사용 방법은 다음과 같습니다

```py
from collections import deque

deq = deque()

# Add element to the start
deq.appendleft(10)

# Add element to the end
deq.append(0)

# Pop element from the start
deq.popleft()

# Pop element from the end
deq.pop()
```
- deque.append(item): item을 데크의 오른쪽 끝에 삽입
- deque.appendleft(item): item을 데크의 왼쪽 끝에 삽입
- deque.pop(): 데크의 오른쪽 끝 엘리먼트를 가져오는 동시에 데크에서 삭제
- deque.popleft(): 데크의 왼쪽 끝 엘리먼트를 가져오는 동시에 데크에서 삭제
- deque.extend(array): 주어진 array를 순환하면서 데크의 오른쪽에 추가
- deque.extendleft(array): 주어진 array를 순환하면서 데크의 왼쪽에 추가
- deque.remove(item): item을 데크에서 찾아 삭제
- deque.rotate(num): 데크를 num만큼 회전(양수면 오른쪽, 음수면 왼쪽).

### rotate()

```py
# Contain 1, 2, 3, 4, 5 in deq
deq = deque([1, 2, 3, 4, 5])

deq.rotate(1)
# deque([5, 1, 2, 3, 4])

deq.rotate(-1)
# deque([1, 2, 3, 4, 5])
```


시작점의 값을 넣고 빼거나, 끝 점의 값을 넣고 빼는 데 최적화된 연산 속도를 제공합니다

 push/pop 연산이 빈번한 알고리즘에서 리스트보다 월등한 속도를 자랑합니다



### Reference
- [deque in python](https://www.geeksforgeeks.org/deque-in-python/)
- [deque](https://chaewonkong.github.io/posts/python-deque.html)

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

리스트의 요소를 지정된 함수로 처리해주는 함수입니다

원본 리스트를 변경하지 않고 새 리스트를 생성합니다

```py
list1 = [1, 2, 3, 4]

list2 = list(map(str, list1))
```

> 출력결과
> ['1', '2', '3', '4']

### join() + map()

리스트를 출력하면 [value, value, value ...] 형식으로 출력됩니다

value value value ... 로 출력 시키는 방법은 다음과 같습니다

```py
printf(' '.join(map(str, list)))
```