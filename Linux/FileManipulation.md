# 파일 조작하기 (**File Manipulation**)

## **디렉토리 만들기**

> **mkdir [options] <Directory>**

```
$ pwd
/home/drv98
$ ls
$ mkdir work
$ ls
```

mkdir /home/drv98/dir1

mkdir ./dir2

mkdir ../dir3

mkdir ~/work/dir4

> 옵션 -p : 필요하면 상위(부모) 디렉토리도 만들기
옵션-v : 어떤 작업을 했는지 설명
> 

$ mkdir -p work/dir_parent/dir_child

$ mkdir -pv work/dir12/dir34

## **빈 파일 만들기**

> **touch [options] <filename>**
> 

$ touch example1 

$ ls
example1

## **파일 / 빈 폴더 삭제하기**

> **rm [options] <file>**
> 

$ rm new_folder 

$ ls

> 명령어 rm 의 옵션으로 '-r' 은 recursive 즉, 재귀적으로 폴더내 폴더까지 삭제
(비어있지 않은 폴더는 -r 옵션없이 삭제불가)
'-f' 은 강제적으로 (permission 없이) 삭제
> 

$ rm -rf /home/drv98/work/dir1

## **절대 사용하지 말것**

$ rm -rf /* 
$ rm -rf /

## **파일 / 폴더 카피하기**

> **cp [options] <source> <destination>**
> 

$ cp source_file dest_file

$ cp hello.txt hello.txt.old

$ cp  *  /home/drv98/download/backup/

> cp -r (recursive) : 폴더 안에 파일이 들어 있을때 폴더 전체 복사
> 

$ cp foo foo2
cp: omitting directory 'foo'
$ cp -r foo foo2
$ ls
foo foo2

## **파일 / 폴더 이동하기**

> mv [options] <source> <destination>
> 

$ ls
barney example1 foo foo2
$ mkdir backups
$ mv foo2 backups/foo3
$ mv barney backups/
$ ls
backups example1 foo

backups 폴더 새로 만들기

foo2 를 backups 폴더내의  foo3 이름으로 이동

barney 파일을  backups 로 그대로 이동

## **파일 / 폴더 이름 바꾸기**

$ ls
backups example1 foo
mv foo foo3
$ ls
backups example1 foo3

$ mkdir work/testdir
$ mv work/testdir /home/drv98/work/fred
