# VIEW

## View 생성

### **sql_invoicing**

![https://postfiles.pstatic.net/MjAxOTA5MjZfMzAw/MDAxNTY5NDkyOTY4OTQy.HgwD6fn-wwHnXpVHsfaeJQBdPjVeysMENmuxt2PoEO4g.FhEnfd9BPLhq9CvfzHm_iEYRfLusMkk17vNyzOa1tL0g.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjZfMzAw/MDAxNTY5NDkyOTY4OTQy.HgwD6fn-wwHnXpVHsfaeJQBdPjVeysMENmuxt2PoEO4g.FhEnfd9BPLhq9CvfzHm_iEYRfLusMkk17vNyzOa1tL0g.PNG.drv98/image.png?type=w773)

```sql
SELECT 
		c.client_id,
    c.name,
    SUM(invoice_total) AS 총판매량
FROM clients c
JOIN invoices i USING (client_id)
GROUP BY client_id, name;
```

![https://postfiles.pstatic.net/MjAxOTA5MjZfMzIg/MDAxNTY5NDkzMTY2NjI1.wbnseN8IHN3yR03AJlcUAUgjzBQYqv4Qy57K3H-kyLAg.N-s3gvwn_IkouU-xAfd4S9_R9UAjeDWv_EtI3PmrmKsg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjZfMzIg/MDAxNTY5NDkzMTY2NjI1.wbnseN8IHN3yR03AJlcUAUgjzBQYqv4Qy57K3H-kyLAg.N-s3gvwn_IkouU-xAfd4S9_R9UAjeDWv_EtI3PmrmKsg.PNG.drv98/image.png?type=w773)

<br>

```sql
-- 뷰 만들기
CREATE VIEW sales_by_client AS
SELECT ...
```

![https://postfiles.pstatic.net/MjAxOTA5MjZfMTI5/MDAxNTY5NDkzMzM4NDYw.vqfzADWQZILni1GSGKb6GKbXk9qo_1BlpvFDqVbAhRog.6dmOPkr0Uy_8yq5oERDM40s_Aza25qt-HJqkEFGUfjYg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjZfMTI5/MDAxNTY5NDkzMzM4NDYw.vqfzADWQZILni1GSGKb6GKbXk9qo_1BlpvFDqVbAhRog.6dmOPkr0Uy_8yq5oERDM40s_Aza25qt-HJqkEFGUfjYg.PNG.drv98/image.png?type=w773)

### **테이블과 마찬가지로 세번째 아이콘으로 뷰를 테이블 처럼 확인가능**

```sql
SELECT *
FROM sales_by_client
WHERE 총판매량 > 500;
```

### **조인도 가능**

```sql
SELECT *
FROM sales_by_client
JOIN clients USING (client_id);
```

<br>

**예제 1) clients 테이블과 invoices 테이블을 (client_id)를 사용해 조인하고 client_id와 name 그룹별로** 

**SUM(invoice_total - payment_total) AS 미납금액**

**아래와 같은 결과의 VIEW 을 만들어라.**

<br>

```sql
CREATE VIEW clients_balance AS
SELECT 문
```

![https://postfiles.pstatic.net/MjAxOTA5MjZfMjA5/MDAxNTY5NDk0MjA1Njk1.B8FXY9wXcciQcrWSVDKpqc2hPBO6F_EOA7c76Ad-5Rkg.lxCQmkMW-ia0WCNs02ejCYFR1Ea0BezAXzfW9zHMKm8g.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjZfMjA5/MDAxNTY5NDk0MjA1Njk1.B8FXY9wXcciQcrWSVDKpqc2hPBO6F_EOA7c76Ad-5Rkg.lxCQmkMW-ia0WCNs02ejCYFR1Ea0BezAXzfW9zHMKm8g.PNG.drv98/image.png?type=w773)

---

<br>

## View의 수정


### **1. 쿼리문을 저장해 놓고 수정한다.**

### **CREATE OR REPLACE + 뷰, 테이블, 인덱스**

### **앞의 예제에서 만들었던 뷰를 다음과 같은 쿼리문으로 수정할 수 있다.**

```sql
CREATE OR REPLACE VIEW clients_balance AS
SELECT 
		c.client_id,
    c.name,
    SUM(invoice_total - payment_total) AS 미납금액
FROM clients c
JOIN invoices i USING (client_id)
GROUP BY client_id, name;
```

<br>

### **2. 왼쪽 뷰에서 2번째 아이콘 클릭하여 수정모드**

![https://postfiles.pstatic.net/MjAxOTA5MjZfMjY1/MDAxNTY5NDk1MDc0Mjg5.sw5p9MiJWZUfUhNvTdz77JDEMFxw-oXmxjdKt0HEXiEg.UndesYPNd33Ugl9mAdoYBhlS5VXKULnJaRhxA7VsmpIg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjZfMjY1/MDAxNTY5NDk1MDc0Mjg5.sw5p9MiJWZUfUhNvTdz77JDEMFxw-oXmxjdKt0HEXiEg.UndesYPNd33Ugl9mAdoYBhlS5VXKULnJaRhxA7VsmpIg.PNG.drv98/image.png?type=w773)

<br>

## **수정**

![https://postfiles.pstatic.net/MjAxOTA5MjZfMTYz/MDAxNTY5NDk1MTkwMDAz.9a0JZR45YFTh5VdSnndj_euyvmdgBb1OowS02POoH2sg.OnE_yfwNR1r6W-YjhB8S5NHmQbg3GtYP-S0PTJSCx48g.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjZfMTYz/MDAxNTY5NDk1MTkwMDAz.9a0JZR45YFTh5VdSnndj_euyvmdgBb1OowS02POoH2sg.OnE_yfwNR1r6W-YjhB8S5NHmQbg3GtYP-S0PTJSCx48g.PNG.drv98/image.png?type=w773)

<br>

## **APPY 클릭**


![https://postfiles.pstatic.net/MjAxOTA5MjZfMTg5/MDAxNTY5NDk1MjMwNDg1.NXJebF36PWIre18Ljf_fJ4lb2VXpARF0dtv94sPL8fcg.Y2TiQN2zDERwrSczvFCvBjrPEKgGA07-oIN1uWWNy0Ag.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjZfMTg5/MDAxNTY5NDk1MjMwNDg1.NXJebF36PWIre18Ljf_fJ4lb2VXpARF0dtv94sPL8fcg.Y2TiQN2zDERwrSczvFCvBjrPEKgGA07-oIN1uWWNy0Ag.PNG.drv98/image.png?type=w773)

<br>

## View의 삭제
```sql
DROP VIEW + 뷰이름;
```
