# 인덱스로 정렬하기(Sorting)
> Filtering Data :  인덱스를 만들어 조건절로 검색등을 빠르게 하는 방법   

<br>

```sql
SHOW INDEXES IN customers;                       -- 인덱스 확인
```

![https://postfiles.pstatic.net/MjAxOTEwMDNfNzEg/MDAxNTcwMDYyMjYzMjE1.kXKsysG2CH5oP_rSRtfGglJ73mvUa8DFLP9VzrJLP20g.EnFsCoFgUXJzj_7v9rLEzhNB30-3xi1ZKrwrTKjRCL0g.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTEwMDNfNzEg/MDAxNTcwMDYyMjYzMjE1.kXKsysG2CH5oP_rSRtfGglJ73mvUa8DFLP9VzrJLP20g.EnFsCoFgUXJzj_7v9rLEzhNB30-3xi1ZKrwrTKjRCL0g.PNG.drv98/image.png?type=w773)

<br>

```sql
EXPLAIN SELECT customer_id FROM customers
ORDER BY first_name;
```

![https://postfiles.pstatic.net/MjAxOTEwMDNfODYg/MDAxNTcwMDYyNzUzMTkw.ePJBGrmLVSt431H-Ic3Qg22N_ByBWVVhu0PAGRSTcuEg.tppPnb4Zb2UaJSZ-04Xe-Fnr1hhgL2hMEBTpxb_TaEkg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTEwMDNfODYg/MDAxNTcwMDYyNzUzMTkw.ePJBGrmLVSt431H-Ic3Qg22N_ByBWVVhu0PAGRSTcuEg.tppPnb4Zb2UaJSZ-04Xe-Fnr1hhgL2hMEBTpxb_TaEkg.PNG.drv98/image.png?type=w773)

<br>

```sql
SHOW STATUS LIKE 'last_query_cost';   
-- 마지막으로 실행한 쿼리문을 실행하기 위해 CPU 연산및 자원사용 정도
```

![https://postfiles.pstatic.net/MjAxOTEwMDNfMjE2/MDAxNTcwMDYyODY3NTE2.IpCeCe4ZLxCijCaROApw2ESfHWSPlxEzXyobKtF2f48g.OYpBKLgMiR6CM_0aLM5HOpxUEQURmhd7j162BDckhhcg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTEwMDNfMjE2/MDAxNTcwMDYyODY3NTE2.IpCeCe4ZLxCijCaROApw2ESfHWSPlxEzXyobKtF2f48g.OYpBKLgMiR6CM_0aLM5HOpxUEQURmhd7j162BDckhhcg.PNG.drv98/image.png?type=w773)

<br>

```sql
EXPLAIN SELECT customer_id FROM customers
ORDER BY state;

SHOW STATUS LIKE 'last_query_cost';
```

![https://postfiles.pstatic.net/MjAxOTEwMDNfNzYg/MDAxNTcwMDYzMjg0NjI2.Pg_obSQEKENYO8xIT4gql_GM_IPWvzMMhvQqw5ftPdAg.yJ6ydpahAJj2VX4stCcsx9rhDM7NC5GK2Nt4FmAW-zIg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTEwMDNfNzYg/MDAxNTcwMDYzMjg0NjI2.Pg_obSQEKENYO8xIT4gql_GM_IPWvzMMhvQqw5ftPdAg.yJ6ydpahAJj2VX4stCcsx9rhDM7NC5GK2Nt4FmAW-zIg.PNG.drv98/image.png?type=w773)

![https://postfiles.pstatic.net/MjAxOTEwMDNfMTg0/MDAxNTcwMDYzMzEzODk0.A-yj2_xH3j6Ho1Xj0SPNe7aeDAlWptGQ4tZ_uHMapoQg.6lgvMqC_PpszZRWBSCC1gPuWp4wSl5WwEJpGlk4tbYwg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTEwMDNfMTg0/MDAxNTcwMDYzMzEzODk0.A-yj2_xH3j6Ho1Xj0SPNe7aeDAlWptGQ4tZ_uHMapoQg.6lgvMqC_PpszZRWBSCC1gPuWp4wSl5WwEJpGlk4tbYwg.PNG.drv98/image.png?type=w773)

### **order by 일반열 VS 인덱스된 열의 차이는 10배**

<br>

```sql
EXPLAIN SELECT customer_id FROM customers
ORDER BY state, points;

SHOW STATUS LIKE 'last_query_cost'; 

ALTER TABLE customers DROP INDEX idx_state;        -- 인덱스(state)삭제
ALTER TABLE customers DROP INDEX idx_points;       -- 인덱스(points)삭제
CREATE INDEX idx_state_points ON customers(state, points);  -- 복합인덱스 생성
SHOW INDEXES IN customers;
```

![https://postfiles.pstatic.net/MjAxOTEwMDNfMjk3/MDAxNTcwMDYzODc3MTUw._BV_TOWJd2ohUKY1IRkHspP5DRGtzOZkvKyzxzygyU8g.hELMPfMB6JkxNRWKcvFc5KqDOoZrqWu7xrJn58yLCf4g.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTEwMDNfMjk3/MDAxNTcwMDYzODc3MTUw._BV_TOWJd2ohUKY1IRkHspP5DRGtzOZkvKyzxzygyU8g.hELMPfMB6JkxNRWKcvFc5KqDOoZrqWu7xrJn58yLCf4g.PNG.drv98/image.png?type=w773)

<br>

```sql
EXPLAIN SELECT customer_id FROM customers
ORDER BY state, points;

SHOW STATUS LIKE 'last_query_cost';
```

![https://postfiles.pstatic.net/MjAxOTEwMDNfMTM4/MDAxNTcwMDY0Njk3MjE3.nbdjbWM4xmWGZw87OARFpNPfACGI92ItbpVKR536ZhMg.6J0OmTYWCXx1cKvCfYecMC93wxuAQb_TUC9Z7hPdzT8g.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTEwMDNfMTM4/MDAxNTcwMDY0Njk3MjE3.nbdjbWM4xmWGZw87OARFpNPfACGI92ItbpVKR536ZhMg.6J0OmTYWCXx1cKvCfYecMC93wxuAQb_TUC9Z7hPdzT8g.PNG.drv98/image.png?type=w773)

![https://postfiles.pstatic.net/MjAxOTEwMDNfMjcy/MDAxNTcwMDY0NzIxMDg0.8uIwEQm5EIUEY4FAZIICrlbp8pEUths17Pu2V3qHF6wg.JNcPjQ38r0BJ2lqF7SDi9w2t2esMbp2dhf5yAj5EPHEg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTEwMDNfMjcy/MDAxNTcwMDY0NzIxMDg0.8uIwEQm5EIUEY4FAZIICrlbp8pEUths17Pu2V3qHF6wg.JNcPjQ38r0BJ2lqF7SDi9w2t2esMbp2dhf5yAj5EPHEg.PNG.drv98/image.png?type=w773)

<br>

## **ORDER BY points, state; ( 순서에 영향 )**

![https://postfiles.pstatic.net/MjAxOTEwMDNfODEg/MDAxNTcwMDY0ODkxODIz.or8DvNPFjwnCVU4ASEVuoVQQVGj6xrOImLhGGYG9Ov0g.7mD36lYKFITYQLSCYyq4Sf8ffj7DzsY49pSsn2Uk6mIg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTEwMDNfODEg/MDAxNTcwMDY0ODkxODIz.or8DvNPFjwnCVU4ASEVuoVQQVGj6xrOImLhGGYG9Ov0g.7mD36lYKFITYQLSCYyq4Sf8ffj7DzsY49pSsn2Uk6mIg.PNG.drv98/image.png?type=w773)

<br>

## **ORDER BY state, points DESC;  ( 두개중 하나가 역방향 )**

![https://postfiles.pstatic.net/MjAxOTEwMDNfODEg/MDAxNTcwMDY0ODkxODIz.or8DvNPFjwnCVU4ASEVuoVQQVGj6xrOImLhGGYG9Ov0g.7mD36lYKFITYQLSCYyq4Sf8ffj7DzsY49pSsn2Uk6mIg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTEwMDNfODEg/MDAxNTcwMDY0ODkxODIz.or8DvNPFjwnCVU4ASEVuoVQQVGj6xrOImLhGGYG9Ov0g.7mD36lYKFITYQLSCYyq4Sf8ffj7DzsY49pSsn2Uk6mIg.PNG.drv98/image.png?type=w773)

## **ORDER BY state DESC, points DESC;  (둘다 역방향)**

![https://postfiles.pstatic.net/MjAxOTEwMDNfMjcy/MDAxNTcwMDY0NzIxMDg0.8uIwEQm5EIUEY4FAZIICrlbp8pEUths17Pu2V3qHF6wg.JNcPjQ38r0BJ2lqF7SDi9w2t2esMbp2dhf5yAj5EPHEg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTEwMDNfMjcy/MDAxNTcwMDY0NzIxMDg0.8uIwEQm5EIUEY4FAZIICrlbp8pEUths17Pu2V3qHF6wg.JNcPjQ38r0BJ2lqF7SDi9w2t2esMbp2dhf5yAj5EPHEg.PNG.drv98/image.png?type=w773)

## summary

### **order by 정렬은 CPU 연산등 자원 사용이 큰편**

<br>

### **INDEX ( a , b )**

<br>

### **정렬 a**

### **정렬 a , b**

### **정렬 a DESC, b DESC**

<br>

**Tips) 정렬할 행의 수를 충분히 줄일수 있다면 (WHERE)**

```sql
EXPLAIN SELECT customer_id FROM customers
WHERE state = 'CA'
ORDER BY points;
SHOW STATUS LIKE 'last_query_cost';
```

![https://postfiles.pstatic.net/MjAxOTEwMDNfMTk5/MDAxNTcwMDY3MDI4NTE2.sM3mNZ8VPx4s76MzWSZ0PDq4XW3fpNeTVCQpb_JUAFkg.Ta2OOtuaLzgHh1m-I8b6fjfeqdslYoc6a-rewA_kNjEg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTEwMDNfMTk5/MDAxNTcwMDY3MDI4NTE2.sM3mNZ8VPx4s76MzWSZ0PDq4XW3fpNeTVCQpb_JUAFkg.Ta2OOtuaLzgHh1m-I8b6fjfeqdslYoc6a-rewA_kNjEg.PNG.drv98/image.png?type=w773)

![https://postfiles.pstatic.net/MjAxOTEwMDNfMTQ0/MDAxNTcwMDY3MDU2Njg0.DypV1THMcP3oZq5I907s2P6P8jw4rYsdcNOqs0HgfAAg.etu2ZS-06ocWLep5VPo5QS8wrXs7jeEkjiB7DIcrpM0g.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTEwMDNfMTQ0/MDAxNTcwMDY3MDU2Njg0.DypV1THMcP3oZq5I907s2P6P8jw4rYsdcNOqs0HgfAAg.etu2ZS-06ocWLep5VPo5QS8wrXs7jeEkjiB7DIcrpM0g.PNG.drv98/image.png?type=w773)

