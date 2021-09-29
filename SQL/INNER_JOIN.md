# INNER JOIN( 내부 조인 )

![https://postfiles.pstatic.net/MjAxOTA5MTJfMTEy/MDAxNTY4Mjc1NjE1NzAz.jdQW0JzZBJvQhoxAtGU4-CBYLEBOPMy644EzXzKk2u4g.HdIlxM2ApOplOylKVlg_n8cUezFi79kKP8hdXlLy5u8g.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MTJfMTEy/MDAxNTY4Mjc1NjE1NzAz.jdQW0JzZBJvQhoxAtGU4-CBYLEBOPMy644EzXzKk2u4g.HdIlxM2ApOplOylKVlg_n8cUezFi79kKP8hdXlLy5u8g.PNG.drv98/image.png?type=w773)

```sql
SELECT *
FROM orders o
JOIN customers c 
	ON o.customer_id = c.customer_id;
```

![https://postfiles.pstatic.net/MjAxOTA5MTJfMTYz/MDAxNTY4Mjc1NTQ2NjA3.JmhWSJAebASm_O0qIbjnYgzpTC7srzzwZdFfndUiFTIg.kOCLAvzjE0qpXRNkxDrU3rkweTFoAAJWUTbf7SzKXHMg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MTJfMTYz/MDAxNTY4Mjc1NTQ2NjA3.JmhWSJAebASm_O0qIbjnYgzpTC7srzzwZdFfndUiFTIg.kOCLAvzjE0qpXRNkxDrU3rkweTFoAAJWUTbf7SzKXHMg.PNG.drv98/image.png?type=w773)

<br>

```sql
SELECT o.order_id, o.customer_id, o.order_date, c.first_name, c.last_name
FROM orders o
JOIN customers c 
	ON o.customer_id = c.customer_id
```

![https://postfiles.pstatic.net/MjAxOTA5MTJfNDEg/MDAxNTY4Mjc1ODMzMjQx.oky1ZSggbyctarJxyDbWy2gfbJlGg8EmLc2EiuSXn8Eg.qUkqpsUJM9CuSgTthAmJmCbu4q4ap7WcnB4iw7c_nUkg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MTJfNDEg/MDAxNTY4Mjc1ODMzMjQx.oky1ZSggbyctarJxyDbWy2gfbJlGg8EmLc2EiuSXn8Eg.qUkqpsUJM9CuSgTthAmJmCbu4q4ap7WcnB4iw7c_nUkg.PNG.drv98/image.png?type=w773)

