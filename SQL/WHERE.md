# WHERE 절

```sql
SELECT * 
FROM customers
WHERE points > 3000
```


>
>=  
<   
<=   
!=   
<>   
>  
---

<br>

### **문자열의 대소문자 구별 X (varchar 형)**

```sql
SELECT * 
FROM customers
-- WHERE state = 'VA'
-- WHERE state = 'va'
WHERE state = 'Va'
```


```sql
SELECT * 
FROM customers
WHERE birth_date > '1990-01-01'
```


