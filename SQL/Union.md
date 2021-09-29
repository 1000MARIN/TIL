# UNION

**날짜기준을 2019년 이후와 이전으로 나눠서 주문을 표시해보자.**

```sql
-- 유니온
SELECT	order_id, order_date, '최신주문' AS 상태
FROM orders
WHERE order_date >= '2019-01-01'
( )
SELECT	order_id, order_date, '이전주문' AS 상태
FROM orders
WHERE order_date < '2019-01-01';
```

![https://postfiles.pstatic.net/MjAxOTA5MTRfNDUg/MDAxNTY4NDQ4Mzc2MzE5.XuKGyedgRUOxR3475eX2FlX3xfcl-pkTPc14DKreJcMg.is-P-HH51mGUo668SEZ0F3qk8odNhEnBrhUD7ftLBv4g.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MTRfNDUg/MDAxNTY4NDQ4Mzc2MzE5.XuKGyedgRUOxR3475eX2FlX3xfcl-pkTPc14DKreJcMg.is-P-HH51mGUo668SEZ0F3qk8odNhEnBrhUD7ftLBv4g.PNG.drv98/image.png?type=w773)

