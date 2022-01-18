# [Tomcat 에러]Several ports (8005, 8080, 8009) required by Tomcat v9.0 Server at localhost are already in use.    
>Several ports (8005, 8080, 8009) required by Tomcat v9.0 Server at localhost are already in use. The server may already be running in another process, or a system process may be using the port. To start this server you will need to stop the other process or change the port number(s).   
>톰캣을 구동시켰을 때 생긴 포트 오류이다.     
>이클립스가 비정상적으로 종료가 된 후에 톰캣을 구동시켰을 때 발생했다.   

<br>

Tomcat이 사용하고 있는 기본 포트(8080, 8009, 8005)가 이미 사용중이라서 생기는 오류이다.

쓰고 있는 포트를 바꿔도 되고, 포트를 사용하고 있는 pid를 확인해서 삭제해주면 된다.

<br>

관리자권한으로 cmd창을 열어서 다음을 친다.

<br>

```cmd
netstat -p tcp -ano

C:\Windows\system32>netstat -p tcp -ano
 
활성 연결
 
  프로토콜  로컬 주소              외부 주소              상태            PID
  TCP    0.0.0.0:135            0.0.0.0:0              LISTENING       1028
  TCP    0.0.0.0:445            0.0.0.0:0              LISTENING       4
  TCP    0.0.0.0:3306           0.0.0.0:0              LISTENING       1076
  TCP    0.0.0.0:7680           0.0.0.0:0              LISTENING       5756
  TCP    0.0.0.0:8009           0.0.0.0:0              LISTENING       9184
  TCP    0.0.0.0:8080           0.0.0.0:0              LISTENING       9184
  TCP    0.0.0.0:33060          0.0.0.0:0              LISTENING       1076
  TCP    0.0.0.0:49664          0.0.0.0:0              LISTENING       672
  TCP    0.0.0.0:49665          0.0.0.0:0              LISTENING       1556
  TCP    0.0.0.0:49666          0.0.0.0:0              LISTENING       1144
  TCP    0.0.0.0:49671          0.0.0.0:0              LISTENING       3052
  TCP    0.0.0.0:49837          0.0.0.0:0              LISTENING       748
  TCP    0.0.0.0:49874          0.0.0.0:0              LISTENING       756
  TCP    0.0.0.0:53320          0.0.0.0:0              LISTENING       10524
  TCP    127.0.0.1:1235         0.0.0.0:0              LISTENING       4012
  TCP    127.0.0.1:8005         0.0.0.0:0              LISTENING       9184
  TCP    127.0.0.1:49675        127.0.0.1:49676        ESTABLISHED     3684
    ...                        ...                    ...                    ...

```

<br>

그러면 포트에 연결된 pid를 전부 볼 수 있다.

Tomcat이 사용하는 기본 포트는 0.0.0.0:8080, 0.0.0.0:8009와 127,0,0,1:8005이다.

10행, 11행 그리고 21행에서 찾을 수 있다. 포트를 사용중인 pid는 9184이다.

그럼 pid 9184를 삭제해주자.

<br>
```cmd
taskkill /f /pid 9184

C:\Windows\system32>taskkill /f /pid 9184
성공: 프로세스(PID 9184)가 종료되었습니다.
```

<br>

pid 프로세스가 종료되었다고 뜨면 된거다.

포트들을 다시 확인해보자.

<br>

```cmd
C:\Windows\system32>netstat -p tcp -ano

활성 연결
 
  프로토콜  로컬 주소              외부 주소              상태            PID
  TCP    0.0.0.0:135            0.0.0.0:0              LISTENING       1028
  TCP    0.0.0.0:445            0.0.0.0:0              LISTENING       4
  TCP    0.0.0.0:3306           0.0.0.0:0              LISTENING       1076
  TCP    0.0.0.0:7680           0.0.0.0:0              LISTENING       5756
  TCP    0.0.0.0:33060          0.0.0.0:0              LISTENING       1076
  TCP    0.0.0.0:49664          0.0.0.0:0              LISTENING       672
  TCP    0.0.0.0:49665          0.0.0.0:0              LISTENING       1556
  TCP    0.0.0.0:49666          0.0.0.0:0              LISTENING       1144
  TCP    0.0.0.0:49671          0.0.0.0:0              LISTENING       3052
  TCP    0.0.0.0:49837          0.0.0.0:0              LISTENING       748
  TCP    0.0.0.0:49874          0.0.0.0:0              LISTENING       756
  TCP    0.0.0.0:53320          0.0.0.0:0              LISTENING       10524
  TCP    127.0.0.1:1235         0.0.0.0:0              LISTENING       4012
  TCP    127.0.0.1:49675        127.0.0.1:49676        ESTABLISHED     3684
    ...                    ...                ....                        ...

```
<br>

8080, 8009, 8005 포트를 사용하는 프로세스는가 없는 것을 확인할 수 있다.

그럼 이제 Tomcat에서 8080, 8009, 8005 포트를 사용할 수 있게 되었다.

Tomcat을 구동하면 에러없이 사용할 수 있다.
