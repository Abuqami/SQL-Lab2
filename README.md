# SQL-Lab2

# We will use the Employees and Awards table below:

 <img src="Lab2.png" width="500" height="500">

### Q1: Choose all employees who have received an award (Nested Query)?
Query:
```SQL
SELECT * FROM employee
WHERE id IN (
SELECT employee_id FROM awards
);
```

Output:
 ![Q1](Q1.png)

### Q2: Choose all employees who have never received an award (Nested Query)?
Query:
```SQL
SELECT * FROM employee
WHERE id NOT IN (
SELECT employee_id FROM awards
); 
```
Output:
![Q2](Q2.png)
 
### Q3: Choose all Developers who make more than all Managers combined (Nested Query)?
Query:
```SQL
SELECT * from employee
WHERE role = 'Developer' AND salary > (
SELECT max(salary) FROM employee
  WHERE role = 'Manager'
);
```

Output:
![Q3](Q3.png)

 
### Q4: Choose all Developers who make more money than any Manager (Nested Query)?
Query:
```SQL
SELECT * from employee
WHERE role = 'Developer' AND salary > (
SELECT salary FROM employee
  WHERE role = 'Manager'
);
```

Output:
![Q4](Q4.png)

 
### Q5: Choose all employees whose salaries are higher than the average for their position. (Nested Query)?
Query:
```SQL
SELECT * FROM employee emp
WHERE salary > (
SELECT avg(salary) FROM employee
  WHERE role = emp.role
);
```

Output:
![Q5](Q5.png)
