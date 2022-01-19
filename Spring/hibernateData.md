# hibernate, data.sql 실행시 오류 해결
>문제 발생   
>User엔티티와 Authority엔티티를 정의하고, User, Authority에 구동시 데이터를 넣어주기 위해 resources 디렉토리 하위에 data.sql스크립트(Insert문 5개)를 추가했다.   
>이 상태로 서버를 구동하고 localhost:8080/h2-console을 치면 테이블이 생성되어있고 데이터들이 들어가야 되는데 Insert 에러가 뜨면서 서버가 구동되지 않는다.


## 프로젝트 환경  
> SpringBoot 2.5.5  
> h2 Database   
> JPA   

application.yml (H2, JPA 설정)

<br>

![image](https://media.vlpt.us/images/kero1004/post/284d2c7f-6f72-4fc9-b5e2-010a47c94706/image.png)

<br>

![image](https://images.velog.io/images/kero1004/post/5e8173e4-6e5d-4d18-8912-47efbc59b980/image.png)

<br>

### 해결 방법  
>Hibernate and data.sql  
>If you want to use data.sql to populate a schema created by Hibernate, set spring.jpa.defer-datasource-initialization to true.  

<br>

2.5 릴리즈노트 를 살펴보니 이런 내용이 적혀있다.  
"Hibernate에 의해 생성된 스키마에 데이터를 채우기를 위해서 data.sql를 사용하고 싶으면 spring.jpa.defer-datasource-initialization를 true로 세팅해주세요" 

그래서 defer-datasource-initialization: true 한줄을 추가하고 서버를 구동하니 잘 돌아간다.

<br>

![image](https://media.vlpt.us/images/kero1004/post/9d0aa588-317c-4ac2-8252-ffb379667580/image.png)



