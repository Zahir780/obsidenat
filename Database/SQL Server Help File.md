44# SQL update from one Table to another based on an ID match
```SQL
UPDATE tbEmployeeAttendanceFinal 
SET tbEmployeeAttendanceFinal.vEmployeeCode = b.vEmployeeCode 
FROM tbEmployeeAttendanceFinal a 
INNER JOIN tbEmpOfficialPersonalInfo b 
ON a.vEmployeeID = b.vEmployeeId  
where isnull(a.vUnitName,'')='' 
```
# SQL update Table data with group by data
```SQL
UPDATE tbProductionEntry
SET mTotalAmount = a.TotalAmount
FROM (
    SELECT b.vEmployeeId, SUM(mAmount) AS TotalAmount
    FROM tbProductionEntry b 
	inner join tbEmployeeInfo c on b.vEmployeeId=c.vEmployeeId 
    WHERE c.vDepartmentId like'%' and 
	YEAR(dEntryDate) = YEAR('2023-05-01') AND MONTH(dEntryDate) = MONTH('2023-05-01')
    GROUP BY b.vEmployeeId,YEAR(dEntryDate),MONTH(dEntryDate) 
) AS a 
WHERE tbProductionEntry.vEmployeeId = a.vEmployeeId AND YEAR(tbProductionEntry.dEntryDate) = YEAR('2023-05-01') 
AND MONTH(tbProductionEntry.dEntryDate) = MONTH('2023-05-01')
```
# How to get number with 4 digits
```SQL
SELECT right('0000' + convert(varchar(10), 1), 5) AS Ticket
```
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
# To get last index of "-"
```SQL
DECLARE @value varchar(150) = 'printing-15-25'
SELECT @value, LEN(@value) - CHARINDEX('-', REVERSE(@value)) + 1 AS LastHyphenIndex
```
# To get number with 4 digits
```SQL
SELECT right('0000' + convert(varchar(10), 1), 5) AS 'Ticket'
```
# when Table data without hyphen just number show
---
SELECT  SUBSTRING(vEmployeeCode, CHARINDEX('-', vEmployeeCode) + 1, LEN(vEmployeeCode)) AS EmployeeNumber  FROM  tbEmployeeInfo

#dulicateCheck:
SELECT 
SUBSTRING(vEmployeeCode, CHARINDEX('-', vEmployeeCode) + 1, LEN(vEmployeeCode)) AS EmployeeNumber FROM tbEmployeeInfo GROUP BY SUBSTRING(vEmployeeCode, CHARINDEX('-', vEmployeeCode) + 1, LEN(vEmployeeCode)) HAVING COUNT(*) > 1

# মাল্টিপল টেবিল থেকে ইনার জয়েন দিয়ে ডাটা ডিলিট করার জন্য :
 
উদাহরনঃ

DELETE  a
FROM OTSheet a
INNER JOIN EmployeeInfo b ON a.vEmployeeId = b.vEmployeeId
WHERE a.vMonth = 'august'
AND a.iYear = 2024
AND b.vSR = 'Salary-8'

# Serially ১ বছরের year and Month Order By করার জন্য :

SELECT * 
FROM salary 
WHERE vSR = 'Salary-4' 
AND iYear IN (2014, 2015) 
AND vEmployeeId = 'Emp-814' 
ORDER BY 
iYear, 
DATEPART(MONTH, CAST(CONVERT(VARCHAR, iYear) + '-' + vMonth + '-01' AS DATETIME));

# Year থেকে Date এ Convert করার জন্য


declare @fdate date ,@tdate date

set @fdate ='2023-07-01'  set @tdate ='2024-06-30'

	
	declare @startYear INT = YEAR(@fdate),			@endYear INT = YEAR(@tdate),
	@previousYear Varchar(100),						@presentYear Varchar(100)
	
	
						
	
    
SET @previousYear = CAST(@startYear AS Varchar)			SET @presentYear = CAST(@endYear AS Varchar)

Select  NetPayable = SUM(NetPayable) from  Bonus where  vEmpid = '648'  
And ((iYear = @previousYear AND vMonth IN ('RyjvB', 'AvMó', '‡m‡Þ¤^i', 'A‡±vei', 'b‡f¤^i', 'wW‡m¤^i'))
OR (iYear = @presentYear AND vMonth IN ('Rvbyqvix', '‡deªæqvix', 'gvP©', 'GwcÖj', '‡g', 'Ryb')));

