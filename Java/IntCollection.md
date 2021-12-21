# 콜렉션
> 데이터관리를 직접 할 필요 없다.   
> 배열의 경우 공간의 크기가 고정,콜렉션은 공간을 늘려준다.    
> 공간을 지운다고 갯수를 지우는 것이 아니다.
<br>

## 예제 : 정수형 콜렉션 구현하기
```java
public class Program {

	public static void main(String[] args) {
		 IntList list = new IntList();
		 list.add(3);
		 list.add(5);
		 int size = list.size();
		 System.out.printf("size : %d\n", size); // clear하기 전 상태
		 
		 list.clear();
		 size = list.size();
		 System.out.printf("size : %d\n", size); // clear한 후 상태
		 
		 list.add(7);
		 int num = list.get(0);
		 System.out.printf("num : %d\n", num);	// 0번째 num값 출력
		 num = list.get(1);		        // 1번째 값 읽기 -> 1번째 값 없음  -> IndexOutOfBoundsException 오류 발생
	} // end of main
} // end of Program
```

```java
public class IntList {
	
	private int[] nums;
	private int current;
	
	public IntList() {
		nums = new int[3];
		current = 0;
	}
	
	public void add(int num) {
		nums[current] = num;
		current++;
	}

	public void clear() {
//		for(int i = 0; i <current; i++) 
//			nums[i] = 0;
		
		//nums = new int[3];
		current = 0;	
	}

	public int size() {
		return current;
	}

	public int get(int index) {
		if(current <= index)
			throw new IndexOutOfBoundsException();
		
		return nums[index];
	}

} // end of IntList
```
