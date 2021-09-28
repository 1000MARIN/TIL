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
### **폴더 삭제하기**
```
rm /home/drv98/new_folder 
```
the *rm* (remove) 명령어

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

## **폴더와 폴더내 하위폴더등 모든 파일 삭제**

The command you are about to read can potentially (if used incorrectly) **destroy** your system!
```
rm -rf /home/drv98/useless_Parent_folder
```
- 명령어 rm 의 옵션으로 '-r' 은  recursive 즉, 재귀적으로 폴더내 폴더까지 삭제 (비어있지 않은 폴더는 -r 옵션없이 삭제불가)

- '-f' 은 강제적으로 (permission 없이)  삭제
```
rm -rf /* 

rm -rf /
```
- **절대 사용하지 말것**

## **root 권한으로 명령어 실행**
```
apt-get install git
```
명령어 앞에 sudo
```
sudo apt-get install git
```
**

## **Backing up your files(파일 백업)**

To create a backup of a file, we're going to use the *cp* (copy) command. The basic syntax for *cp* is as follows:
```
cp source_file dest_file
```
```
cp hello.txt hello.txt.old
```
```
cp *  /home/drv98/download/backup/
```
## **폴더 복사**

*cp* *-r* (recursive)
```
cp -r /directory/  where/to/copy/to/
```
## **Checking system performance**

현재 cpu 사용률 등 프로세스 사용 상황을 알고 싶을때:
```
top
```
## **Check Devices (장치 관리)**

USB Devices:

현재 USB 장치가 동작하는지 연결/해제 되었는지 체크:
```
lsusb
```
PCI Devices:

As PCI devices are checked with:
```
lspci
```
## **네트워크 정보 보기**
```
ip addr
```
## **와이파이 정보 보기**
```
iwconfig
```
## **본인 계정의 홈위치 /home/아이디 이동**
```
**cd ~**
```
