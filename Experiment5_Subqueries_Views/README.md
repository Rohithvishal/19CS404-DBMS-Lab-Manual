# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
--
<img width="1192" height="662" alt="image" src="https://github.com/user-attachments/assets/a63ada99-25e1-4676-9684-84e3f72bec21" />


```sql
SELECT student_name, grade
FROM GRADES
WHERE grade = (
    SELECT MIN(grade)
    FROM GRADES g2
    WHERE g2.subject = GRADES.subject
);

```

**Output:**

<img width="846" height="437" alt="image" src="https://github.com/user-attachments/assets/d3251f26-1d22-43f7-bb36-d8e4c2399a86" />


**Question 2**
---
<img width="1198" height="793" alt="image" src="https://github.com/user-attachments/assets/958b77f1-cf6c-4253-929d-89be0eb413f1" />


```sql
SELECT o.ord_no, o.purch_amt, o.ord_date, o.customer_id, o.salesman_id
FROM ORDERS o
JOIN SALESMAN s ON o.salesman_id = s.salesman_id
WHERE s.city = 'New York';

```

**Output:**

<img width="1187" height="431" alt="image" src="https://github.com/user-attachments/assets/e05ffe77-649e-4992-a95d-f1c368563400" />


**Question 3**
---
<img width="1047" height="681" alt="image" src="https://github.com/user-attachments/assets/626b277b-7aef-4de9-a707-4a89b4bb03f8" />


```sql
SELECT *
FROM CUSTOMERS
WHERE SALARY > 1500;
```

**Output:**

<img width="1346" height="551" alt="image" src="https://github.com/user-attachments/assets/ece1bf25-86b1-4a8c-81d1-a2f407326f37" />


**Question 4**
---
<img width="1167" height="570" alt="image" src="https://github.com/user-attachments/assets/77a527d6-beec-4a14-9573-ea6cbe17049e" />


```sql
SELECT *
FROM GRADES
WHERE grade = (
    SELECT MAX(grade)
    FROM GRADES g2
    WHERE g2.subject = GRADES.subject
);
```

**Output:**

<img width="1237" height="411" alt="image" src="https://github.com/user-attachments/assets/11db83e5-41db-46e2-8768-ca17b6c9766f" />


**Question 5**
---
<img width="1207" height="629" alt="image" src="https://github.com/user-attachments/assets/d264d560-c79d-42bc-8723-2b3247ad5959" />


```sql
SELECT o.ord_no, o.purch_amt, o.ord_date, o.customer_id, o.salesman_id
FROM Orders o
JOIN Salesman s ON o.salesman_id = s.salesman_id
WHERE s.city = 'New York';
```

**Output:**
<img width="1238" height="424" alt="image" src="https://github.com/user-attachments/assets/8aad1aaf-5515-4d3d-8a83-d85981749916" />


**Question 6**
---
<img width="1122" height="490" alt="image" src="https://github.com/user-attachments/assets/30cb1402-84ed-4904-a534-f847d22d06a2" />

```sql
SELECT *
FROM customer
WHERE city <> (
    SELECT city
    FROM customer
    WHERE id = (SELECT MAX(id) FROM customer)
);
```

**Output:**

<img width="1217" height="393" alt="image" src="https://github.com/user-attachments/assets/5be09227-edd8-4a40-8e77-febc0a055a68" />


**Question 7**
---
<img width="1225" height="452" alt="image" src="https://github.com/user-attachments/assets/5bc295c6-0926-4cb2-ae30-138004025139" />

```sql
SELECT grade, COUNT(*)
FROM customer
GROUP BY grade
HAVING grade >
    (SELECT AVG(grade)
     FROM customer
     WHERE city = 'New York');
```

**Output:**

<img width="703" height="297" alt="image" src="https://github.com/user-attachments/assets/e19bca5d-40cd-4427-80f1-e06839ecd11b" />


**Question 8**
---
<img width="848" height="571" alt="image" src="https://github.com/user-attachments/assets/1553531b-eb33-43d3-8df5-62765eb4db6e" />


```sql
SELECT *
FROM CUSTOMERS
WHERE ADDRESS = 'Delhi';
```

**Output:**
<img width="1117" height="286" alt="image" src="https://github.com/user-attachments/assets/7feb057d-ee0f-45d5-bcd1-83b17a330a27" />


**Question 9**
---
<img width="1173" height="575" alt="image" src="https://github.com/user-attachments/assets/1bb6a6da-a892-47e6-a4d5-02ac35a078cb" />


```sql
SELECT o.ord_no, o.purch_amt, o.ord_date, o.customer_id, o.salesman_id
FROM Orders o
JOIN Salesman s ON o.salesman_id = s.salesman_id
WHERE s.city = 'London';
```

**Output:**

<img width="1168" height="363" alt="image" src="https://github.com/user-attachments/assets/d07dc15e-7b42-4671-bfa6-2281e51eb62f" />


**Question 10**
---
<img width="981" height="605" alt="image" src="https://github.com/user-attachments/assets/337cde03-a8ca-415d-a256-ce8e0c48cee3" />


```sql
SELECT commission 
FROM salesman 
WHERE salesman_id IN 
(SELECT salesman_id FROM customer WHERE city = 'Paris');
```

**Output:**

<img width="612" height="305" alt="image" src="https://github.com/user-attachments/assets/69d89d5b-b3c7-4408-b045-7db072b4b71a" />



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
