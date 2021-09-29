# 서브쿼리

```sql
USE sql_store; -- sql_store 데이터베이스 사용
```

![https://postfiles.pstatic.net/MjAxOTA5MjJfNjkg/MDAxNTY5MTAzNDA1NTI4.ShrSQe4FbxkoDJoxXGscQfYgNkKbrpWKb4lyX1AfNbsg.ZcKw-EWARfRAcuFfTk-Z7eJI2doIH-ye-4gKPtSpwMcg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjJfNjkg/MDAxNTY5MTAzNDA1NTI4.ShrSQe4FbxkoDJoxXGscQfYgNkKbrpWKb4lyX1AfNbsg.ZcKw-EWARfRAcuFfTk-Z7eJI2doIH-ye-4gKPtSpwMcg.PNG.drv98/image.png?type=w773)

products 테이블

<br>

```sql
-- products 테이블
-- product_id 3보다 비싼 가격의 제품을 출력
SELECT *
FROM products
WHERE unit_price > (
	SELECT unit_price 
	FROM products 
	WHERE product_id = 3
);
```

![https://postfiles.pstatic.net/MjAxOTA5MjJfMTYw/MDAxNTY5MTAyOTgzMzM4.8KiGSeIExNJCxq82tAgUHowbV0K5Mxqznyr_peeugGwg.Hl4FQh_MJEk5YaRWzjhDZDRptidETftGXB_DQNCWF4Qg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjJfMTYw/MDAxNTY5MTAyOTgzMzM4.8KiGSeIExNJCxq82tAgUHowbV0K5Mxqznyr_peeugGwg.Hl4FQh_MJEk5YaRWzjhDZDRptidETftGXB_DQNCWF4Qg.PNG.drv98/image.png?type=w773)

