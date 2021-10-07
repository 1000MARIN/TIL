# 스프링 개발환경 구축하기

*** 1. 시스템 환경변수 JAVA_HOME 을 JDK 경로로 설정


*** 2. 시스템 환경변수 path에 %JAVA_HOME%\bin 경로를 추가하고, 해당 경로를 가장 높은 우선순위로 제일 위에 두기


*** 3. STS(Spring Tool Suite) jar 설치파일을 다운로드 받기

  * https://spring.io/tools


*** 4. 다운받은 sts 설치파일을 설치할 폴더로 옮긴 후 해당 경로를 명령 프롬프트로 열기.


  ```
  java -jar spring-tool-suite-4-4.11.1.RELEASE-e4.20.0-win32.win32.x86_64.self-extracting.jar
  ```

  위 명령어 입력하여 설치하기


*** 5. Eclipse Marketplace에서 "Spring Tools 3 Add-On for Spring Tools 4" 플러그인을 설치 후 STS를 재시작


*** 6. 롬복 플러그인 설치

  * https://projectlombok.org/

  ```
  java -jar lombok.jar
  ```

*** 7. Eclipse Marketplace에서 "Web Developer Tools" 로 검색하여 플러그인 2개를 각각 설치 후 STS를 재시작
