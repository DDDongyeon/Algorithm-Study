# LinkedList

- 자료의 논리적인 순서와 메모리 상의 물리적인 순서가 일치하지 않고, 개별적으로 위치하고 있는 각 원소를 연결하여 하나의 전체적인 자료구조를 이룬다. 

- 링크를 통해 원소에 접근하므로, 순차 리스트에서처럼 물리적인 순서를 맞추기 위한 작업이 필요하지 않다.

- 자료구조의 크기를 동적으로 조정할 수 있어, 메모리의 효율적인 사용이 가능하다. 

=> 노드를 연결시킨 자료구조!

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Ft1.daumcdn.net%2Fcfile%2Ftistory%2F99A76F495BD5882507)

제일 앞에 있는 노드는 헤드(head), 제일 끝 노드는 테일(tail)이라고 한다.

----
### 왜 쓰는가?
리스트의 길이가 가변적이다! 다음 노드만 추가하면 되기 때문에 리스트의 사이즌를 조정하는데, 큰 비용이 들지 않는다.
배열의 단점 커버 가능하다.

### but,
링크드 리스트는 어떤 노드를 search하거나 데이터를 변경할 때 바로 찾아낼 수가 없다.
링크드리스트를 전부 탐색해야할 수도 있음!

---

### LinkedList 요소 추가 / 삽입
linkedlist는 arraylist와 다르게 중간에 데이터가 추가되거나 중간에 있는 데이터가 삭제되어도 앞으로 땡기거나 뒤로 미는 동작이 없다!
-> 추가되거나 삭제될 노드 위치의 바로 앞뒤쪽에 있는 노드의 참조를 변경하기만 하면 된다.

```java

LinkedList<String> list = new LinkedList<>(Arrays.asList("A", "B", "C")));

// 가장 앞에 데이터 추가
list.addFirst("new");

// 가장 뒤에 데이터 추가
list.addLast("new");

// index 1에 중간 위치에 데이터 10 추가
list.add(1, "new");


출처: https://inpa.tistory.com/entry/JAVA-☕-LinkedList-구조-사용법-완벽-정복하기 [Inpa Dev 👨‍💻:티스토리]
```
### LinkedList 요소 삭제
```java

LinkedList<String> list = new LinkedList<>(Arrays.asList("A", "B", "C")));

// 첫 번째 값 제거
list.removeFirst();

// 마지막 데이터 제거
list.removeLast();

// index 1 중간 위치 제거
list.remove(1);

// 모든 값 제거
list.clear();

출처: https://inpa.tistory.com/entry/JAVA-☕-LinkedList-구조-사용법-완벽-정복하기 [Inpa Dev 👨‍💻:티스토리]
```

### LinkedList 요소 검색
```java
LinkedList<String> list = new LinkedList<>(Arrays.asList("A", "B", "C")));

// 해당 값을 가지고 있는 요소 위치를 반환 (앞에서 부터 검색) 
list1.indexOf("B"); // 1

// 해당 값을 가지고 있는 요소 위치를 반환 (뒤에서 부터 검색) 
list1.lastIndexOf("D"); // -1 : 찾고자 하는 값이 없으면

LinkedList list1 = new LinkedList();
list1.add("1");
list1.add("2");

// list1안에 "1" 값이 있는지 확인
list1.contains("1"); // true


LinkedList list2 = new LinkedList();
list2.add("1");
list2.add("2");
 
// list1에 list2의 모든 노드가 포함되어 있는지 확인
list1.containsAll(list2); // true

출처: https://inpa.tistory.com/entry/JAVA-☕-LinkedList-구조-사용법-완벽-정복하기 [Inpa Dev 👨‍💻:티스토리]
```
### LinkedList 요소 얻기
개별 단일 요소를 얻고자 하면 get 메서드로 얻어올 수 있다. 단, LinkedList는 ArrayList와 달리 만일 100번째 노드를 확인하기 위해서는 첫번째 노드부터 100번째 노드까지 참조를 따라서 일일히 이동해야 하기 때문에 탐색 성능은 좋지 않은 편이다. 

```java
list.get(0); // 0번째 index 요소의 값 출력
```
### LinkedList 요소 변경
set 메서드에서 주의할 점은 LinkedList라고 해도 기본적으로 리스트이기 때문에 리스트의 크기를 넘기는 인덱스를 할당하게 되면 `IndexOUtOfBoundsException` 예외가 발생한다.

```java
LinkedList<String> list = new LinkedList<>();
list1.add("10");
list1.add("20");
list1.add("30");
 
list1.set(1, "A"); // index 1번의 데이터를 문자열 "A"로 변경한다.
System.out.println(list1); // // [10, A, 30]

```

---
### ArrayDeque와 LinkedList 무슨 차이일까?

```java
public class LinkedList<E>
	extends AbstractSequentialList<E>
	implements List<E>, Deque<E>, Cloneable, java.io.Serializable
```
```java
public class ArrayDeque<E> extends AbstractCollection<E>
						   implements Deque<E>, Cloneable, Serializable
```
`LinkedList`는 `List`, `Deque` 인터페이스를 구현했고 
`ArrayDeque`는 `Deque` 인터페이스를 구현했다.

-> ArrayDeque가 List 인터페이스는 구현하지 않았다는 점이 다름.

### 1. Deque란?
- 원소의 추가와 삭제를 둘 다 끝부분에서 지원하는 선형 collection이다.

### 2. ArrayDeque란?
- Deque interface의 사이즈 조정이 가능한 array의 구현체이다.<br>
- null은 안된다.<br>
- stack으로 쓸 때 Stack보다는 빠르고 queue로 쓸 때 LinkedList보다 빠르다.

### 3. ArrayDeque vs LinkedList
- ArrayDeque는 Array에 의해 지원되고 Array는 LinkedList보다 cache-locality 친화적이다.
- ArrayDeque는 다음 노드에 추가적인 reference를 유지할 필요가 없기 때문에 LinkedList보다 메모리 효율적임. 그래서 ArrayDeque를 queue로 사용할 때 LinkedList 대신에 사용한다.

=> 인덱스로 데이터에 접근하고 끝에 삽입, 삭제만 할 경우에는 ArrayList를 사용<br>
stack, queue, deque는 ArrayDeque 사용<br>
리스트를 순회할 때 삽입, 삭제하거나 O(1)인 최악의 경우에 마지막에 삽입 시 LinkedList 사용

`case by case로 어떤 것이 나은지 판단하고 사용하면 될 듯하다.`

