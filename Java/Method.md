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
