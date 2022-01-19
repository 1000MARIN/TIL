# hibernate, data.sql 실행시 오류 해결  
## 프로젝트 환경  
> SpringBoot 2.5.5  
> h2 Database   
> JPA   

application.yml (H2, JPA 설정)



상황발생
User엔티티와 Authority엔티티를 정의하고, User, Authority에 구동시 데이터를 넣어주기 위해 resources 디렉토리 하위에 data.sql스크립트(Insert문 5개)를 추가했다.
이 상태로 서버를 구동하고 localhost:8080/h2-console을 치면 테이블이 생성되어있고 데이터들이 들어가있어야 정상인데... Insert 에러가 뜨면서 서버가 구동되지 않는다.


참고하는 프로젝트는 2.4, 보면서 실습하려고 내가 생성한 프로젝트는 2.5.5
음...버전업되면서 달라졌나?! 🤔


🔎 해결 방법
사실 릴리즈 노트나 공홈을 거의(아예) 보지 않는데 요즘 무료로 해주는 강의들을 보면서 "아 이렇게 살면 망하는구나"를 느껴서 그런지 아무것도 모르지만 일단 뒤적뒤적 해보려고 노력중이다..

2.5 릴리즈노트 를 살펴보니 이런 내용이 적혀있다.
"Hibernate에 의해 생성된 스키마에 데이터를 채우기를 위해서 data.sql를 사용하고 싶으면 spring.jpa.defer-datasource-initialization를 true로 세팅해"

Hibernate and data.sql
If you want to use data.sql to populate a schema created by Hibernate, set spring.jpa.defer-datasource-initialization to true.

그래서 defer-datasource-initialization: true 한줄을 추가하고 서버를 구동하니 잘 돌아간다.






ps. JPA가 처음이라 h2를 먼저 실행시켜야 되는줄 알았는데 h2는 따로 먼저 실행 안 시켜도된다. 프로젝트만 실행시키고 브라우저에 localhost:8080/h2-console로 접속하면 된다. 😯
