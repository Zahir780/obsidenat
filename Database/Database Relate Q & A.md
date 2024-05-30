1. Consider the following bank database relations, where the primary keys are underlined. 	

	Branch (branch-name(PK), branch-city(PK), assets) 
	Customer (customer-name(PK), customer-street, customer-city) 
	Loan (loan-number(PK), branch-name(PK), amount) 
	Borrower (customer-name(PK), loan-number) 
	Account (account-number(PK), branch-name, balance) 
	Depositor (customer-name(PK), account number) 

* Write down the SQL expressions for the following queries. 

i. Find all customers who have account but no loan in bank. 
```sql
SELECT DISTINCT c.customer_name
FROM Customer c
JOIN Depositor d ON c.customer_name = d.customer_name
LEFT JOIN Borrower b ON c.customer_name = b.customer_name
WHERE b.loan_number IS NULL;
```
ii. Delete all loan amount between 10000/- and 25000/- 
```sql
DELETE FROM Loan
WHERE amount BETWEEN 10000 AND 25000;
```
iii. Find the names of all customers who have a loan at Perryridge branch. 
```sql
SELECT DISTINCT c.customer_name
FROM Customer c
JOIN Borrower b ON c.customer_name = b.customer_name
JOIN Loan l ON b.loan_number = l.loan_number
WHERE l.branch_name = 'Perryridge';
```
iv. Delete all loans with amount in the range 0 to 500. 
```sql
DELETE FROM Loan
WHERE amount BETWEEN 0 AND 500;
```

2. Consider the employee database consisting of the following relations, where the primary keys are underlined. 

	Employee (emplovee-id(PK), employee-name, street, city) 
	Works (emplovee-id(PK), company-name, salary) 
	Company (company-name(PK), city) 
	Manager (employee-id(PK), manager-name) 

* Write down the SQL expressions for the following queries: 

i. Find the company that has the most employees. 
```sql
SELECT TOP 1 w.company_name
FROM Works w
GROUP BY w.company_name
ORDER BY COUNT(w.emplovee_id) DESC;
```
ii. Find the average salaries at each company. 
```sql
SELECT w.company_name, AVG(w.salary) AS average_salary
FROM Works w
GROUP BY w.company_name;
```
iii. Find all employees who live in Barisal city, but their company is not in Barisal. 
```sql
SELECT e.employee_name
FROM Employee e
JOIN Works w ON e.emplovee_id = w.emplovee_id
JOIN Company c ON w.company_name = c.company_name
WHERE e.city = 'Barisal' AND c.city <> 'Barisal';
```
iv. Find the names of all employees who work for First Bank Corporation. 
```sql
SELECT e.employee_name
FROM Employee e
JOIN Works w ON e.emplovee_id = w.emplovee_id
WHERE w.company_name = 'First Bank Corporation';
```

3. Consider the banking database consisting of the banking database consisting of the following tables, where the primary keys are underlined. 

	Branch (branch-name(PK), branch-city, assets) 
	Customer (customer-name(PK), customer-street, customer-city) 
	Loan-account (loan-number(PK), branch-name, amount) 
	Borrower (customer-name(PK), loan-number) 
	Saving-account (account number(PK), branch-name, balance) 
	Depositor (customer-name(PK), account number(PK)) 

* Write down the SQL expressions for the following queries: 

i. Find all customers of the bank who have both loan and a saving account. 
```sql
SELECT DISTINCT c.customer_name
FROM Customer c
JOIN Borrower b ON c.customer_name = b.customer_name
JOIN Depositor d ON c.customer_name = d.customer_name;
```
ii. Find all average account balance at each branch. 
```sql
SELECT s.branch_name, AVG(s.balance) AS average_balance
FROM Saving_account s
GROUP BY s.branch_name;
```
iii. Deduct 3% service charge from saving account balance that have both loan and a saving account otherwise deduct 5% service charge from saving account balarnice. 
```sql
UPDATE Saving_account
SET balance = balance * CASE 
    WHEN EXISTS (
        SELECT 1 
        FROM Borrower b
        JOIN Depositor d ON b.customer_name = d.customer_name
        WHERE d.account_number = Saving_account.account_number
    ) THEN 0.97
    ELSE 0.95
END;
```

4. Consider the employee database consisting of the following tables, where the primary keys are underlined. 

	Employee (employee-name(PK), street, city) 
	Works (emplovee-name(PK), company-name(PK), salary) 
	Company (company-name(PK), city) 
	Manages (employee-name(PK), manages-name) 

* Write down the SQL expressions for the following queries: 

i. Find the names, cities and salaries of all employees who work for IFIC Bank Ltd. 
```sql
SELECT e.employee_name, e.city, w.salary
FROM Employee e
JOIN Works w ON e.employee_name = w.emplovee_name
WHERE w.company_name = 'IFIC Bank Ltd';
```
ii. Find the total salaries of each company.
```sql
SELECT w.company_name, SUM(w.salary) AS total_salary
FROM Works w
GROUP BY w.company_name;
```
iii. Give all employees of First Bank Corporation a 20 percent salary raise. 
```sql
UPDATE Works
SET salary = salary * 1.20
WHERE company_name = 'First Bank Corporation';
```
iv. Find the names of all employees in this database who do not work for First Bank Corporation. 
```sql
SELECT e.employee_name
FROM Employee e
WHERE e.employee_name NOT IN (
    SELECT w.emplovee_name
    FROM Works w
    WHERE w.company_name = 'First Bank Corporation'
);
```

5. Consider the following schemas for "car_insurance" database relations, where the primary keys are underlined. 

	Person (driver-id(PK), name, address) 
	Car (license(PK), model, year) 
	Accident (report-number(PK), date, location) 
	Owns (driver-id(PK), license(PK)) 
	Participate (driver-id(PK), car(PK), report-number(PK), damage amount) 

* Write down the SQL expressions for the following queries: 

i. Add a new accident to the database (assume any values for required attributes). 
```sql
INSERT INTO Accident (report_number, date, location)
VALUES ('AR1234', '2024-05-19', 'Dhaka');
```
ii. Delete the Toyota belonging to "Simanto". 
```sql
DELETE FROM Car
WHERE license IN (
    SELECT c.license
    FROM Car c
    JOIN Owns o ON c.license = o.license
    JOIN Person p ON o.driver_id = p.driver_id
    WHERE p.name = 'Simanto' AND c.model = 'Toyota'
);
```
iii. Find the total number of people who owned cars that were involved in accidents in 2020. 
```sql
SELECT COUNT(DISTINCT p.driver_id) AS total_people
FROM Person p
JOIN Owns o ON p.driver_id = o.driver_id
JOIN Participate pa ON o.license = pa.car
JOIN Accident a ON pa.report_number = a.report_number
WHERE YEAR(a.date) = 2020;
```
iv. Update the damage amount for the car with license number "DHAKA 4000" in the accident with report number "AR 2197" to 30,000/-.
```sql
UPDATE Participate
SET damage_amount = 30000
WHERE car = 'DHAKA 4000' AND report_number = 'AR 2197';
```