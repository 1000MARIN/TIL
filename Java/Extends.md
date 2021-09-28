# 상
> 상속(extends) : 기존 클래스를 확장하는 것   
> class A extends b{ } : A클래스는 B를 상속(또는 확장)   
> 상속의 장점 : 프로그램 확장성을 증가, 코드 중복을 줄임   


![image](https://user-images.githubusercontent.com/84886987/135016162-952430e9-5953-4d39-89b4-763716f596a8.png)

<br>

![image](https://user-images.githubusercontent.com/84886987/135016168-ecf596f7-f5d8-4625-be85-5f4d92c859fc.png)

```java
class Cal{
	public int sum(int v1, int v2) {
		return v1 + v2;
	}
	// Overloading 
	// : 상속과는 관계 없이 동일 Class 내에 동일한 Method 이름으로 
	// parameter 등을 추가하여 사용하는 것이다.
	public int sum(int v1, int v2, int v3) {
		return this.sum(v1, v2) + v3; // this : 자기 Class의 것
	}
	
}

//상속(Interitance): 부모 클래스의 메소드 및 필드를 가져옴으로써 코드 중복을 줄일 수 있는 장점	
class Cal3 extends Cal{ 
	// 기능추가
	public int minus(int v1, int v2) {
		return v1 - v2;
	}
	// Overriding Parent Class와 Child Class 내 동일한 Method가 있을 경우 
	//상속받은 Parent Class 에 있는 Method 는 실행이 안되고 
	//자신의 Class에 있는 method 가 실행되는 것
	public int sum(int v1, int v2) {
		System.out.println("Cal3!!");
		return super.sum(v1, v2); // super : 자기 부모 Class의 것
	}
	
}
public class InheritanceApp {
	public static void main(String[] args) {
		Cal c = new Cal();
		System.out.println(c.sum(2, 1));
		System.out.println(c.sum(2, 1, 1));
		
		Cal3 c3 = new Cal3();
		System.out.println(c3.sum(2, 1));
		System.out.println(c3.minus(2, 1));
		System.out.println(c3.sum(2, 1));
		
	}

}
```

<br>

## 예제 (엘프 - 하이엘프 - 엘프로드)

![image](https://user-images.githubusercontent.com/84886987/135016178-c6d8315d-1123-4697-9d38-e5b484438e4b.png)

![image](https://user-images.githubusercontent.com/84886987/135016189-da4fba99-c5ae-40f4-bb4f-ef709325afb3.png)

<br>

```java
import java.util.ArrayList;

public class ElvesTest {

	public static void main(String[] args) {
		// 엘프의 진화
		
		// 엘프 객체 생성 & 업캐스팅(부모 타입으로 해석)
		Elf a = new Elf("티란테", 100);
		Elf b = new HighElf("말퓨리온", 160, 100);
		Elf c = new ElfLord("마이에브", 230, 140, 100);
		
		// 객체 배열 생성
		//Elf[] elves = { a, b, c };
		ArrayList<Elf> list = new ArrayList<Elf>();	// Elf를 담기위한 ArrayList 생성
		list.add(a);
		list.add(b);
		list.add(c);
		
		// 반복을 이용한 출력
//		for (int i = 0; i < elves.length; i++) {
//			System.out.println(elves[i].toString());
//		}
		for (int i = 0; i < list.size(); i++) {
			System.out.println(list.get(i).toString());
		}
	} // end of main
} // end of ElvesTest

class Elf {
	protected String name;
	protected int hp;
	
	public Elf(String name, int hp) {
		this.name = name;
		this.hp = hp;
	}
	
	public String toString() {
		return String.format("[엘프] Name: %s, HP: %d", this.name, this.hp);
	}
} // end of Elf

class HighElf extends Elf {
	// name, hp 를 상속 받음
	protected int mp;
	
	public HighElf(String name, int hp, int mp) {
		super(name, hp); // 부모 클래스 생성자 호출
		this.mp = mp;
	}
	
	// 메소드 오버라이딩 (재정의)
	public String toString() {
		return String.format("[하이엘프] Name: %s, HP: %d, MP: %d", super.name, super.hp, this.mp);
	}
} // end of HighElf

class ElfLord extends HighElf {
	// name, hp, mp 를 상속 받음
	protected int shield;
	
	public ElfLord(String name, int hp, int mp, int shield) {
		super(name, hp, mp); // 부모 생성자 호출
		this.shield = shield;
	}
	
	// 메소드 오버라이딩 (재정의)
	public String toString() {
		return String.format("[엘프로드] Name: %s, HP: %d, MP: %d, SH: %d", name, hp, mp, shield);
	}
} // end of ElfLord
```

- protected : 상속 관계 접근 허용
- 메소드 오버라이딩 : 부모 메소드를 자식에서 재정의
