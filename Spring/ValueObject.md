# 엔티티 타입 vs 값 타입

<br>

## 엔티티 타입

  * `@Entity`로 정의하는 객체
  * 식별자를 통해 지속적으로 추적이 가능해 값을 변경해도 식별자를 통해 같은 객체인지 인식 가능
  * 생성, 소멸, 영속 등의 생명 주기가 존재
  * 다른 객체에서 참조가 가능

## 값 타입
  * int, Integer, String 등 단순히 값으로 사용하는 자바 기본 타입이나 객체
  * 식별자가 없고 값만 존재하기 때문에 추적이 변경시 불가능
  * 생명주기를 엔티티에 의존. 의존하는 엔티티가 제거되면 함께 삭제
  * 공유하지 않는 것이 안전
  
<br>  

# 기본 값 타입
>basic value type
>기본 타입, 래퍼 클래스나 String 등을 사용한다.
>값 타입의 속성은 식별자 값이 없으며, 공유를 막아야 한다. 만약 공유를 허용하면 회원의 이름을 변경할 때 다른 회원의 이름까지 변경될 위험이 존재하기 때문이다.
>또한, 생명주기도 소속된 엔티티에 의존한다. 회원을 삭제하면 회원의 나이나 이름도 함께 삭제된다.

```java
@Entity
public class Member {
    ...
    private String name; // 기본 값 타입
    
    private int age; // 기본 값 타입
    ...
}
```

<br>

# 임베디드 타입(복합 값 타입)
>embedded type, components   
>새로운 값 타입을 직접 정의해 사용하는 것   

값을 새로 정의해 사용하면 재사용이 가능하고, 응집성이 높아지게 된다. 또한, 값마다 특정 메소드를 생성할 수 있기 때문에 객체 지향적인 설계가 가능해진다.

임베드드 타입도 값 타입이기 때문에 엔티티가 아닌 단순한 엔티티의 값이다. 때문에 추척도 불가능하고 엔티티에 생명주기를 의존한다.

임베디드 타입의 경우 기본 생성자를 필수적으로 생성해야 한다.

* `@Embedded` : 값 타입을 사용하는 곳에 작성한다.
* `@Embeddable` : 값 타입을 사용하는 곳에 작성한다.

둘 중 하나만 명시해도 되지만, 둘 다 적는 것이 좋다.

```java
@Entity
public class Member {
  ...
  @Embedded // 값 타입을 사용
  private Period workPeriod;
  ...
}
```

```java
@Embeddable // 값 타입 정의
@NoArgsConstructor // 기본 생성자 필수
public class Period {
    private LocalDateTime startDate;
    private LocalDateTime endDate;
    
    public boolean isWork(Date date){
        // 별도의 메소드 정의가 가능
    }
}
```

<br>

## 테이블 매핑

임베디드 타입은 엔티티에 값일 뿐이기 때문에 임베디드 타입을 엔티티에 적용해도 **데이터베이스 테이블의 형태는 적용하기 전과 동일**하다.

덕분에 객체와 테이블을 세밀하게(fine-grained) 매핑하는 것이 가능하다. 잘 설계한 ORM 애플리케이션은 매핑한 테이블의 수보다 클래스 수가 더 많게 된다.

<br>

## 연관 관계

임베디드 타입은 **값 타입**을 포함하거나 **엔티티의 참조**가 가능하다.

```java
@Entity 
public class Member {
    ...
    @Embedded
    private Address address;
    
    @Embedded
    private PhoneNumber phoneNumber;
    ...
}
```

```java
@Embeddable
public class Address {
    private String city;
    private String street;
    
    @Embedded
    private Zipcode zipcode; // 임베디드 타입 포함
}
```

```java
@Embeddable
public class PhoneNumber {
    private String number;
    
    @ManyToOne
    private PhoneServiceProvider provider; // 엔티티 참조
}
```

<br>

## @AttributeOverride

만약 한 엔티티에 같은 임베디드 타입을 추가한다면 매핑하는 컬럼명이 중복되게 되는데, 이 때 `@AttributeOverride`를 통해 임베디드 타입에 정의한 **매핑 정보를 재정의**하면 된다.

```java
@Entity 
public class Member {
    ...
    @Embedded
    private Address homeAddress;
    
    @Embedded
    @AttributeOverrides({ // 새로운 컬럼에 저장 (컬럼명 속성 재정의)
        @AttributeOverride(name = "city", column = @Column(name = "COMPANY_CITY")),
        @AttributeOverride(name = "street", column = @Column(name = "COMPANY_STREET")),
        @AttributeOverride(name = "zipcode", column = @Column(name = "COMPANY_ZIPCODE"))
    })
    private Address companyAddress;
    ...
}
```

`homeAddress`는 기존 컬럼명이 그대로 저장되고 `companyAddress`는 새로 정의된 컬럼명을 사용하게 된다.

<br>

## null

만약 임베디드 타입을 `null`로 매핑한다면 매핑한 컬럼의 값은 모두 `null`이 된다. 만약 회원 주소에 `null`을 매핑하면 CITY, STREET, ZIPCODE가 모두 `null`이 된다.

```java
member.setAddress(null);
em.persist(member);
```

<br>

# 값 타입과 불변 객체
>값 타입은 객체를 단순화하려고 만든 개념이기 때문에 값 타입은 안전하고 단순하게 다룰 수 있어야 한다.

<br>

## 값 타입 공유 객체

임베디드 타입은 같은 값 타입을 여러 객체에서 공유하면 다양한 Side Effect(부작용)가 발생할 수 있기 때문에 위험하다. 만약 서로 다른 회원이 같은 객체를 참조할 경우 다른 회원의 정보도 변경될 수 있고, 이러한 버그는 찾아내기 어렵기 때문에 굉장히 주의해야 한다.

```java
Address address = new Address("Old City", "Street", "12345");

member1.setAddress(address);
em.persist(member1);

member2.setAddress(address);
em.persist(member2);

member1.getAddress().setCity("New City"); // Member1의 주소를 변경하고 싶음

tx.commit(); // UPDATE 쿼리가 2번 발생해 member1과 2의 주소가 모두 변경
```


<br>

## 값 타입 복사
만약 같은 값 타입을 사용하고 싶다면 값(인스턴스)를 복사해 사용해야 한다.


```java
Address address = new Address("Old City", "Street", "12345");

member1.setAddress(address);
em.persist(member1);

Address copyedAddress = new Address(address.getCity(), address.getStree(), address.getZipcode());
// Address copyedAddress = address.clone(); clone()메소드를 구현해 복사해도 된다!

member2.setAddress(copyedAddress); // 복사된 주소로 저장한다.
em.persist(member2);

member1.getAddress().setCity("New City"); // member1의 주소만 변경된다.
```

자바는 객체에 값을 대입하면 항상 참조값을 전달하기 때문에 같은 인스턴스를 조회하게 되는데, 값을 복사해 사용하면 공유 객체를 사용해 발생하는 문제점을 피할 수 있다.

<br>

## 불변 객체(Immutable Object)
값을 복사해 사용하면 복사를 하지 않고 원본 객체를 넘기는 것을 컴파일 단계에서 막을 수 없는데, 이를 해결하는 방법은 객체의 값을 수정하지 못하는 ``불변 객체(Immutable Object)``로 설계하면 된다. **같은 객체를 참조하더라도 값을 수정할 수 없기 때문에 부작용이 발생하지 않는다.**

불변 객체를 만들기 위해서는 생성자로만 값을 설정하고, setter를 만들지 않으면 된다. 래퍼 클래스와 String은 자바가 제공하는 대표적인 불변 객체이다.

<br> 

만약 값을 변경하고 싶다면 새로운 객체를 생성해 새로 할당해줘야 한다.

## 값 타입 비교

자바가 제공하는 객체의 비교는 2가지가 존재

  * 동일성(Identity) : 인스턴스의 `참조 값`을 비교하는 것. `==`를 사용
  * 동등성(Equivalence) : 인스턴스의 `값`을 비교하는 것. `equals()`를 사용

<br>

```java
Address a = new Address("City", "Street", "12345");
Address b = new Address("City", "Street", "12345");
```

만약 `a == b`로 동일성을 비교하면 둘은 다른 인스턴스이므로 `false`가 반환된다. 때문에 `값 타입을 비교`하려면 `equals()`를 `재정의해 동등성 비교`를 해야 한다. 또한, `equals()`를 재정의하면 hashCode()도 함께 재정의하는 것이 좋다.

<br>
<br>

# 컬렉션 값 타입
>collection value type    
>값 타입을 하나 이상 저장하려면 컬렉션에 보관하고 `@ElementCollction`, `@CollectionTable` 애노테이션을 사용하면 된다.   

<br>

```java
@Entity
public class Member {
    ...
    @ElementCollection
    @CollectionTable(
        name = "ADDRESS",
        joinColumns = @JoinColumn(name = "MEMBER_ID"))
    private List<Address> addressHistory = new ArrayList<>();
    
    @ElementCollection
    @CollectionTable(
        name = "FAVORITE_FOOD",
        joinColumns = @JoinColumn(name = "MEMBER_ID"))
    @Column(name = "FOOD_NAME") // 컬럼명 지정
    private Set<String> favoriteFoods = new HashSet<>();
    ...
}
```
데이터베이스 테이블은 컬럼 안에 컬렉션을 담을 수 없고, 값만 보관할 수 있다. 때문에 별도의 테이블을 추가해야 하는데, `@CollectionTable`을 사용해 추가한 테이블을 매핑해야 한다. 만약 `@CollctionTable`을 생략하면 기본 값을 사용해서 매핑하게 된다.

  * {엔티티 이름}_{컬렉션 이름}
  * Member의 addressHistory => MEMBER_ADDRESSHISTORY
 

매핑되는 테이블의 컬럼이 하나라면 `@Column`을 사용해 컬럼명을 지정할 수 있다. 또한, 테이블의 매핑 정보를 변경하고 싶다면 `@AttributeOverride`를 통한 재정의도 가능하다.

<br>

## 사용

<br>

### 저장

```java
// INSERT 1
Member member = new Member();
Address address = new Address("city", "street", "12345");

member.setHomeAddress(address); // 임베디드 값이기 때문에 회원을 저장할 때 함께 저장

member.getFavoriteFoods().add("피자"); // INSERT 2
member.getFavoriteFoods().add("치킨"); // INSERT 3
member.getFavoriteFoods().add("콜라"); // INSERT 4

member.getAddressHistory().add(new Address("old city1", "street1", "10001")); // INSERT 5
member.getAddressHistory().add(new Address("old city2", "street2", "10002")); // INSERT 6

em.persist(member);

tx.commit();
```

`em.persist(member)`를 호출하면 총 6개의 INSERT 쿼리가 실행된다.

<br> 

값 타입들은 Member에 소속된 값으로 라이프 사이클이 Member에 의존된다. 때문에 영속성 전이(cascade)와 고아 객체 제거(orphan remove)를 설정한 것과 동일하다.

<br>

### 조회

컬렉션 값 타입도 fetch 전략을 사용할 수 있는데 기본적으로 LAZY 전략을 사용한다. `@ElementCollection(fetch = FetchType.LAZY)`

때문에 Member를 조회하면 Embedded값인 Address는 함께 조회되지만 컬렉션들은 아직 조회되지 않은 상태이고, 실제 사용할 때 SELECT 쿼리를 통해 가져오게 된다.

```java
Member member = em.find(Member.class, id); // SELETE 1

Address address = member.getAddress(); // 이미 값을 가지고 있어 새로운 쿼리 발생❌

// SELECT 2
List<Address> addressHistory = findMember.getAddressHistory();
for (Address address : addressHistory) {
    // 로직
}

// SELECT 3
Set<String> favoriteFoods = findMember.getFavoriteFoods();
for (String favoriteFood : favoriteFoods) {
    // 로직
}
```

<br>

### 수정

```java
// 1.
member.setAddress(new Address("New City", "New Street", "54321"));

// 2.
Set<String> favoriteFoods = member.getFavoriteFoods();
favoriteFoods.remove("치킨");
favoriteFoods.add("뿌링클");

// 3.
List<Address> addressHistory = member.getAddressHistory();
addressHistory.remove(new Address("old city1", "street1", "10001"));
addressHistory.add(new Address("city", "street", "12345"));
```

1.임베디드 값 타입 수정
  * address는 MEMBER 테이블과 매핑했기 때문에 MEMBER 테이블만 UPDATE

2. 기본 값 타입 수정

  * String은 불변 객체이기 때문에 삭제하고 새로운 객체를 넣어야 한다.
  * 컬렉션의 값만 변경해도 JPA가 변경사항을 알고 UPDATE를 실행

3. 컬렉션 값 타입 수정

  * `equals()`와 `hashCode()`가 반드시 구현되어 있어야 한다.
  * 불변 객체이기 때문에 기존에 있던 주소를 삭제하고 새로운 주소를 등록

<br>

## 제약 사항

엔티티는 식별자가 있어 값 변경시에 저장된 원본 데이터를 쉽게 찾아서 변경이 가능하다. 하지만, 값 타입은 식별자가 없어 값을 변경하면 데이터베이스에 있는 원본 데이터를 찾기 어렵다.

컬렉션 값 타입의 값들은 별도의 테이블에 보관된다. 때문에 보관된 값이 변경되면 데이터베이스에 있는 원본을 찾기 어렵다.

<br>

JPA에서는 이러한 문제를 해결하기 위해 `컬렉션 값 타입에 변경 사항이 발생하면 엔티티와 연관된 모든 데이터를 삭제하고 현재 컬렉션에 있는 모든 값을 데이터베이스에 다시 저장`한다.

실무에서는 정말 단순한 경우가 아니라면 일대다 관계를 사용하는 것이 좋다! 일대다 관계를 위한 엔티티를 생성하고, 여기서 값타입을 사용하는 방법으로 해결할 수가 있다. 추가적으로 영속성 전이(cascade)와 고아 객체 제거(orphan remove)를 사용하면 값 타입과 유사하게 사용이 가능하다.

```java
@Entity
public class Member {
    ...
    @OneToMany(cascade = CascadeType.ALL, orphanRemoval = true)
    @JoinColumn(name = "MEMBER_ID")
    private List<Address> addressHistory = new ArrayList<>();
    ...
}
```

```java
@Entity
public class AddressEntity {
    @Id
    @GeneratedValue
    private Long id;
    
    @Embedded
    private Address address;
    ...
}
```


<br>
<br>
<br>

*** 

<br>

## Reference
>김영한, 『자바 ORM 표준 JPA 프로그래밍』
