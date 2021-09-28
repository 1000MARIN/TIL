# Java API
> 자바 API : 프로그래밍을 위해 미리 준비된 도구들   
> 패키지 : 자바 API가 담겨진 일종의 폴더   
> 패키지의 그룹화 : 관련 API를 한데 묶음   
> 패키지로 분류화 : 이름은 같지만 내용이 다른것을 구분   

<br>

# 대표적인 자바 API

## Math 클래스 : 수학 관련 기능을 제공

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/966b08c4-6543-4888-a1f2-e369eacb30fc/Math.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/966b08c4-6543-4888-a1f2-e369eacb30fc/Math.png)

## Random 클래스 : 임의의 수 생성에 특화

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cfef1227-d42b-4288-8b5b-00daba79b017/Random.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cfef1227-d42b-4288-8b5b-00daba79b017/Random.png)

## ArrayList 클래스 : 객체를 저장하는, 배열의 업그레이드 버전

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a74c8a29-f7c9-4960-906f-ebc202f6060d/ArrayList.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a74c8a29-f7c9-4960-906f-ebc202f6060d/ArrayList.png)

## 예제 (로또 번호 생성기)

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.Collections;

public class SimpleLottoMachine {

	public static void main(String[] args) {
		// 로또 번호 생성기
		
		// 45개의 공을 만든다.
		// Integer를 담기위한 객체 생성
		// Integer : int 타입을 클래스로 변형한 것
		ArrayList<Integer> numbers = new ArrayList<Integer>(); 
		for (int i = 1; i <= 45; i++) {
			numbers.add(i);	// 1 ~ 45
		}
				
		// 섞는다.
		Collections.shuffle(numbers); // ArrayList를 무작위로 섞음
		
		// 뽑는다.
		int[] picked = new int[6];
		for (int i = 0; i < 6; i++) {	// numbers의 앞 6개 숫자를 가져옴
			picked[i] = numbers.get(i);
		}
		
		// 결과 출력
		// Arrays.toString(picked); -> 배열을 간편하게 출력
		System.out.printf("자동 생성 번호: %s", Arrays.toString(picked)); 
		// 자동 생성 번호: [37, 31, 30, 17, 40, 39]
	} // end of main

} // end of SimpleLottoMachine
```
