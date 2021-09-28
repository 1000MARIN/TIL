# 클래스와 객체

![image](https://user-images.githubusercontent.com/84886987/135014205-e141fd66-8992-4edf-8802-e3bc36597844.png)

# 클래스 구현 및 객체 만들기

```java
public class CatTest {

	public static void main(String[] args) {
		// Cat 객체 생성
		Cat c = new Cat();
		
		// 객체의 필드 값을 변경하시오.
		c.name = "네로";
		c.breed = "페르시안";
		c.age = 3;
		c.weight = 5.12;
		
		// Cat 객체 필드 값 출력
		System.out.printf("이름: %s\n", c.name);
		System.out.printf("품종: %s\n", c.breed);
		System.out.printf("나이: %s\n", c.age);
		System.out.printf("무게: %skg\n", c.weight);
		
		c.claw();
		c.claw();
		c.claw();
		c.claw();
		
		c.meow();
		c.meow();
		c.meow();
		c.meow();
		
	} // end of main
}

class Cat {
	
	// 필드 영역
	String name;	// 이름
	String breed;	// 품종
	int age;		// 나이
	double weight; 	// 무게
	
	// 메소드 영역
	void claw() {	
		System.out.println("할퀴기!");
	}
	
	void meow() {	
		System.out.println("야 옹~~");
	}
} // end of Cat
```

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/63b5a583-5ff0-4d41-827d-838267f6c638/Cat.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/63b5a583-5ff0-4d41-827d-838267f6c638/Cat.png)

# 객체 생성

```java
public class BicycleTest {

	public static void main(String[] args) {
		// 자전거 객체 생성
		Bicycle b1 = new Bicycle();
		Bicycle b2 = new Bicycle();
		
		// 객체 필드값 초기화
		b1.name = "로드형 자전거";
		b1.weight = 7.25;
		b1.price = 326000;
		
		b2.name = "산악형 자전거";
		b2.weight = 8.32;
		b2.price = 296000;
		
		// 객체 정보 출력
		System.out.printf("b1->{%s, %.2f, %d}\n", b1.name, b1.weight, b1.price); // b1->{로드형 자전거, 7.25, 326000}
		System.out.printf("b2->{%s, %.2f, %d}\n", b2.name, b2.weight, b2.price); // b2->{산악형 자전거, 8.32, 296000}
	} // end of main

}

class Bicycle {
	// 필드
	String name;	// 이름
	double weight;	// 무게
	int price;		// 가격

	// 메소드
	void move() {
		System.out.println("자전거를 타고 이동합니다.");
	}
	void horn() {
		System.out.println("따르르릉! 지나갈게요~");
	}
}
```

# 인스턴스 메소드 호출

```java
public class CatTest {

	public static void main(String[] args) {
		// Cat 객체 생성
		Cat c1 = new Cat();
		Cat c2 = new Cat();
		
		// 객체의 필드 값을 변경하시오.
		c1.name = "네로";
		c1.breed = "페르시안";
		c1.age = 3;
		c1.weight = 5.12;
		
		// Cat 객체 필드 값 출력
		System.out.printf("이름: %s\n", c1.name);
		System.out.printf("품종: %s\n", c1.breed);
		System.out.printf("나이: %s\n", c1.age);
		System.out.printf("무게: %skg\n", c1.weight);
		
		// 메소드 호출
		c1.claw();
		c1.claw();		
		c1.meow();
		c1.meow();
		
		c2.claw();
		c2.claw();
		c2.meow();
		c2.meow();
		
	} // end of main
}

class Cat {
	
	// 필드 영역
	String name;	// 이름
	String breed;	// 품종
	int age;		// 나이
	double weight; 	// 무게
	
	// 메소드 영역
	void claw() {	
		System.out.println("할퀴기!");
	}
	
	void meow() {	
		System.out.println("야 옹~~");
	}
} // end of Cat
```

# 클래스 스코프

```java
public class CatTest {

	public static void main(String[] args) {
		// Cat 객체 생성
		Cat c1 = new Cat();
		Cat c2 = new Cat();
		
		// 객체의 필드 값을 변경하시오.
		c1.name = "네로";
		c2.name = "나비";
		
		// 메소드 호출
		c1.claw();
		c2.claw();
		
		c1.meow();
		c2.meow();
	} // end of main
}

class Cat {
	
	// 필드 영역
	String name;	// 이름
	String breed;	// 품종
	int age;		// 나이
	double weight; 	// 무게
	
	// 메소드 영역
	void claw() {	
		System.out.printf("[%s]할퀴기!\n", name);
	}
	
	void meow() {	
		System.out.printf("[%s]야 옹~~\n", name);
	}
} // end of Cat
```

# 메소드 스코프(scope)

- 클래스 스코프 : 필드
- 메소드 스코프 : 파라미터, 지역변수

```java
public class DrinkMachineTest {

	public static void main(String[] args) {
		// 객체생성
		DrinkMachine machine1 = new DrinkMachine();
		DrinkMachine machine2 = new DrinkMachine();
	
		// 음료 뽑기
		machine1.pushButton(1);
		machine2.pushButton(2);
		
		// 음료 확인
		machine1.printOutput();
		machine2.printOutput();
		// 사이다
		// 맥주
	
	} // end of main

}

class DrinkMachine {
	// 필드
	String output;
	
	// 메소드
	void pushButton(int num) {
		String[] drink = { "콜라", "사이다", "맥주" };
		output = drink[num];
	}
	
	void printOutput() {
		System.out.println(output);
	}
} // end of DrinkMachine
```

# 정사각형 객체의 넓이

```java
public class SquareTest {

	public static void main(String[] args) {
		// 1. 객체생성
		Square s = new Square();
		// 2. 필드 초기화 (값 변경)
		s.length = 4;
		// 3. 결과 출력
		System.out.printf("한 변의 길이가 %d인 정사각형의 넓이 : %d", s.length, s.area()); // 한 변의 길이가 4인 정사각형의 넓이 : 16
	} // end of main

}

// 4. 정사각형 클래스 구현
class Square {
	// 필드 - 한 변의 길이
	int length;
	
	// 메소드 - 정사각형의 넓이 반환
	int area() {
		return length * length;
	}

} // end of Square
```
