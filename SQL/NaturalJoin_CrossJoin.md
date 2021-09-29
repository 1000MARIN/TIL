# Natural Join / Cross Join

## Natural Join

```sql
-- natural join
SELECT o.order_id, c.first_name
FROM orders o
NATURAL JOIN customers c;
```

![https://postfiles.pstatic.net/MjAxOTA5MTRfNzMg/MDAxNTY4NDQ3NDY4MzI5.doDy0R9VxRzIsXNYZUnZUAR4WFpd0rEKQ39YPgf9zj8g.IMetsOOnLoQyi3bss1DpgRJHmMTa8i77nDTSYY8bKrog.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MTRfNzMg/MDAxNTY4NDQ3NDY4MzI5.doDy0R9VxRzIsXNYZUnZUAR4WFpd0rEKQ39YPgf9zj8g.IMetsOOnLoQyi3bss1DpgRJHmMTa8i77nDTSYY8bKrog.PNG.drv98/image.png?type=w773)

---

## Cross Join

```sql
-- Cross Join
SELECT c.first_name AS 고객, p.name AS 상품
FROM customers c
CROSS JOIN products p
ORDER BY c.first_name;
```

**모든 고객의 이름과 상품의 이름의 숫자의 곱의 행 생성**

![https://postfiles.pstatic.net/MjAxOTA5MTRfMjAy/MDAxNTY4NDQ3ODc5Mjc3.Q0nUXe_p2awz7Y1Epj5R4BXnwUSEGNFFW-X85VtiSnMg.nJtwxBX27hhQDnWCptqijEGdoNNkeEy6lpoH_TqsufEg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MTRfMjAy/MDAxNTY4NDQ3ODc5Mjc3.Q0nUXe_p2awz7Y1Epj5R4BXnwUSEGNFFW-X85VtiSnMg.nJtwxBX27hhQDnWCptqijEGdoNNkeEy6lpoH_TqsufEg.PNG.drv98/image.png?type=w773)

