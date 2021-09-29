# **SELECT 문**

![https://postfiles.pstatic.net/MjAxOTA5MTFfMTIw/MDAxNTY4MTk0MzQ5MjAx._-tG6YGbzV0FhWmChiv_Q0FjZiHvE69rWQ2Ib24aJowg.PrTo9Yr1QCVbr8KhF_f0Js2rTv2IcVmJdz685RDRcPog.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MTFfMTIw/MDAxNTY4MTk0MzQ5MjAx._-tG6YGbzV0FhWmChiv_Q0FjZiHvE69rWQ2Ib24aJowg.PrTo9Yr1QCVbr8KhF_f0Js2rTv2IcVmJdz685RDRcPog.PNG.drv98/image.png?type=w773)

```sql
--데이터베이스 선택, 왼쪽 더블클릭 가능, 마우스 드래그(이름) 가능
USE sql_store;
SELECT *
FROM customers
WHERE customer_id = 1
ORDER BY first_name;
```

# **SELECT 절**

```sql
SELECT last_name, first_name
FROM customers
```

```sql
SELECT last_name, first_name, points, points*10
FROM customers;
```

```sql
SELECT 
		last_name, 
    first_name, 
    points, 
    (points + 10) * 100 AS 포인트  
    --AS 로 별칭, 생략가능, 중간에 뛰워쓰기나 특수문자 있는경우 문자열 ' ' " " 사용
FROM customers;
```

# ****

****

**예제)  제품들(product)의 이름, 유닛가격, 가격 (unit_price * 1.1) 으로 출력하라.**

```sql
SELECT 
		name, 
    unit_price, 
    unit_price *1.1 가격
FROM products;
```

![https://postfiles.pstatic.net/MjAxOTA5MTFfMjc0/MDAxNTY4MTk5MjIwNDA2.sVmQNbDxZcw2E1v98fWS5ezR42DaIy_hcrliJogilN8g.JgXA89jXcDiyE6hkNQU4gAZ3ojRrcIwKdYfkYZMLz50g.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MTFfMjc0/MDAxNTY4MTk5MjIwNDA2.sVmQNbDxZcw2E1v98fWS5ezR42DaIy_hcrliJogilN8g.JgXA89jXcDiyE6hkNQU4gAZ3ojRrcIwKdYfkYZMLz50g.PNG.drv98/image.png?type=w773)
