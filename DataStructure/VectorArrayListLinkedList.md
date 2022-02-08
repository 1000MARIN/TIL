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

<br>
<br>

# ArrayList

<br>

## ArrayList 클래스
  * java.util.ArrayList<E>
  * 객체들을 삽입, 삭제, 검색할 수 있는 컨테이너 클래스.
  * 배열 길이 제한단점을 극복할 수 있다.
