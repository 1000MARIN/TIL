# 오류의 종류

1. 에러 (Error)
    - 개발자가 해결할 수 없는 치명적인 오류
    - 하드웨어의 잘못된 동작 또는 고장으로 인한 오류
    - 에러가 발생되면 프로그램 종료
    - 정상 실행 상태로 돌아갈 수 없음
2. 예외 (Exception)
    - 개발자가 해결할 수 있는 오류
    - 사용자의 잘못된 조작 또는 개발자의 잘못된 코딩으로 인한 오류
    - 예외가 발생되면 프로그램 종료
    - 예외 처리 추가하면 정상 실행 상태로 돌아갈 수 있읃ㅁ
    - 예외가 발생하면 비정상적인 종료를 막고, 프로그램을 계속 진행할 수 있도록 우회 경로를 제공하는 것이 바람직

---

<br>

# 예외의 종류

1. 일반(컴파일 체크) 예외
    - 예외 처리를 하지 않으면 컴파일 오류가 발생하므로 꼭 처리해야하는 검사형 예외
2. 실행 예외 (RuntimeException)
    - 개발자의 실수로 발생할 수 있으며, 예외 처리를 하지 않아도 컴파일할 수 있는 비검사형 예외

![https://blog.kakaocdn.net/dn/wgy0r/btqKooDlR4P/fwK8aD90ZcbaRRlKr5FRJk/img.png](https://blog.kakaocdn.net/dn/wgy0r/btqKooDlR4P/fwK8aD90ZcbaRRlKr5FRJk/img.png)

### 실행 예외 (RuntimeException)

- 예외가 발생하면 JVM은 해당하는 실행 예외 객체를 생성
- 실행 예외는 컴파일러가 예외 처리 여부를 확인하지 않음. 따라서 개발자가 예외 처리 코드의 추가 여부를 결정

대표적인 실행 예외 예
- ArithmeticException : 0으로 나누기와 같은 부적절한 산술 연산을 수행할 때 발생
- IllegalArgumentException : 메서드에 부적절한 인수를 전달할 때 발생
- IndexOutOfBoundsException : 배열, 벡터 등에서 범위를 벗어난 인덱스를 사용할 때 발생한다.
- NoSuchElementException : 요구한 원소가 없을 때 발생한다.
- NullPointerException : null 값을 가진 참조 변수에 접근할 때 발생한다.
- NumberFormatException : 숫자로 바꿀 수 없는 문자열을 숫자로 변환하려 할 때 발생한다.


### 일반 예외

- 컴파일러는 발생할 가능성을 발견하면 컴파일 오류를 발생
- 개발자는 예외 처리 코드를 반드시 추가

대표적인 일반 예외 예
- ClassNotFoundException : 존재하지 않는 클래스를 사용하려고 할 때 발생한다.
- InterruptedException : 인터럽트 되었을 때 발생한다.
- NoSuchFieldException : 클래스가 명시한 필드를 포함하지 않을 때 발생한다.
- NoSuchMethodException : 클래스가 명시한 메서드를 포함하지 않을 때 발생한다.
- IOException : 데이터 읽기 같은 입출력 문제가 있을 때 발생한다.

---

<br>

## 예외 처리의 두가지 방법

### 1. 예외 잡아 처리하기

![https://blog.kakaocdn.net/dn/Pg84Y/btqKrLq2Gl8/03ktU6N98pjxY3b0eLprY1/img.png](https://blog.kakaocdn.net/dn/Pg84Y/btqKrLq2Gl8/03ktU6N98pjxY3b0eLprY1/img.png)

![https://blog.kakaocdn.net/dn/sWk91/btqKoqgQcPG/7vBYYWvdAoyQNXutu2U0Ak/img.png](https://blog.kakaocdn.net/dn/sWk91/btqKoqgQcPG/7vBYYWvdAoyQNXutu2U0Ak/img.png)

Throwable 클래스의 주요 메서드
- public String getMessage() : Throwable 객체의 자세한 메시지를 반환한다.
- public String toString() : Throwable 객체의 간단한 메시지를 반환한다.
- public void printStackTrace() : Throwable 객체와 추적 정보를 콘솔 뷰에 출력한다.

### 예시

![https://blog.kakaocdn.net/dn/JW4WW/btqKrJUjqZK/s6pk5HN7gHcRjf1MKMTggk/img.png](https://blog.kakaocdn.net/dn/JW4WW/btqKrJUjqZK/s6pk5HN7gHcRjf1MKMTggk/img.png)

### 특징

- 하나의 try 문에서 여러 개의 예외가 발생할 수 있지만 동시에 발생하지는 않음
- 하나의 예외가 발생하면 즉시 try 블록의 실행을 멈추고 해당 catch 블록으로 이동
- 예외 발생 여부와 관계없이 무조건 수할 실행문이 있다면 try~catch 문에 **finally** 블록 추가

![https://blog.kakaocdn.net/dn/ckwFL0/btqKoqBdh0N/TZol7KWYbJv3U3eNC7BMMk/img.png](https://blog.kakaocdn.net/dn/ckwFL0/btqKoqBdh0N/TZol7KWYbJv3U3eNC7BMMk/img.png)

### 예시 2

![https://blog.kakaocdn.net/dn/dvxYab/btqKopCfvZb/Fy1fK8qgEKdisDwH5Hqnek/img.png](https://blog.kakaocdn.net/dn/dvxYab/btqKopCfvZb/Fy1fK8qgEKdisDwH5Hqnek/img.png)

### 다중 catch 블록일 때 catch 순서

- 다중 catch 블록일 때 try 블록에서 예외가 발생하면 발생한 예외를 catch 블록 순서대로 비교
- 앞에 있는 catch 블록의 예외 객체가 나중 catch 블록 예외 객체의 부모라면 앞에 있는 catch 블록이 먼저 가로챔 -> 컴파일러는 오류를 발생시킴
- **구체적인 예외를 먼저 처리해야 함.**

### 예제 3

![https://blog.kakaocdn.net/dn/nlY2U/btqKmojBECk/rBCLc2wAQiE0t85B6rUU3K/img.png](https://blog.kakaocdn.net/dn/nlY2U/btqKmojBECk/rBCLc2wAQiE0t85B6rUU3K/img.png)

### try ~ with ~ resource 문

- try 블록에서 파일 등과 같은 **리소스를 사용한다면 try 블록을 실행한 후 자원 반환 필요**
- 리소스를 관리하는 코드를 추가하면 가독성도 떨어지고, 개발자도 번거로움
- JDK7 부터는 예외 발생 여부와 상관없이 사용한 리소스를 자동 반납하는 수단 제공단, 리소스는 AutoCloseable의 구현 객체
- JDK 7과 8에서는 try()의 괄호 내부에서 자원 선언 필요
- JDK 9부터는 try 블록 이전에 자원 선언 가능. 단, 선언된 자원 변수는 사실상 final이어야 함.

![https://blog.kakaocdn.net/dn/LFkr7/btqKrqAEi4v/D7PpbrKk3uVQFzB2UPKKrk/img.png](https://blog.kakaocdn.net/dn/LFkr7/btqKrqAEi4v/D7PpbrKk3uVQFzB2UPKKrk/img.png)

---

### 2. 예외 떠넘기기

메서드에서 발생한 예외를 내부에서 처리하기가 부담스러울 때는 **throws 키워드를 사용해 예외를 상위 코드 블록으로 양도 가능**

![https://blog.kakaocdn.net/dn/bzqEtZ/btqKsoClIxC/NV0v3gDIQgPF6YkgAagxVk/img.png](https://blog.kakaocdn.net/dn/bzqEtZ/btqKsoClIxC/NV0v3gDIQgPF6YkgAagxVk/img.png)

### 사용 방법

메소드에서 처리하지 않은 예외를 호출한 곳으로 떠넘김

![https://blog.kakaocdn.net/dn/cwbBk5/btqKnpo01En/1VvyPCIDFuTi6o0MvvKbPK/img.png](https://blog.kakaocdn.net/dn/cwbBk5/btqKnpo01En/1VvyPCIDFuTi6o0MvvKbPK/img.png)

![https://blog.kakaocdn.net/dn/1yP4B/btqKnpWREy8/vQKUshOx9b3vuHnFUzN991/img.png](https://blog.kakaocdn.net/dn/1yP4B/btqKnpWREy8/vQKUshOx9b3vuHnFUzN991/img.png)

### 사용시 주의 사항

- **throws** 절이 있는 메소드를 오버라이딩 할 때는 메소드에 선언한 예외보다 더 광범위한 검사형 예외(일반 예외)를 던질 수 없음
- **부모 클래스의 메소드에 예외를 떠넘기는 throws 절이 없다면** 자식 클래스의 메소드를 오버라이딩 할 때 어떤 예외도 떠넘길 수 없음.
- 자바 API 문서를 보면, 많은 메서드가 예외를 발생시키고 상위 코드로 예외 처리를 떠넘긴다.

public static void sleep(long millis, int nanos) throws InterruptedException예제

![https://blog.kakaocdn.net/dn/bYqjg6/btqKuHameTc/0rjRmV9TgXtp3Vb0FlOCdk/img.png](https://blog.kakaocdn.net/dn/bYqjg6/btqKuHameTc/0rjRmV9TgXtp3Vb0FlOCdk/img.png)
