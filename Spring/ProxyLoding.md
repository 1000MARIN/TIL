# 프록시
>엔티티를 조회하고 항상 연관된 엔티티가 사용되는 것은 아니다. 회원을 조회했다고 해도 회원이 가입한 팀을 사용하지 않을 수도 있다. 
>때문에 회원을 조회할 때 항상 팀 엔티티를 함께 조회하는 것은 효율적이지 않다.
>JPA는 엔티티가 실제로 사용되기 전까지 데이터베이스 조회를 지연할 수 있도록 제공하는데 이를 __**지연 로딩**__이라 한다. 
>실제 사용하는 시점에 데이터베이스에서 필요한 데이터를 가져오는 것이다.
>하지만 지연 로딩을 사용하면 실제 엔티티 객체 대신 가짜 객체가 필요한데 이것이 __**프록시 객체**__이다.

<br>

## 프록시 객체

JPA에서는 식별자로 엔티티를 조회할 때 `EntityManager.find()`를 사용하는데 이 메소드는 영속성 컨텍스트에 엔티티가 없으면 데이터베이스를 조회한다. 이렇게 조회하면 사용하지 않더라도 데이터베이스를 조회하는데 만약 실제 사용 시점까지 미루고 싶다면 `EntityManager.getReference()`를 사용할 수 있다.

<br>

이 메소드는 데이터베이스 접근을 위임한 프록시 객체를 반환하는데, 프록시 클래스는 실제 클래스를 상속받아 만들어지므로 실제 클래스와 모양이 동일하다. 따라서 사용자는 프록시 객체인지 구분하지 않고 그대로 사용하면 된다. 프록시 객체는 실 객체에 대한 참조(target)을 보관하기 때문에 **프록시 객체의 메소드를 호출하면 실제 객체의 메소드를 호출**하게 된다.

<br>

프록시 객체에 메소드를 호출했을 때 실제 엔티티가 없다면 영속성 컨텍스트에 실제 엔티티 생성을 요청(초기화)한다. 영속성 컨텍스트는 데이터베이스를 조회해 실제 엔티티 객체를 생성한다. 실제 엔티티에 대한 참조를 target 변수에 저장하고 실제 엔티티의 메소드를 호출해 결과를 반환한다.

<br>

프록시 객체를 초기화하더라도 실제 엔티티로 바뀌지 않고 프록시 객체를 통해 접근한다. 만약 영속성 컨텍스트에 객체가 존재하면 `EntityManager.getReference()`를 호출해도 실제 엔티티를 반환하게 된다. 초기화에 영속성 컨텍스트가 반드시 필요하기 때문에 준영속 상태의 객체를 초기화 하면 예외(`LazyInitializationException`) 발생

<br>

## 프록시와 식별자

엔티티는 조회할 때 식별자를 파라미터로 전달하게 되는데 프록시는 이 값을 보관한다.

만약 엔티티 접근방식이 `@Access(AccessType.PROPERTY)`라면 식별자 값을 조회하는 메소드를 사용해도 초기화하지 않고, `@Access(AccessType.FIELD)`라면 초기화한다.

<br>

## 프록시 확인

`PersistenceUnitUtil.isLoaded(Object entity)`를 사용하면 초기화 여부를 확인할 수 있다. 초기화 되었거나 프록시 인스턴스가 아니라면 `true`를 반환하고, 초기화 되지 않은 프록시 인스턴스는 `false`를 반환한다.

<br> 

만약 프록시 객체인지 확인하고 싶다면, `getClass().getName()`을 호출했을 때 클래스 명 뒤에 `javassist`가 붙어있다면 프록시 객체이다.

<br>
<br>

# 즉시 로딩, 지연로딩

## 즉시 로딩(EAGER LODING)
>엔티티를 조회할 때 연관된 엔티티를 함께 조회한다. 즉시 로딩을 사용하고 싶다면 연관 관계 매핑의 fetch 속성을 `FetchType.EAGER`로 지정하면 된다.

```java
public class Member {
    ...
    @ManyToOne(fetch = FetchType.EAGER)
    @JoinColumn(name = "TEAM_ID")    
    private Team team;
}
```

```sql
SELECT 
	...
FROM 
	MEMBER M LEFT OUTER JOIN TEAM T
		ON M.TEAM_ID=T.TEAM_ID
WHERE
	M.MEMBER_ID="id"
```

하이버네이트는 즉시 로딩을 최적하하기 위해 가능하면 조인 쿼리를 통해 연관 엔티티를 한 번에 조회한다.

이 때, 실행되는 SQL은 내부 조인(INNER JOIN)이 아닌 외부 조인(LEFT OUTER JOIN)을 사용한다. 회원은 팀이 없을 수 있어 NULL값을 허용하기 때문에 외부 조인을 해야한다.

 

하지만 성능 최적화에서는 내부 조인이 유리하기 때문에 `@JoinColumn(nullable = false)`를 사용하면 내부 조인을 사용한다.

<br>

## 지연 로딩(LAZY LOADING)
>연관된 엔티티를 실제로 사용할 때 조회한다. 연관 관계 매핑의 fetch 속성을 `FetchType.LAZY`로 지정하면 사용할 수 있다.

```java
@Entity
public class Member {
    ...
    @ManyToOne(fetch = FetchType.LAZY)
    @JoinColumn(name = "TEAM_ID")    
    private Team team;
}
```

회원을 조회하면 바로 팀을 조회하지 않고, team 멤버 변수에 프록시 객체를 넣어둔다. 실제 데이터가 필요한 순간에서야 데이터베이스를 조회해 프록시 객체를 초기화한다. 만약 영속성 컨텍스트에 객체가 이미 존재한다면 프록시 객체가 아닌 실제 객체를 사용한다.

<br>

필요할 때마다 SQL을 실행해 연관된 엔티티를 데이터베이스에 접근해 가져오는 것이 항상 좋은 것은 아니다. 만약 팀과 회원을 항상 함께 사용한다면 처음부터 한 번에 가져오는 것이 효율적이다. 상황에 맞게 선택하는 것이 좋다.

<br>
<br>

### 컬렉션 래퍼
```java
@Entity
public class Member {
    ...
    @OneToMany(fetch = FetchType.LAZY, mappedBy = "member")
    private List<Order> orders;
}
```

<br>

만약 엔티티에 컬렉션이 있다면 컬렉션을 관리할 목적으로 하이버네이트의 내장 컬렉션으로 변경하는데 이를 컬렉션 래퍼라고 한다.
```java
Member member = em.find(Member.class, "id1");
System.out.println(member.getOrders().getClass().getName()); // org.hibernate.collection.internal.PersistentBag
```

컬렉션은 컬렉션 래퍼가 지연 로딩을 처리해주는데 컬렉션 래퍼도 컬렉션에 대한 프록시 역할을 수행한다. `member.getOrders()`를 호출한다고 해서 초기화가 되지 않고 컬렉션에서 데이터를 조회(`member.getOrders().get(0)`)할 때 초기화한다.

<br>

## JPA 기본 전략

* `@ManyToOne`, `@OneToOne` : 즉시 로딩
* `@OneToMany`, `@ManyToMany` : 지연 로딩

모든 연관 관계에 지연 로딩을 사용하는 것을 추천한다. 이후, 완성 단계에서 반드시 즉시 로딩이 필요한 경우에만 사용하는 것이 최적화하는데 유리하다.

### 즉시 로딩 주의점
* `@ManyToOne`, `@OneToOne`

  - optional = false : 내부 조인
  - optional = true : 외부 조인

* `@OneToMany`, `@ManyToMany`

  - optional = false : 외부 조인
  - optional = true : 외부 조인

컬렉션 하나 이상을 즉시 로딩을 권장하지 않는다. 컬렉션과 조인은 일대다 조인이므로 두 테이블의 엔티티 수의 곱만큼 SQL이 실행되게 되어 성능의 저하가 심각하게 발생하게 된다.

 <br>

컬렉션 즉시 로딩은 NULL이 존재할 수 있기 때문에 항상 외부 조인을 사용하는데, 외래키에 not null 제약 조건을 사용하면 변경이 가능하다.

일대다 조인은 항상 외부 조인인데, 만약 팀에 회원이 한 명도 존재하지 않는다면 해당 팀은 조회하지 않게 되기 때문에 항상 외부 조인을 사용해야 한다.

<br>
<br>
<br>

***

<br>

## Reference
>김영한, 『자바 ORM 표준 JPA 프로그래밍』
