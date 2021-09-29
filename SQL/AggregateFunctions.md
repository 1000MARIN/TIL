# 집게 함수 Aggregate Functions

```sql
SELECT 
		MAX(invoice_total) AS 최고값,
    MIN(invoice_total) AS 최저값,
    AVG(invoice_total) AS 평균값,
    SUM(invoice_total) AS 합계,
    COUNT(invoice_total) AS 행의수
FROM invoices;
```

![https://postfiles.pstatic.net/MjAxOTA5MjFfNDIg/MDAxNTY5MDMxNTE0NDQ2.MbCc-Ike12LOv53UEgKCkQzM0kti8h3tahIOWmGrPA0g.RPeXdUhWIey-eMtVO3wLMdPhcbHgC-MGKqvWOfTku3gg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjFfNDIg/MDAxNTY5MDMxNTE0NDQ2.MbCc-Ike12LOv53UEgKCkQzM0kti8h3tahIOWmGrPA0g.RPeXdUhWIey-eMtVO3wLMdPhcbHgC-MGKqvWOfTku3gg.PNG.drv98/image.png?type=w773)

<br>

**COUNT 함수는 NULL을 카운트 하지 않는다. 단, 전체(*)는 제외**

![https://postfiles.pstatic.net/MjAxOTA5MjFfMjkx/MDAxNTY5MDMxNTkxMzA1.x5lDDibtN7RIiWdyKeVADVXXqRYcEOe9mkbX2l5b4zQg.LuGRyPHfa980g9YmPRYNFvwPsmCoH6kY3-b2gaL_6KMg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjFfMjkx/MDAxNTY5MDMxNTkxMzA1.x5lDDibtN7RIiWdyKeVADVXXqRYcEOe9mkbX2l5b4zQg.LuGRyPHfa980g9YmPRYNFvwPsmCoH6kY3-b2gaL_6KMg.PNG.drv98/image.png?type=w773)

