# SQL update from one Table to another based on an ID match
```
UPDATE tbEmployeeAttendanceFinal 
SET tbEmployeeAttendanceFinal.vEmployeeCode = b.vEmployeeCode 
FROM tbEmployeeAttendanceFinal a 
INNER JOIN tbEmpOfficialPersonalInfo b 
ON a.vEmployeeID = b.vEmployeeId  
where isnull(a.vUnitName,'')='' 
```
# SQL update Table data with group by data
```
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
```
SELECT right('0000' + convert(varchar(10), 1), 5) AS Ticket
```
# How To Delete All Data From All Table
```
EXEC sp_MSForEachTable 'ALTER TABLE ? NOCHECK CONSTRAINT ALL'
GO
EXEC sp_MSForEachTable 'DELETE FROM ?'
GO
-- enable referential integrity again
EXEC sp_MSForEachTable 'ALTER TABLE ? WITH CHECK CHECK CONSTRAINT ALL'
GO
```
# How To Truncate All Data From All Table
```
EXEC sp_MSForEachTable 'ALTER TABLE ? NOCHECK CONSTRAINT ALL'
GO
EXEC sp_MSForEachTable 'TRUNCATE TABLE ?'
GO
-- enable referential integrity again
EXEC sp_MSForEachTable 'ALTER TABLE ? CHECK CONSTRAINT ALL'
GO
```
