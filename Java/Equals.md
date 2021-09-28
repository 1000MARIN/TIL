# ==과 equals의 차이점
> primitive (원시의) 자료형 : char, boolean, int, double, float, short, long ...   
> non primitive(비원시의) 자료형 : String, File, Date, class ..   
![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/093ffeeb-af85-45a8-be01-dcc229c1dfa7/_equals_.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/093ffeeb-af85-45a8-be01-dcc229c1dfa7/_equals_.png)

```java
public class AuthApp2 {
 
    public static void main(String[] args) {
         
        String id = "egoing";
        String inputId = args[0];
         
        String pass = "1111";
        String pass2 = "2222";
        String inputPass = args[1];
         
        System.out.println("Hi.");
        boolean isRightPass = (inputPass.equals(pass) || inputPass.equals(pass2));
        if(inputId.equals(id) && isRightPass ) {
            System.out.println("Master!");
        } else {
            System.out.println("Who are you?");
        }       
 
    }
 
}
```

- == : 두 비교 대상의 데이터의 저장된 위치가 같은가? => 원시 데이터 사용
- equals : 두 비교 대상의 데이터 내용이 같은가? => 원시 데이터 아닌 데이터에 사용
- 예외> String
