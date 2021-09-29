# INSERT

## 한출 입력하기

![https://postfiles.pstatic.net/MjAxOTA5MThfMTk0/MDAxNTY4NzY2NTEyMzQ0.1K5NdnuOnQb17mpTBH596XcNAgnHNlNH6EG1mntOj0Qg.tin7PrpxE_AX0ylRyqkkMM8pD4ItsVq6wH7xOlPXMCwg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MThfMTk0/MDAxNTY4NzY2NTEyMzQ0.1K5NdnuOnQb17mpTBH596XcNAgnHNlNH6EG1mntOj0Qg.tin7PrpxE_AX0ylRyqkkMM8pD4ItsVq6wH7xOlPXMCwg.PNG.drv98/image.png?type=w773)

```sql
INSERT INTO customers
VALUES (
		DEFAULT, 
    'John', 
    'Smith', 
    '1990-01-01', 
    NULL, 
    'address',
    'city',
    'CA',
    DEFAULT );
```

위에서 입력하지 않은 디폴트,널 값들을 제외하고 입력을 하면

```sql
INSERT INTO customers(
					first_name,
          last_name,
          birth_date,
          address,
          city,
          state)
VALUES (
  'John', 
  'Smith', 
  '1990-01-01', 
  'address',
  'city',
  'CA');
```

쿼리문 실행 ( Ctrl + Enter)

![https://postfiles.pstatic.net/MjAxOTA5MThfMTQy/MDAxNTY4NzY2OTUxNzY5.qiqp15kZZt5TD7VpMjNXOBRH_ZnGHe4XP2DEGPa8absg.yTuCvFPbERVc3U9C4bABBGrtug-Zg4KJi1wvmCWXRY0g.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MThfMTQy/MDAxNTY4NzY2OTUxNzY5.qiqp15kZZt5TD7VpMjNXOBRH_ZnGHe4XP2DEGPa8absg.yTuCvFPbERVc3U9C4bABBGrtug-Zg4KJi1wvmCWXRY0g.PNG.drv98/image.png?type=w773)

<br>

## 여러줄 입력

shippers 테이블

![https://postfiles.pstatic.net/MjAxOTA5MThfNyAg/MDAxNTY4NzY3MjA5MTY5.AzTsjQHVc3qFzwKEA8ArKXryO3QnZ2J2GUGV4nAphJcg.GMlx1-ikBF_LQzveAV3MairDJx8b4xnzlFfGvIOK0BAg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MThfNyAg/MDAxNTY4NzY3MjA5MTY5.AzTsjQHVc3qFzwKEA8ArKXryO3QnZ2J2GUGV4nAphJcg.GMlx1-ikBF_LQzveAV3MairDJx8b4xnzlFfGvIOK0BAg.PNG.drv98/image.png?type=w773)

```sql
INSERT INTO shippers (name)
VALUES ('Shipper1'),
	   ('Shipper2'),
       ('Shipper3')
```
