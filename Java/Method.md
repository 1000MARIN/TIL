# 메소드

![image](https://user-images.githubusercontent.com/84886987/135013379-8fa8bf4c-ee59-4d0c-ba7b-53aa0b377716.png)
![image](https://user-images.githubusercontent.com/84886987/135013386-1e7577a8-e291-4c9d-85af-0819cfe730e7.png)

<br>

## Method의 기본형식

- 메소드 - 함수
- 기능 : 리팩토링 (복잡한 코드를 심플하게 만든다)
- 마우스 우클릭 -> 리릭터 -> Extract Method -> pubilc check

![image](https://user-images.githubusercontent.com/84886987/135013493-95fd31da-6ea2-4e28-b8dd-2146b3b0724f.png)


```java
public class WhyMethod {
     
    public static void main(String[] args) {
         
        // 100000000
        printTwoTimesA();
        // 100000000
        printTwoTimesA();
        // 100000000
        printTwoTimesA();
 
    }
 
    public static void printTwoTimesA() {
        System.out.println("-");
        System.out.println("a");
        System.out.println("a");
    }
 
}
```

<br>

## Method의 입력 값

1. **인자, argument**
    
    사용자가 해당 메소드에 집어 넣어 원하는 결과를 얻기 위해 입력하는 값, 매개변수를 통해 메소드로 들어가 지역변수에 의해 위치를 잡고 해당위치의 코드의 실행한 결과값의 원인이 되는 값
    
2. **매개 변수, parameter**
    
    메소드의 밖에서 메소드를 인자와 같이 사용했을 때 인자를 메소드 안으로 불러들이는 매개체
    
3. **지역 변수, Local Variable**
    
    메소드 안에서 매개변수가 불러들인 인자가 들어갈 지점을 알려주는 변수
    

```java
public class WhyMethod {
     
    public static void main(String[] args) {
         
                         //인자, argument
            printTwoTimes("a", "-");
            // 100000000
            printTwoTimes("a", "*");
            // 100000000
            printTwoTimes("a", "&");
            printTwoTimes("b", "!");
 
    }
                                     //매개변수,parameter 
    public static void printTwoTimes(String text, String delimiter) {
        System.out.println(delimiter);
        System.out.println(text);
        System.out.println(text);
    }
 
}
```

<br>

## Method의 출력

```java
public class OutputMethod {
     
    public static String a() {
        // ... 
        return "a";
    }
     
    public static int one() {
        return 1;
        //...
    }
 
    public static void main(String[] args) {
 
        System.out.println(a);
        System.out.println(one);
         
    }
 
}
```

## return; 의미 하는 것?

return **; 가 뜻하는것은 메소드의 실행 결과 값이 **가 된다는 뜻

동시에 그 메소드가 종료된다고 알려주는것이기도 하지요. 그래서 리턴뒤에 아무리 씨부려도 그 코드들은 죽은 코드들이 됩니다. 실행이 안돼요.

이런 메소드는 출력을 위해서 조건을 가지고 있는데요,

메소드는 메소드의 리턴값이 어떤 자료형으로 리턴되는지에 대해서 초반에 적시해주어야 합니다.

public static String ~() {} , public static int ~() {}, 와 같이 메소드는 어떤 값으로 출력이 되는것이기 때문에 그 값에 대한 자료형을 명기해주어야 해요.

근데 return 값을 지정해주지 않을 때에는 자료형의 자리에 우리가 그렇게 많이 보아왔던 public static void , void 를 써주면 됩나다.

자, 이런 메소드의 리턴값으로 출력되는 형태가 왜 중요하나? 라고 물을수 있겠지요, 영상도 점점 어려워지기도 하고. 뭔소린지도 모르고 멍때릴때도 많구요.

정신 바짝 차려 강의를 듣다보면 우리는 지금까지 항상 sysout, sout 형태로 화면에 출력하는 코드들을 중점적으로 다루었음을 보게 됩니다.

즉, 화면에 출력하는것 그 이상의 코드 재활용성이 떨어지게 된다는것이지요. 화면을 출력하는 것으로 끝난거니까요 그친구는.

그런데, 리턴값을 가지는 메소드는 sysout형태로 존재하는것이 아니라 하나의 "값"으로 존재하기 떄문에 어디다가 가져다가 써도 만사 오케이의 재활용성을 확보하게 됩니다.

그래서 여러군데서 쓸 수 있는거고, 강의에서 보여주신 예시는 이런 값들이 실제로 이렇게 쓰일 수 있다는것을 보여주신겁니다.

그래서 정리를 좀 하자면,

- 1. 메소드는 입력값이 있습니다. 그리고 그것을 처리해서 출력해줍니다.
- 2. 이런 출력을 위해서 사용하는 핵심 키워드는 return 이고, 이런 리턴에서 사용되는 값의 자료형을 앞서 메소드가 시작될때 명기해주어야 합니다. (리턴값 지정 안해줘도 되는건 void로 작성합니다.)
- 3. return 값을 가지고는 메소드는 메소드의 재사용성이 높아집니다.

## void

void라는 것은 return 값이 없다는 것이므로 return 값이 없는 method를 만들 때 사용한다.
