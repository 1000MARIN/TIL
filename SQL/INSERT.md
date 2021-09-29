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

<br>

## AI 참조 입력

### 기본키(PK) , 유일(UK)  ==(참조)==> 외래키 (FK)

orders 테이블 칼럼

![https://postfiles.pstatic.net/MjAxOTA5MThfMjg3/MDAxNTY4NzgxMjQxODIy.XAbZ2QyWSHoCvOuWj_P4QE-P3wJCKE3_Zl0wIWVDq0Mg.mmWcM_JFkmnwwbf_RTZw8Y6tg1kZ7-nBeGtTpEEI4Kog.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MThfMjg3/MDAxNTY4NzgxMjQxODIy.XAbZ2QyWSHoCvOuWj_P4QE-P3wJCKE3_Zl0wIWVDq0Mg.mmWcM_JFkmnwwbf_RTZw8Y6tg1kZ7-nBeGtTpEEI4Kog.PNG.drv98/image.png?type=w773)

```sql
INSERT INTO orders (customer_id, order_date)
VALUES (1, '2019-01-02');
```

![https://postfiles.pstatic.net/MjAxOTA5MThfMjYx/MDAxNTY4NzgyMzM5OTgw.Kbyi10b5m1q_38kqZNA51Eny8mz5ZCaOqUv-wKo6Jbog.XqoL1ztpR3Ozi_OgNrqtf8w5lXZy89aSp4ZSTKMh-OQg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MThfMjYx/MDAxNTY4NzgyMzM5OTgw.Kbyi10b5m1q_38kqZNA51Eny8mz5ZCaOqUv-wKo6Jbog.XqoL1ztpR3Ozi_OgNrqtf8w5lXZy89aSp4ZSTKMh-OQg.PNG.drv98/image.png?type=w773)

<br>

orders 테이블의 order id 를 참조하는 order_items 테이블

![https://postfiles.pstatic.net/MjAxOTA5MThfMTc2/MDAxNTY4NzgyNTQzNjI0.LPZBI8J3e373HkX3EEQLlWdTsEKX5i-hUEnqZy65jPMg.kp5EQStFHpKMN7zGilstoyp9aUdIvzWptSBPvaj11u8g.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MThfMTc2/MDAxNTY4NzgyNTQzNjI0.LPZBI8J3e373HkX3EEQLlWdTsEKX5i-hUEnqZy65jPMg.kp5EQStFHpKMN7zGilstoyp9aUdIvzWptSBPvaj11u8g.PNG.drv98/image.png?type=w773)

```sql
SELECT last_insert_id();
-- 이전에 오토인크리스(AI)로 증가된 ID값을 가져온다.
```

```sql
INSERT INTO order_items
VALUES( last_insert_id(), 1, 1, 2.95),
	  ( last_insert_id(), 2, 1, 3.95),
```

![https://postfiles.pstatic.net/MjAxOTA5MThfMTg1/MDAxNTY4NzgyOTU3NDc2.O9O8zgC61PvBVhdVG-tQOND7izIx5XfuPCWFVp5imWog.vC_NTnNU8Vx03MJ5XLlEKiEumPqEvZ9zEEzDEpUDDYgg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MThfMTg1/MDAxNTY4NzgyOTU3NDc2.O9O8zgC61PvBVhdVG-tQOND7izIx5XfuPCWFVp5imWog.vC_NTnNU8Vx03MJ5XLlEKiEumPqEvZ9zEEzDEpUDDYgg.PNG.drv98/image.png?type=w773)
