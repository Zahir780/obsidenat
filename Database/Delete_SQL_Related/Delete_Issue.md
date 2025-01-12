# মাল্টিপল টেবিল থেকে ইনার জয়েন দিয়ে ডাটা ডিলিট করার জন্য :
 
উদাহরনঃ

DELETE  a
FROM OTSheet a
INNER JOIN EmployeeInfo b ON a.vEmployeeId = b.vEmployeeId
WHERE a.vMonth = 'august'
AND a.iYear = 2024
AND b.vSR = 'Salary-8'

# How To Delete All Data From All Table
```SQL
EXEC sp_MSForEachTable 'ALTER TABLE ? NOCHECK CONSTRAINT ALL'
GO
EXEC sp_MSForEachTable 'DELETE FROM ?'
GO
-- enable referential integrity again
EXEC sp_MSForEachTable 'ALTER TABLE ? WITH CHECK CHECK CONSTRAINT ALL'
GO
```
# How To Truncate All Data From All Table
```SQL
EXEC sp_MSForEachTable 'ALTER TABLE ? NOCHECK CONSTRAINT ALL'
GO
EXEC sp_MSForEachTable 'TRUNCATE TABLE ?'
GO
-- enable referential integrity again
EXEC sp_MSForEachTable 'ALTER TABLE ? CHECK CONSTRAINT ALL'
GO
```
