# final
>final의 의미는 최종적이란 뜻을 가지고 있다.   
>final 필드는 초기값이 저장되면 최종적인 값이 되어 프로그램 실행 도중에 수정을 할 수 없다.

## final 필드

```java
final int number = 1; //final 타입 필드 [= 초기값];
```

final 필드는 위와 같이 선언하며 final 필드의 초기값을 줄 수 있는 방법은 딱 두가지 방법밖에 없습니다. 첫번째는 필드 선언시에 주는 방법이 있고, 두번째는 생성자를 통해서 주는 방법이 있습니다. 단순 값이라면 필드 선언시에 주는 것이 가장 간단하지만 복잡한 초기화 코드가 필요하거나 객체 생성 시에 외부 데이터로 초기화를 시켜야한다면 생성자를 통해서 초기값을 부여하는 방법을 써야 합니다. 생성자는 final 필드의 최종 초기화를 마쳐야 하는데 만약 초기화가 되지 않은 final 필드가 있다면 컴파일 에러가 발생합니다.

<br>

## final 객체

```java
class Company{
    String name = "회사명";

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}

public class Final_ex {
    public static void main(String[] args) {
    	final Company company = new Company();
    	//company = new Company(); //객체를 한번 생성했다면 재생성 불가능
    	company.setName("ex회사"); //클래스의 필드는 변경가능
    }
}
```

객체 변수에 final로 선언하면 그 변수에 다른 참조 값을 지정할 수 없습니다. 즉 한번 생성된 final 객체는 같은 타입으로 재생성이 불가능합니다. 객체자체는 변경이 불가능하지만 객체 내부 변수는 변경 가능합니다.

<br>

## final 클래스

```java
//final 클래스
final class Company{
    String name = "회사명";
}

//상속 불가능
class A_Company extends Company{
	
}
```

클래스에 final을 사용하게되면 그 클래스는 최종상태가 되어 더이상 상속이 불가능합니다. final 클래스여도 필드는 Setter함수를 통하여 변경은 가능합니다.

<br>

## final 메서드

```java
class Company{
	
    String name = "회사명";

    public final void print() {
        System.out.println("회사 이름은 :"+name+" 입니다.");
    }
}

class A_Company extends Company{
	
    String name = "a회사";
	
    //메서드 오버라이드 불가능
    public void print() {
		
    }
}
```

메서드에 final을 사용하게되면 상속받은 클래스에서 부모의 final 메서드를 재정의 할 수 없습니다. 자신이 만든 메서드를 변경할 수 없게끔 하고싶을때 사용되며 시스템의 코어부분에서 변경을 원치 않는 메서드에 많이 구현되어 있습니다. 

<br>


## 메소드의 인자값에 final을 사용하는 경우

```java
class Company{
    String name = "회사명";

    public void setName(final String name) {
    	//name = "ex회사2"; //인자값으로 받은 final변수는 변경 불가능
        this.name = name;
    }
}

public class Final_ex {
    public static void main(String[] args) {
    	final Company company = new Company();
    	company.setName("ex회사");
    }
}
```
잘 사용하지는 않지만 코딩을 좀 더 명확하게 하고 싶은 경우 메서드의 인자값에 final을 사용하시는 분들이 종종 있습니다. final 필드와 마찬가지로 인자값에 final을 사용하는 경우 final 인자값의 변경이 불가능합니다.


