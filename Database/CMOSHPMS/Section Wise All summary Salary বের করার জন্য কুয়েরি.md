4SELECT 
    SectionName,  -- Include department ID in the result
    -- Adding salary components
    SUM(VIEW_RptSalary.mBasic) + 
    SUM(VIEW_RptSalary.mHouseRent) + 
    SUM(VIEW_RptSalary.mMedical) + 
    SUM(VIEW_RptSalary.mConveyence) + 
    SUM(VIEW_RptSalary.mOthers) + 
    SUM(VIEW_RptSalary.mClinical) + 
    SUM(VIEW_RptSalary.mDearnessAllow) + 
    SUM(VIEW_RptSalary.mSpecial) + 
    SUM(VIEW_RptSalary.mNPA) + 
    SUM(VIEW_RptSalary.mOTAmount) + 
    SUM(VIEW_RptSalary.mOtherAmount) + 
    SUM(VIEW_RptSalary.mBonus) -

    -- Subtracting deductions
    (
        SUM(VIEW_RptSalary.mRCharge) + 
        SUM(VIEW_RptSalary.mSCut) + 
        SUM(VIEW_RptSalary.mITax) + 
        SUM(VIEW_RptSalary.mKallyan) + 
        SUM(VIEW_RptSalary.mKhichuri) + 
        SUM(VIEW_RptSalary.mStamp) + 
        SUM(VIEW_RptSalary.mP_Fund) + 
        SUM(VIEW_RptSalary.mCPFLoan)
    ) AS TotalSalary

FROM 
    VIEW_RptSalary
WHERE 
    iYear = 2024 
    AND vMonth = 'December'
    AND sectionID IN ('S1', 'S10', 'S100', 'S101', 'S102', 'S103', 'S104', 'S105', 
                      'S106', 'S107', 'S108', 'S109', 'S11', 'S110', 'S111', 'S112', 
                      'S12', 'S13', 'S14', 'S15', 'S16', 'S17', 'S18', 'S19', 'S2', 
                      'S20', 'S21', 'S22', 'S23', 'S24', 'S25', 'S26', 'S28', 'S29', 
                      'S3', 'S30', 'S31', 'S32', 'S33', 'S34', 'S35', 'S36', 'S37', 
                      'S38', 'S39', 'S4', 'S40', 'S41', 'S42', 'S43', 'S44', 'S45', 
                      'S46', 'S47', 'S48', 'S49', 'S5', 'S50', 'S51', 'S52', 'S53', 
                      'S54', 'S55', 'S56', 'S57', 'S58', 'S59', 'S6', 'S60', 'S61', 
                      'S62', 'S63', 'S64', 'S65', 'S66', 'S67', 'S68', 'S69', 'S7', 
                      'S70', 'S71', 'S72', 'S73', 'S74', 'S75', 'S76', 'S77', 'S78', 
                      'S79', 'S8', 'S80', 'S81', 'S82', 'S83', 'S84', 'S85', 'S86', 
                      'S87', 'S88', 'S89', 'S9', 'S90', 'S91', 'S92', 'S93', 'S94', 
                      'S95', 'S96', 'S98', 'S99')
    AND vDepartmentId LIKE '%' 
GROUP BY 
 SectionName order by SectionName
