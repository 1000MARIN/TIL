# ArrayList와 LinkedList의 차이

<br>

### ArrayList 구조

![image](https://user-images.githubusercontent.com/84886987/151286777-d9766db9-153e-4ca8-9319-9a8ae3d2c96f.png)

>ArrayList는 내부적으로 **배열의 형태**를 지니고 있다.

<br>

### LinkedList 구조

![image](https://user-images.githubusercontent.com/84886987/151286901-0d8f34a8-7088-420b-b3ea-6baddbc2fec9.png)

>[JAVA LinkedList](https://docs.oracle.com/javase/8/docs/api/java/util/LinkedList.html)를 보게 되면 LinkedList는 이중 연결 리스트의 형태를 가지고 있음을 알 수 있다.  

<br>

***

<br>

### 1. 공간적 제약
  * ArrayList : 결국 배열이므로 길이가 고정되어 있습니다. 때문에, 새로 배열에 새로운 요소를 추가하려고 할 때, 배열의 용량이 이미 가득 차있다면 새로운 배열을 생성해주어야 합니다. 이 때, 새로 생성된 배열이 메모리 상에 연속해서 생길 수도 있지만, 이미 다른 값이 메모리를 사용하고 있는 경우, 새로운 위치에 배열이 생성되어야 하고 이는 모든 요소를 옮긴다는 얘기가 됩니다. 또 메모리에 여유공간이 없는 경우 에러가 발생할 수도 있습니다.
  * LinkedList: 한 개의 Node는 다른 Node에 대한 참조만 가지고 있습니다. 따라서 공간적 제약을 ArrayList에 비해 받지 않습니다.

<br>

### 2. 새로운 요소 추가
  * ArrayList : 새로운 요소를 추가할 때, 여유 공간이 있는 경우엔 O(1)이지만, 여유공간이 없는 경우엔 O(n)이므로 O(n)입니다.
  * LinkedList : 새로운 요소를 추가할 때, 항상 O(1)입니다. 왜냐하면, 그냥 마지막 요소에서 다음 참조값을 가지게만 하면 되기 때문입니다.

<br>

### 3. 임의 접급과 순차 접근
  * 임의 접근(Random Access) : 어떤 요소에 바로 접근하는 것.
  * 순차 접근(Sequential Access) : 어떤 요소에 접근할 때, 차례차례 접근하는 것.
  * ArrayList :임의 접근, 바로 접근이 가능하다는 것은 곧 O(1)을 의미한다.
  * LinkedList : 순차 접근만 가능, O(n)이 걸리게 됩니다.

<br>

### 4. 새로운 요소 삽입(중간에)
  * ArrayList는 해당 요소뒤의 요소들도 전부 옮겨야 합니다.
  * LinkedList는 앞 뒤 요소의 값만 바꾸어주면 됩니다.

<br>

### 5. 요소 삭제(중간에)
  * ArrayList는 뒤의 요소들을 전부 앞으로 이동시켜야합니다.
  * LinkedList의 경우에는 앞 뒤 요소의 값만 바꾸어주면 됩니다.

<br>

***

<br>

# 시간 복잡도

|   |array|arrayList|
|------|------|------|
|get / set|O(1)|O(n)|
|add(시작)|O(n)|O(1)|
|add(끝)|O(1)|O(1)|
|add(일반)|O(n)|O(n)|
|remove(시작)|O(n)|O(1)|
|remove(끝)|O(1)|O(1)|
|remove(일반)|O(n)|O(n)|

<br>

# 선택
 * 일반적으로 get/set을 자주 사용한다면? **`ArrayList`**
 * 처음이나 끝에 잦은 삽입, 삭제가 발생한다면? **`LinkedList`**
 * 하지만, 공간 복잡도의 경우 `ArrayList`는 `연속된 메모리안에 저장`되므로 낭비되는 공간이 없기 때문에 종종 속도가 더 빠른 경우가 발생하기도 한다. 
 * `LinkedList`는 요소마다 두개의 참조 노드가 필요하기 때문에 `더 많은 공간을 차지`하고, 메모리 여기저기 노드가 흩어져 존재하는 경우 효율이 더욱 떨어질 수 있으니 잘 선택하자!


