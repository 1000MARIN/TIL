# 테이블 복사/ 서브쿼리 입력

orders_copy라는 테이블을 기존의 orders 테이블을 복사하여 만들어 보자.

```sql
-- 테이블의 복사
CREATE TABLE orders_copy AS
SELECT * FROM orders;
```

orders 테이블의 모든 데이터가 복사되었고, 제약조건은 NN만 복사된다.

![https://postfiles.pstatic.net/MjAxOTA5MThfMTA1/MDAxNTY4NzgzNzYxMzU3.4CqAOqgo9f9Jh-eVntj7FByebcFkZGnCaJXuuAvUQlAg.kSUexOhbAYs7CnmxusJhBTDGk3cK67Mu8WDpuwINxXkg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MThfMTA1/MDAxNTY4NzgzNzYxMzU3.4CqAOqgo9f9Jh-eVntj7FByebcFkZGnCaJXuuAvUQlAg.kSUexOhbAYs7CnmxusJhBTDGk3cK67Mu8WDpuwINxXkg.PNG.drv98/image.png?type=w773)

order_id는 원래 PK에 AI 를 제약조건으로 가지고 있었지만,  복사될때는 PK의 특성( UK+NN) 중 NN만 남게 된다.

<br>

**TRUNCATE TABLE : 테이블의 모든 데이터(줄,row)를 삭제한다. drop table 은 테이블 자체를 삭제하지만 , TRUNCATE는 테이블 자체는 남아 있다.**

****

![https://postfiles.pstatic.net/MjAxOTA5MThfMTUz/MDAxNTY4Nzg0MjIzNDM5.PkQrmMHXVjdFQ3yuoxCexwwAbH8jG_Xa6zQOdwUt-Ggg.YqOU82CmJjYbBhPW8VxhKrgW4XYSJE-E51fTbPPioCwg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MThfMTUz/MDAxNTY4Nzg0MjIzNDM5.PkQrmMHXVjdFQ3yuoxCexwwAbH8jG_Xa6zQOdwUt-Ggg.YqOU82CmJjYbBhPW8VxhKrgW4XYSJE-E51fTbPPioCwg.PNG.drv98/image.png?type=w773)

마우스 우클릭 => Truncate Table

<br>

```sql
SELECT *
FROM orders
WHERE order_date < '2018-01-01';
```

![https://postfiles.pstatic.net/MjAxOTA5MThfMjE3/MDAxNTY4Nzg0OTM3ODY2.ARZkvAMV9nUKBb53MN7E8S-6blxw7fiji-x8NhLlz_og.7t495-0Mqr06ex98SJ6XE0whmwwvKPD2xrLQYgBnHwQg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MThfMjE3/MDAxNTY4Nzg0OTM3ODY2.ARZkvAMV9nUKBb53MN7E8S-6blxw7fiji-x8NhLlz_og.7t495-0Mqr06ex98SJ6XE0whmwwvKPD2xrLQYgBnHwQg.PNG.drv98/image.png?type=w773)

<br>

### **이 내용을 orders_copy 테이블에 입력하자.**

```sql
-- 서브쿼리를 사용해 필요 내용 입력
INSERT INTO orders_copy
SELECT ...
```

<br>

**예제) sql_invoicing 데이타베이스에서 invoices 테이블 확인**

SELECT * FROM sql_invoicing.invoices;

![https://postfiles.pstatic.net/MjAxOTA5MThfMjQw/MDAxNTY4Nzg3MDU4OTcz._SRysvPLLoq6CUgBWohDzRYRL8SvojBVzU0y4WKYAGgg.Ht7bC2tNL4kGxFCr-DXouei1EfBt7j2g8DISc1rIrSEg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MThfMjQw/MDAxNTY4Nzg3MDU4OTcz._SRysvPLLoq6CUgBWohDzRYRL8SvojBVzU0y4WKYAGgg.Ht7bC2tNL4kGxFCr-DXouei1EfBt7j2g8DISc1rIrSEg.PNG.drv98/image.png?type=w773)

****

**1. invoices 테이블에서 client_id 컬럼을 해당하는 고객의 이름으로**

**2. invoice(송장,청구서)의 payment가 지불된 invoice 들만**

**3. invoice_archived 테이블을 만들어 위에 해당하는 invoice들을 입력하라!**

****

<br>


**결과**

```sql
SELECT * FROM sql_invoicing.invoices_archived;
```

![https://postfiles.pstatic.net/MjAxOTA5MThfMjQw/MDAxNTY4Nzg4Mjc4ODg0.B61HkvYEr5eIa3JC0wIqkc0lvN56bj2CCPDJmICK-Qog.ddq4rFDi2BLmKc4K4j3NUfqu6fsVLCFmOEGU8c8Xv6Ig.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MThfMjQw/MDAxNTY4Nzg4Mjc4ODg0.B61HkvYEr5eIa3JC0wIqkc0lvN56bj2CCPDJmICK-Qog.ddq4rFDi2BLmKc4K4j3NUfqu6fsVLCFmOEGU8c8Xv6Ig.PNG.drv98/image.png?type=w773)

# ****
