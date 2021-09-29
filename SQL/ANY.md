# ANY 키워드

> **인보이스 테이블에서 클라이언트가 적어도 2개이상의 인보이스를 가지는 client의 모든 정보 출력**

<br>

```sql
SELECT client_id, COUNT(*)
FROM invoices
GROUP BY client_id 
HAVING COUNT(*) >= 2;
```

![https://postfiles.pstatic.net/MjAxOTA5MjNfNjcg/MDAxNTY5MTg5MTY3NTU3.AgLIaX9VOL_HnhJoNu32AokGS95KfZ9-wlsNYuaYwmsg.sVL-4edAlbHPasdQRDTasVdnF00FII_IC9MF10tRa60g.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjNfNjcg/MDAxNTY5MTg5MTY3NTU3.AgLIaX9VOL_HnhJoNu32AokGS95KfZ9-wlsNYuaYwmsg.sVL-4edAlbHPasdQRDTasVdnF00FII_IC9MF10tRa60g.PNG.drv98/image.png?type=w773)

<br>

```sql
SELECT *
FROM clients
WHERE client_id IN (
	SELECT client_id
	FROM invoices
	GROUP BY client_id 
	HAVING COUNT(*) >= 2
);
```

![https://postfiles.pstatic.net/MjAxOTA5MjNfMjA2/MDAxNTY5MTkxMjk1NjU1.BZYrYGdUgjz_OR3e4VfVBsVqnZO0GmyZZBjwSIMTe7wg.ZZyj2fvWOLQ6hFHDh-zxYd-ieJmZqEZdGDL-E2YVVX8g.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjNfMjA2/MDAxNTY5MTkxMjk1NjU1.BZYrYGdUgjz_OR3e4VfVBsVqnZO0GmyZZBjwSIMTe7wg.ZZyj2fvWOLQ6hFHDh-zxYd-ieJmZqEZdGDL-E2YVVX8g.PNG.drv98/image.png?type=w773)

<br>

```sql
SELECT *
FROM clients
WHERE client_id = ANY (
	SELECT client_id
	FROM invoices
	GROUP BY client_id 
	HAVING COUNT(*) >= 2
)
```

---

<br>

### **동일하게 사용**

### **IN**

### **= ANY**
