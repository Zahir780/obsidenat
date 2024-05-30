```
USE [SEPL_ASP]
GO
/****** Object:  UserDefinedFunction [dbo].[funGetData]    Script Date: 2023-07-11 3:50:09 PM ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO

-------------------------------------------
-- Author: Mohammad Didarul Alam
-- Create Date: 14-06-2023
-- Update Date: 14-06-2023
-- Description: Monthly Salary Calculation
-------------------------------------------

alter function funGetData
(
	@pDepartmentId varchar(150),		@pSectionId varchar(150),			@pEmployeeId varchar(150)
)
returns @tbSalary table
(
	vEmployeeId varchar(150),			vEmployeeCode varchar(150),			vEmployeeName varchar(150)
)
as
begin
	Declare 
	@vEmployeeId varchar(150),			@vEmployeeCode varchar(150),		@vEmployeeName varchar(150)
	
	declare csrSalary cursor for
		select vEmployeeId from tbEmployeeInfo 
		where vEmployeeId like @pEmployeeId and vDepartmentId like @pDepartmentId and vSectionId like @pSectionId
	open csrSalary

	fetch next from csrSalary into @vEmployeeId
	
	while @@FETCH_STATUS=0
	begin
		select @vEmployeeCode=vEmployeeCode,@vEmployeeName=vEmployeeName from tbEmployeeInfo 
		where vEmployeeId like @vEmployeeId

		insert into @tbSalary
		(
			vEmployeeId,vEmployeeCode,vEmployeeName
		)
		values
		(
			@vEmployeeId,@vEmployeeCode,@vEmployeeName
		)		
		fetch next from csrSalary into @vEmployeeId
	end
	close csrSalary
	deallocate csrSalary	
	return
end

/*
select * from tbEmployeeInfo where vDepartmentId like '3' and vSectionId like '8'
select * from funGetData('3','8','%')

*/
```
