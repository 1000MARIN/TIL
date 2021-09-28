# reference 와 static

## 1. 레퍼런스란?

![image](https://user-images.githubusercontent.com/84886987/135015254-9ef60aef-c45a-482f-9b01-d3430ca44875.png)

<br>

## 2. 레퍼런스 변수 , 기본 변수

![image](https://user-images.githubusercontent.com/84886987/135015263-c63426dd-5e74-462c-95a5-fa8276e37496.png)

<br>

## 1. static 이란?

: 필드 & 메소드에 적용 가능한 공유의 키워드

![image](https://user-images.githubusercontent.com/84886987/135015471-716176fc-7d3a-4b41-8476-52436f9da1d2.png)

<br>

## 2. 클래스 변수

- 클래스 변수 : 객체 외부 클래스 영역에서 공유되는 변수
- 인스턴스 변수 : 객체 내부 변수

![image](https://user-images.githubusercontent.com/84886987/135015480-ea2bc1b8-fa4f-4fc9-89e5-f25e77bd47c0.png)

<br>

## 3. 클래스 메소드

- 클래스 매소드 : 클래스가 동작시키는 메소드
- 인스턴스 메소드 : 주체 객체가 동작하는 메소드

![image](https://user-images.githubusercontent.com/84886987/135015491-276a16fb-4ce9-412f-afce-71913fc4da95.png)

<br>

## 4. 예제 (두 점 사이의 거리)

```java
public class PointTest {

	public static void main(String[] args) {
		// 두점 사이의 거리
		
		// 객체 생성
		Point p1 = new Point(0, 0);				// 생성자 호출 및 초기화
		Point p2 = new Point(3, 4);				// 생성자 호출 및 초기화
		
		// 거리 계산
		double dist = Point.distance(p1, p2); 	// 클래스 메소드 호출 (주체 객체 없이도 호출 가능)
	
		// 결과 출력
		System.out.printf("두 점 A%s, B%s 사이의 거리: %.2f", p1.toStr(), p2.toStr(), dist); 
		// 두 점 A(0, 0), B(3, 4) 사이의 거리: 5.00
	
	} // end of main
} // end of PointTest

class Point {									// 생성자 정의
	// 1. 필드를 만드시오
	int x;										// 인스턴스 변수
	int y;										// 인스턴스 변수
	
	// 2. 생성자를 정의하시요.
	Point (int _x, int _y) {
		x = _x;
		y = _y;
	}
	
	// 3. 객체 정보를 문자열로 반환하는 인스턴스 메소드를 만드시오.
	String toStr() {							//인스턴스 메소드
		return String.format("(%d, %d)", x, y);
	}
	
	// 4. 두 점 사이의 거리를 반환하는 클래스 메소드를 만드시오.
	static double distance(Point p, Point q) { 
		double dX = p.x - q.x;					// x좌표의 변화량
		double dY = p.y - q.y;					// y좌표의 변화량
		return Math.sqrt((dX * dX) + (dY * dY));// Math.sqrt는 루트 메소드
	}
} // end of Point
```
