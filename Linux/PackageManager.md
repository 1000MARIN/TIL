# **Package manager**

**패키지 관리자**(package manager, 패키지 매니저), **패키지 관리 시스템**(package management system)은 컴퓨터의 운영 체제를 위해 일정한 방식으로 컴퓨터 프로그램의 설치, 업그레이드, 구성, 제거 과정을 자동화하는 소프트웨어 도구들의 모임이다.

=> **리눅스의 앱스토어**

****

****

## **apt 를 사용하여 패키지 관리하는 방법**

****

**apt-get update :** 패키지들의 **리스트**를 업데이트

jb@jb-W65-67SH:~/Work$ apt-get update

jb@jb-W65-67SH:~/Work$ sudo apt-get update

### 패키지 리스트 업데이트 이후

### **sudo apt-cache search <패키지>**

### **=> 패키지 리스트에서 htop 란 패키지가 있는지 check**

jb@jb-W65-67SH:~/Work$ sudo apt-cache search htop
htop - 대화형 프로세스 뷰어
aha - ANSI color to HTML converter
libauthen-oath-perl - Perl module for OATH One Time Passwords
pftools - build and search protein and DNA generalized profiles

jb@jb-W65-67SH:~/Work$ sudo apt-get install htop 

### **htop 으로 프로그램 실행**

![https://postfiles.pstatic.net/MjAxOTA4MDRfMjMy/MDAxNTY0OTIyMDU1MjAx.cpvbLI69ZeN5Dxw1AqcKKboTPcApzrnR32dVaQzoUPEg.smGAZ1BdrGZNQt0m17u8jLEXGBi4btlNGRsJcToBWOsg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA4MDRfMjMy/MDAxNTY0OTIyMDU1MjAx.cpvbLI69ZeN5Dxw1AqcKKboTPcApzrnR32dVaQzoUPEg.smGAZ1BdrGZNQt0m17u8jLEXGBi4btlNGRsJcToBWOsg.PNG.drv98/image.png?type=w773)

**q => 종료**

****

**sudo apt-get update : 최신 패키지 리스트 업데이트 
sudo apt-get install ( ) : 패키지 설치
sudo apt-get upgrade : 모든 패키지를 최신으로 업그레이드
sudo apt-get remove ( ) : 패키지 삭제**

****

****

## **APT 정리**

apt-get(Advanced Packaging Tool)은 우분투(Ubuntu)를 포함안 데비안(Debian)계열의 리눅스에서 쓰이는 패키지 관리 명령어 도구입니다. sudo는 superuser권한으로 실행하기 위함입니다.

**패키지 인덱스 정보를 업데이트 :** apt-get은 인덱스를 가지고 있는데 위치는 /etc/apt/sources.list에 있습니다.

이곳에 저장된 저장소에서 사용할 패키지의 정보를 얻습니다.

sudo apt-get update

**설치된 패키지 업그래이드 :** 설치되어 있는 패키지를 모두 새버전으로 업그래이드 합니다.

sudo apt-get upgrade

**패키지 설치**

sudo apt-get install 패키지이름

**패키지 재설치**

apt-get --reinstall install 패키지이름

**패키지 삭제** 

sudo apt-get remove 패키지이름

**패키지 검색** 

sudo apt-cache search 패키지이름
