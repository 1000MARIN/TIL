# 배열
> 같은 타입의 여러 변수를 하나의 묶음으로 다루는 것   
> 자바에서 배열은 String과 같은 객체

![image](https://user-images.githubusercontent.com/84886987/135013136-10336869-287e-4218-ad4e-f6df39c7f232.png)


```java
public class LoopArray {
 
    public static void main(String[] args) {
        /*
         *  <li>egoing</li>
         *  <li>jinhuck</li>
         *  <li>youbin</li>
         */
         
        String[] users = new String[3];
        users[0] = "egoing";
        users[1] = "jinhuck";
        users[2] = "youbin";
         
        for(int i=0; i<users.length; i++) {
            System.out.println(users[i]+",");
        }
         
    }
 
}
```

- 출발 순서 정할 수 있음 i=1 (두번째에서 시작), i=2 (세번째에서 시작)
- uesrs.length : 배열의 갯수






## 배열 예제 (하루 평균 사용자 구하기)

```java
public class DailyUser {

	public static void main(String[] args) {
		// 하루 평균 사용자 구하기
		
		// 배열의 평균값
		int [] counts = { 581, 512, 527, 495, 423, 141, 236 };		
		
		// 메소드 호출을 통한 계산
		double result = average(counts);
		
		// 결과 출력
		System.out.printf("하루 평균 사용자: %.2f명", result); // 하루 평균 사용자: 416.43명
	} // end of main

	private static double average (int[] arr) {
		//총합
		double sum = 0;
		for (int i = 0; i < arr.length; i++) {
			sum += arr[i];
		}
		
		// 평균
		// int / int => int
		// double / double => double
		double avg = sum / arr.length; // 총합 / 개수 => 평균
		
		// 결과값 반환
		return avg;
	} // end of average
}
```

```java
// 장점은 편하지만 단점은 출발 순서를 지정할 수 없다.
		for (String name : strArr) {
			System.out.println(name);
		}
```
