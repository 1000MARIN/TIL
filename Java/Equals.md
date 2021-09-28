# ==과 equals의 차이점
> primitive (원시의) 자료형 : char, boolean, int, double, float, short, long ...   
> non primitive(비원시의) 자료형 : String, File, Date, class ..   

<br>

![_equals_](https://user-images.githubusercontent.com/84886987/135011913-236f8515-504d-41a6-88ee-871fd1c2f234.png)



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
