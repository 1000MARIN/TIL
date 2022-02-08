# Vector

<br>

## Vector 클래스

  * java.util.Vector
  * List 인터페이스를 구현한 클래스
  * 객체들을 삽입, 삭제, 검색 할 수 있는 콘테이너 클래스
  * 배열의 길이 제한 단점을 극복
  * 아이템을 맨 마지막이나 중간에 삽입할 수 있음
  * 객체수가 많아지면 자동으로 크기 조절
    - 맨 뒤에 객체 추가 : 공간이 모자르면 자동 늘림
    - 중간에 객체 추가 : 뒤에 존재하는 객체 한칸씩 뒤로이동
    - 객체 삭제 : 삭제 후 한칸씩 앞으로 자동이동
    

<br>

## Vector 내부구조

  * add() 메소드로 요소 삽입
  * get() 메소드로 요소 검색
  * String, Integer, Person 등 다양한 타입의 객체 삽입 가능
  * 요소들은 인덱스로 관리 (0부터 시작)

<br>

## Vector 주요 메소드

  * add(E e) : 벡터 맨 뒤에 요소추가
  * add(int index, E e) : 지정된 인덱스에 지정된 객체 추가
  * capacity() : 벡터 현재 용량 반환
  * addAll(c) : c가 지정하는 모든 요소 벡터 맨 뒤에 추가
  * clear() : 벡터 모든 요소 삭제  
  * contains(Object o) : 벡터가 지정된 객체를 포함하고 있으면 true
  * elementAt(int index) : 지정된 인덱스 요소 반환
  * get(int index) : 지정된 인덱스 요소 반환
  * indexOf(Object o) : 지정된 객체와 같은 첫 번째 요소 인스 반환. 없으면 -1 반환
  * isEmpty() : 벡터가 비어있으면 true
  * remove(int index) : 지정된 인덱스 요소 삭제
  * remove(Objcect o) : 지정된 객체와 같은 첫째 요소 벡터에서 삭제
  * removeAllElements() : 모돈 요소 삭제하고 크기를 0으로 만듬
  * size() : 벡터가 포함하는 요소의 개수 반환
  * toArray() : 벡터의 모든 요소를 포함하는 배열 반환

<br>

```java
// Integer 를 담는 Vector
Vector<Integer> integerVector = new Vector<Integer>();
integerVector.add(1); // 맨뒤에 요소 추가
integerVector.add(2);
integerVector.add(3);
integerVector.add(3,4); // 지정된 위치에 요소추가
System.out.println(integerVector); // [1, 2, 3, 4]
for(int i=0; i<integerVector.size(); i++){ // Vector.size()    
System.out.println(integerVector.get(i));  // Vector.get() }
integerVector.remove(1);
System.out.println(integerVector); // [1, 3, 4]
System.out.println(integerVector.capacity()); // 10 --> 벡터의 현재 용량 반환
//integerVector.clear();
integerVector.removeAllElements(); // 벡터의 모든요소 삭제 후 크기 0
System.out.println(integerVector); // []
System.out.println(integerVector.isEmpty()); // true
// String 을 담는 Vector
Vector<String> stringVector = new Vector<String>();
stringVector.add("Hello");stringVector.add("World");
stringVector.add(0,"Vector");
System.out.println(stringVector); // [Vector, Hello, World]
for(int j=0; j<stringVector.size(); j++){  // Vector.size()    
System.out.println(stringVector.get(j)); // Vector.get()}
```


# ArrayList

<br>

## ArrayList 클래스
 * java.util.ArrayList
 * 객체들을 삽입, 삭제, 검색할 수 있는 컨테이너 클래스.
 * 배열 길이 제한단점을 극복할 수 있다.
  - 배열 선언 시 인덱스를 다 채우거나 못 채울 경우 해결
  - 배열은 인덱스가 꽉 차면 더 이상 값을 넣을 수 없다.
  - 배열은 인덱스가 비어있으면 메모리가 낭비된다.

 * 객체수가 많아지면 자동으로 크기조절
 * 아이템을 벡터의 마지막이나 중간에 삽입할 수 있다.
  - 맨 뒤에 객체 추가 : 공간이 모자르면 자동 늘림
  - 중간에 객체 추가 : 뒤에 존재하는 객체 한칸씩 뒤로이동
  - 객체 삭제 : 삭제 후 한칸씩 앞으로 자동이동


<br>

## ArrayList 내부구조
 
  * add() 메소드로 요소 삽입
  * get() 메소드로 요소 검색
  * String, Integer, Person 등 다양한 타입의 객체 삽입 가능
  * 요소들은 인덱스로 관리 (0부터 시작)
 
<br>

## ArrayList 주요 메소드 

  * aad(E e) : 맨 뒤에 요소추가
  * add(int index, E e) : 지정된 인덱스에 지정된 객체 추가
  * addAll(c) : c가 지정하는 모든 요소 벡터 맨 뒤에 추가
  * clear() : 모든 요소 삭제  
  * contains(Object o) : 지정된 객체를 포함하고 있으면 true
  * elementAt(int index) : 지정된 인덱스 요소 반환
  * get(int index) : 지정된 인덱스 요소 반환
  * indexOf(Object o) : 지정된 객체와 같은 첫 번째 요소 인스 반환. 없으면 -1 
  * isEmpty() : 비어있으면 true
  * remove(int index) : 지정된 인덱스 요소 삭제
  * remove(Objcect o) : 지정된 객체와 같은 첫째 요소 벡터에서 삭제
  * size() : 포함하는 요소의 개수 반환
  * toArray() : 모든 요소를 포함하는 배열 반환
 
<br>

```java
// Integer 를 담는 ArrayList
ArrayList<Integer> integerArrayList = new ArrayList<Integer>();
integerArrayList.add(1); // 맨뒤에 요소추가
integerArrayList.add(2); // 맨뒤에 요소추가
integerArrayList.add(3); // 맨뒤에 요소추가
integerArrayList.add(3,4); // 지정된 위치에 요소추가
System.out.println(integerArrayList); // [1, 2, 3 ,4]
for(int k=0; k<integerArrayList.size(); k++) { // Vector.size()
    System.out.println(integerArrayList.get(k)); // Vector.get()
}
integerArrayList.remove(1);
System.out.println(integerArrayList); // [1, 3, 4]
integerArrayList.clear();
System.out.println(integerArrayList); // []
System.out.println(integerArrayList.isEmpty()); // true
```


## 요약 

 * ector 와 ArrayList는 List 인터페이스를 상속받는다.
 * 둘은 같은 동작을 수행하는 클래스이다.
 * 사용하는 메소드가 거의 비슷하다. 
 * Vector는 기존 코드와의 호환성을 위해 남아있다. 
 * ArrayList 클래스를 사용하는 것이 좋다.

<br>

***

<br>

# Vector 와 ArrayList 주요 차이점

1. 동기화(Synchronize)
 * Vector 는 한번에 하나의 스레드만 접근 가능하다.
 * ArrayList는 동시에 여러 스레드가 작업할 수 있다.
  - 여러 스레드가 동시에 접근하드 경우 개발자가 명시적으로 동기화하는 코드를 추가해야 한다.

2. 스레드 안전(Thread Safe)
 * 멀티 스레드 프로그래밍에서 여러 스레드가 동시에 접근이 이루어져도 프로그램 실행에 문제가 없음을 의미
 * Vector 는 동기화 되어있기 때문에 한번에 하나의 스레드만 접근할 수 있으므로 Thread Safe 하다.
 * ArrayList는 동기화 되지 않았기 때문에 명시적으로 동기화 할 필요가 있다.

3. 성능
 * ArrayList는 동기화 되지 않았기 때문에 Vector보다 빠르다.

4. 크기 증가
 * Vector는 현재 배열의 크기의 100%가 증가
 * ArrayList는 현재 배열의 크기의 50% 증가

<br>

## 요약
 * 멀티 스레드 환경이 아닌경우 ArrayList사용이 바람직하다.
 * Vector가 동기화 한다는 것은 복수의 스레드로부터 추가/삭제가 이루어져도 내부의 데이터 처리는 안전하게 한번에 하나의 스레드만 처리되도록 보장한다는 의미이다. 데이터 처리가 안정적으로 이루어지도록 보장하는 것이다. 
 * 단일 스레드의 경우 자동으로 동기화를 보장하는 것이 오히려 성능 저하를 일으킬 수 있기 때문에 동기화를 진행하지 않는 ArrayList가 더 효율적인 성능을 보장한다고 할 수 있다. 

<br>
<br>

***

<br>
<br>

# LinkedList

## LinkedList 클래스 

 * java.util.LinkedList
 * ArrayList 의 단점을 극복하기 위해 고안되었다.
 * 내부적으로 연결리스트를 이용하여 요소를 저장한다.
   - 배열은 저장된 요소가 순차적으로 저장된다.
   - 저장된 요소가 비 순차적으로 분포되며, 요소 사이를 링크로 연결하여 구성한다.
 * List 인터페이스를 상속받기 때문에 ArrayList의 메소드와 거의 같은 메소드를 사용할 수 있다.
 * 단일 연결 리스트(singly linked list) 
   - 요소의 저장과 삭제작업이 다음 요소를 가리키는 참조만 변경되어 빠르게 처리된다.
   - 현재 요소에서 이전 요소로 접근하기 매우 어렵다.
 * 이중 연결 리스트(doubly linked list)
   - 이전 요소를 가리키는 참조도 가지고 있다.
   - 이전 요소로 접근하기 용이하다. 

```java
// Integer 를 담는 LinkedList
LinkedList<Integer> integerLinkedList = new LinkedList<Integer>();
integerLinkedList.add(1); // 맨뒤에 요소추가
integerLinkedList.add(2); // 맨뒤에 요소추가
integerLinkedList.add(3); // 맨뒤에 요소추가
integerLinkedList.add(3,4); // 지정된 위치 요소추가
System.out.println(integerLinkedList); // [1, 2, 3 ,4]
for(Integer e : integerLinkedList){
    System.out.println(e);
}
integerLinkedList.remove(1);
System.out.println(integerLinkedList); // [1, 3, 4]
integerLinkedList.clear();
System.out.println(integerLinkedList); // []
System.out.println(integerLinkedList.isEmpty()); // true
```

Vector - ArrayList - LinkedList는 사용방법이나 동작 결과에 큰 차이는 없다. 내부적으로 저장하는 방법이 다른것이고 그것을 구분하여 설명할 줄 아는것이 중요한 것 같다. 

<br>

# 정리

 * Vector와 ArrayList 그리고 LinkedList는 모두 같은 동작을 구현하는 클래스이며 List 인터페이스를 상속 받으므로 거의 비슷한 메소드를 사용한다. 사용방법과 동작 결과의 큰 차이는 없지만 내부 동작이 다르다. 
 * Vector와 ArrayList의 주요 차이점중 하나는 동기화이다. 
 * Vector는 내부적으로 여러개의 스레드가 접근 할 때 데이터 안정성을 위해 한개의 스레드씩 순차적으로처리할 수 있도록 동기화 되어있다. 안정성을 보장하는 만큼 일을 많이 처리한다는 의미이고 메모리를 많이 사용한다고 볼 수 있다. 
 * ArrayList는 동기화되어있지 않기때문에 여러개의 스레드에서 접근 할 때 필요에 따라 동기화 처리를 해주어야 한다. 
 * 단일 스레드 작업시 동기화가 필요 없으므로 같은 동작을 하는 ArrayList를 사용하는 것이 성능적인 면에서 용이하다. 
 
