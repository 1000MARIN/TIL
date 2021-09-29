# GROUP BY

**그룹으로 나누어서 각각의 그룹에 집계함수를 적용하여 결과 출력**

SELECT 절에 집계함수가 있을때, 다른 컬럼(열)이 있다면 그 칼럼은

GROUP BY 다음에 적는 칼럼과 같다.

```sql
-- GROUP BY 절
SELECT	
	SUM(invoice_total) AS 총판매금액
FROM invoices
GROUP BY client_id;
```

![https://postfiles.pstatic.net/MjAxOTA5MjFfOTcg/MDAxNTY5MDUyMjQwNjQw.zJInFzpEWbqKs8aHSaCRLXZyheH0A2iT4pUVts4ENL8g.uH52ferYWtlUD77LKtPbygEVQnJxcNJFeU69AseW-vEg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjFfOTcg/MDAxNTY5MDUyMjQwNjQw.zJInFzpEWbqKs8aHSaCRLXZyheH0A2iT4pUVts4ENL8g.uH52ferYWtlUD77LKtPbygEVQnJxcNJFeU69AseW-vEg.PNG.drv98/image.png?type=w773)

```sql
SELECT
	client_id AS 고객아이디,
	SUM(invoice_total) AS 총판매금액
FROM invoices
GROUP BY client_id
ORDER BY 총판매금액 DESC
```

![https://postfiles.pstatic.net/MjAxOTA5MjFfMjUz/MDAxNTY5MDUyMjc5ODM2.lBRW-ACLTwnmjqq7mV5VtxXjAFa0CDtczHz1p8tTzoMg.UQh37YbUWqRwaeUPcukmM9QvKEXWwIcfN5syIV9300og.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjFfMjUz/MDAxNTY5MDUyMjc5ODM2.lBRW-ACLTwnmjqq7mV5VtxXjAFa0CDtczHz1p8tTzoMg.UQh37YbUWqRwaeUPcukmM9QvKEXWwIcfN5syIV9300og.PNG.drv98/image.png?type=w773)

****

**여기서 조건절을 넣는다면**

**만약 invoice_date가 2019년 7월 1일 이후라는 조건절을 추가하자.**

**- 주의: 조건절의 위치는 GROUP BY 전(위)**

```sql
SELECT
	client_id AS 고객아이디,
	SUM(invoice_total) AS 총판매금액
FROM invoices
WHERE invoice_date >= '2019-07-01'
GROUP BY client_id
ORDER BY 총판매금액 DESC
```

<br>

**여기서 인보이스 테이블에 있는 client_id (외래키)로 client 테이블을 조인하고 client 테이블에 city와 state 로 그룹을 지어 출력하자**

![https://postfiles.pstatic.net/MjAxOTA5MjFfMjU3/MDAxNTY5MDUyOTM4MTEx.y7XmdvmmplS3iAtx9yCc0ReEL1UGt8-GO5R-dBRckygg.ueTVIUQufk_wgdIcinUEvw70CTbt_9Ise20m28aamHYg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjFfMjU3/MDAxNTY5MDUyOTM4MTEx.y7XmdvmmplS3iAtx9yCc0ReEL1UGt8-GO5R-dBRckygg.ueTVIUQufk_wgdIcinUEvw70CTbt_9Ise20m28aamHYg.PNG.drv98/image.png?type=w773)

clients 테이블

<br>

```sql
-- 멀티열 그룹, 조인
SELECT	
	state, 
	city,	
	SUM(invoice_total) AS 총판매금액
FROM invoices i
JOIN clients c USING (client_id)
GROUP BY state, city;
```

![https://postfiles.pstatic.net/MjAxOTA5MjFfMTYz/MDAxNTY5MDUzMDcyNzE1.l9QMbX6pBtbGa1njwe4iiSB--_Mr2Ri79T27eac84Gog.whZTfo5XZUas0xUwt-WG_anLT28I9lMjeLw4JVZ9ocEg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjFfMTYz/MDAxNTY5MDUzMDcyNzE1.l9QMbX6pBtbGa1njwe4iiSB--_Mr2Ri79T27eac84Gog.whZTfo5XZUas0xUwt-WG_anLT28I9lMjeLw4JVZ9ocEg.PNG.drv98/image.png?type=w773)

