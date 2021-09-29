# ALL 키워드

![https://blogfiles.pstatic.net/MjAxOTA5MjNfMjQ3/MDAxNTY5MTc2MzcyNzMy.SZiAD3R40FiBxJEULh4fFizGEJwRFnDeYkZ_rb1sOCYg.6Xc6Aw8WNRVbxfWbKuI1whNb4yb09PA4SZvMJR0auq8g.PNG.drv98/image.png](https://blogfiles.pstatic.net/MjAxOTA5MjNfMjQ3/MDAxNTY5MTc2MzcyNzMy.SZiAD3R40FiBxJEULh4fFizGEJwRFnDeYkZ_rb1sOCYg.6Xc6Aw8WNRVbxfWbKuI1whNb4yb09PA4SZvMJR0auq8g.PNG.drv98/image.png)

sql_invoicing

<br>

**인보이스 테이블에서**

**클라이언트3의 invoice_total 값보다 큰 인보이스 검색**

```sql
-- 클라이언트3의 인보이스들을 확인
SELECT *
FROM invoices
WHERE client_id = 3
```

![https://postfiles.pstatic.net/MjAxOTA5MjNfMzMg/MDAxNTY5MTg3OTMzMzU5.Vrba0orOeAUfoWAiMbrSqqDQ9eT9VOGiAYsQ2HteR4Ug.ca507OjINy2UjQ2TIoKHfSglntP27uY96s2Kftf8Aysg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjNfMzMg/MDAxNTY5MTg3OTMzMzU5.Vrba0orOeAUfoWAiMbrSqqDQ9eT9VOGiAYsQ2HteR4Ug.ca507OjINy2UjQ2TIoKHfSglntP27uY96s2Kftf8Aysg.PNG.drv98/image.png?type=w773)

<br>

**그러므로 결과값중 가장큰 167.29 보다 큰 값을 가진 인보이스 검색**

```sql
-- 서브쿼리 집계함수 사용
SELECT *
FROM invoices
WHERE invoice_total > (
	SELECT MAX(invoice_total) 
	FROM invoices	
	WHERE client_id = 3
);
```

![https://postfiles.pstatic.net/MjAxOTA5MjNfMTY1/MDAxNTY5MTg4MzMwMjAy.xA9h6MmI-AzY9wJgnLpTUaM8HjF8yp7AD_KwAQX05hUg.mX4USSehBpQ47ECFGuCScfkeddRnGYC9TjryJQ4Ahxwg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjNfMTY1/MDAxNTY5MTg4MzMwMjAy.xA9h6MmI-AzY9wJgnLpTUaM8HjF8yp7AD_KwAQX05hUg.mX4USSehBpQ47ECFGuCScfkeddRnGYC9TjryJQ4Ahxwg.PNG.drv98/image.png?type=w773)

<br>

**다른 방법으로 클라이언트 아이디 3번의 invoice total 값은**

```sql
SELECT invoice_total
FROM invoices
WHERE client_id = 3;
```

![https://postfiles.pstatic.net/MjAxOTA5MjNfNTIg/MDAxNTY5MTg4NTE2NTU4.m6Kr9U4grC5O6RHvdHkwtOxCwC8ARqqlMx63LAYUbqgg.exFXbFPnlH7fkrUP79qWC3isecHpkhPpgrB2rvTgke0g.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjNfNTIg/MDAxNTY5MTg4NTE2NTU4.m6Kr9U4grC5O6RHvdHkwtOxCwC8ARqqlMx63LAYUbqgg.exFXbFPnlH7fkrUP79qWC3isecHpkhPpgrB2rvTgke0g.PNG.drv98/image.png?type=w773)

**결과값은 여러행이다.**

**그러므로 서브쿼리로 사용할때**

```sql
-- ALL
SELECT *
FROM invoices
WHERE invoice_total > (
	SELECT invoice_total 
	FROM invoices	
	WHERE client_id = 3
);
```

Error Code: 1242. Subquery returns more than 1 row ( 한행 이상이 서브쿼리 결과값이므로 단일행 연산자는 에러가 난다.)

<br>

## **=> WHERE 절의 서브쿼리 괄호 앞에 ALL 키워드를 붙인다.**

```sql
WHERE invoice_total > ALL(
	SELECT invoice_total
  FROM invoices
	WHERE client_id = 3
);

-- WHERE invoice_total > ALL(150, 130, 167, ... ) 와 같은 것이다.
```

![https://postfiles.pstatic.net/MjAxOTA5MjNfMTYg/MDAxNTY5MTg4ODcwODYw.8TufY4CIz8_TbUo3tUwU2CW1RwvEHla4ZfUI4lx5Oh8g.rBPD7yu0qC_epfWm7Pc7vn-iPUow8NNWvtb79TiyFuYg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjNfMTYg/MDAxNTY5MTg4ODcwODYw.8TufY4CIz8_TbUo3tUwU2CW1RwvEHla4ZfUI4lx5Oh8g.rBPD7yu0qC_epfWm7Pc7vn-iPUow8NNWvtb79TiyFuYg.PNG.drv98/image.png?type=w773)
