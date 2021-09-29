# UPDATE

## 한줄 업데이트
**sql_invoicing 데이터베이스에 invoices 테이블을 보면**

```sql
SELECT * FROM sql_invoicing.invoices;
```

![https://postfiles.pstatic.net/MjAxOTA5MThfOTUg/MDAxNTY4Nzg4NzgxOTUx.8o3bk64XidhOBm-UWvSjq3RNAj4mFID345DQX6igwnYg.ogG1TRy2dIyX1YcYkdOBfzqvVrM3RJO2bqpLinKmemog.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MThfOTUg/MDAxNTY4Nzg4NzgxOTUx.8o3bk64XidhOBm-UWvSjq3RNAj4mFID345DQX6igwnYg.ogG1TRy2dIyX1YcYkdOBfzqvVrM3RJO2bqpLinKmemog.PNG.drv98/image.png?type=w773)

**위와 같이 id 1은 payment_total 의 값과 payment_date가 입력되지 않았다.**

<br>

**이를 업데이트 해보자.**

```sql
UPDATE invoices
SET payment_total = 10, payment_date = '2019-03-01'
WHERE invoice_id = 1;
```

![https://postfiles.pstatic.net/MjAxOTA5MThfMTk2/MDAxNTY4Nzg4ODk2MDg5.qM7vr7qZsAFzY0wGy8RUQmkWugF08oL7PzDSP35uvV8g.oiGRLtu3EpiL8b_QNnXn4hdq7p645CPnFrSFiD1Xeaog.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MThfMTk2/MDAxNTY4Nzg4ODk2MDg5.qM7vr7qZsAFzY0wGy8RUQmkWugF08oL7PzDSP35uvV8g.oiGRLtu3EpiL8b_QNnXn4hdq7p645CPnFrSFiD1Xeaog.PNG.drv98/image.png?type=w773)

<br>

**다시 id =1 의 줄을 payment_total을 0 으로, payment_date를 Null 값으로 업데이트**

```sql
UPDATE invoices
SET payment_total = 0, payment_date = NULL
-- SET payment_total = DEFAULT, payment_date = DEFAULT
WHERE invoice_id = 1;
```

![https://postfiles.pstatic.net/MjAxOTA5MThfMjE3/MDAxNTY4Nzg5MDY5Mzg5.-NX5YIJ2NC1Y8AEKWrE5MEu1oKLHLLVESyT4x3MKH64g.PogaH4xHGviPXn2zp0eGLUErZUoFbTEL37Jt0llbW64g.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MThfMjE3/MDAxNTY4Nzg5MDY5Mzg5.-NX5YIJ2NC1Y8AEKWrE5MEu1oKLHLLVESyT4x3MKH64g.PogaH4xHGviPXn2zp0eGLUErZUoFbTEL37Jt0llbW64g.PNG.drv98/image.png?type=w773)

---

##  여러줄(rows) 업데이트
![https://postfiles.pstatic.net/MjAxOTA5MThfMjIz/MDAxNTY4NzkwNTUzMDMx.Hjag9xprvcYGOFCKUymWkdrhKs7eGKjG7_322DaZ_1cg.wWzheuP6KtKzAwymHey00Ny-kNsowzfnbfErNm-zV6Ag.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MThfMjIz/MDAxNTY4NzkwNTUzMDMx.Hjag9xprvcYGOFCKUymWkdrhKs7eGKjG7_322DaZ_1cg.wWzheuP6KtKzAwymHey00Ny-kNsowzfnbfErNm-zV6Ag.PNG.drv98/image.png?type=w773)

여러줄을 업데이트 하기 위해 SAFE 업데이트 옵션을 끈다.

옵션을 재설정 한 다름 워크벤치를 종료한 뒤 새로 실행한다.

<br>

```sql
UPDATE invoices
SET 
		payment_total = invoice_total * 0.5,
    payment_date = due_date
WHERE client_id = 3;
```

![https://postfiles.pstatic.net/MjAxOTA5MThfMjYw/MDAxNTY4NzkwMTMwOTQy.dU-L7Na5a8tIPDgx1AuffKcXeYkdJX5VpWSNQ00rwsMg.Iedcjmod1OYGKhUnMkGQ7fLX2OhkFL_SATHFKem5qEwg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MThfMjYw/MDAxNTY4NzkwMTMwOTQy.dU-L7Na5a8tIPDgx1AuffKcXeYkdJX5VpWSNQ00rwsMg.Iedcjmod1OYGKhUnMkGQ7fLX2OhkFL_SATHFKem5qEwg.PNG.drv98/image.png?type=w773)

---

## 서브쿼리를 이용한 업데이트

```sql
UPDATE invoices
SET 
		payment_total = invoice_total * 0.5,
    payment_date = due_date
WHERE client_id = 3;
```

위의 업데이트문은 이전 업데이트에서 client_id가  3번인 모든 invoice를 업데이트 했다.

client_id 대신 client의 이름을 'Myworks' 로 알고 있을때, 서브쿼리를 사용해 해당하는 client_id의 줄을 업데이트 하자.

<br>

```sql
SELECT client_id
FROM clients
WHERE name = 'Myworks';
```

위의 셀렉트 문을 서브쿼리로 사용하면 다음과 같이

<br>


```sql
UPDATE invoices
SET 
		payment_total = invoice_total * 0.5,
    payment_date = due_date
WHERE client_id = 
                   (SELECT .... )
```

![https://postfiles.pstatic.net/MjAxOTA5MThfNzQg/MDAxNTY4ODAyNDYyMjE4.pzNRtAhqzDQzsQjdGRAQ8EVRBI7k9-WkvB-wo7xJ5C4g.PRYxyw1JFpIZ5uN9PFAx6BbAeyxQH52YaHJp-GER2Bgg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MThfNzQg/MDAxNTY4ODAyNDYyMjE4.pzNRtAhqzDQzsQjdGRAQ8EVRBI7k9-WkvB-wo7xJ5C4g.PRYxyw1JFpIZ5uN9PFAx6BbAeyxQH52YaHJp-GER2Bgg.PNG.drv98/image.png?type=w773)

<br>

```sql
SELECT client_id
		FROM clients
		WHERE state IN('CA', 'NY');
```

![https://postfiles.pstatic.net/MjAxOTA5MThfMTQ4/MDAxNTY4ODAyNTI4ODIw.y0JZyoyE_DazwNQ7L_XoAQZ5aj8TZpbPis6RjsQYidcg.-hCIcmRXQx3RNM_eIFcEIoARtQ2S_Dq1j6_t6mn_Ejsg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MThfMTQ4/MDAxNTY4ODAyNTI4ODIw.y0JZyoyE_DazwNQ7L_XoAQZ5aj8TZpbPis6RjsQYidcg.-hCIcmRXQx3RNM_eIFcEIoARtQ2S_Dq1j6_t6mn_Ejsg.PNG.drv98/image.png?type=w773)

```sql
UPDATE invoices
SET 
		payment_total = invoice_total * 0.5,
    payment_date = due_date
WHERE client_id = 
    ( SELECT client_id
		  FROM clients
		  WHERE state IN('CA', 'NY') );
```

**멀티로우(row) 값이 출력되는 서브쿼리에 맞는 연산자를 사용 => IN ANY ALL**


