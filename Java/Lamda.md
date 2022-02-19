# 람다식(Lamda Expression)
>프로그래밍 언어에서 사용되는 개념으로 '익명함수(Anonymous Function)'를 지칭하는 용어
>수학에서 사용하는 함수를 보다 단순하게 표현하는 법(함수를 변수처럼 사용)
>Java 8부터 기능이 포함됨

<br>

## 특징
  * 이름이 필요 없음 - 익명 함수(Anonymous Function)
  * 파라미터가 있는 함수는 괄호 안에 지정하여 사용

<br>

## 람다식의 장점

  * 코드의 라인수가 줄어듬
    - 메소드로 표현된 코드에 비해 확연히 라인 수가 줄어듬
  * 병렬 프로그래밍이 가능
    - iteration 방식은 반복 대상을 일일히 루프에서 지정하는 반면에, 함수형 프로그래밍에서는 반복 대상을 사용자 코드에서 직접 지정하지 않음
  * 람다식으로 바로 실행문을 전달할 수 있음
    - 자바 메소드로 값이나 객체를 생성하여 전달하던 예전 방식과 달리, 람다식에서는 실행문 자체를 람다식으로 전달하여 구현
  * 의도의 명확성
    - 가독성이 높음

<br>

## 람다식의 단점

  * 람다식은 재사용이 불가

    - 일회용 함수 정의가 목적

  * 불필요하게 너무 사용하게 되면 가독성이 오히려 떨어짐

    - 같은 기능의 함수를 여러 번 정의하는 상황이 발생할 수 있음

<br>


## 람다식의 표현

(매개변수) -> {함수 구현부}
() -> {함수 구현}

  * 람다식은 화살표(->)를 사용
  * 매개변수가 하나일 경우 매개변수 생략 가능
  * 작성할 실행문이 단일일 경우 괄호({}) 생략 가능
  * 단, return 식의 단일 실행문의 경우 괄호 생략 불가

<br>

### 예제 코드

```java
// FunctionalInterface : 구현해야할 추상 메소드가 한개인 인터페이스
@FunctionalInterface
interface Print {
    void print(int a, int b);
}

class Test {
    public void testMethod(Print print) {
        print.print(1, 2);
        System.out.println("콘솔 출력 실행문");
    }
}

public class LamdaExample1 {
    public static void main(String[] args) {

        Test noLamda = new Test();
        noLamda.testMethod(new Print() {
            @Override
            public void print(int a, int b) {
                System.out.println("a와 b의 합은 " + (a + b));
                System.out.println("a와 b의 차은 " + (a - b));
            }
        });

        Test lamdaTest = new Test();
        lamdaTest.testMethod((a, b) -> {
            System.out.println("a와 b의 합은 " + (a + b));
            System.out.println("a와 b의 차은 " + (a - b));
        });
    }
}
```

<br>

```java
// FunctionalInterface : 구현해야할 추상 메소드가 한개인 인터페이스
@FunctionalInterface
interface BigNumber {
    int getBigNumber(int num1, int num2);
}

public class LamdaExample2 {
    public static void main(String[] args) {

        BigNumber bigNumber = (x, y) ->{
            if (x > y) {
                return x;
            } else {
                return y;
            }
        };

        int result = bigNumber.getBigNumber(2156, 12382);
        System.out.println(result);
    }
}
```

<br>

```java
// FunctionalInterface : 구현해야할 추상 메소드가 한개인 인터페이스
@FunctionalInterface
interface BigNumber {
    int getBigNumber(int num1, int num2);
}

public class LamdaExample2 {
    public static void main(String[] args) {
        BigNumber bigNumber = (x, y) ->{
            if (x > y) {
                return x;
            } else {
                return y;
            }
        };
        int result = bigNumber.getBigNumber(2156, 12382);
        System.out.println(result);
    }
}
```

