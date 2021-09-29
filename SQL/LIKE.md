# LIKE 연산자


```sql
SELECT *
FROM customers
WHERE last_name LIKE 'b%'
```

![https://postfiles.pstatic.net/MjAxOTA5MTJfMzIg/MDAxNTY4MjU0ODA1MjA4.zmqpyhaBJpmmkXWvkK3LPMd4JxZTvZn7_anH22oE_a0g.QO3icmbojKRPq2g3B4KGcBuS5cvmwFpGf7G7QPEmBawg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MTJfMzIg/MDAxNTY4MjU0ODA1MjA4.zmqpyhaBJpmmkXWvkK3LPMd4JxZTvZn7_anH22oE_a0g.QO3icmbojKRPq2g3B4KGcBuS5cvmwFpGf7G7QPEmBawg.PNG.drv98/image.png?type=w773)

```sql
WHERE last_name LIKE '%b%'
```

![https://postfiles.pstatic.net/MjAxOTA5MTJfMTE0/MDAxNTY4MjU0OTIxNTQ1.jyeGWr2NCHFuh5zue7F4-orIKnvhGyiRIa2errethocg.nWYhJ-LfG-qXM6BCtZWBEIMXtY39Vl-QkxC5u9TU814g.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MTJfMTE0/MDAxNTY4MjU0OTIxNTQ1.jyeGWr2NCHFuh5zue7F4-orIKnvhGyiRIa2errethocg.nWYhJ-LfG-qXM6BCtZWBEIMXtY39Vl-QkxC5u9TU814g.PNG.drv98/image.png?type=w773)

```sql
WHERE last_name LIKE '%y'
```

![https://postfiles.pstatic.net/MjAxOTA5MTJfMjQw/MDAxNTY4MjU1MDAwODcy.U4HoqEQaETGByOAScz4faelERwunNQuXuUW0O1Cvx9gg.qcVN-hi3VoT28xzI0W3zkA0UpnIvcuU7hV79MsqVvVQg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MTJfMjQw/MDAxNTY4MjU1MDAwODcy.U4HoqEQaETGByOAScz4faelERwunNQuXuUW0O1Cvx9gg.qcVN-hi3VoT28xzI0W3zkA0UpnIvcuU7hV79MsqVvVQg.PNG.drv98/image.png?type=w773)

```sql
WHERE last_name LIKE '_____y'
-- 끝의 y앞의 5개의 자리(_)
-- % : 자리수에 상관없음   _ : 개수만큼의 정확한 자리수
```

![https://postfiles.pstatic.net/MjAxOTA5MTJfMjIx/MDAxNTY4MjU1MTc0MzUz.iw6nxKBg-u1qYE49VAUhRKKCnNlBI4H281YfQSsBr2Qg.JhoUcbbjr0UVwzcxjl-7OM22V29dglwP0TUBDf0zhNwg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MTJfMjIx/MDAxNTY4MjU1MTc0MzUz.iw6nxKBg-u1qYE49VAUhRKKCnNlBI4H281YfQSsBr2Qg.JhoUcbbjr0UVwzcxjl-7OM22V29dglwP0TUBDf0zhNwg.PNG.drv98/image.png?type=w773)
