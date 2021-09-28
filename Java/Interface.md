# 인터페이스
> 인터페이스(interface) : 메소드 묶음의 역할 정의 방법
> 프로토타입 메소드 : 내용이 없는 껍데기 메소드
> implements : 클래스에게 역할을 부여하는 것
> 인터페이스의 장점 : 인터페이스를 통한 업캐스팅 가능, 프로그램 설계의 명확성 증가

<br>

![image](https://user-images.githubusercontent.com/84886987/135173095-7cf98eab-1b7f-448d-b39a-1521bc019781.png)


## 예제: 인터페이스로 추상화(Sounding)

```java
import java.util.ArrayList;

public class InterfaceReview {

	public static void main(String[] args) {
		// 인터페이스의 하위 객체 생성 & 업캐스팅(부모 타입으로 해석)
		Sounding dog = new Dog();
		Sounding baby = new Baby();
		Sounding tiger = new Tiger();
		Sounding robot = new Robot();
		
		// ArrayLIst를 통한 객체 저장
		ArrayList<Sounding> list = new ArrayList<Sounding>();
		list.add(dog);
		list.add(baby);
		list.add(tiger);
		list.add(robot);
		
		// 인터페이스 배열 생성
		//Sounding[] arr = { dog, baby, tiger, robot };
		
		// 소리내기
//		for (int i = 0; i < arr.length; i ++) {
//			arr[i].sound();
//		}
		
		for (int i = 0; i < list.size(); i ++) {
			list.get(i).sound();
		}
	} // end of main
} // end of InterfaceReview

interface Sounding {
	public void sound();
}

class Dog implements Sounding{
	public void sound() {					// 메소드 오버라이딩 (부모 메소드를 자식에서 재정의)
		System.out.println("Dog: 멍멍!");
	}
} // end of Dog

class Baby implements Sounding{
	public void sound() {					// 메소드 오버라이딩 (부모 메소드를 자식에서 재정의)
		System.out.println("Baby: 응애!");
	}
} // end of Baby

class Tiger implements Sounding{
	public void sound() {					// 메소드 오버라이딩 (부모 메소드를 자식에서 재정의)
		System.out.println("Tiger: 어흥!");
	}
} // end of Tiger

class Robot implements Sounding{
	public void sound() {					// 메소드 오버라이딩 (부모 메소드를 자식에서 재정의)
		System.out.println("Robot: 삐빕!");
	}
} // end of Robot
```
