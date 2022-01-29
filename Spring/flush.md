# flush
>플러시는 영속성 컨텍스트의 변경 내용을 DB에 반영하는 것
>플러시를 한다고 commit이 이루어지는 것이 아님

<br>

### 동작 과정
  1. 변경 감지를 동작해 영속성 컨텍스트의 모든 엔티티를 스냅샷과 비교해 수정된 엔티티를 찾음(Dirty Checking)
  2. 수정된 엔티티는 쿼리를 만들어 쿼리를 저장
  3. 저장된 쿼리를 DB에 전송

<br>

## 플러시 하는 방법

### 직접 호출

```java
em.flush();
```

영속성 컨텍스트를 강제로 플러시한다.

플러시를 하더라도 1차 캐시에 있는 내용은 지워지지 않고 저장된 쿼리만 DB에 전송하게 된다.

<br>

### 커밋시 자동 호출

* JPA가 트랜잭션을 커밋할 때 플러시를 자동으로 호출해 변경 내용을 반영하게 된다.

<br>

### JPQL 쿼리 실행시 자동 호출
```java
Member member = new Member();
em.persist(member);

query = em.createQuery("select m from Member m", Member.class);
List<Member> memberList = query.getResultList();
```
왜 JPQL을 실행할 때 자동으로 플러시를 실행할까?

<br>

* member를 새로 생성해 영속 상태로 만들었지만 데이터 베이스에 반영이 되지 않았기 때문에 JPQL을 실행하면 쿼리의 결과에 존재하지 않게 된다. 
* 때문에 쿼리를 실행하기 직접 플러시를 통해 변경된 내용을 반영해야만 쿼리가 제대로 동작이 가능
* 따라서, JPQL을 실행할 때 자동으로 플러시를 호출한다. 단, 식별자를 기준으로 조회하는 `find()`메소드를 호출하면 플러시가 실행되지 않는다.

<br>

## 모드 옵션
>EntityManager에 모드를 지정할 수 있다.

```java
em.setFlushMode(MODE);
```

* FlushModeType.AUTO : 커밋이나 쿼리를 실행할 때 플러시(default)
* FlushModeType.COMMIT : 커밋할 때에만 플러시. 성능을 최적화할 때 사용

<br>
<br>
<br>

***

<br>

## Reference
>김영한, 『자바 ORM 표준 JPA 프로그래밍』
