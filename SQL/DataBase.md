# 데이터 베이스와 테이블 만들기

> **IF EXISTS : 있다면**   
> **IF NOT EXISTS : 없다면**   

```sql
CREATE DATABASE IF NOT EXISTS sql_store2;
USE sql_store2;
DROP TABLE IF EXISTS customers;
CREATE TABLE customers
(
		customer_id INT PRIMARY KEY AUTO_INCREMENT,
    이름 VARCHAR(50) NOT NULL,
    포인트 INT NOT NULL DEFAULT 0,
    이메일 VARCHAR(255) NOT NULL UNIQUE
);
```

### **에러없이 계속해서 쿼리문을 실행가능**
