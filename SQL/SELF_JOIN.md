# SELF JOIN ( 자체 조인 )

## sql_hr 데이터베이스의 employees 테이블 확인

```sql
SELECT * FROM sql_hr.employees;
```

![https://postfiles.pstatic.net/MjAxOTA5MTNfMTM5/MDAxNTY4MzQxNzQxOTk2.im7iEmDsH1lBlAlNzuYpI9xvnRGBetntAbMGyhgfRLkg.QN9S3WgRGkJaHj-Du_OJN4Pchge4F5sEw2oyDxG1IE0g.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MTNfMTM5/MDAxNTY4MzQxNzQxOTk2.im7iEmDsH1lBlAlNzuYpI9xvnRGBetntAbMGyhgfRLkg.QN9S3WgRGkJaHj-Du_OJN4Pchge4F5sEw2oyDxG1IE0g.PNG.drv98/image.png?type=w773)

<br>

```sql
SELECT e.employee_id, e.first_name, m.first_name AS manager
FROM employees e
JOIN employees m    ON e.reports_to = m.employee_id
-- e 테이블의 reports_to(매니저)와 m 테이블의 employee_id 가 같음 
-- ON e.employee_id = m.reports_to 로 해서는 안됨
-- ON 기본테이블.외래키 = 참조하는테이블.기본키
```
