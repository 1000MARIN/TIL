# LIMIT 절


```sql
SELECT *
FROM customers
LIMIT 3;
-- LIMIT 300
```

![https://postfiles.pstatic.net/MjAxOTA5MTJfMTk4/MDAxNTY4MjYyNjA4NDEx.rno-cI8FcabTs7lhUjGDIcVpbN_CGXrjkVH0tlkTyCQg.hrvDmnWsbEgB5f4_uKaRx3RnDD7jjtBjAsa9FOAakMsg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MTJfMTk4/MDAxNTY4MjYyNjA4NDEx.rno-cI8FcabTs7lhUjGDIcVpbN_CGXrjkVH0tlkTyCQg.hrvDmnWsbEgB5f4_uKaRx3RnDD7jjtBjAsa9FOAakMsg.PNG.drv98/image.png?type=w773)

<br>

**결과값의 6번째 고객부터 9번째 고객까지만 출력한다면?**

```sql
LIMIT 6,3;
```

![https://postfiles.pstatic.net/MjAxOTA5MTJfMjUg/MDAxNTY4MjYyNzc2OTY0.vueFAj-OYgu7PhPbe6cCsgR-j8elbf7E4A_l9g96XFQg.m8UOsUzTjvp3a7Cv_2PdhiX9oTTq9vleErRSog5ilVsg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MTJfMjUg/MDAxNTY4MjYyNzc2OTY0.vueFAj-OYgu7PhPbe6cCsgR-j8elbf7E4A_l9g96XFQg.m8UOsUzTjvp3a7Cv_2PdhiX9oTTq9vleErRSog5ilVsg.PNG.drv98/image.png?type=w773)
