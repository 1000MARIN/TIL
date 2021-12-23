# 래퍼 클래스(Wrapper class)
> 프로그램에 따라 기본 타입의 데이터를 객체로 취급해야 하는 경우  
> 기본 타입의 데이터를 먼저 객체로 변환한 후 작업을 수행 

이렇게 8개의 기본 타입에 해당하는 데이터를 객체로 포장해 주는 클래스를 래퍼 클래스(Wrapper class)라고 한다.  
래퍼 클래스는 각각의 타입에 해당하는 데이터를 인수로 전달받아, 해당 값을 가지는 객체로 만들어 준다.   
이러한 래퍼 클래스는 모두 java.lang 패키지에 포함되어 제공.   

|기본 타입|래퍼 클래스|
|--------|--------|
|byte|Byte|
|short|Short|
|int|Integer|
|long|Long|
|float|Float|
|double|Double|
|char|Character|
|boolean|Boolean|

<br>

## 박싱(Boxing)과 언박싱(UnBoxing)
> 래퍼 클래스(Wrapper class)는 산술 연산을 위해 정의된 클래스가 아니므로, 인스턴스에 저장된 값을 변경할 수 없다.   
> 단지, 값을 참조하기 위해 새로운 인스턴스를 생성하고, 생성된 인스턴스의 값만을 참조할 수 있다.   

![img_java_boxing_unboxing](https://user-images.githubusercontent.com/84886987/147170928-2f83860b-192a-4dcb-b531-493699fbe198.png)
