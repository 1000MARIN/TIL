# 반복문

```java
public class LoopApp {
 
    public static void main(String[] args) {
         
        System.out.println(1);
        System.out.println("=== while ===");
        int i = 0;
        //..
        while(i < 3) {
            System.out.println(2);
            System.out.println(3);
//          i = i + 1;
            //..
            i++;
        }
        System.out.println("=== for ===");
        for(int j=0; j < 3; j++) {
            System.out.println(2);
            System.out.println(3);
        }
         
        System.out.println(4);
 
    }
 
}
```

## 반복문 예제 (구구단 출력)
```java
public class GuGuDan {

	public static void main(String[] args) {
		// 구구단 호출 (2단 ~ 9단)
		PrintGuGuDan();
	} // end of main

	//구구단 출력 메소드!
	public static void PrintGuGuDan() {
		for (int i = 2; i <= 9; i++) {
			printDan(i); // i단 출력
		}
	} // end of PrintGuGuDan
	
	// i을 출력한다.
	// 예를 들어 i = 2 이면, 2 x 1 = 2, ... , 2 x 9 = 18
	public static void printDan(int dan) {
		System.out.printf("%d단\n", dan);
		
		// 반복문을 사용
		for (int k = 1; k <= 9; k++) {
			System.out.printf("\t");
			System.out.printf("%d x %d = %d\n", dan, k, dan * k);
		}
	} // end of printDan
}
```

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e42c5cd3-679d-4879-8dc7-19288931f47c/.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e42c5cd3-679d-4879-8dc7-19288931f47c/.png)
