# DELETE

![https://postfiles.pstatic.net/MjAxOTA5MjFfMjQ5/MDAxNTY5MDI2MjA0Mzk1.hEBbml7XaJrrdu0sT-HDWmerwbh3sI8mfy_u6j2lQNcg.nMLmeQeho2NmRuNCbZ3_dJghOZI7i1HOQG33v7BfFqkg.PNG.drv98/image.png?type=w773](https://postfiles.pstatic.net/MjAxOTA5MjFfMjQ5/MDAxNTY5MDI2MjA0Mzk1.hEBbml7XaJrrdu0sT-HDWmerwbh3sI8mfy_u6j2lQNcg.nMLmeQeho2NmRuNCbZ3_dJghOZI7i1HOQG33v7BfFqkg.PNG.drv98/image.png?type=w773)

서브쿼리를 이용한 행의 삭제

```sql
-- 행을 삭제하기
DELETE FROM invoices
WHERE client_id = (	
	SELECT client_id	
	FROM clients	
	WHERE name = 'Myworks'
);
```
