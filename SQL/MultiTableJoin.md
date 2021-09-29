# 멀티 테이블 조인

### 주문 테이블        ( 주문번호, 고객번호, 주문시간, 상태 등등)

### 고객 테이블         ( 고객에 대한 정보 )

### 주문 상태 테이블 ( 현재 주문이 진행, 배송, 완료 )

```sql
SELECT o.order_id, o.order_date, c.first_name, os.name AS 주문상태
FROM orders o
JOIN customers c ON o.customer_id = c.customer_id
JOIN order_statuses os ON o.status = os.order_status_id;
```

![https://postfiles.pstatic.net/MjAxOTA5MTNfMjIx/MDAxNTY4MzQ1NDA1NzQy.4cOmemGGKNmFtQybuJFWvFVlubQ3YvWtWpW_h76Pl2kg.UjbJlSfCk6ssUQdrsiCWFCGA1d9AbF_iNd3K71GPAKQg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MTNfMjIx/MDAxNTY4MzQ1NDA1NzQy.4cOmemGGKNmFtQybuJFWvFVlubQ3YvWtWpW_h76Pl2kg.UjbJlSfCk6ssUQdrsiCWFCGA1d9AbF_iNd3K71GPAKQg.PNG.drv98/image.png?type=w773)

<br>

### **인보이스 데이터베이스를 이용해서**

```sql
USE sql_invoicing;
```
