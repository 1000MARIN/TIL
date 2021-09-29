# 상호연관 서브쿼리

### **sql_hr 에서**

### **직원(employee)들의 월급(salary)이 현재 직원이 소속된 부서(office_id)의 평균보다 높은 직원들만 출력하라.**

<br>

```sql
SELECT *
FROM employees e
WHERE salary > (
	SELECT AVG(salary)
    FROM employees
    WHERE office_id = e.office_id
);
```

<br>

### **1. 메인쿼리에서 직원을 한명 검색하고**

### **2. 서브쿼리 안의 where 절에서 e.office_id 는 메인쿼리의 현재 검색되고 있는 직원의 office_id 의 평균 월급을 계산해서 비교해 준다.**

### **3. 그러므로 이 서브쿼리는 한번만 실행되는것이 아니라, 직원한명씩 검색할때 마다 직원의 office_id에 따라 여러번 실행되어 비교한다.**
