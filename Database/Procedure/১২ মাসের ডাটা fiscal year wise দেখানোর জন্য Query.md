4Example:
DECLARE @mBasic1 MONEY, @mCount1 INT, @mBasic2 MONEY, @mCount2 INT

	;WITH CTE AS (
		SELECT 
			mBasic,
			COUNT(*) AS BasicCount,
			ROW_NUMBER() OVER (ORDER BY COUNT(*) DESC) AS RowNum
		FROM 
			Salary
		WHERE 
			vEmployeeId = @pEmployeeId
			AND (
				(iYear = @previousYear AND vMonth IN ('July', 'August', 'September', 'October', 'November', 'December'))
				OR 
				(iYear = @presentYear AND vMonth IN ('January', 'February', 'March', 'April', 'May', 'June'))
			)
		GROUP BY 
			mBasic
	)
	SELECT
		@mBasic1 = MAX(CASE WHEN RowNum = 1 THEN mBasic ELSE NULL END),
		@mCount1 = MAX(CASE WHEN RowNum = 1 THEN BasicCount ELSE NULL END),
		@mBasic2 = MAX(CASE WHEN RowNum = 2 THEN mBasic ELSE NULL END),
		@mCount2 = MAX(CASE WHEN RowNum = 2 THEN BasicCount ELSE NULL END)
	FROM 
		CTE
এটা হচ্ছে query 

ট্যাক্স FULL PROCEDURE:
USE [CMOSHPMS(Evision)]
GO
/****** Object:  StoredProcedure [dbo].[prcTempIncomeTax]    Script Date: 09/03/2024 17:48:31 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO



/****************************************
Author		:<zahir>
Create Date	:<12-08-2024>
Update Date	:<12-08-2024 by Zahir>
*****************************************/

ALTER Procedure [dbo].[prcTempIncomeTax]
(
	@pTaxYear varchar(150),		@pEmployeeId varchar(150)
)

AS
BEGIN
	truncate table tbTempIncomeTax
	Declare @FiscalYear varchar(150),	@TaxYear varchar(150),			@dDate datetime,				@EmpType varchar(150),
	@EmpID varchar(150),				@EmpName varchar(150),			@Dept varchar(150),				@Designation varchar(150),
	@vSR varchar(150),					@Basic money,					@CLA money,						@NPA money,		
	@SpecialAllow money,				@Others money,					@DAllow money,					@FesBonus money,
	@CoCon money,						@TotalEarnings money,			@HR money,						@Medical money,
	@FirstTotal money,					@SecondTotal money,				@ThirdTotal money,				@FourthTotal money,
	@FirstPercent money,				@SecondPercent money,			@ThirdPercent money,			@FourthPercent money,
	@FifthPercent money,				@FirstAmount money,				@SecondAmount money,			@ThirdAmount money,
	@FourthAmount money,				@FifthAmount money,				@TotalTax money,				@ActualInvest1 money,
	@ActualInvest2 money,				@ActualInvest3 money,			@ActualInvest4 money,			@ActualInvest5 money,
	@TotalInvestment money,				@TaxRebate money,				@netPayable money,				@AssetTax money,
	@FinalTax money,					@minTax money,					@vIncomeTax money,				@FifthTotal money,
	@SixthPercent money,				@SixthAmount money,				@vUser varchar(150),			@vComputer varchar(150),
	@dDateTime datetime,				@mActual1 money,				@mActual2 money,				@mActual3 money,
	@mActual4 money,					@mActual5 money,				@Conveyence money,
	@tempIncome money,					@dJoiningDate varchar(150),		@fromDate varchar(150),			@toDate varchar(150)




	select @FiscalYear=FiscalYear,@TaxYear=TaxYear,@dDate=dDate,@EmpType=EmpType,@EmpID=EmpID,@EmpName=EmpName,@Dept=Dept,
	@Designation=Designation,@vSR=vSR,@Basic=Basic,@CLA=CLA,@NPA=NPA,@SpecialAllow=SpecialAllow,@Others=Others,@DAllow=DAllow,
	@FesBonus=FesBonus,@CoCon=CoCon,@TotalEarnings=TotalEarnings,@HR=HR,@Medical=Medical,@Conveyence=Conveyence,@FirstTotal=FirstTotal,@SecondTotal=SecondTotal,
	@ThirdTotal=ThirdTotal,@FourthTotal=FourthTotal,@FirstPercent=FirstPercent,@SecondPercent=SecondPercent,@ThirdPercent=ThirdPercent,
	@FourthPercent=FourthPercent,@FifthPercent=FifthPercent,@FirstAmount=FirstAmount,@SecondAmount=SecondAmount,@ThirdAmount=ThirdAmount,
	@FourthAmount=FourthAmount,@FifthAmount=FifthAmount,@TotalTax=TotalTax,@ActualInvest1=ActualInvest1,@ActualInvest2=ActualInvest2,
	@ActualInvest3=ActualInvest3,@ActualInvest4=ActualInvest4,@ActualInvest5=ActualInvest5,@TotalInvestment=TotalInvestment,
	@TaxRebate=TaxRebate,@netPayable=netPayable,@AssetTax=AssetTax,@FinalTax=FinalTax,@minTax=minTax,@vIncomeTax=vIncomeTax,
	@FifthTotal=FifthTotal,@SixthPercent=SixthPercent,@SixthAmount=SixthAmount,@vUser=vUser,@vComputer=vComputer,@dDateTime=dDateTime 
	from IncomeTax where FiscalYear like @pTaxYear and EmpID like @pEmployeeId 
	
	select @dJoiningDate=convert(varchar, dJoiningDate, 103)from EmployeeInfo where vEmployeeId=@pEmployeeId
	

	DECLARE @mBasic MONEY,					@mMedicalAllowance MONEY,		@mHouseRent MONEY,			@mConveyanceAllowance MONEY,
	@mNonPracticeAllowance MONEY,			@mSpecialAllowance MONEY,		@mOtherAllowance MONEY,
	@mDearnessAllowance MONEY,				@mClinicalAllowance MONEY,		@fromYear  varchar(100),			
	@toYear varchar(100),					@previousYear  varchar(100),	@presentYear  varchar(100)



		SET @fromYear =  SUBSTRING(@FiscalYear, 1, CHARINDEX('-', @FiscalYear) - 1);
		SET @toYear =  SUBSTRING(@FiscalYear, CHARINDEX('-', @FiscalYear) + 1, 15);
		SET @previousYear = @fromYear 
		SET @presentYear =  @toYear
			


	SELECT   @mBasic = MAX(ISNULL(mBasic, 0)), @mMedicalAllowance = MAX(ISNULL(mMedical, 0)),@mHouseRent = MAX(ISNULL(mHouseRent, 0)),
    @mConveyanceAllowance = MAX(ISNULL(mConveyence, 0)), @mNonPracticeAllowance = MAX(ISNULL(mNPA, 0)),
    @mSpecialAllowance = MAX(ISNULL(mSpecial, 0)), @mOtherAllowance = MAX(ISNULL(mOthers, 0)),
    @mDearnessAllowance = MAX(ISNULL(mDearnessAllow, 0)), @mClinicalAllowance = MAX(ISNULL(mClinical, 0))from 
    Salary where vEmployeeId = @pEmployeeId and iYear=@presentYear and vMonth='June'
    --AND (
    --    (iYear = 2023 AND vMonth IN ('July', 'August', 'September', 'October', 'November', 'December'))
    --    OR 
    --    (iYear = 2024 AND vMonth IN ('January', 'February', 'March', 'April', 'May', 'June'))
    --);

declare @mBonus MONEY

  select Distinct @mBonus = mBonus from BonusInfo WHERE 
    vEmployeeId = @pEmployeeId
  AND (
        (iYear = @previousYear AND vMonth IN ('July', 'August', 'September', 'October', 'November', 'December'))
        OR 
        (iYear = @presentYear AND vMonth IN ('January', 'February', 'March', 'April', 'May', 'June'))
    ) and mBonus>0
    
   declare  @mContributionFund MONEY
    
       select  @mContributionFund = MAX(ISNULL(mP_Fund, 0)) from salary where
           vEmployeeId = @pEmployeeId
  AND (
        (iYear = @previousYear AND vMonth IN ('July', 'August', 'September', 'October', 'November', 'December'))
        OR 
        (iYear = @presentYear AND vMonth IN ('January', 'February', 'March', 'April', 'May', 'June'))
    )
    
     declare @count_fund int
     
      select @count_fund=COUNT(mP_Fund) from Salary  where mP_Fund<>0 and   vEmployeeId = @pEmployeeId
  AND (
        (iYear = @previousYear AND vMonth IN ('July', 'August', 'September', 'October', 'November', 'December'))
        OR 
        (iYear = @presentYear AND vMonth IN ('January', 'February', 'March', 'April', 'May', 'June'))
    )
DECLARE @mBasic1 MONEY, @mCount1 INT, @mBasic2 MONEY, @mCount2 INT

	;WITH CTE AS (
		SELECT 
			mBasic,
			COUNT(*) AS BasicCount,
			ROW_NUMBER() OVER (ORDER BY COUNT(*) DESC) AS RowNum
		FROM 
			Salary
		WHERE 
			vEmployeeId = @pEmployeeId
			AND (
				(iYear = @previousYear AND vMonth IN ('July', 'August', 'September', 'October', 'November', 'December'))
				OR 
				(iYear = @presentYear AND vMonth IN ('January', 'February', 'March', 'April', 'May', 'June'))
			)
		GROUP BY 
			mBasic
	)
	SELECT
		@mBasic1 = MAX(CASE WHEN RowNum = 1 THEN mBasic ELSE NULL END),
		@mCount1 = MAX(CASE WHEN RowNum = 1 THEN BasicCount ELSE NULL END),
		@mBasic2 = MAX(CASE WHEN RowNum = 2 THEN mBasic ELSE NULL END),
		@mCount2 = MAX(CASE WHEN RowNum = 2 THEN BasicCount ELSE NULL END)
	FROM 
		CTE

  
    
	set  @mActual1=0	set @mActual2=0		set @mActual3=0		set @mActual4=0		set  @mActual5=0
	
	set @tempIncome=@TotalEarnings
	
	if @tempIncome>@FirstTotal
	begin
		set @mActual1=@FirstTotal
		set @tempIncome=@tempIncome-@mActual1
		
		if @tempIncome>0
		begin
			if @tempIncome>@SecondTotal
			begin
				set @mActual2=@SecondTotal
				set @tempIncome=@tempIncome-@mActual2		
						
				if @tempIncome>0
				begin
					if @tempIncome>@ThirdTotal
					begin
						set @mActual3=@ThirdTotal
						set @tempIncome=@tempIncome-@mActual3						
						
						if @tempIncome>0
						begin
							if @tempIncome>@FourthTotal
							begin
								set @mActual4=@FourthTotal
								set @tempIncome=@tempIncome-@mActual4
								
								if @tempIncome>0
								begin
									if @tempIncome>@FifthTotal
									begin
										set @mActual5=@FifthTotal
										set @tempIncome=@tempIncome-@mActual5
									end
									else
									begin
										set @mActual5=@tempIncome
									end
								end
								
							end
							else
							begin
								set @mActual4=@tempIncome
							end
						end
						
					end
					else
					begin
						set @mActual3=@tempIncome
					end
				end
			end
			else
			begin
				set @mActual2=@tempIncome
			end
		end
	end
	
	set @FinalTax=@netPayable-@AssetTax
	
	set @fromDate='01-07-'+SUBSTRING(@FiscalYear,0,(CHARINDEX('-',@FiscalYear)))
	set @toDate='30-06-'+SUBSTRING(@FiscalYear,(CHARINDEX('-',@FiscalYear)+1),15) 
	set @TaxYear=@fromDate+' to '+@toDate
	

  	insert into tbTempIncomeTax
	(
		FiscalYear,TaxYear,dDate,EmpType,EmpID,EmpName,Dept,Designation,vSR,Basic,CLA,NPA,SpecialAllow,Others,DAllow,FesBonus,
		CoCon,TotalEarnings,HR,Medical,Conveyence,FirstTotal,SecondTotal,ThirdTotal,FourthTotal,FirstPercent,SecondPercent,ThirdPercent,FourthPercent,
		FifthPercent,FirstAmount,SecondAmount,ThirdAmount,FourthAmount,FifthAmount,TotalTax,ActualInvest1,ActualInvest2,ActualInvest3,
		ActualInvest4,ActualInvest5,TotalInvestment,TaxRebate,netPayable,AssetTax,FinalTax,minTax,vIncomeTax,FifthTotal,SixthPercent,
		SixthAmount,vUser,vComputer,dDateTime,mActual1,mActual2,mActual3,mActual4,mActual5,dJoiningDate,mBasic,mHouseRent,mMedical,
		mConveyence,mNPA,mSpecial,mOthers,mDearnessAllow,mP_Fund,mClinical,mBonus,count_fund,mBasic1, mCount1, mBasic2, mCount2 
	)
	values
	(
		@FiscalYear,@TaxYear,@dDate,@EmpType,@pEmployeeId,@EmpName,@Dept,@Designation,@vSR,@Basic,@CLA,@NPA,@SpecialAllow,@Others,@DAllow,@FesBonus,
		@CoCon,@TotalEarnings,@HR,@Medical,@Conveyence,@FirstTotal,@SecondTotal,@ThirdTotal,@FourthTotal,@FirstPercent,@SecondPercent,@ThirdPercent,
		@FourthPercent,@FifthPercent,@FirstAmount,@SecondAmount,@ThirdAmount,@FourthAmount,@FifthAmount,@TotalTax,@ActualInvest1,@ActualInvest2,
		@ActualInvest3,@ActualInvest4,@ActualInvest5,@TotalInvestment,@TaxRebate,@netPayable,@AssetTax,@FinalTax,@minTax,@vIncomeTax,@FifthTotal,
		@SixthPercent,@SixthAmount,@vUser,@vComputer,@dDateTime,@mActual1,@mActual2,@mActual3,@mActual4,@mActual5,@dJoiningDate,@mBasic,@mHouseRent,
		@mMedicalAllowance ,@mConveyanceAllowance , @mNonPracticeAllowance ,@mSpecialAllowance , @mOtherAllowance, @mDearnessAllowance ,
		@mContributionFund ,@mClinicalAllowance,@mBonus,@count_fund,@mBasic1, @mCount1, @mBasic2, @mCount2 
	
	)
	
	
END;

--exec prcTempIncomeTax '2024-2025','Emp-706'
--select * from IncomeTax
--select * from tbTempIncomeTax

--select * from IncomeTax

