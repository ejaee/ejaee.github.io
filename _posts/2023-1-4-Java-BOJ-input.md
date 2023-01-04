---
layout: post
title: [Java, BaekJoon] 자바로 백준 입력받기
subtitle: "자바로 코딩테스트를 준비합니다"
type: "CODING_TEST"
---

자바로 코딩테스트를 준비합니다

# 🔆 자바로 백준 입력 받는 법

백준 문제를 자바로 풀다보면 Scanner 대신 BufferReader 를 사용해야만 하는 문제들이 있습니다

BufferReader 의 성능에 대한 개념은 [BufferReader]()를 참고 해주시기 바랍니다

---

# 🔆 BufferReader

사용하기 위해서는 IOException 을 추가해주어야 합니다

```java
public static void main(String[] args) throws IOException
```

---

# 🔆 StringTokenizer

공백으로 한 글자씩 구분되는 입력의 경우 공백의 대상을 설정하고 입력받을 수 있습니다

```java
int [] targetArray = new int[100];
st = new StringTokenizer(sc.readLine()," ");

for(int i = 0 ; i < M ; i++){
    targetArray[i] = Integer.parseInt(st.nextToken());
}
```

---

# 🔆 입력값 예시

1. `한 줄`에 두개 이상의 `숫자`
```
3 4
```

```java
BufferReader br = new BufferReader(new InputStreamReader(System.in));
StringTokenizer st = new StringTokenizer(br.readLine());
int x = Integer.parseInt(st.nextToken());
int y = Integer.parseInt(st.nextToken());
```

2. `입력받을 줄 수`를 입력받고 각각 `입력받을 숫자 수`와 `해당 숫자들`
```
3
1 5
3 10 11 12
5 1 2 3 4 5
```

```java
BufferReader br = new BufferReader(new InputStreamReader(System.in));
int n = Integer.parseInt(br.readLine());

for (int i = 0; i < n; i++) {
    StringTokenizer st = new StringTokenizer(br.readLine());
    int s = Integer.parseInt(st.nextToken());

    for (int j = 0; i < s; j++) {
        int data = Integer.parseInt(st.nextToken());
        System.out.printLn(data);
    }
}
```

---


# 🔆 문자열 입력

readLine 을 사용해 한 줄씩 읽습니다

```java
BufferReader br = new BufferReader(new InputStreamReader(System.in));

String str = "";
str = br.readLine();
```

전체를 입력하고 싶은 경우에는 다음과 같은 방법이 있습니다

```java
String str = "";
String buf = "";

while((buf = br.readLine())!= null) {
    str += tmp + "\n";
}
```

---

# 🔆 정수 입력

readLine() 은 기본적으로 String 으로 읽어오기 때문에 형 변환이 필요합니다 

```java
BufferReader br = new BufferReader(new InputStreamReader(System.in));

int a = "";
a = Integer.parseInt(br.readLine());
```

---

**Reference**

- [[Java , BaekJoon] 자바로 백준 입력 받는 법 정리](https://rhsalska55.tistory.com/6) 
- [자바로 백준 풀 때의 팁 및 주의점](https://nahwasa.com/172)