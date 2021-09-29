# 인덱스 만들기

load_1000_customers.sql

[파일 다운로드](https://blogattach.naver.net/3faa239081dddb072bcfaf95a0423a47e5bf4bae1a/20190926_145_blogfile/drv98_1569508977048_IpCE08_sql/load_1000_customers.sql)

### **우선 인덱스를 테스트하기 위해 위의 1000개의 레코드(행)의 데이터를 입력한다.**

<br>

```sql
SELECT customer_id
FROM customers
WHERE state = 'CA';
```

![https://postfiles.pstatic.net/MjAxOTA5MjZfMTM1/MDAxNTY5NTA5MDY2MDE2.VH_c_ex8fJF9HP6obo8GN2kKhsb19Hpz0-OZW6mlpCog.kD1nTu5v3Mo4cUqKc0edB1UxTHmZkEulW33t3NJFVvQg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjZfMTM1/MDAxNTY5NTA5MDY2MDE2.VH_c_ex8fJF9HP6obo8GN2kKhsb19Hpz0-OZW6mlpCog.kD1nTu5v3Mo4cUqKc0edB1UxTHmZkEulW33t3NJFVvQg.PNG.drv98/image.png?type=w773)

```sql
EXPLAIN SELECT customer_id
FROM customers
WHERE state = 'CA';
```

![https://postfiles.pstatic.net/MjAxOTA5MjZfMjEw/MDAxNTY5NTA5MTc1NjQ4.BHFWjFuFECpHWM4SUlbIGDVeSsaV8nETrEfboOciH-wg.m6UANWONiIAdowDsnlAEUD48DVgDeyCpvssp8fFuS44g.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjZfMjEw/MDAxNTY5NTA5MTc1NjQ4.BHFWjFuFECpHWM4SUlbIGDVeSsaV8nETrEfboOciH-wg.m6UANWONiIAdowDsnlAEUD48DVgDeyCpvssp8fFuS44g.PNG.drv98/image.png?type=w773)

type : ALL ( 모든 테이블의 레코드를 검색) ,    rows : 1010 (검색한 행 수)

<br>

# **인덱스 생성**

**인덱스의 이름은 항상 의미있는 이름으로**

**( 좋지 않은 예: idx1, idx2 .... )**

```sql
CREATE INDEX idx_state ON customers (state);
```

```sql
EXPLAIN SELECT customer_id
FROM customers
WHERE state = 'CA';
```

![https://postfiles.pstatic.net/MjAxOTA5MjZfMjgy/MDAxNTY5NTA5NDgwMTY4.lISJxc05aT1CEfgCK8J5jKNUc47Xdtv227RpYYiRoWYg.kJBLjg_wDPhzsWcefouvzOjt7TU2JcYmJrNCEYE-QpEg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjZfMjgy/MDAxNTY5NTA5NDgwMTY4.lISJxc05aT1CEfgCK8J5jKNUc47Xdtv227RpYYiRoWYg.kJBLjg_wDPhzsWcefouvzOjt7TU2JcYmJrNCEYE-QpEg.PNG.drv98/image.png?type=w773)

**type : All => ref (더이상 풀 스캔하지 않음)**

**rows : 1010 => 112 (검색 행)**

