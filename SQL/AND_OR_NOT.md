# AND, OR , NOT 연산자

## **AND / OR**

```sql
SELECT * 
FROM customers
-- WHERE birth_date > '1990-01-01' AND points > 1000
-- WHERE birth_date > '1990-01-01' OR points > 1000
WHERE birth_date > '1990-01-01' OR points > 1000 AND state = 'VA'
```

```sql
WHERE birth_date > '1990-01-01' OR 
	 ( points > 1000 AND state = 'VA' )
```

## **NOT**

```sql
-- WHERE birth_date > '1990-01-01' OR points > 1000
WHERE NOT ( birth_date > '1990-01-01' OR points > 1000 )/
```
