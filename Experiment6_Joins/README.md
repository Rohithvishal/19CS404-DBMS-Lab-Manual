# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
<img width="1266" height="907" alt="image" src="https://github.com/user-attachments/assets/2a8304c3-3ba7-4fb6-8128-5791c6a210d1" />


```sql
SELECT 
    customer.cust_name,
    customer.city,
    orders.ord_no,
    orders.ord_date,
    orders.purch_amt as "Order Amount"
FROM 
    customer
LEFT JOIN 
    orders
ON 
    customer.customer_id = orders.customer_id
ORDER BY 
    orders.ord_date ASC;
```

**Output:**

<img width="1270" height="908" alt="image" src="https://github.com/user-attachments/assets/d7186c8e-89c5-47b7-bdc2-c640e580a62b" />


**Question 2**
---
<img width="1290" height="476" alt="image" src="https://github.com/user-attachments/assets/8096c3b2-c04e-4e13-b1b3-5fa560e781f7" />


```sql
SELECT 
    p.*
FROM 
    patients p
INNER JOIN 
    test_results t
ON 
    p.patient_id = t.patient_id
WHERE 
    t.test_name = 'X-Ray'
    AND t.result = 'Normal';
```

**Output:**

<img width="1120" height="216" alt="image" src="https://github.com/user-attachments/assets/d8700c53-1c9d-440e-8de3-01135d20c9ed" />


**Question 3**
---
<img width="1276" height="469" alt="image" src="https://github.com/user-attachments/assets/32281ba5-2b16-488d-8463-be7ca064cdbe" />


```sql
SELECT 
    p.first_name AS patient_name, 
    t.*
FROM 
    patients p
INNER JOIN 
    test_results t
ON 
    p.patient_id = t.patient_id
WHERE 
    t.test_name = 'Blood Pressure';
```

**Output:**

<img width="1241" height="248" alt="image" src="https://github.com/user-attachments/assets/ba352efb-4f0b-435e-a40d-c588c93ac034" />


**Question 4**
---
<img width="1306" height="993" alt="image" src="https://github.com/user-attachments/assets/1311d705-de6f-4e52-81ad-ef0a8407bbac" />

```sql
SELECT 
    c.cust_name,
    c.city,
    o.ord_no,
    o.ord_date,
    o.purch_amt AS "Order Amount",
    s.name,
    s.commission
FROM 
    customer c
LEFT JOIN 
    orders o ON c.customer_id = o.customer_id
LEFT JOIN 
    salesman s ON c.salesman_id = s.salesman_id
```

**Output:**

<img width="1187" height="633" alt="image" src="https://github.com/user-attachments/assets/3789a626-1f03-4bd9-a6d3-e953142cbb84" />


**Question 5**
---
<img width="1292" height="625" alt="image" src="https://github.com/user-attachments/assets/241f432a-f459-4d80-8461-a50e90b19f3f" />


```sql
SELECT 
    p.first_name AS patient_name,
    d.specialization AS Doctor_specialization
FROM 
    patients p
INNER JOIN 
    doctors d
ON 
    p.doctor_id = d.doctor_id
WHERE 
    p.admission_date BETWEEN '2024-01-01' AND '2024-01-31';
```

**Output:**

<img width="635" height="304" alt="image" src="https://github.com/user-attachments/assets/35a655b7-7555-4ced-9635-3db2b1788043" />


**Question 6**
---
<img width="1274" height="520" alt="image" src="https://github.com/user-attachments/assets/02e4e9ca-0f90-4868-8352-318773e5a83f" />

```sql
SELECT c.*
FROM customer c
LEFT JOIN orders o ON c.customer_id = o.customer_id
WHERE o.ord_date BETWEEN '2012-08-01' AND '2012-08-30';
```

**Output:**

<img width="1234" height="341" alt="image" src="https://github.com/user-attachments/assets/a6ac1007-2fa9-49ce-abba-c9262457b4f3" />


**Question 7**
---
<img width="1255" height="777" alt="image" src="https://github.com/user-attachments/assets/1f3a7e6f-88a3-44b5-8754-78cb6a43447f" />


```sql
SELECT 
    c.cust_name,
    c.city,
    c.grade,
    s.name AS Salesman,
    s.city
FROM 
    customer c
INNER JOIN 
    salesman s ON c.salesman_id = s.salesman_id
ORDER BY 
    c.customer_id ASC;
```

**Output:**

<img width="1238" height="705" alt="image" src="https://github.com/user-attachments/assets/834a4883-71db-42ea-b864-6f7ee3e23b98" />


**Question 8**
---
<img width="1258" height="607" alt="image" src="https://github.com/user-attachments/assets/c7684eef-4c06-4325-9bc8-bd50f83107d9" />


```sql
SELECT 
    p.first_name AS patient_name,
    t.test_name
FROM 
    patients p
INNER JOIN 
    test_results t
ON 
    p.patient_id = t.patient_id;
```

**Output:**

<img width="809" height="484" alt="image" src="https://github.com/user-attachments/assets/58233969-b6f7-47db-a289-f82d153b0921" />


**Question 9**
---
<img width="1226" height="568" alt="image" src="https://github.com/user-attachments/assets/6b75b531-4a43-458e-9bab-26376c99458f" />


```sql
SELECT 
    p.*
FROM 
    patients p
INNER JOIN 
    test_results t
ON 
    p.patient_id = t.patient_id
WHERE 
    t.test_date BETWEEN '2024-03-01' AND '2024-03-31';

```

**Output:**

<img width="1070" height="192" alt="image" src="https://github.com/user-attachments/assets/3c1d943c-4195-475b-803c-c7f407f450a7" />


**Question 10**
---
<img width="1187" height="650" alt="image" src="https://github.com/user-attachments/assets/c05fbc0d-a2c2-49eb-a22e-85faaae9e56f" />


```sql
SELECT 
    p.first_name AS patient_name,
    t.*
FROM 
    patients p
INNER JOIN 
    test_results t
ON 
    p.patient_id = t.patient_id
WHERE 
    p.admission_date BETWEEN '2024-01-01' AND '2024-01-31';
```

**Output:**

<img width="1202" height="254" alt="image" src="https://github.com/user-attachments/assets/ede4e0b3-dc45-45cf-979e-ba4b4b61635d" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
