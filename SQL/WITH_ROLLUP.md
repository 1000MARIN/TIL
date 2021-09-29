# WITH ROLLUP 연산자 ( MYSQL)

![https://postfiles.pstatic.net/MjAxOTA5MjFfNjkg/MDAxNTY5MDU4ODU2Nzc4.ItOUsLqVaNZY56OAHt8SaZfQPJo_TBBb9_qqBkiKnxUg.ET-xbtutgYUIpOBmIjTWUTsGQPkcM7ECBSqxugXYupMg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjFfNjkg/MDAxNTY5MDU4ODU2Nzc4.ItOUsLqVaNZY56OAHt8SaZfQPJo_TBBb9_qqBkiKnxUg.ET-xbtutgYUIpOBmIjTWUTsGQPkcM7ECBSqxugXYupMg.PNG.drv98/image.png?type=w773)

인보이스 테이블

### **인보이스 테이블에서 client_id 그룹별로 총판매금액( invoice_total의 합계)을 출력**

```sql
-- ROLLUP
SELECT	
	client_id, 
	SUM(invoice_total) AS 총판매금액
FROM invoices
GROUP BY client_id WITH ROLLUP;
```

![https://postfiles.pstatic.net/MjAxOTA5MjFfMjY5/MDAxNTY5MDU4OTgxMTAz.KpBVakpIgGYrNRBcb97NRuNsXmHFsI2TMrZNEvC5Y0Ag.RtmxmdP_JL1Cdqog2tX4bOaaVhAihGWOsBmZqeM6DXIg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjFfMjY5/MDAxNTY5MDU4OTgxMTAz.KpBVakpIgGYrNRBcb97NRuNsXmHFsI2TMrZNEvC5Y0Ag.RtmxmdP_JL1Cdqog2tX4bOaaVhAihGWOsBmZqeM6DXIg.PNG.drv98/image.png?type=w773)

<br>

### **client_id를 이용해 clients 테이블과 조인하여 clients 테이블의 state 와 city별로 총 판매금액을 ROLLUP 과 함께 출력**


```sql
SELECT 
	state,
  city,
  SUM(invoice_total) AS 총판매금액
FROM invoices i
JOIN clients c USING (client_id)
GROUP BY state, city WITH ROLLUP;
```

![https://postfiles.pstatic.net/MjAxOTA5MjFfMjgx/MDAxNTY5MDU5MjE0NjMz.PKo42eJIXfy2wHUcSrLLIV5TMwHLX4qXwvYZMBY9ZGkg.dBqhx_G5LQRcVhgRWf-20vI1MC_Lx8i_YqAwE0yzx6Ag.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjFfMjgx/MDAxNTY5MDU5MjE0NjMz.PKo42eJIXfy2wHUcSrLLIV5TMwHLX4qXwvYZMBY9ZGkg.dBqhx_G5LQRcVhgRWf-20vI1MC_Lx8i_YqAwE0yzx6Ag.PNG.drv98/image.png?type=w773)

