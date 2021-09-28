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
