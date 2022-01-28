# EntityManagerFactory & EntityManager

<br>

## EntityManagerFactory
>말 그대로의 Entity Manger를 만드는 공장
>데이터베이스를 하나만 사용한다면 한개의 EntityManagerFactory를 생성
>스레드에 안전하기 때문에 서로 다른 스레드간의 공유를 해도 문제가 없고 생성하는데의 비용이 크기 때문에 Application 로딩 시점에 생성해 공유하도록 설계

<br>

```java
<!-- persistence.xml -->
<persistence-unit name="mydatabase">
	...
</persistence-unit>
```

```java
EntityManagerFactory emf = Persistence.createEntityManagerFactory("mydatabase"); // EntityManagerFactory 생성

emf.close(); // EntityManagerFactory 종료
```

<br>

## EntityManager
>EntityManagerFactory는 고객의 요청이 들어올 때(스레드가 하나 생성될 때)마다 새로운 EntityManager를 생성
>EntityManager는 스레드가 동시에 접근하면 동시성 문제가 발생하기 때문에 공유하면 안되기 때문
>EntityManager는 데이터 베이스의 연결이 필요한 시점까지 커넥션을 얻지 않다가 트랜잭션을 시작할 때 커넥션풀에서 커넥션을 획득
>트랜잭션의 수행이 완료되면 반드시 재사용이 불가능하도록 EntityManager를 닫아야하고, 내부적으로 DB Connection의 반환 됨

<br>

```java
EntityManager em = emf.createEntityManager(); // EntityManager 생성

em.persist(member); // 저장
member.setName("name"); // 수정
em.remove(member); // 삭제
em.find(Member.class, id); // 조회
em.close(); // EntityManager 종료
```

<br>

## EntityTransaction
>JPA를 사용하면 항상 트랜잭션 안에서만 데이터를 변경해야 하고 트랜잭션 없이 변경하면 예외가 발생
>트랜잭션은 EntityManger에서 받아와 사용

<br>

```java
EntityTranscation tx = em.getTransaction(); // 트랜잭션 얻기

try {
    tx.begin(); // 트랜잭션 시작
    
    ////////////
    // 비즈니스 로직
    ///////////
    
    tx.commit(); // 트랜잭션 커밋
    
} catch (Exception e){
    tx.rollback(); // 예외 발생으로 인한 트랜잭션 롤백
}
```

<br>

## 영속성 컨텍스트(persistence context)
>`Entity를 영구적으로 저장하는 환경`
>JPA에서 가장 중요한 용어이고 논리적인 개념.
>영속성 컨텍스는 EntityManager를 생성할 때 함께 만들어지고 EntityManager를 통해 접근하고 관리

<br>

### 특징

  * 영속성 컨텍스트는 엔티티를 식별자 값으로 구분하기 때문에 영속 상태의 엔티티는 반드시 식별자값이 존재해야하고 없다면 예외가 발생
  * 영속성 컨텍스트에 엔티티를 저장하면 트랜잭션을 커밋하는 순간 데이터베이스에 반영

<br>

#### 1차 개시

![image](https://user-images.githubusercontent.com/84886987/151465106-12b9ba2d-3486-487f-85a2-08564bc8debe.png)

- 영속성 컨텍스트는 내부에 Map형태로 된 1차 캐시를 가지고 있다.
- key : @Id로 선언한 필드, 데이터베이스의 기본키와 매핑
- value : 엔티티 인스턴스

<br>

```java
// 비영속
Member member = new Member();
member.setId("userId");

// 영속
em.persist(member);
```

1차 캐시에 저장되어 있지만 아직 DB에 저장하지 않은 상태

<br>

```java
em.find(Member.class, id); // T find(Class<T> entityClass, Object primaryKey)
```

`find()`를 호출

* 1차 캐시 존재
  - 1차 캐시에 있떤 엔티티를 찾아 반환
* 1차 캐시에 없음
  - 찾는 엔티티가 1차 캐시에 없다면 그 때 DB에서 조회를 하고 엔티티를 생성해 1차 캐시에 저장
  - 이후 영속 상태인 엔티티를 반환

<br>

>이렇게 되면 같은 엔티티를 조회하게 되면 1차 캐시에 있는 같은 엔티티 인스턴스를 반환하기 때문에 동일성을 보장하게 된다는 장점을 가지게 된다. 
>또한 반복 읽기(Repeatable Read) 등급의 트랜잭션 격리 수준을 애플리케이션에서 제공이 가능하게 된다.
 
<br>

#### 트랜잭션을 지원하는 쓰기 지연(transactional write-behind)
>EntityManager는 트랜잭션을 커밋하기 전까지 데이터베이스에 저장하지 않고 쿼리 저장소에 SQL을 모아두고 커밋할 때 모아둔 쿼리를 한번에 보내게 된다.

<br>

```java
// 트랜잭션 시작
EntityTransaction tx = em.getTransaction();
tx.begin();

// 1.
em.persist(memberA);

// 2.
tx.commit();
```

##### 1. `persist()`
  * 회원 엔티티를 1차 캐시에 저장
  * 동시에 쓰기 지연 SQL 저장소에 INSERT SQL을 만들어 저장

##### 2. `commit()`
  * EntityManger는 영속성 컨텍스트를 `flush()`
    - `flush()`❓1차 캐시에 있는 내용을 지우는 것이 아닌 쿼리를 DB에 날려 싱크를 맞추는 역할
    - 영속성 컨텍스트의 변경 내용을 DB에 동기화하는 작업. 쓰기 지연 SQL 저장소에 모인 쿼리를 DB에 보낸다
  * 변경 내용을 동기화한 후 실제 DB 트랜잭션을 커밋

<br>

#### 변경 감지(Dirty Checking)
>엔티티의 변경사항을 데이터베이스에 자동으로 반영하는 기능을 가지고 있기 때문에 JPA로 엔티티를 수정한다면 엔티티를 조회해서 변경하면 된다.

* `em.update()`같은 메소드는 없다!

엔티티를 영속성 컨텍스트에 보관할 때 최초 상태를 복사해서 스냅샷으로 저장해둔다.

<br>

* 변경 감지 흐름

1. 트랜잭션 커밋시 EntityManager 내부에서 `flush()`가 호출
2. 엔티티와 스냅샷을 비교하고 변경된 엔티티를 찾음
3. 변경된 엔티티가 존재하면 수정 쿼리를 생성하고 쓰기 지연 SQL 저장소에 넣음
4. 쓰기 지연 SQL 저장소의 SQL을 DB에 보내고 트랜잭션을 커밋

<br>

참고)
* JPA의 기본 전략은 수정된 필드만이 아닌 모든 필드를 업데이트한다.
* 모든 필드를 수정하면 전송량이 증가한다.
* `@DynamicUpdate`를 사용하면 데이터를 저장할 때 수정된 데이터만 사용해 동적인 UPDATE SQL을 생성할 수 있다.

<br>

#### 삭제

* `em.remove()`를 사용하면 대상 엔티티를 삭제하지만 즉시 삭제하는 것이 아닌 삭제 쿼리를 쓰기 지연 SQL 저장소에 저장하고 커밋을 호출할 때 DB에 삭제 쿼리를 전달한다.
* 이렇게 삭제된 쿼리는 자연스럽게 가비지 컬렉터의 대상이 된다.

<br>
<br>
<br>

***

<br>

## Reference
>김영한, 『자바 ORM 표준 JPA 프로그래밍』

