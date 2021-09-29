# IN 연산자

다음과 같이 사는 주(state)가 버지니아(VA), 조지아(GA), 플로리다(FL)인 고객들의 정보를 출력하자.

```sql
SELECT * 
FROM customers
WHERE state = 'VA' OR state = 'GA' OR state = 'FL'
```

![https://postfiles.pstatic.net/MjAxOTA5MTJfMTY5/MDAxNTY4MjUwMDA1NTA3.ZNIU6aatIV2foQY54nJBxPsjcrherUi02OzgqC5lDxkg.hksplkE6aADI3tWPiHDYv5vXyK7_q6cwRut5utmiWV0g.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MTJfMTY5/MDAxNTY4MjUwMDA1NTA3.ZNIU6aatIV2foQY54nJBxPsjcrherUi02OzgqC5lDxkg.hksplkE6aADI3tWPiHDYv5vXyK7_q6cwRut5utmiWV0g.PNG.drv98/image.png?type=w773)

IN 연산자를 사용해서 같은 결과를 만듭니다.

```sql
WHERE ? IN (? ? ?)
```

<br>

사는 주(state)가 버지니아(VA), 조지아(GA), 플로리다(FL)가 **아닌** 고객들의 정보

```sql
WHERE ? ? IN (? ? ?)
```
