# HAVING 절

> **WHERE 조건절로는 그룹에 대한 조건을 입력할수가 없으므로**   
> **HAVING 절을 사용하여 GRUOP BY 절 뒤에 그룹에 대한 조건 입력**   

<br>

![https://postfiles.pstatic.net/MjAxOTA5MjFfMjYw/MDAxNTY5MDU0Njk3MDE3.wDbSZ6UNrC682BtMVLT_fb2d5IOOxV7QZctyqwH6XCMg.mf3wO14HOWIHd0Ef9mnKaswHVi1Prc6o0c_5fu3kQ3Ag.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjFfMjYw/MDAxNTY5MDU0Njk3MDE3.wDbSZ6UNrC682BtMVLT_fb2d5IOOxV7QZctyqwH6XCMg.mf3wO14HOWIHd0Ef9mnKaswHVi1Prc6o0c_5fu3kQ3Ag.PNG.drv98/image.png?type=w773)

인보이스 테이블

<br>

```sql
-- HAVING
SELECT 
	client_id AS 고객아이디,	
	SUM(invoice_total) AS 전체판매금액, 
	COUNT(*) AS 인보이스개수
FROM invoices
GROUP BY client_id;
```

![https://postfiles.pstatic.net/MjAxOTA5MjFfODcg/MDAxNTY5MDU0ODQ4NTc5.KFeoFj6JA_B8cqmOYZMSP9YCr543MQqqfCZkpRx59ecg.O6Zo7TyJtaJMyfTr3xUFuZzroiGexMnTZ9MwAdzrl7Mg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjFfODcg/MDAxNTY5MDU0ODQ4NTc5.KFeoFj6JA_B8cqmOYZMSP9YCr543MQqqfCZkpRx59ecg.O6Zo7TyJtaJMyfTr3xUFuZzroiGexMnTZ9MwAdzrl7Mg.PNG.drv98/image.png?type=w773)

<br>

## **여기서 고객아이디별로 전체판매금액이 500달러 이상만 출력하도록 하면**

```sql
SELECT 
	client_id AS 고객아이디,
	SUM(invoice_total) AS 전체판매금액,
  COUNT(*) AS 인보이스개수
FROM invoices
GROUP BY client_id
HAVING 전체판매금액 > 500;
```

![https://postfiles.pstatic.net/MjAxOTA5MjFfMTU3/MDAxNTY5MDU0OTkyMDc2.xOPBDJwdd12KVt1TeQ4FznAd2dIv4-7NU1v4FTOYbegg.6TJjQKiGaheU0AnMbCFODJJcEkRpZ37-w0EBlCbsKAIg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjFfMTU3/MDAxNTY5MDU0OTkyMDc2.xOPBDJwdd12KVt1TeQ4FznAd2dIv4-7NU1v4FTOYbegg.6TJjQKiGaheU0AnMbCFODJJcEkRpZ37-w0EBlCbsKAIg.PNG.drv98/image.png?type=w773)

<br>

## **여기서 인보이스개수가 5개 보다 많은 조건을 더하면**


![https://postfiles.pstatic.net/MjAxOTA5MjFfMjUx/MDAxNTY5MDU1MTEwMDc5.lhtLvECDr9_QBB1mJdEo8kpLzyraew8X8p21d1dgsRQg.Oo3H4wic8Fm9OEFHeFgVFOVeyPdknJn8wQNJZCoIWgEg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjFfMjUx/MDAxNTY5MDU1MTEwMDc5.lhtLvECDr9_QBB1mJdEo8kpLzyraew8X8p21d1dgsRQg.Oo3H4wic8Fm9OEFHeFgVFOVeyPdknJn8wQNJZCoIWgEg.PNG.drv98/image.png?type=w773)

