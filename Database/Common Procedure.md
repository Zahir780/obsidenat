```
USE [SEPL_ASP]
GO
/****** Object:  StoredProcedure [dbo].[prcDataUpdate]    Script Date: 2023-07-11 4:15:21 PM ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
-----------------------------------------
-- Author: Mohammad Didarul Alam
-- Create Date: <02-08-2022>
-- Update By:	<10-09-2018> Didarul Alam 
-----------------------------------------

ALTER Procedure prcDataUpdate
(
	@pDepartmentId varchar(150),		@pSectionId varchar(150),			@pEmployeeId varchar(150)
)
AS
BEGIN 
	Declare 
	@vEmployeeId varchar(150),			@vEmployeeCode varchar(150),		@vEmployeeName varchar(150)
	
	declare curCursor cursor for
		select vEmployeeId from tbEmployeeInfo 
		where vEmployeeId like @pEmployeeId and vDepartmentId like @pDepartmentId and vSectionId like @pSectionId
	open curCursor
	fetch next from curCursor into @vEmployeeId

	while @@FETCH_STATUS=0
	begin	
		select @vEmployeeCode=vEmployeeCode,@vEmployeeName=vEmployeeName from tbEmployeeInfo 
		where vEmployeeId like @vEmployeeId

		fetch next from curCursor into @vEmployeeId
	end
	close curCursor
	deallocate curCursor
END;

/*
exec prcDataUpdate '3','8','%'

*/
```
