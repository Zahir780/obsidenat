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

# Year থেকে Date এ Convert করার জন্য(Fiscal Year অনুযায়ী)


declare @fdate date ,@tdate date

set @fdate ='2023-07-01'  set @tdate ='2024-06-30'

	
	declare @startYear INT = YEAR(@fdate),			@endYear INT = YEAR(@tdate),
	@previousYear Varchar(100),						@presentYear Varchar(100)
	
	
						
	
    
SET @previousYear = CAST(@startYear AS Varchar)			SET @presentYear = CAST(@endYear AS Varchar)

Select  NetPayable = SUM(NetPayable) from  Bonus where  vEmpid = '648'  
And ((iYear = @previousYear AND vMonth IN ('RyjvB', 'AvMó', '‡m‡Þ¤^i', 'A‡±vei', 'b‡f¤^i', 'wW‡m¤^i'))
OR (iYear = @presentYear AND vMonth IN ('Rvbyqvix', '‡deªæqvix', 'gvP©', 'GwcÖj', '‡g', 'Ryb')));

# Year থেকে Date এ Convert করার জন্য(যে কোন date to date select এর জন্য )


 
 
 declare @fdate date, @tdate date
 
 set @fdate ='2023-01-01'
 set @tdate ='2023-12-31'
 
 
 
 
  select NetPayable= ISNULL(SUM(mBonus) ,0) from 
  (
     select *,case when 
			vMonth='‡g' then CAST(iYear  as varchar(120))+'-05-31'  when --may
			vMonth='AvMó' then CAST(iYear  as varchar(120))+'-08-31' when-- august
			vMonth='A‡±vei' then CAST(iYear  as varchar(120))+'-10-31' when--october
			vMonth='Ryb' then CAST(iYear  as varchar(120))+'-06-30' when--june
			vMonth='‡m‡Þ¤^i' then CAST(iYear  as varchar(120))+'-09-30' when--september
			vMonth='RyjvB' then CAST(iYear  as varchar(120))+'-07-31' when--july
			vMonth='b‡f¤^i' then CAST(iYear  as varchar(120))+'-11-30' when--november
			vMonth='‡deªæqvix' then CAST(iYear  as varchar(120))+'-02-28' when--feb
			vMonth='GwcÖj' then CAST(iYear  as varchar(120))+'-04-30' when--april
			vMonth='Rvbyqvix' then CAST(iYear  as varchar(120))+'-01-31' when---january
			vMonth='wW‡m¤^i' then CAST(iYear  as varchar(120))+'-12-31' when--december
			vMonth='gvP©' then CAST(iYear  as varchar(120))+'-03-31'---March
  else 
		'2000-01-01' 
		end as generateDate  
		from Bonus 
		where vEmpID='112'
  
  )  
  as temp 
where generateDate between @fdate and  @tdate

==অথবা==

DECLARE @fdate DATE = '2023-01-01';
DECLARE @tdate DATE = '2023-12-31';

SELECT NetPayable = ISNULL(SUM(mBonus), 0)
FROM (
    SELECT *, 
        generateDate = CASE vMonth
            WHEN '‡g' THEN DATEADD(MONTH, 4, CAST(iYear AS VARCHAR(4)) + '-01-01')  -- May 31
            WHEN 'AvMó' THEN DATEADD(MONTH, 7, CAST(iYear AS VARCHAR(4)) + '-01-01')  -- August 31
            WHEN 'A‡±vei' THEN DATEADD(MONTH, 9, CAST(iYear AS VARCHAR(4)) + '-01-01')  -- October 31
            WHEN 'Ryb' THEN DATEADD(MONTH, 5, CAST(iYear AS VARCHAR(4)) + '-01-01')  -- June 30
            WHEN '‡m‡Þ¤^i' THEN DATEADD(MONTH, 8, CAST(iYear AS VARCHAR(4)) + '-01-01')  -- September 30
            WHEN 'RyjvB' THEN DATEADD(MONTH, 6, CAST(iYear AS VARCHAR(4)) + '-01-01')  -- July 31
            WHEN 'b‡f¤^i' THEN DATEADD(MONTH, 10, CAST(iYear AS VARCHAR(4)) + '-01-01')  -- November 30
            WHEN '‡deªæqvix' THEN DATEADD(MONTH, 1, CAST(iYear AS VARCHAR(4)) + '-01-01')  -- February 28
            WHEN 'GwcÖj' THEN DATEADD(MONTH, 3, CAST(iYear AS VARCHAR(4)) + '-01-01')  -- April 30
            WHEN 'Rvbyqvix' THEN CAST(iYear AS VARCHAR(4)) + '-01-31'  -- January 31
            WHEN 'wW‡m¤^i' THEN CAST(iYear AS VARCHAR(4)) + '-12-31'  -- December 31
            WHEN 'gvP©' THEN DATEADD(MONTH, 2, CAST(iYear AS VARCHAR(4)) + '-01-01')  -- March 31
            ELSE '2000-01-01'  -- Default date
        END
    FROM Bonus
    WHERE vEmpID = '112'
) AS temp
WHERE generateDate BETWEEN @fdate AND @tdate;
