# 1. Optional이란? Optional 개념 및 사용법

## NPE(NullPointerException)
개발을 할 때 가장 많이 발생하는 예외 중 하나가 바로 NPE(NullPointerException)이다. NPE를 피하기 위해서는 null을 검사하는 로직을 추가해야 하는데, null 검사를 해야하는 변수가 많은 경우 코드가 복잡해지고 로직이 상당히 번거롭다. 그렇기 때문에 null 대신 초기값을 사용하길 권장하기도 한다.

```java
List<String> names = getNames(); 
names.sort(); 
// names가 null이라면 NPE가 발생함 

List<String> names = getNames(); 
// NPE를 방지하기 위해 null 검사를 해야함 
if(names != null){ names.sort(); }
```

<br>

## Optional이란?
Java8에서는 Optional 클래스를 사용해 NPE를 방지할 수 있도록 도와준다. Optional는 `null이 올 수 있는 값을 감싸는 Wrapper 클래스`로, 참조하더라도 NPE가 발생하지 않도록 도와준다. Optional 클래스는 아래와 같은 value에 값을 저장하기 때문에 null이더라도 바로 NPE가 발생하지 않으며, 클래스이기 때문에 각종 메소드를 제공해준다.

```java
public final class Optional<T> { 


// If non-null, the value; if null, indicates no value is 

present private final T value; 

... 
}
```

<br>

# 2. Optional 활용하기

## Optional 생성하기
Optional은 Wrapper 클래스이기 때문에 빈 값이 올수도 있는데, 빈 객체는 아래와 같이 생성할 수 있다.

```java
Optional<String> optional = Optional.empty(); 
System.out.println(optional); // Optional.empty 
System.out.println(optional.isPresent()); // false
```

<br>

만약 어떤 데이터가 null이 올 수 있는 경우에는 해당 값을 Optional로 감싸서 생성할 수 있다. 그리고 orElse 또는 orElseGet 메소드를 이용해서 값이 없는 경우라도 안전하게 값을 가져올 수 있다.

```java
// Optional의 value는 값이 있을 수도 있고 null 일 수도 있다. 
Optional<String> optional = Optional.ofNullable(getName()); 
String name = optional.orElse("anonymous"); // 값이 없다면 "anonymous" 를 리턴
```

<br>

## Optional 사용하기
기존에는 아래와 같이 null 검사를 한 후에 null일 경우에는 새로운 객체를 생성해주어야 했다. 이러한 과정을 코드로 나타내면 다소 번잡해보이는데, Optional와 Lambda를 이용하면 해당 과정을 보다 간단하게 표현할 수 있다.

```java
// Java8 이전 
List<String> names = getNames(); 
List<String> tempNames = list != null ? list : new ArrayList<>(); 

List<String> nameList = Optional.ofNullable(getList()).orElseGet(() -> new ArrayList<>());
```

<br>

## Optional 활용 예시(1)
예를 들어 아래와 같은 우편번호를 꺼내는 null 검사 코드가 있다고 하자.

```java
public String findPostCode() { 
  UserVO userVO = getUser(); 
  if (userVO != null) { 
    Address address = user.getAddress(); 
      if (address != null) { 
        String postCode = address.getPostCode(); 
          if (postCode != null) { 
            return postCode; 
          } 
        } 
      } 
      return "우편번호 없음"; 
    }
```

<br>

하지만 이러한 코드를 Optional을 사용하면 아래와 같이 표현할 수 있다.

```java
public String findPostCode() { 
  // 위의 코드를 Optional로 펼쳐놓으면 아래와 같다. 
  Optional<UserVO> userVO = Optional.ofNullable(getUser()); 
  Optional<Address> address = userVO.map(UserVO::getAddress); 
  Optional<String> postCode = address.map(Address::getPostCode); 
  String result = postCode.orElse("우편번호 없음"); 
  
  // 그리고 위의 코드를 다음과 같이 축약해서 쓸 수 있다. 
  String result = user.map(UserVO::getAddress) 
    .map(Address::getPostCode) 
    .orElse("우편번호 없음"); 
}
```

<br>

## Optional 활용 예시(2)

예를 들어 아래와 같이 이름을 대문자로 변경하는 코드에서 NPE 처리를 해준다고 하자.

```java
String name = getName(); 
String result = ""; 
try { 
  result = name.toUpperCase(); 
} catch (NullPointerException e) { 
  throw new CustomUpperCaseException(); 
}
```

<br>

위의 코드는 다소 번잡하고 가독성이 떨어지는데 이를 Optional를 활용하면 아래와 같이 표현할 수 있다.

```java
Optional<String> nameOpt = Optional.ofNullable(getName()); 
String result = nameOpt.orElseThrow(CustomUpperCaseExcpetion::new) 
          .toUpperCase();
```

## Optional 정리

  * Optional은 `null 또는 실제 값을 value로 갖는 wrapper로 감싸서 NPE(NullPointerException)로부터 자유로워지기 위해 나온 Wrapper 클래스`이다. 
  * 따라서 Optional을 반환하는 메소드는 절대 null을 갖는 value를 반환해서는 안된다. 
  * 또한 `Optional은 값을 Wrapping하고 다시 풀고, null일 경우에는 대체하는 함수를 호출하는 등의 오버헤드가 있으므로 성능이 저하될 수 있다.` 
  * 그렇기 때문에 `메소드의 반환 값이 절대 null이 아니라면 Optional을 사용하지 않는 것이 성능저하가 적다.` 
  * 즉, Optional은 `메소드의 결과가 null이 될 수 있으며, 클라이언트가 이 상황을 처리해야 할 때` 사용하는 것이 좋다.

<br>

# Optional의 orElse와 orElseGet 차이

## orElse VS orElseGet
Optional API의 단말 연산에는 orElse와 orElseGet 함수가 있다. 비슷해 보이는 두 함수는 엄청난 차이가 있는데, 해당 내용을 요약하면 아래와 같다.

  * orElse: Optional 안의 값이 null이든 아니든 항상 호출된다.
  * orElseGet: Optional 안의 값이 null일 경우에만 호출된다.

<br>

## orElse와 orElseGet 차이 예시

```java
public void findUserEmail() { 
  String userEmail = "Empty"; 
  String result1 = Optional.ofNullable(userEmail).orElse(getUserEmail()); 
  System.out.println(result1); 
  
  userEmail = "Empty"; 
  String result2 = Optional.ofNullable(userEmail).orElseGet(this::getUserEmail); 
  System.out.println(result2); 
} 

private String getUserEmail() { 
  System.out.println("getUserEmail() Called"); 
  return "userEmail@gmail.com"; } 
  
  //getUserEmail() Called 
  //Empty 
  
  //Empty
```

<br>

출력 결과를 분석해보면 `orElse의 경우 값이 null이든 아니든 호출`되어야 하므로 뒤의 연산이 진행되어야 하며, 출력 결과를 통해 해당 함수가 호출되었음을 볼 수 있다. 
하지만 `orElseGet의 경우에는 null일 때만 해당 연산이 진행`되므로 userEmail이 null이 아니기 때문에 getUserEmail()이 호출되지 않았음을 확인할 수 있다. 
또한 위의 코드에서 orElse의 경우는 getUserEmail()을 매개변수로 사용하고, orElseGet은 this::getUserEmail을 매개변수로 사용하고 있다. 
그 이유는 orElse는 값을 취하고 orElseGet은 Supplier를 취하기 때문이다. 

<br>

위의 코드를 보다 직관적으로 수정하면 아래와 같다.

```java
public void findUserEmail() { 
  String userEmail = "Empty"; 
  String value = getUserEmail(); 
  String result1 = Optional.ofNullable(userEmail).orElse(value); 
  System.out.println(result1); 
  
  userEmail = "Empty"; 
  Supplier<String> supplier = this::getUserEmail; 
  String result2 = Optional.ofNullable(userEmail).orElseGet(supplier); 
  System.out.println(result2); 
  
} 
  
  private String getUserEmail() { 
  System.out.println("getUserEmail() Called");
  return "userEmail@gmail.com"; 
}
```

<br>

## orElse와 orElseGet에 의한 장애
orElse와 orElseGet은 명확하고 중요한 차이점을 가지고 있는데, 차이점을 정확히 인식하지 못하면 장애가 발생할 수 있다. 예를 들어 userEmail을 Unique한 값으로 갖는 시스템에서 아래와 같은 코드를 작성하였다고 하자.

```java
public void findByUserEmail_Wrong(String userEmail) { 
  // orElse에 의해 userEmail이 이미 존재해도 유저 생성 함수가 호출되어 에러 발생 
  return userRepository.findByUserEmail(userEmail) 
    .orElse(createUserWithEmail(userEmail)); 
} 

public void findByUserEmail_Right(String userEmail) { 
  // orElse를 null일 때만 호출되는 orElseGet으로 수정해야 함 
  return userRepository.findByUserEmail(userEmail) 
    .orElseGet(createUserWithEmail(userEmail)); 
} 

public void findByUserEmailDetail(String userEmail) { 
  User newUser = createUserWithEmail(userEmail); 
  return userRepository.findByUserEmail(userEmail).orElse(newUser); 
} 

private String createUserWithEmail(String userEmail) { 
  User newUser = new User(); 
  newUser.setUserEmail(userEmail); 
  return userRepository.save(newUser); 
}
```

위의 예제는 Optional의 단말 연산으로 **orElse**를 사용하고 있기 때문에, `입력으로 들어온 userEmail을 사용중인 User를 발견하더라도 해당 userEmail을 갖는 사용자를 생성`하게 된다. 보다 직관적으로 이해하기 위해 findByUserEmail 코드를 자세하게 풀어쓰면 findByUserEmailDetail과 같다. 하지만 Database에서는 userEmail이 Unique로 설정되어 있기 때문에 오류가 발생하게 된다. 그렇기 때문에 위와 같은 경우에는 해당 코드를 `orElseGet으로 수정`해야 한다. 실제 서비스에서 위와 같은 오류를 범한다면 큰 시스템 장애로 돌아오게 된다. 설령 문제가 없다고 하더라도 `orElse는 orElseGet보다 비용이 크므로 최대한 사용을 피해야 한다.`

그러므로 orElse와 orElseGet의 차이점을 정확히 이해하고 사용하도록 하자.

<br>

## orElse VS orElseGet 사용 정리

  * orElse
    - Optional의 값이 null이든 아니든 항상 호출된다.
    - 그에 따른 비용이 추가되고, 문제가 발생할 수 있다.
    - 값이 미리 존재하는 경우에 사용한다.

  * orElseGet
    - Optional의 값이 null일 경우에만 호출된다.
    - 비용이 orElse보다 저렴하며, 불필요한 문제가 발생하지 않는다.
    - 값이 미리 존재하지 않는 거의 대부분의 경우에 orElseGet을 사용하면 된다.

