---
layout: post
title: (Python) For Coding Test
subtitle: "문제를 먼저 풀어보며 개념을 역추적 학습 합니다"
type: "TIL"
---

문제를 먼저 풀어보며 개념을 역추적 학습 합니다

# Contents
- [Basic](#basic)
	- [Casting](#casting)	
	- [enumerate()](#enumerate)

- [input](#input)
- [List](#list)
    - [init list()](#init-list)
    - [리스트 연산자](#리스트-연산자)
    - [리스트 함수](#리스트-함수)

- [Data Structure](#data-structure)
	- [depue()](#depue)
    - [rotate()](#rotate)

- [function](#function)
	- [split()](#split)
	- [join()](#join)
  	- [map()](#map)
  	- [join() + map()](#join--map)


---

# 📌 Basic

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

# 📌 input()

- input()

```py
str = input() -> 문자열 입력

num = int(input()) -> 숫자 입력
```

- input().split()

```py
str = input().split()
>>> ['you','are','welcome']
```

- map()

```py
map(int, input().split())  # 숫자형을 입력받겠다.
map(str, input().split()) # 문자형을 입력받겠다.
```

- sys.stdin.readline()

대량의 데이터를 반복적으로 입력해야할 때

input()대신 sys.stdin.readline()을 이용하면 성능(속도)이 향상됩니다

_like Scanner -> BufferedReader in java_



```py
import sys
read =  sys.stdin.readline() -> 123 456
print(read) -> 123 456

# 각각의 str를 저장하고 싶을때
read2 =  sys.stdin.readline().split() -> 123 456 789
print(read2) -> ['123', '456', '789']


# 각각의 리스트 원소를 저장하고 싶을때
year, month, date =  map(int, sys.stdin.readline().split()) -> 2022 01 01
print(year, month, date) -> 2022 1 1
```

readline() 은 '\n'도 받습니다

따라서 `rstrip()`을 통해 제거할 수 있습니다

```py
import sys

input_data = sys.stdin.readline().rstrip()
```

- 배열

```py
a = [0 for _ in range(5)]

-> [0, 0, 0, 0, 0]
```

- 2차원 배열

```py
m, n = 5,4
a = [[0]*m for _ in range(n)]

-> [[0, 0, 0, 0, 0], [0, 0, 0, 0, 0], [0, 0, 0, 0, 0], [0, 0, 0, 0, 0]]
```

- for문을 이용한 N번 입력

```py
answer = [int(input()) for _ in range(N)]

-> N = 5 이면 원소가 다섯개인 리스트를 생성할 수 있습니다
```

**Reference**

- [input](https://velog.io/@tbnsok40/파이썬-다양한-입력방법-input-read-readline)


---

# 📌 enumerate()

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


**Reference**

- [enumerate](https://devpouch.tistory.com/74)


---

# 📌 List

리스트 내부에 넣는 자료를 요소(element)라고 부른다

## init list()

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

## 리스트 연산자

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

## 리스트 함수

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

**기타 내장함수**

```py

sum(list) - list의 합계 반환

sum(list, start) - list의 합계와 start의 합을 반환

len(list) - 리스트의 전체 길이 반환

max(list) - 리스트 중 최대 값 반환

min(list) - 리스트 중 최소 값 반환

list.count(obj) - 리스트 중 obj의 갯수 count 반환

list.index(obj) - 리스트 중 obj가 있는 가장 작은 idx를 반환

list.insert(index, obj) - 리스트의 idx 위치에 obj 삽입

list.remove(obj)

list.reverse()

list.sort()
```

**Reference**

- [List](https://codesyun.tistory.com/174)
- [List func](https://m.blog.naver.com/wideeyed/221541104629)


---

# 📌 dictionary

딕셔너리 타입은 immutable한 키(key)와 mutable한 값(value)으로 맵핑되어 있는 순서가 없는 집합입니다

중괄호로 되어있고 `키`와 `값`이 있습니다

```py
>>> {"a" : 1, "b":2}
{'a': 1, 'b': 2}
```

값은 중복될 수 있지만, 키가 중복되면 마지막 값으로 덮어씌워집니다

```py
>>> {"a" : 1, "a":2}
{'a': 2}
```

순서가 없기 때문에 인덱스로는 접근할수 없고, 키로 접근 할 수 있습니다

```py
>>> d = {'abc' : 1, 'def' : 2}
>>> d[0]
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
KeyError: 0

>>> d['abc']
1
```

mutable 한 객체이므로 키로 접근하여 값을 변경할 수 있습니다

```py
>>> d['abc'] = 5
>>> d
{'abc': 5, 'def': 2}
```

새로운 키와 값을 아래와 같이 추가할 수 있습니다.

```py
>>> d['ghi'] = 999
>>> d
{'abc': 5, 'def': 2, 'ghi': 999}
```

## dict 선언 방법

```py
# 1
>>> e = {}
>>> type(e)
<class 'dict'>

# 2
>>> f = dict()
>>> type(f)
<class 'dict'>
```

키와 값을 다음과 같이 바로 할당할 수 있습니다

```py
>>> dict_a = dict( alice = 5, bob = 20, tony= 15, suzy = 30)
>>> dict_a
{'alice': 5, 'bob': 20, 'tony': 15, 'suzy': 30}
```

## dict for 문

dict 를 for문 돌리면 key 값이 할당 됩니다

```py
>>> a = {'alice': [1, 2, 3], 'bob': 20, 'tony': 15, 'suzy': 30}
>>> for key in a:
...     print(key)
... 
alice
bob
tony
suzy
```

value 값으로 돌리고 싶다면 `values()` 를 사용합니다

```py
>>> a = {'alice': [1, 2, 3], 'bob': 20, 'tony': 15, 'suzy': 30}
>>> for val in a.values():
...     print(val)
... 
[1, 2, 3]
20
15
30    
```

key와 value를 한꺼번에 반복하고 싶다면 `items()` 를 사용합니다

```py
>>> a = {'alice': [1, 2, 3], 'bob': 20, 'tony': 15, 'suzy': 30}
>>> for key, val in a.items():
...     print("key = {key}, value={value}".format(key=key,value=val))
... 
key = alice, value=[1, 2, 3]
key = bob, value=20
key = tony, value=15
key = suzy, value=30
```

**Reference**

- [dict_wiki](https://wikidocs.net/16043)














---

# 📌 Data Structure

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

## rotate()

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



**Reference**
- [deque in python](https://www.geeksforgeeks.org/deque-in-python/)
- [deque](https://chaewonkong.github.io/posts/python-deque.html)

---

# 📌 algorithm

## union - find algorithm

간단하게 다수의 노드들 중에 연결된 노드를 찾거나 노드들을 합칠때 사용하는 알고리즘입니다

서로 중복되지 않는 부분 집합들로 나눠진 원소들에 대한 정보를 저장하고 조작하는 자료 구조입니다

![_config.yml](/images/algo-union_find.png)

1, 2, 3, 4, / 5, 6, 7, 8, / 9, 10

|1|2|3|4|5|6|7|8|9|10|
|1|1|2|3|5|5|6|7|9|9|

root 노드를 값으로 가지기 위해서는 순차적으로 아래와 같은 절차를 진행해야 합니다

1. 원소 3과 2는 연결되어 있다
2. 원소 3의 연결 정보를 2로 변경한다
3. 여기서 원소 2와 1은 연결되어 있다
4. 즉, 3의 연결 정보를 1로 변경한다

|1|2|3|4|5|6|7|8|9|10|
|1|1|1|1|5|5|5|5|9|9|

이를 구현하기 전에 Disjoint Set 에 대해 알아야 합니다

**Disjoint Set**

_서로소 집합_

서로 공통된 원소를 가지고 있지 않은 두 개 이상의 집합을 말합니다

Disjoint Set 자료구조를 통해 서로 다른 원소들이 같은 집합에 속해 있는지,

혹은 속해있지 않은지 판별하는데 유용하게 사용할 수 있습니다

**구현**

- 초기화: N 개의 원소가 각각의 집합에 포함되어 있도록 초기화
- Union 연산: 두 원소 a, b가 주어질 때, 이들이 속한 두 집합을 하나로 합침
- Find 연산: 어떤 원소 a가 주어질 때 이 원소가 속한 집합을 반환

구현 방법으로 배열과 트리 두 가지 방식이 있습니다

효율성을 위해 트리 구조를 사용합니다

```py
# 특정 원소가 속한 집합을 찾기
def find_parent(parent, x):
    # 루트 노드가 아니라면, 루트 노드를 찾을 때까지 재귀적으로 호출
    if parent[x] != x:
        return find_parent(parent, parent[x])
    return x

        # 연결 직전 노드가 아닌, 루트 노드를 모두 입력해주고 싶다면
        if parent[x] != x:
             parent[x] = find_parent(parent, parent[x])
        return parent[x]

# 두 원소가 속한 집합을 합치기
def union_parent(parent, a, b):
    a = find_parent(parent, a)
    b = find_parent(parent, b)
    if a < b:
        parent[b] = a
    else:
        parent[a] = b

# 노드의 개수와 간선(Union 연산)의 개수 입력 받기
v, e = map(int, input().split())
parent = [0] * (v + 1) # 부모 테이블 초기화하기

# 부모 테이블상에서, 부모를 자기 자신으로 초기화
for i in range(1, v + 1):
    parent[i] = i

    # 부모 테이블 초기화 + 자기자신 초기화 한꺼번에 하는법
    parent = [x for x in range(N + 1)]

# Union 연산을 각각 수행
for i in range(e):
    a, b = map(int, input().split())
    union_parent(parent, a, b)

# 각 원소가 속한 집합 출력하기
print('각 원소가 속한 집합: ', end='')
for i in range(1, v + 1):
    print(find_parent(parent, i), end=' ')

print()

# 부모 테이블 내용 출력하기
print('부모 테이블: ', end='')
for i in range(1, v + 1):
    print(parent[i], end=' ')
```


***Reference***
- [union-find](https://brownbears.tistory.com/460)
- [union-find_code](https://velog.io/@woo0_hooo/알고리즘-union-find-알고리즘)








---

# 📌 function

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

## join() + map()

리스트를 출력하면 [value, value, value ...] 형식으로 출력됩니다

value value value ... 로 출력 시키는 방법은 다음과 같습니다

```py
printf(' '.join(map(str, list)))
```