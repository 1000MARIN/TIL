# REGEXP(레귤러 익스프레션) 연산자

<br>

## 특정 문자 포함 문자열 검색

```sql
SELECT *
FROM customers
-- WHERE last_name LIKE '%field%'
WHERE last_name REGEXP 'field'
```

![https://postfiles.pstatic.net/MjAxOTA5MTJfMjU1/MDAxNTY4MjU2Nzg3NDQy.B0im213dqk9926F-6XzGSNNPCeVWR7fei6KapID8f-Ig.yw3A67RMzDqGKXtuhsSUUcxbUYoTh9ycXUyh5_ypvnMg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MTJfMjU1/MDAxNTY4MjU2Nzg3NDQy.B0im213dqk9926F-6XzGSNNPCeVWR7fei6KapID8f-Ig.yw3A67RMzDqGKXtuhsSUUcxbUYoTh9ycXUyh5_ypvnMg.PNG.drv98/image.png?type=w773)

<br>


## 시작하는 문자열로 검색 : ^ + 시작하는 문자열

```sql
WHERE last_name REGEXP '^b'
WHERE last_name REGEXP '^brush'
```

![https://postfiles.pstatic.net/MjAxOTA5MTJfMTE1/MDAxNTY4MjU2OTQzMzIy.lXrCD2_mOOgB11tjuYakPRw1HdrMs2ro809wcyd7QzMg.4QvCoQ4TqAyPZhaDVgYZKVYo2sQyAP4E8iTN6rXajQsg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MTJfMTE1/MDAxNTY4MjU2OTQzMzIy.lXrCD2_mOOgB11tjuYakPRw1HdrMs2ro809wcyd7QzMg.4QvCoQ4TqAyPZhaDVgYZKVYo2sQyAP4E8iTN6rXajQsg.PNG.drv98/image.png?type=w773)

<br>


## 끝나는 문자열로 검색 : 끝나는 문자열 + $

```sql
WHERE last_name REGEXP 'ey$'
```

![https://postfiles.pstatic.net/MjAxOTA5MTJfMjMy/MDAxNTY4MjU3MTg1ODkz.SDZng1C2wvq7GlnZc1BWQSjU-CnJtrMHvboC7SCB1b0g.Dv6RyDXhBtOZjYDiwbH2yWzk6FcbJJ__Ey01wgtIungg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MTJfMjMy/MDAxNTY4MjU3MTg1ODkz.SDZng1C2wvq7GlnZc1BWQSjU-CnJtrMHvboC7SCB1b0g.Dv6RyDXhBtOZjYDiwbH2yWzk6FcbJJ__Ey01wgtIungg.PNG.drv98/image.png?type=w773)


<br>



## 여러개의 문자열중 하나라도 포함할때 : ' 문자 | 문자 '

```sql
WHERE last_name REGEXP 'field|mac'
```

![https://postfiles.pstatic.net/MjAxOTA5MTJfMTcx/MDAxNTY4MjU3NDkxMjAx.TecwZ3WZEUHe6Nc2fm1f7k247hawf4DDpN8aRm3-tDkg.Nb7b0vj-IcL46XtY5Gt88r-JWioguk9CBKAgytrzop8g.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MTJfMTcx/MDAxNTY4MjU3NDkxMjAx.TecwZ3WZEUHe6Nc2fm1f7k247hawf4DDpN8aRm3-tDkg.Nb7b0vj-IcL46XtY5Gt88r-JWioguk9CBKAgytrzop8g.PNG.drv98/image.png?type=w773)

```sql
WHERE last_name REGEXP 'ey$|rose|^b'
```

![https://postfiles.pstatic.net/MjAxOTA5MTJfOTcg/MDAxNTY4MjU3NzU5Nzkx.zBhAVX5CxDVAUOE01OzJ8H_yIBXoLFLP5J7KlGXdiDkg.enC5YXTc9oOrBT6tUNHkPrg7-C92TZ9kdVwdNBofaOYg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MTJfOTcg/MDAxNTY4MjU3NzU5Nzkx.zBhAVX5CxDVAUOE01OzJ8H_yIBXoLFLP5J7KlGXdiDkg.enC5YXTc9oOrBT6tUNHkPrg7-C92TZ9kdVwdNBofaOYg.PNG.drv98/image.png?type=w773)

<br>


## 문자의 조합으로 검색 : [ 문자 ]문자

```sql
WHERE last_name REGEXP '[gim]e'
-- ge , ie, me 검색
```

![https://postfiles.pstatic.net/MjAxOTA5MTJfMjcx/MDAxNTY4MjU4OTIyODUy.INtwU6gOsIY3B2Oynoujoqb2SjC1wzdGbptASaPPZhIg.T8dEl6iDfqxOYEOLxLBMiw-shjgPyZJz095eZ_G45iog.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MTJfMjcx/MDAxNTY4MjU4OTIyODUy.INtwU6gOsIY3B2Oynoujoqb2SjC1wzdGbptASaPPZhIg.T8dEl6iDfqxOYEOLxLBMiw-shjgPyZJz095eZ_G45iog.PNG.drv98/image.png?type=w773)

```sql
WHERE last_name REGEXP 'a[a-h]'
-- aa, ab, ac, ad, ae ... ah 검색
```

![https://postfiles.pstatic.net/MjAxOTA5MTJfMjc1/MDAxNTY4MjU5MjM4MDYy.MkmYMbaHDcsX_K-hz1QIuV4Nv-SBKdvK__hdKcejHTcg.ErJua1P9swHqHhgMK835e--QHB9DKhChq-chjz2fNogg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MTJfMjc1/MDAxNTY4MjU5MjM4MDYy.MkmYMbaHDcsX_K-hz1QIuV4Nv-SBKdvK__hdKcejHTcg.ErJua1P9swHqHhgMK835e--QHB9DKhChq-chjz2fNogg.PNG.drv98/image.png?type=w773)

