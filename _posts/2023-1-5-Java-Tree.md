---
layout: post
title: (JAVA) Tree 자료구조
subtitle: "자료구조를 정리합니다"
type: "DATA_STRUCTURE"
published: true
---

자료구조 Tree에 대해 정리하고 java로 구현해봅니다

# Tree

트리(Tree)는 계층적 관계를 표현하는 자료구조로,

데이터 저장, 삭제, 검색을 용이하도록 만든 구조가 아닌, 무엇인가 표현 하기위한 구조 입니다

하나의 `루트 노드`에서

`여러 노드`들이 `간선`으로 연결되어있는 형태를 가집니다

세부적인 설명은 제가 C로 구현한 [Tree 개념 정리](https://github.com/ejaee/Study_C/tree/master/C-DataStructure/Ch08.Tree)를 참고하시면 되겠습니다

# Tree 구현 by Java

Tree 구조로 데이터를 저장하는 방법은 크게 세 부분으로 나뉩니다

1. 데이터와 연결 상태를 저장할 클래스 공간, Node 생성
2. 각각의 Node들에 값 저장
3. Node 간 연결 상태 정의

가장 먼저 데이터 값을 저장할 class를 만듭니다

```java
public class Node {
    Object data;
    Node left;
    Node right;
}
```

각각의 노드를 생성하면서 data 값을 저장, left, right 값을 초기화 합니다

```java

    public Node(Object data){
        this.data = data;
        left = null;
        left = right;
    }
```

연결을 위한 메서드들을 정의합니다

Node에 대한 기능은 다음과 같습니다

### Node

- void addLeft(Node node)
 현재 노드의 좌측에 노드 연결 정보를 추가한다.
- void addRight(Node node)
 현재 노드의 우측에 노드 연결 정보를 추가한다.
- void deleteLeft()
 현재 노드의 좌측 노드 연결 정보를 삭제한다.
- void deleteRight()
 현재 노드의 좌측 노드 연결 정보를 삭제한다.

```java
    public void addLeft(Node node) {
		left = node;
		count++;
	}

	public void addRight(Node node) {
		right = node;
		count++;
	}

	public void deleteLeft() {
		left = null;
		count--;
	}

	public void deleteRight() {
		right = null;
		count--;
	}
```

* class Node

```java

    public class Node {
		Object data;
		Node left;
		Node right;
	
		public Node(Object data) {
			this.data = data;
			left = null;
			right = null;
		}

		public void addLeft(Node node) {
			left = node;
			count++;
		}

		public void addRight(Node node) {
			right = node;
			count++;
		}

		public void deleteLeft() {
			left = null;
			count--;
		}

		public void deleteRight() {
			right = null;
			count--;
		}
	}
```

Node 클래스를 가진 Tree 클래스를 정의합니다

Tree에 저장된 데이터의 개수를 관리합니다

```java
public class Tree {
    int count;

    public Tree() {
        count = 0;
    }
}
```

Tree에 대한 기능은 다음과 같습니다

### Tree

- Node addNode(Object data)
 노드를 새롭게 생성한다.(저장될 데이터는 data 변수 안에 존재하는 값)
- void preOrder(Node node)
 전위 순회 방법을 이용해 출력한다.
- void inOrder(Node node)
 중위 순회 방법을 이용해 출력한다.
- void postOrder(Node node)
 후위 순회 방법을 이용해 출력한다.

 ```java
    public Node addNode(Object data) {
		Node node = new Node(data);
		return node;
	}
	
	public void preOrder(Node node) {
		if(node == null) {
			return;
		}
		
		System.out.print(node.data + " ");
		preOrder(node.left);
		preOrder(node.right);
	}

	public void inOrder(Node node) {
		if(node == null) {
			return;
		}
		
		inOrder(node.left);
		System.out.print(node.data + " ");
		inOrder(node.right);
	}

	public void postOrder(Node node) {
		if(node == null) {
			return;
		}
		
		postOrder(node.left);
		postOrder(node.right);
		System.out.print(node.data + " ");
	}
 ```

 * class Tree

 ```java
package Tree;

public class Tree {
	int count;
	
	public Tree() {
		count = 0;
	}
	
	public class Node {
		Object data;
		Node left;
		Node right;
	
		public Node(Object data) {
			this.data = data;
			left = null;
			right = null;
		}

		public void addLeft(Node node) {
			left = node;
			count++;
		}

		public void addRight(Node node) {
			right = node;
			count++;
		}

		public void deleteLeft() {
			left = null;
			count--;
		}

		public void deleteRight() {
			right = null;
			count--;
		}
	}
	
	public Node addNode(Object data) {
		Node node = new Node(data);
		return node;
	}
	
	public void preOrder(Node node) {
		if(node == null) {
			return;
		}
		
		System.out.print(node.data + " ");
		preOrder(node.left);
		preOrder(node.right);
	}

	public void inOrder(Node node) {
		if(node == null) {
			return;
		}
		
		inOrder(node.left);
		System.out.print(node.data + " ");
		inOrder(node.right);
	}

	public void postOrder(Node node) {
		if(node == null) {
			return;
		}
		
		postOrder(node.left);
		postOrder(node.right);
		System.out.print(node.data + " ");
	}
}

 ```

 Reference
 - [C-DataStructure/Ch08.Tree/](https://github.com/ejaee/Study_C/tree/master/C-DataStructure/Ch08.Tree)
 - [[자료구조, Java] 트리(Tree) 개념 정리 및 구현](https://readerr.tistory.com/35)