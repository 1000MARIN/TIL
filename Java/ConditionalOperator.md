# 조건문
> if   
> if-else   
> else-if   

### if
![if](https://user-images.githubusercontent.com/84886987/135010962-cf172f9a-1202-4198-800b-d91b1848f7a5.png)

### if-else
![if-else](https://user-images.githubusercontent.com/84886987/135011229-bf0f963c-3949-4f28-878c-53096b11b333.png)

### else-if
![else-if](https://user-images.githubusercontent.com/84886987/135011364-aeb7738b-97c5-4978-97bf-cce70dbc210d.png)

![conditiona](https://user-images.githubusercontent.com/84886987/135011370-8c1153a4-84dd-40c2-be76-2ef0bdb0f4aa.png)

- 조건문 if는 if(true)면 if문을 실행하고 if(false)면 다음 조건문이 실행되거나 다음 조건문이 없으면 if문을 빠져나간다.
- else의 경우 조건이 반대일 때 사용한다.
- else if의 경우 if문 다음 특정 조건을 넣어줄 때 쓴다.

    ```java
    public class IfApp {
     
        public static void main(String[] args) {
     
            System.out.println("a");
            if(false) {
                System.out.println(1);
            } else if(true) {
                System.out.println(2);
            } else {
                System.out.println(3);
            }
            System.out.println("b");
     
        }
     
    }
    ```

- if문이 사용하기 위해서 값이 true일 때도 있고 false일 때도 있어야 한다.
- 문자열 비교 시에 == 를 쓰면 안되고 equals()라는 메소드를 써야한다.

    ```java
    public class AuthApp {
     
        public static void main(String[] args) {
             
            String id = "egoing";
            String inputId = args[0];
             
            System.out.println("Hi.");
             
            //if(inputId == id) {
            if(inputId.equals(id)) {
                System.out.println("Master!");
            } else {
                System.out.println("Who are you?");
            }
     
        }
     
    }
    ```

- 논리 연산자 && 를 통해서 if문을 여러개 쓰지 않고 한 if문안에 두개의 조건을 넣을 수 있다

    ```java
    public class AuthApp {
     
        public static void main(String[] args) {
             
            String id = "egoing";
            String inputId = args[0];
             
            String pass = "1111";
            String inputPass = args[1];
             
            System.out.println("Hi.");
             
            if(inputId.equals(id) && inputPass.equals(pass)) {
                System.out.println("Master!");
            } else {
                System.out.println("Who are you?");
            }       
     
        }
     
    }
    ```

ex) if( A && B ) ==> A, B 둘다 참이면 if문을 실행 하게된다!

프로그램을 아주 쉽게 정의하면 입력  값에 대한 결과 값을 내놓는 도구라고 생각하면 되는데 이때 조건문을 쓰면 원하는 조건에 따라 입력 값이 달라지므로 결과 값도 달라지는 환상적인 도구이며 매우 광범위하게 쓸 수 있다는 것을 인지하자!

## 예제 (윤년 계산)

```java
public class LeapYear {
	public static void main(String[] args) {
		// 윤년 계산하기
		// 윤년 : 1년이 366일인 해
		// 기본 적으로 년수가 4의 배수이면 윤년이다.
		// 그러나 100으로 나누어지고 떨어지는 경우 윤년이 아니다.
		// 특별히 1000으로 나누어 떨어지는 경우에는 윤년이 된다.
		
		// 입력값 받기
		int input = Integer.parseInt(args[0]); // "1988" => 1988
		
		// 윤년 여부 계산
		boolean output = isLeapYear(input); // 1988 => true
	
		
		// 결과 출력
		System.out.printf("%d년은 윤년입니까? %s", input, output);
	} // end of main
	
	// 윤년 판별 메소드
	private static boolean isLeapYear(int year) {
		// 변수 생성
		boolean result = false;
	
	
		// 조건문 처리 ( 윤년 여부 판별 )
		if ((year % 4) == 0) {
			result = true;
			
			if ((year % 100) == 0) {
				result = false;
				
				if((year % 1000) == 0) {
					result = true;
				}
			}
		}
	
		// 결과값 반환
		return result;
	}		
}
```
