# 영속성 전이(transitive persistence)
>특정 엔티티를 영속 상태로 만들 때, 영관된 엔티티도 함께 영속 상태로 만드는 것이다.
>`CASCADE` 옵션을 사용하면 부모 엔티티를 저장할 때, 자식 엔티티도 함께 저장이 가능하다.

<br>

엔티티를 저장할 때에는 연관된 모든 엔티티가 영속상태여야하기 때문에 부모 엔티티를 저장하려면 부모 엔티티와 연관된 자식 엔티티 각각 영속 상태로 만들어야 한다.

```java
@Entity
public class Parent {
    ...
	@OneToMany(mappedBy = "parent")
	private List<Child> children = new ArrayList<Child>();
}
```

```java
@Entity
public class Child {
    ...
    @ManyToOne
    private Parent parent;
}
```

```java
Parent parent = new Parent();
em.persist(parent); // 부모 저장

Child child = new Child();
child.setParent(parent);
parent.getChildren().add(child);
em.persist(child); // 자식 저장
```

<br>

하지만, `CASCADE`옵션을 사용하면 연관된 엔티티도 함께 영속 상태로 만들어준다.

```java
@Entity
public class Parent {
    ...
	@OneToMany(mappedBy = "parent", cascade = CascadeType.PERSIST)
	private List<Child> children = new ArrayList<Child>();
}
```

```java
Parent parent = new Parent();
Child child = new Child();
child.setParent(parent);
parent.getChildren().add(child);

em.persist(parent);
```

CascadeType.PERSIST를 지정하면 부모 엔티티를 영속화할 때 연관된 자식 엔티티도 함께 영속화된다.

<br>

만약 삭제시 연관된 엔티티를 함께 삭제하고 싶다면 CascadeType.REMOVE로 지정하면 부모 엔티티가 삭제될 때 함께 삭제된다.

<br>

## 종류

* ALL : 모두 적용
* PERSIST : 영속
* MERGE : 병합
* REMOVE : 삭제
* REFRESH
* DETACH

`cascade = {CascadeType.PERSIST, CascadeType.REMOVE}`로 한 번에 여러 속성을 지정할 수 있다. PERSIST와 REMOVE는 `em.persist()`, `em.remove()`를 실행할 때 바로 전이되는 것이 아닌 플러시가 호출될 때 전이된다.


<br>

# 고아 객체(ORPHAN)
>JPA에서 부모와 연관 관계가 끊어진 자식 엔티티를 자동으로 삭제하는 `고아 객체 제거` 기능을 제공한다.

<br>

```java
@Entity
public class Parent {
    ...
	@OneToMany(mappedBy = "parent", orphanRemoval = true)
	private List<Child> children = new ArrayList<Child>();
}
```

```java
Parent parent = em.find(Member.class, id);
parent.getChildren().remove(0); // 자식 참조 제거
```
 
 컬렉션에서 자식 엔티티를 제거하면 데이터베이스의 데이터도 함께 삭제된다. 바로 실행되지 않고 플러시할 때 적용되면 DELETE SQL이 실행되게 된다.
 
 ```sql
 DELETE FROM CHILD WHERE ID=?
 ```
 
참조가 제거된 엔티티는 다른 곳에서 참조하지 않는 고아 객체로 보고 삭제한다. 단, 참조하는 객체가 여러개라면 문제가 발생할 수 있기 때문에 `@OneToOne`, `@OneToMany`에만 사용이 가능하다.

<br> 

만약 부모가 제거되면 자식은 고아가 되기 때문에 자식도 함께 제거되는데, casecase에 REMOVE를 설정한 것과 동일하다.


<br>
<br>
<br>

***

<br>

## Reference
>김영한, 『자바 ORM 표준 JPA 프로그래밍』

 
