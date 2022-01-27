# Array와 LinkedList의 차이

<br>

### 1. 접근
  * Array : Random Access를 지원한다. 요소들을 인덱스를 통해 직접 접근할 수 있다. 따라서 특정 요소에 접근하는 시간복잡도는 O(1)이다.
  * Linkedlist는 Sequential Access를 지원한다. 어떤 요소를 접근할 때 순차적으로 검색하며 찾아야 한다. 따라서 특정 요소에 접근할 때 시간복잡도는 O(N)이다.

<br>

### 2. 삽입과 삭제
  * 저장방식도 배열에서 요소들은 인접한 메모리 위치에 연이어 저장된다.
  * Linkedlist에서는 새로운 요소에 할당된 메모리 위치 주소가 linkedlist의 이전 요소에 저장된다.배열에서 삽입과 삭제는 O(N)이 소요되지만, Linkedlist에서 삽입과 삭제는 O(1)이 소요된다.

<br>

### 3. 크기
  * Array : 크기 고정
  * LinkedList : 크기 동적

