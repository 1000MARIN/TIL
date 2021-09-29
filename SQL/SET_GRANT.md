# 비밀번호 수정 / 권한 부여 / 권한 확인 / 권한 삭제

## **비밀번호 수정**

```sql
SET PASSWORD FOR john = '12345' ;
```

---

<br>

## **권한 부여**

```sql
GRANT 권한 [, 권한, ..]
ON 데이터베이스.테이블
TO 유저이름;
```

<br>

### **1. 데이터베이스를 검색/입력/수정/삭제 권한 부여**

```sql
CREATE USER moon_app IDENTIFIED BY '1234';   -- moon_app 유저 생성

GRANT SELECT, INSERT, UPDATE, DELETE        -- 권한부여
ON sql_store.customers
TO moon_app;
```

![https://postfiles.pstatic.net/MjAxOTEwMDNfMTI4/MDAxNTcwMDk1MTg0Njgw.K3ulXwv2gcyv8amb5i7EeFd91RnfmtmdqgMdohq98Cgg.rOBg4O_HYCSeX3mM1vyFL2EJEooiVp-XNIQmuQdGP6Ig.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTEwMDNfMTI4/MDAxNTcwMDk1MTg0Njgw.K3ulXwv2gcyv8amb5i7EeFd91RnfmtmdqgMdohq98Cgg.rOBg4O_HYCSeX3mM1vyFL2EJEooiVp-XNIQmuQdGP6Ig.PNG.drv98/image.png?type=w773)

<br>

```sql
USE sql_store;
SELECT * FROM customers;
```

![https://postfiles.pstatic.net/MjAxOTEwMDNfMTQx/MDAxNTcwMDk1NDA1NjQw.r3f6hBd5gBKMas-9qQsXDTvcJ3u_pmIms13srHf3uKQg.wLNmwc3ZHnO4TcAPxNvr4eDyi1Il33K_5tG8ZtM7mfsg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTEwMDNfMTQx/MDAxNTcwMDk1NDA1NjQw.r3f6hBd5gBKMas-9qQsXDTvcJ3u_pmIms13srHf3uKQg.wLNmwc3ZHnO4TcAPxNvr4eDyi1Il33K_5tG8ZtM7mfsg.PNG.drv98/image.png?type=w773)

<br> 

### **2. admin 관리자 권한 부여**

![https://postfiles.pstatic.net/MjAxOTEwMDNfMjQx/MDAxNTcwMDk1Njc1NDkz.fqjt6VOjb0YQuoT1q91PmScRPCEKFdDmJdkQUk4U47Eg.Qg0RNaq-ngMtSmOINoIuYwT21UepKEZCjD9HgT4Pvy4g.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTEwMDNfMjQx/MDAxNTcwMDk1Njc1NDkz.fqjt6VOjb0YQuoT1q91PmScRPCEKFdDmJdkQUk4U47Eg.Qg0RNaq-ngMtSmOINoIuYwT21UepKEZCjD9HgT4Pvy4g.PNG.drv98/image.png?type=w773)

MySQL 8.0 Privileges 검색

```sql
GRANT ALL
ON *.*
TO john; -- john 유저에게 모든 권한 부여
```


---

<br>

## **권한 확인**


```sql
SHOW GRANTS FOR john;
```

![https://postfiles.pstatic.net/MjAxOTEwMDNfMjg1/MDAxNTcwMDk1OTU4MTQz.Y7J9swhxl7-rBabpJDQXNA2e73POtYjXiYSEbnl_MWMg.TKLQDfuIdHlArPOBJZQ0A8-RdbF-Wi28UIItEVj0xCsg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTEwMDNfMjg1/MDAxNTcwMDk1OTU4MTQz.Y7J9swhxl7-rBabpJDQXNA2e73POtYjXiYSEbnl_MWMg.TKLQDfuIdHlArPOBJZQ0A8-RdbF-Wi28UIItEVj0xCsg.PNG.drv98/image.png?type=w773)

---

<br>
## **권한 삭제**

<br>

### **권한 부여**

#### moon_app 유저에게 sql_store데이터 베이스에서 테이블등을 만들수 있는

#### CREATE 권한을 부여

```sql
GRANT CREATE
ON sql_store.*
TO moon_app;
```

```sql
CREATE TABLE moon_table(
	id INT
);
```

<br>

## **권한 삭제**

REVOKE 권한 [, 권한, ..]
ON 데이터베이스.테이블
**FROM 유저이름;**

```sql
REVOKE CREATE
ON sql_store.*
FROM moon_app;
```

```sql
REVOKE SELECT, INSERT, UPDATE, DELETE
ON sql_store.*
FROM moon_app;
```
