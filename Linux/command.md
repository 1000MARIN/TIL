# 기초명령어

##**셸(Shell) 개요**

리눅스는 GUI 환경도 있지만 GUI 환경이 제공되기 이전 터미널 환경을 이용하여 명령어를 직접 타이핑하여 컴퓨터를 운용하였다. 현재 많은 리눅스 GUI 버전이 생겼지만 아직도 터미널환경을 사용하는것이 GUI 처럼 직관적이지는 않지만 강력한 기능을 제공하기 때문에 여전히 많이 사용되고 있으며 이때 **터미널에 입력한 명령을 해석하고 관리하는 프로그램을 셸(shell)** 이라고 한다. 셸은 사용자 커널 사이에 연결시켜주는 역활을 하며 사용자가 입력한 명령을 해석하여 운영체제가 해당명령을 이해할 수 있게 해준다.

**— CLI ( Command-Line Interface ) : 텍스트 명령 줄 인터페이스**

셸의 종류
Bourne Shell              - sh    - 벨 연구소의 스티브본 (Stephen Bourne) 개발, 많은 셸 스크립트의 기반이 되는 셸   
C Shell                   - csh   - C언어 구문과 유사, Bourne Shell 을 확장하여 히스토리, 작업제어, 엘리어스 등 기능 추가 개발자들에게 유용한 기능들을 제공한다.   
TC Schell                 - tcsh  - C Shell 에 명령 행 완성 과 명령 행 편집 기능을 추가      
Korn Shell                - ksh   - Bourne Shell 가 호환되며 C Shell 의 많은 기능을 포함, Unix 계열에서 많이 사용된다.   
Bourne Again Shell (bash) - bash  - 리눅스에서 가장많이 사용되는 셸로 Bourne 셀을 토대로 C셸과 Korn Shell 의 기능들을 통합시켜 개발되었다.   
# ****

# **리눅스 기본 명령어**

****

리눅스 명령어는 결국 쉘이 제공하는 명령어

리눅스 기본 쉘이 bash 이므로, bash에서 제공하는 기본 명령어를 배우는 것 입니다.   

```
$ echo $SHELL   
/bin/bash   
```



### pwd : 현재 디렉토리 위치

```
$ pwd
/home/work
```

### ls : 파일 목록 출력

```
$ ls
```

### **ls [options] [location]**

```
$ ls
$ ls -l
$ ls /etc
$ ls -l /etc
```

### mkdir : 폴더 만들기

```
$ mkdir hello_linux
$ ls
hello_linux
```

### cd (chang directory) : 디렉토리 이동

**cd [location]**

```
$ cd /
$ ls
$ cd ~
$ cd ..
$ cd ~/hello_linux
```

cd 또는 cd ~ :  자기 자신의 홈디렉토리로 이동

cd / : 최상위 루트디렉토리(/)로 이동

cd ..  :  한 단계 상위디렉토리로 이동

cd - : 바로전에 위치했던 디렉토리로 이동

cd /etc/sysconfig : /etc/sysconfig 디렉토리로 이동

# **Summary**

### **pwd**

Print Working Directory : 현재 위치하는 디렉토리위치를 출력

### **ls**

List the contents of a directory. : 디렉토리의 내용을 리스트해서 출력

### **cd**

Change Directories : 다른 디렉토리로 위치이동
