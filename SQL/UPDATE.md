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

