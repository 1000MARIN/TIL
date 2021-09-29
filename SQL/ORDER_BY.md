# ORDER BY 절

```sql
SELECT *
FROM customers;
```

![https://postfiles.pstatic.net/MjAxOTA5MTJfMTI5/MDAxNTY4MjYxMzU5NjM1.wLo9ECTAGEn8Vdc2c5olF0BvxRfsRyqMDdrpShdSIWMg.7u-GBcVXjpM9T9FBzHXaOabhCtdZFGZASgYYEypzbtEg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MTJfMTI5/MDAxNTY4MjYxMzU5NjM1.wLo9ECTAGEn8Vdc2c5olF0BvxRfsRyqMDdrpShdSIWMg.7u-GBcVXjpM9T9FBzHXaOabhCtdZFGZASgYYEypzbtEg.PNG.drv98/image.png?type=w773)

![https://postfiles.pstatic.net/MjAxOTA5MTJfNDIg/MDAxNTY4MjYxMzM2NzIz.x-d1raIWgQyEWwqkQJelCgtjVrufCcKDpo4GJ4VPz7Yg.wlj5mR3xMBSDqQoWu5ZOt8QKnivYO6e4kqftSU-yQOsg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MTJfNDIg/MDAxNTY4MjYxMzM2NzIz.x-d1raIWgQyEWwqkQJelCgtjVrufCcKDpo4GJ4VPz7Yg.wlj5mR3xMBSDqQoWu5ZOt8QKnivYO6e4kqftSU-yQOsg.PNG.drv98/image.png?type=w773)

![https://postfiles.pstatic.net/MjAxOTA5MTJfOTgg/MDAxNTY4MjYxOTk1NzI2.EkxbPuXcuu8LPMJrxLnkMLnbUdCbkwAUpSK1WNHRUd4g.ktxXWUANhw2cQrSVqm7Ix-scVxp3hyKpAZTqPYj7VnEg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MTJfOTgg/MDAxNTY4MjYxOTk1NzI2.EkxbPuXcuu8LPMJrxLnkMLnbUdCbkwAUpSK1WNHRUd4g.ktxXWUANhw2cQrSVqm7Ix-scVxp3hyKpAZTqPYj7VnEg.PNG.drv98/image.png?type=w773)

<br>

```sql
SELECT customer_id, first_name, last_name, state
FROM customers
ORDER BY state, first_name;
```

![https://postfiles.pstatic.net/MjAxOTA5MTJfODEg/MDAxNTY4MjYxOTU3MzE4.BQh0GXwRrGhAuDYKKCJJtagzS2PW8jRDc0RZFpoa488g.D6UwZ3pfkAhqIpI7-xuqeL1B7vuubZatIjUovVBPrXYg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MTJfODEg/MDAxNTY4MjYxOTU3MzE4.BQh0GXwRrGhAuDYKKCJJtagzS2PW8jRDc0RZFpoa488g.D6UwZ3pfkAhqIpI7-xuqeL1B7vuubZatIjUovVBPrXYg.PNG.drv98/image.png?type=w773)
