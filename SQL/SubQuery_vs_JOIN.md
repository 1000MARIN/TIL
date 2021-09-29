# 서브쿼리

> **이전 페이지에서 했었던 서브쿼리문**
> **클라이언트(clients)중 인보이스가 없는 클라이언트**

<br>

```sql
SELECT *
FROM clients
WHERE client_id NOT IN (
	SELECT DISTINCT client_id
  FROM invoices
);
```

![https://postfiles.pstatic.net/MjAxOTA5MjJfMjUw/MDAxNTY5MTA1NjkxOTI3.C2NzC30XtZ8eLNKJQZ_zTy55gNmWhJGnRpctt1-jpA8g.sf8tjAV_LZqLa-aVuF_gwNdBqM2pJdCZ5HYuqidH3zAg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjJfMjUw/MDAxNTY5MTA1NjkxOTI3.C2NzC30XtZ8eLNKJQZ_zTy55gNmWhJGnRpctt1-jpA8g.sf8tjAV_LZqLa-aVuF_gwNdBqM2pJdCZ5HYuqidH3zAg.PNG.drv98/image.png?type=w773)

---

<br>

# **조인**

<br>

```sql
- 조인
SELECT *
FROM clients
JOIN invoices USING (client_id)
```

![https://postfiles.pstatic.net/MjAxOTA5MjJfMTkw/MDAxNTY5MTA1OTI3MTc0.444GrkRljsshTOP9p6R081PNww815C7y9zgh_RwINwkg.obWdlFXaJrKSA_DLudPS0OYFZTylZ0Es0Ph5frl_wHIg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjJfMTkw/MDAxNTY5MTA1OTI3MTc0.444GrkRljsshTOP9p6R081PNww815C7y9zgh_RwINwkg.obWdlFXaJrKSA_DLudPS0OYFZTylZ0Es0Ph5frl_wHIg.PNG.drv98/image.png?type=w773)

<br>

### **클라이언츠 테이블에서 인보이스테이블과 조인시에 왼쪽 조인을 하게 되면 오른쪽 테이블인 인보이스 테이블이 없더라도(NULL) 왼쪽의 클라이언트가 출력된다. => LEFT JOIN**

```sql
-- LEFT 조인
SELECT *
FROM clients
LEFT JOIN invoices USING (client_id);
```

![https://postfiles.pstatic.net/MjAxOTA5MjJfMTI1/MDAxNTY5MTA2MTE0NzU4.Fzv9624vIm240k0TNfeNDDTkMCyNpnZkt3iektBr4FUg.LmxKtBez51J5aysQxWRETbDdyxFnnl0r-FlGqIn9pNMg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjJfMTI1/MDAxNTY5MTA2MTE0NzU4.Fzv9624vIm240k0TNfeNDDTkMCyNpnZkt3iektBr4FUg.LmxKtBez51J5aysQxWRETbDdyxFnnl0r-FlGqIn9pNMg.PNG.drv98/image.png?type=w773)

<br>

### **최종적으로**

![https://postfiles.pstatic.net/MjAxOTA5MjJfMTg0/MDAxNTY5MTA2MTcyMzMz.DHZeNYVWDxEXc6RRBk3AHlH5T-VQzITXeCkAgG6H6ccg._r_j57zINKVdclZgy0Nk2DFdBhSwM4ye52R9xKneWMog.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjJfMTg0/MDAxNTY5MTA2MTcyMzMz.DHZeNYVWDxEXc6RRBk3AHlH5T-VQzITXeCkAgG6H6ccg._r_j57zINKVdclZgy0Nk2DFdBhSwM4ye52R9xKneWMog.PNG.drv98/image.png?type=w773)

---

<br>

### **결과 비교**

```sql
-- 클라이언트 중에 인보이스가 없는 사람
1.
SELECT *
FROM clients
WHERE client_id NOT IN (
	SELECT DISTINCT client_id 
	FROM invoices
);

2.
SELECT *
FROM clients
LEFT JOIN invoices USING (client_id)
WHERE invoice_id IS NULL;
```

### **결과적으로 누구나 읽기가 쉬운 가독성이 높은 쿼리를 사용한다.**

### **기본적으로 이해하기 쉬운문은 1.서브쿼리 이다.**

### **그러나 1. 서브쿼리가 너무 복잡하다 => 2 조인문으로 작성**

<br>

![https://postfiles.pstatic.net/MjAxOTA5MjNfMjcw/MDAxNTY5MTg2MzczMjQ4.0WQ09XMySkGe-Nl3y2uIlF23C_gwkCZZHG8Y2MncPL0g.2efYROpci2jMKAQnlpEhlKTgyX7JmuqDHAA-I5wrMaAg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjNfMjcw/MDAxNTY5MTg2MzczMjQ4.0WQ09XMySkGe-Nl3y2uIlF23C_gwkCZZHG8Y2MncPL0g.2efYROpci2jMKAQnlpEhlKTgyX7JmuqDHAA-I5wrMaAg.PNG.drv98/image.png?type=w773)

테이블 관계도

**sql_store 에서 product_id 가 3번인 lettuce를 주문한 고객(customer)의 고객아이디, 성, 이름 을 아래와 같이 출력**

![https://postfiles.pstatic.net/MjAxOTA5MjJfNjEg/MDAxNTY5MTA4NjAyNjQ5.xoV6hwBwbu4c1Y5Abf8Gtg6LqpsoOh2lrvWhywt-oSEg.KJ4wIkNX0nYxh5lGfL5XyRlSTFJi6HPfksHbUcWUb9Eg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjJfNjEg/MDAxNTY5MTA4NjAyNjQ5.xoV6hwBwbu4c1Y5Abf8Gtg6LqpsoOh2lrvWhywt-oSEg.KJ4wIkNX0nYxh5lGfL5XyRlSTFJi6HPfksHbUcWUb9Eg.PNG.drv98/image.png?type=w773)

