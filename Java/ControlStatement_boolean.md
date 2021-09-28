# boolean
> boolean data type은 true, false 두가지로 나뉜다.   
> 참, 거짓을 구분할 때 쓰인다.   

```java
public class BooleanApp {
 
    public static void main(String[] args) {
         
        System.out.println("One");
        System.out.println(1);
         
        System.out.println(true);
        System.out.println(false);
         
        String foo = "Hello world";
        // String true = "Hello world"; reserved word
         
        System.out.println(foo.contains("world"));
        System.out.println(foo.contains("egoing"));
 
    }
 
}
```

예를 들면 java의 메소드에는 contains라는 메소드가 있는데 내가 입력한 문장을 포함하고있는지 확일할때 쓰는 메소드이다. 그리고 결과는 true, false로 결정된다.

**String Foo = "Hello World"**

**System.out.println(Foo.contains("World"));**

--> 결과는 true가 된다. Foo에는 World라는 단어가 포함되어있기 때문이다.
