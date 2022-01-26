# Spring DI(의존성 주입, Dependency Injection)   
>의존성 주입은 IoC(Inversion of Control - 제어권 역전)의 일종   


<br>


* 일반적인 의존성에 대한 제어권 : 개발자가 직접 의존성을 만든다.  
* 의존성은 쉽게 말해 어떤 객체가 사용해야 할 객체라고 할 수 있고, 이것을 직접 new 등을 써서 만들어 쓰면 의존성을 자기가 직접 만들어 쓴다고 할 수 있다.   

<br>

```java
public class OwnerController {
	private OwnerRepository ownerRepository = new OwnerRepository();
}
// OwnerController가, 필요한 OwnerRepository의 객체를 직접 생성하는 경우
```

<br>

### Inversion of Control - 제어권 역전   
* IoC 라는 말 자체는 어렵게 들릴 수 있지만, 위에서처럼 직접적으로 의존성을 만들지 않고, 외부에서 의존성을 가져오는 경우를 말한다.    
* 즉, 밖에서 나에게 의존성을 주입해주는 것을 DI(Dependency Injection) 라고 합니다. 따라서 DI는 IoC의 일종이라고 생각하시면 e된다.    

<br>

```java
public OwnerController(OwnerRepository clinicService, VisitRepository visits) {
		this.owners = clinicService;
		this.visits = visits;
}
// OwnerController의 생성자에서 OwnerRepository를 인자로 받고, owners에 담고 있다.
// 이는 앞의 예시처럼 객체를 직접 생성하지 않고, 외부의 객체를 받고 있는 것이다.
```

<br>

## 스프링에서 의존성을 주입하는 방법

<br>

* 생성자에서 주입    
* 필드에서 주입    
* setter 에서 주입    

<br>

스프링에서 @Autowired 어노테이션은 filed, 생성자, setter 메소드 등에 붙여서 사용할 수 있다.
이는 의존성을 주입할 때 붙이게 되는데, 스프링 4.3 이상부터는 생성자로 의존성을 주입할 때에는 @Autowired 어노테이션을 생략할 수 있다.

### (1) 생성자 활용 : OwnerController에 OwnerRepository 의존성을 생성자를 통해 주입
```java
public OwnerController(OwnerRepository clinicService, VisitRepository visits) {
		this.owners = clinicService;
		this.visits = visits;
	}
```

<br>

### (2) 필드에서 주입
```java
@Autowired
private OwnerRepository owners; // OwnerRepository가 이미 Bean으로 등록된 상태에서, owners에 의존성을 주입해 달라는 의미
// 필드가 final 변수일 경우 주입받을 수 없습니다.
```

<br>

### (3) setter 메소드 에서 주입
```java
@Autowired
public void setOwners(OwnerRepository owners){
	this.owners = owners;
}
```

<br>

이 중 <span style="color:red">스프링 레퍼런스에서 권장하는 방법은 (1) 생성자에서 주입받는 것.</span>

이것이 권장되는 이유는, 필수적으로 사용해야 하는 레퍼런스(객체, 의존성) 없이는 인스턴스를 만들지 못하도록 강제하는 역할을 할 수 있기 때문.

가령 위의 (1)번 예시에서는 생성자의 인자에 OwnerRepository type의 객체를 받고 있기 때문에, OwnerController는 OwnerRepository 없이는 객체 생성이 불가능.
