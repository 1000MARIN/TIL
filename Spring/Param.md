# [JPA]JPQL 에러   
>For queries with named parameters you need to use provide names for method parameters.  
>Use @Param for query method parameters, or when on Java 8+ use the javac flag -parameters.  

<br>

```java
@Query
    (
        "SELECT user " +
        "FROM FMSUser user " +
//        "   LEFT JOIN FETCH user.roles role " +
        "   JOIN FETCH user.company company " +
        "WHERE user.email = :email"
    )
    User fetchByEmailWithAuthorities(String email);
```

<br>

## 해결 방법
>@Param("email") String email 넣기   

<br>

```java
@Query
    (
        "SELECT user " +
        "FROM FMSUser user " +
//        "   LEFT JOIN FETCH user.roles role " +
        "   JOIN FETCH user.company company " +
        "WHERE user.email = :email"
    )
    User fetchByEmailWithAuthorities(@Param("email") String email);
```

<br>

