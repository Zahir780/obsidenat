4var commonUrl = "https://localhost:44359";

$(document).ready(function () {

    init();
    visibility();
    $('input[type=radio][name=porto_is]').change(async function () {
        /*    $('#preview').show();*/
        $("#ParameterContener").show();
        /*  $("#parameterSection").show();*/4
        //console.log("reportMenu");
        visibility();
        reportMenuAction($(this).val());
    });

    othersAction();

});

/*initial Function */
function init() {
    var date = getCDay() + "-" + getCMonth() + "-" + getCYear();
    $("#inpFromDate").val(date);
    $("#inpToDate").val(date);
    $("#inpFromDateTo").val(date);
    $("#inpToDateTo").val(date);
    clear();
}
function visibility() {
    document.getElementById('pMonthConfirmation').style.display = "none";
    document.getElementById('rdoStatus').style.display = "none";
    document.getElementById('rdoConfirmationDate').style.display = "none";
    document.getElementById('pDate').style.display = "none";
    document.getElementById('fromDateTo').style.display = "none";
    document.getElementById('pBankBranchId').style.display = "none";
    document.getElementById('pBankId').style.display = "none";
    document.getElementById('pUnitId').style.display = "none";
    document.getElementById('pDepartmentId').style.display = "none";
    document.getElementById('pSectionId').style.display = "none";
    document.getElementById('comServiceType').style.display = "none";
    document.getElementById('comFiscYear').style.display = "none";
    document.getElementById('comEmployeeId').style.display = "none";
    document.getElementById('divSalaryMonth').style.display = "none";
    document.getElementById('divTotalBonusYear').style.display = "none";
    document.getElementById('pSalaryType').style.display = "none";
    document.getElementById('pAttendanceType').style.display = "none";
    document.getElementById('pSalaryHoldStatus').style.display = "none";
    document.getElementById('pWithOrWithOutGross').style.display = "none";
    document.getElementById('pMonthId').style.display = "none";
    document.getElementById('pEmployeeType').style.display = "none";
    document.getElementById('rdoMoneyTransferTypeId').style.display = "none";
    document.getElementById('pDesignation').style.display = "none";
    document.getElementById('pBranchName').style.display = "none";
    document.getElementById('pAddress').style.display = "none";
    document.getElementById('comAccountNo').style.display = "none";
    document.getElementById('comReferenceNo').style.display = "none";
    document.getElementById('comCertifiedBy').style.display = "none";
    document.getElementById('comDesignation').style.display = "none";
    document.getElementById('comContact').style.display = "none";
    document.getElementById('pBasedOn').style.display = "none";
    document.getElementById('pTillAsOn').style.display = "none";
    document.getElementById('comApplicationDate').style.display = "none";
    document.getElementById('fromDate').style.display = "none";
    document.getElementById('comLoanStatus').style.display = "none";
    document.getElementById('rdoBankTypeId').style.display = "none";
    document.getElementById('comServiceStatus').style.display = "none";
    document.getElementById('comReligion').style.display = "none";
    document.getElementById('pCategory').style.display = "none";
    document.getElementById('pJobDuratoion').style.display = "none";
    document.getElementById('comItem').style.display = "none";
    document.getElementById('comYear').style.display = "none";
    document.getElementById('pIncrementProposal').style.display = "none";
    document.getElementById('pDesignationId').style.display = "none";
    document.getElementById('pTableData').style.display = "none";
    document.getElementById('comOptionReligion').style.display = "none";
    document.getElementById('comTo').style.display = "none";
    document.getElementById('comOccasion').style.display = "none";
    document.getElementById('rdoBonusAmount').style.display = "none";
    document.getElementById('rdoRptType').style.display = "none";
}

function removeModalClass() {
    document.getElementById("reportViewer").classList.remove("landscapeA4");
    document.getElementById("reportViewer").classList.remove("landscapeA42");
    document.getElementById("reportViewer").classList.remove("portraitA4");
}

function reportMenuAction(type) {
    reportMenuActionMasterReport(type);
    reportMenuActionAttendanceReport(type);
    reportMenuActionLeaveReport(type);
    reportMenuActionSalaryReport(type);
    reportMenuActionOTReport(type);
    reportMenuActionLoanReport(type);
    reportMenuActionIncomeTaxReport(type);
    reportMenuActionOtherReport(type);
}
function reportMenuActionMasterReport(type) {
    if (type == "RptEmployeeProfileBioData") {
        $("#ReportTitle").text('Employee Profile (Bio-Data)');
        RptEmployeeProfileBioDataWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }
    if (type == "RptEmployeeList") {
        $("#ReportTitle").text('Employee List');
        RptEmployeeWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }
    if (type == "RptConfirmationJoiningLeftList") {
        $("#ReportTitle").text('Confirmation/Joining/Left List');
        RptConfirmationJoiningLeftListDate();
        document.getElementById("reportViewer").className += " portraitA4";
    }
    if (type == "RptMonthWiseConfirmation/Joining/LeftList") {
        $("#ReportTitle").text('Employee Joining/Confirmation Date');
        RptMonthWiseConfirmationJoiningLeftList();
        document.getElementById("reportViewer").className += " portraitA4";
    }
    if (type == "RptLengthOfService") {
        $("#ReportTitle").text('Length Of Service');
        RptLengthOfServiceWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }
    if (type == "RptApplicationAndAppointmentLetter") {
        $("#ReportTitle").text('Application And Appointment Letter');
        RptApplicationAndAppointmentLetterWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }
    if (type == "RptCertification") {
        $("#ReportTitle").text('Certification');
        RptCertificationWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }
    if (type == "RptIdCard") {
        $("#ReportTitle").text('ID Card Generate');
        RptIdCardWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }
    if (type == "RptTemporaryEmployee") {
        $("#ReportTitle").text('Temporary Employee');
        RptTemporaryEmployeeWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }
    if (type == "RptPermanentEmployee") {
        $("#ReportTitle").text('Permanent Employee');
        RptPermanentEmployeeWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }
    if (type == "RptFinalSettlement") {
        $("#ReportTitle").text('Final Settlement');
        RptFinalSettlementWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }
}
function reportMenuActionAttendanceReport(type) {

    if (type == "RptMonthlyDutyRoster") {
        $("#ReportTitle").text('Monthly Duty Roster');
        RptMonthlyDutyRoster();
        document.getElementById("reportViewer").className += " portraitA4";
    }

    if (type == "RptInLieu") {
        $("#ReportTitle").text('In Lieu');
        RptInLieuWork();
        document.getElementById("reportViewer").className += " landscapeA4";
    }


    if (type == "RptShiftInfo") {
        $("#ReportTitle").text('Shift Info');
        RptShiftInfo();
        document.getElementById("reportViewer").className += " portraitA4";
    }

    if (type == "RptRamadan") {
        $("#ReportTitle").text('Ramdan Shift Info');
        RptRamadanWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }




    if (type == "RptDailyAttendanceStatement") {
        $("#ReportTitle").text('Daily Attendance Statement');
        RptDailyAttendanceStatementWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }


    if (type == "RptDailyAbsentStatement") {
        $("#ReportTitle").text('Daily Attendance Statement');
        RptDailyAbsentStatementWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }


    if (type == "RptDailyLateInEmployeeList") {
        $("#ReportTitle").text('Daily LateIn Employee List');
        RptDailyLateInEmployeeListWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }
    if (type == "RptDailyEarlyOutEmployeeList") {
        $("#ReportTitle").text('Daily Early Out Employee List');
        RptDailyEarlyOutEmployeeListWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }
    if (type == "RptIndividualEmployeeAttendance") {
        $("#ReportTitle").text('Individual Employee Attendance');
        RptIndividualEmployeeAttendanceWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }
    if (type == "RptMonthlyAttendanceSummary") {
        $("#ReportTitle").text('Monthly Attendance Summary');
        RptMonthlyAttendanceSummaryWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }
    if (type == "RptShortViewOfAttendance") {
        $("#ReportTitle").text('Short View Of Attendance');
        RptShortViewOfAttendanceWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }
    if (type == "RptMonthlyAttendanceSummaryManual") {
        $("#ReportTitle").text('Monthly Attendance Summary(Manually)');
        RptMonthlyAttendanceSummaryManualWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }
    if (type == "RptMonthlyMealInformation") {
        $("#ReportTitle").text('Monthly Meal Information');
        RptMonthlyMealInformationWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }
    if (type == "RptMonthlyMealInformation") {
        $("#ReportTitle").text('Monthly Meal Information');
        RptMonthlyMealInformationWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }
    if (type == "RptHoliday") {
        $("#ReportTitle").text('Holiday Report');
        RptHolidayWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }


    if (type == "RptIncompleteAttendanceList") {
        $("#ReportTitle").text('Incomplete Attendance ListWork');
       RptIncompleteAttendanceListWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }
    if (type == "RptAttendanceDailyMovement") {
        $("#ReportTitle").text('Attendance Daily Movement');
        RptAttendanceDailyMovementWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }
}
function reportMenuActionLeaveReport(type) {
    if (type == "RptLeaveApplication") {
        $("#ReportTitle").text('Leave Application');
        RptLeaveApplicationWork();
        document.getElementById("reportViewer").className += " landscapeA4";
    }
    if (type == "RptLeaveRegister") {
        $("#ReportTitle").text('Leave Register');
        RptLeaveRegisterWork();
        document.getElementById("reportViewer").className += " landscapeA4";
    }

    if (type == "RptLeaveEncashment") {
        $("#ReportTitle").text('Leave Encashment');
        LeaveEncashmentWork();
        document.getElementById("reportViewer").className += " landscapeA4";
    }


    if (type == "RptIndividualLeaveRegister") {
        $("#ReportTitle").text('Leave Register');
        RptIndividualLeaveRegisterWork();
        document.getElementById("reportViewer").className += " landscapeA4";
    }
}
function reportMenuActionSalaryReport(type) {
    if (type == "RptMonthlySalary") {
        $("#ReportTitle").text('Monthly Salary');
        RptMonthlySalaryWork();
        document.getElementById("reportViewer").className += " landscapeA4";
    }


    if (type == "RptBonus") {
        $("#ReportTitle").text('Bonus');
        RptBonusWork();
        document.getElementById("reportViewer").className += " landscapeA4";
    }

    if (type == "RptBonusAdvice") {
        $("#ReportTitle").text('Bonus Advice');
        RptBonusAdviceWork();
        document.getElementById("reportViewer").className += " landscapeA4";
    }


    if (type == "RptPaySlip") {
        $("#ReportTitle").text('PaySlip');
        RptPaySlipWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }
    if (type == "RptBankAdviceWithForwardingLetter") {
        $("#ReportTitle").text('Bank Advice With Forwarding Letter');
        RptBankAdviceWithForwardingLetterWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }
    if (type == "RptNoteRequisition") {
        $("#ReportTitle").text('Note Requisition');
        RptNoteRequisitionWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }
    if (type == "RptSalaryCertificate") {
        $("#ReportTitle").text('PaySlip');
        RptSalaryCertificateWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }

    if (type == "RptSummaryReportOfSalary") {
        $("#ReportTitle").text('Summary Report Of Salary');
        RptSummaryReportOfSalaryWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }

    if (type == "RptOtherEarning") {
        $("#ReportTitle").text('Other Earning');
        RptOtherEarningWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }

    if (type == "RptOtherDeduction") {
        $("#ReportTitle").text('Other Deduction');
        RptOtherDeductionWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }

    if (type == "RptMobileExtra") {
        $("#ReportTitle").text('Mobile Extra');
        RptMobileExtraWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }
}
//function reportMenuActionOTReport(type) {
//    if (type == "RptMonthWiseOfStatement") {
//        $("#ReportTitle").text('Month Wise Of Statement');
//        RptMonthWiseOfStatementWork();
//        document.getElementById("reportViewer").className += " portraitA4";
//    }
//}

//Arrow Function Used
var reportMenuActionOTReport = (type) => {
    if (type === "RptMonthWiseOfStatement") {
        $("#ReportTitle").text('Month Wise Of Statement');
        RptMonthWiseOfStatementWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }
};

function reportMenuActionLoanReport(type) {
    if (type == "RptLoanApplication") {
        $("#ReportTitle").text('Loan Application');
        RptLoanApplicationWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }
    if (type == "RptIndividualLoanStatement") {
        $("#ReportTitle").text('Individual Loan Statement');
        RptIndividualLoanStatementWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }
    if (type == "RptLoanRegister") {
        $("#ReportTitle").text('Loan Register');
        RptLoanRegisterWork();
        document.getElementById("reportViewer").className += " landscapeA4";
    }
    if (type == "RptAdvanceSalaryLoan") {
        $("#ReportTitle").text('Advance Salary Loan');
        RptAdvanceSalaryLoanWork();
        document.getElementById("reportViewer").className += " landscapeA4";
    }

    if (type == "RptAdvanceSalaryLoanRegister") {
        $("#ReportTitle").text('Advance Salary Loan Register');
        RptAdvanceSalaryLoanRegisterWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }
}
function reportMenuActionIncomeTaxReport(type) {
    if (type == "RptIncomeTax") {
        $("#ReportTitle").text('Income Tax');
        RptIncomeTaxWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }
    if (type == "RptIncomeTaxSummary") {
        $("#ReportTitle").text('Income Tax Summary');
        RptIncomeTaxSummaryWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }
    if (type == "RptIncomeTaxCalculation") {
        $("#ReportTitle").text('Income Tax Summary');
        RptIncomeTaxCalculationWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }

}
function reportMenuActionOtherReport(type) {
    if (type == "RptItemDistrubationReport") {
        $("#ReportTitle").text('Item Distrubation Report');
        RptItemDistrubationReportWork();
        document.getElementById("reportViewer").className += " landscapeA4";
    }
    if (type == "RptIncrementProposal") {
        $("#ReportTitle").text('Increment Proposal');
        RptIncrementProposalWork();
        document.getElementById("reportViewer").className += " landscapeA4";
    }

    if (type == "RptIncrementReport") {
        $("#ReportTitle").text('Increment Report');
        RptRptIncrementReportWork();
        document.getElementById("reportViewer").className += " landscapeA4";
    }
    if (type == "RptSalaryIncrementStatement") {
        $("#ReportTitle").text('Salary Increment Statement');
        RptSalaryIncrementStatementWork();
        document.getElementById("reportViewer").className += " landscapeA4";
    }
    if (type == "RptEmployeePromotionReport") {
        $("#ReportTitle").text('Employee Promotion Report');
        RptEmployeePromotionReportWork();
        document.getElementById("reportViewer").className += " landscapeA4";
    }

    if (type == "RptContributionAndProfitStatement") {
        $("#ReportTitle").text('Contribution And Profit Statement');
        RptContributionAndProfitStatementWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }

    if (type == "RptContributionAndProfitSummary") {
        $("#ReportTitle").text('Contribution And Profit Summary');
        RptContributionAndProfitSummaryWork();
        document.getElementById("reportViewer").className += " landscapeA4";
    }

    if (type == "RptContributionAndProfitDetails") {
        $("#ReportTitle").text('Contribution And Profit Details');
        RptContributionAndProfitDetailsWork();
        document.getElementById("reportViewer").className += " landscapeA4";
    }

    if (type == "RptOrientation") {
        $("#ReportTitle").text('Orientation');
        Orientation();
        document.getElementById("reportViewer").className += " portraitA4";
    }



    if (type == "RptIncomeTax") {
        $("#ReportTitle").text('Income Tax');
        RptIncomeTaxWork();
        document.getElementById("reportViewer").className += " portraitA4";
    }

}

/*Master Report Data Load Action Start*/
function RptEmployeeProfileBioDataWork() {
    document.getElementById('comEmployeeId').style.display = "flex";
    clear();
    var type = "RptEmployeeProfileBioData";
    $("#type").val(type);
    if (type != "") {
        getEmployee(type, "0", "0", "0", "0", "0", "0", "0", "0");
    }
}
function RptEmployeeWork() {
    document.getElementById('pCategory').style.display = "flex";
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    document.getElementById('comOptionReligion').style.display = "flex";
    document.getElementById('pTableData').style.display = "flex";
    document.getElementById('comServiceStatus').style.display = "flex";
    document.getElementById('pWithOrWithOutGross').style.display = "flex";
    clear();
    var type = "RptEmployeeList";
    $("#type").val(type);
    var vStatus = $("input[name='vStatus']:checked").val();
    if (vStatus == "Active") {
        vStatus = "1";
    }
    else if (vStatus == "Inactive") {
        vStatus = "0";
    }
    else if (vStatus == "All") {
        vStatus = "%";
    }
    if (type != "") {
        getCategory(type, "0", "0", "0");
    }
    getRankTableData();
    getDesignationTableData();
    getServiceStatusTableData();
}
function RptConfirmationJoiningLeftListDate() {

    document.getElementById('rdoConfirmationDate').style.display = "flex";
    document.getElementById('fromDateTo').style.display = "flex";
    document.getElementById('pCategory').style.display = "flex";
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    document.getElementById('pDesignationId').style.display = "flex";
    document.getElementById('comReligion').style.display = "flex";
    document.getElementById('comServiceStatus').style.display = "flex";

    clear();
    var type = "RptConfirmationJoiningLeftList";
    var vReportType = $("input[name='vReportType']:checked").val();
    var inpFromDateTo = getBdToDbFormat($("#inpFromDateTo").val());
    var inpToDateTo = getBdToDbFormat($("#inpToDateTo").val());
    $("#type").val(type);
    if (type != "") {
        getCategory(type, vReportType, inpFromDateTo, inpToDateTo);
    }

}

function RptLengthOfServiceWork() {
    document.getElementById('pDate').style.display = "flex";
    document.getElementById('pCategory').style.display = "flex";
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    document.getElementById('comEmployeeId').style.display = "flex";
    document.getElementById('pJobDuratoion').style.display = "flex";

    document.getElementById('pBasedOn').style.display = "flex";
    document.getElementById('comServiceStatus').style.display = "flex";
    clear();
    var type = "RptLengthOfService";
    $("#type").val(type);
    if (type != "") {
        getCategory(type, "0", "0", "0");
    }

}
function RptApplicationAndAppointmentLetterWork() {
    document.getElementById('comEmployeeId').style.display = "flex";
    clear();
    var type = "RptApplicationAndAppointmentLetter";
    $("#type").val(type);
    if (type != "") {
        getEmployee(type, "0", "0", "0", "0", "0", "0", "0", "0");
    }
}
function RptCertificationWork() {
    document.getElementById('comEmployeeId').style.display = "flex";
    document.getElementById('comCertifiedBy').style.display = "flex";
    document.getElementById('comDesignation').style.display = "flex";
    document.getElementById('comReferenceNo').style.display = "flex";
    clear();
    var type = "RptCertification";
    $("#type").val(type);
    if (type != "") {
        getEmployee(type, "0", "0", "0", "0", "0", "0", "0");
        getCertifiedBy(type);
    }
}
function RptIdCardWork() {
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    document.getElementById('comEmployeeId').style.display = "flex";
    clear();
    var type = "RptIdCard";
    $("#type").val(type);
    if (type != "") {
        getUnit(type, "0", "0", "0", "0", "0", "0");
    }
}
function RptTemporaryEmployeeWork() {

    clear();
    var type = "RptTemporaryEmployee";
    $("#type").val(type);
}

function RptPermanentEmployeeWork() {
    /*   document.getElementById('pUnitId').style.display = "flex";*/
    document.getElementById('comEmployeeId').style.display = "flex";
    clear();
    var type = "RptPermanentEmployee";
    $("#type").val(type);
    if (type != "") {
        getEmployee(type, "0", "0", "0", "0", "0", "0", "0", "0");
    }
}

function RptFinalSettlementWork() {
    /*   document.getElementById('pUnitId').style.display = "flex";*/
    document.getElementById('comEmployeeId').style.display = "flex";

    clear();
    var type = "RptFinalSettlement";
    $("#type").val(type);
    if (type != "") {
        getEmployee(type, "0", "0", "0", "0", "0", "0", "0", "0");
    }
}



function RptIdCardWork() {
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    document.getElementById('comEmployeeId').style.display = "flex";
    clear();
    var type = "RptIdCard";
    $("#type").val(type);
    if (type != "") {
        getUnit(type, "0", "0", "0", "0", "0", "0");
    }
}

/*Master Report Data Load Action End*/

/*Attendance Report Data Load Action  Start*/
function RptMonthlyDutyRoster() {
    document.getElementById('pMonthId').style.display = "flex";
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    document.getElementById('comEmployeeId').style.display = "flex";
    clear();
    var type = "RptMonthlyDutyRoster";
    $("#type").val(type);
    if (type != "") {
        getMonth(type, "0");
    }
}
function RptInLieuWork() {
    document.getElementById('pMonthId').style.display = "flex";
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    document.getElementById('comEmployeeId').style.display = "flex";
    clear();
    var type = "RptInLieu";
    $("#type").val(type);
    if (type != "") {
        getMonth(type, "0");
    }
}

function RptShiftInfo()
{
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    clear();
    var type = "RptShiftInfo";
    $("#type").val(type);
    if (type != "") {
        getUnit(type, "0");
    }
}
function RptRamadanWork()
{
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    document.getElementById('fromDate').style.display = "flex";
    clear();
    var type = "RptRamadan";
    $("#type").val(type);
    if (type != "") {
        getUnit(type, "0");
    }
}






function RptDailyAttendanceStatementWork() {
    document.getElementById('pDate').style.display = "flex";
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    document.getElementById('pDesignationId').style.display = "flex";
    document.getElementById('comServiceType').style.display = "flex";
    document.getElementById('pEmployeeType').style.display = "flex";
    clear();
    var type = "RptDailyAttendanceStatement";
    var dDate = getBdToDbFormat($("#dDate").val());
    $("#type").val(type);
    if (type != "") {
        if (dDate != "") {
            getUnit(type, dDate, "0", "0", "0", "0");
        }
    }
}
function RptAttendanceDailyMovementWork() {
    document.getElementById('pDate').style.display = "flex";
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    document.getElementById('pDesignationId').style.display = "flex";
    document.getElementById('comServiceType').style.display = "flex";
    clear();
    var type = "RptAttendanceDailyMovement";
    var dDate = getBdToDbFormat($("#dDate").val());
    $("#type").val(type);
    if (type != "") {
        if (dDate != "") {
            getUnit(type, dDate, "0", "0", "0", "0");
        }
    }
}
function RptDailyAbsentStatementWork() {
    document.getElementById('pDate').style.display = "flex";
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    document.getElementById('pDesignationId').style.display = "flex";
    document.getElementById('comServiceType').style.display = "flex";
    clear();
    var type = "RptDailyAbsentStatement";
    var dDate = getBdToDbFormat($("#dDate").val());
    $("#type").val(type);
    if (type != "") {
        if (dDate != "") {
            getUnit(type, dDate, "0", "0", "0", "0");
        }
    }
}
function RptDailyLateInEmployeeListWork() {
    document.getElementById('pDate').style.display = "flex";
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    document.getElementById('pDesignationId').style.display = "flex";
    document.getElementById('comServiceType').style.display = "flex";
    clear();
    var type = "RptDailyLateInEmployeeList";
    var dDate = getBdToDbFormat($("#dDate").val());
    $("#type").val(type);
    if (type != "") {
        if (dDate != "") {
            getUnit(type, dDate, "0", "0", "0", "0");
        }
    }
}
function RptDailyEarlyOutEmployeeListWork() {
    document.getElementById('pDate').style.display = "flex";
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    document.getElementById('pDesignationId').style.display = "flex";
    document.getElementById('comServiceType').style.display = "flex";
    clear();
    var type = "RptDailyEarlyOutEmployeeList";
    var dDate = getBdToDbFormat($("#dDate").val());
    $("#type").val(type);
    if (type != "") {
        if (dDate != "") {
            getUnit(type, dDate, "0", "0", "0", "0");
        }
    }
}
function RptIndividualEmployeeAttendanceWork() {
    document.getElementById('pMonthId').style.display = "flex";
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    document.getElementById('comEmployeeId').style.display = "flex";

    clear();
    var type = "RptIndividualEmployeeAttendance";
    $("#type").val(type);
    if (type != "") {
        getMonth(type, "0");
    }
}
function RptMonthlyAttendanceSummaryWork() {
    document.getElementById('pAttendanceType').style.display = "flex";
    document.getElementById('pMonthId').style.display = "flex";
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    document.getElementById('comEmployeeId').style.display = "flex";
    clear();
    var type = "RptMonthlyAttendanceSummary";
    $("#type").val(type);
    if (type != "") {
        getMonth(type, "0");
    }
}
function RptIncompleteAttendanceListWork() {
    document.getElementById('pMonthId').style.display = "flex";
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    document.getElementById('comServiceType').style.display = "flex";
    clear();
    var type = "RptIncompleteAttendanceList";
    $("#type").val(type);
    if (type != "") {
        getMonth(type, "0");
    }
}
function RptShortViewOfAttendanceWork() {
    document.getElementById('pMonthId').style.display = "flex";
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    document.getElementById('comEmployeeId').style.display = "flex";
    clear();
    var type = "RptShortViewOfAttendance";
    $("#type").val(type);
    if (type != "") {
        getMonth(type, "0");
    }
}
function RptMonthlyAttendanceSummaryManualWork() {
    document.getElementById('pAttendanceType').style.display = "flex";
    document.getElementById('pMonthId').style.display = "flex";
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    document.getElementById('comEmployeeId').style.display = "flex";
    clear();
    var type = "RptMonthlyAttendanceSummaryManual";
    $("#type").val(type);
    if (type != "") {
        getMonth(type, "0");
    }
}
function RptMonthlyMealInformationWork() {
    document.getElementById('pAttendanceType').style.display = "flex";
    document.getElementById('pMonthId').style.display = "flex";
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    document.getElementById('comEmployeeId').style.display = "flex";
    clear();
    var type = "RptMonthlyMealInformation";
    $("#type").val(type);
    if (type != "") {
        getMonth(type, "0");
    }
}
function RptHolidayWork() {
    document.getElementById('comYear').style.display = "flex";
    clear();
    var type = "RptHoliday";
    $("#type").val(type);

}

/*Attendance Report Data Load Action End*/

/*Salary Report Data Load Action Start*/
function RptMonthlySalaryWork() {

    document.getElementById('pMonthId').style.display = "flex";
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    document.getElementById('comEmployeeId').style.display = "flex";
    document.getElementById('pSalaryType').style.display = "flex";
    document.getElementById('rdoMoneyTransferTypeId').style.display = "flex";
    document.getElementById('pSalaryHoldStatus').style.display = "flex";
    clear();
    var type = "RptMonthlySalary";
    var vSalaryType = $("input[name='vSalaryType']:checked").val();

    $("#type").val(type);
    if (type != "") {
        getMonth(type, vSalaryType);
    }
}
function RptBonusWork() {

    document.getElementById('pMonthId').style.display = "flex";
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    document.getElementById('comEmployeeId').style.display = "flex";
    document.getElementById('comOccasion').style.display = "flex";
    document.getElementById('pSalaryType').style.display = "flex";
    document.getElementById('rdoMoneyTransferTypeId').style.display = "flex";
    document.getElementById('rdoBonusAmount').style.display = "flex";
    document.getElementById('rdoRptType').style.display = "flex";

    clear();
    var type = "RptBonus";
    var vSalaryType = $("input[name='vSalaryType']:checked").val();

    $("#type").val(type);
    if (type != "") {
        getMonth(type, vSalaryType);
    }
}
function RptPaySlipWork() {
    document.getElementById('pMonthId').style.display = "flex";
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    document.getElementById('comEmployeeId').style.display = "flex";
    document.getElementById('pSalaryType').style.display = "flex";
    document.getElementById('pSalaryHoldStatus').style.display = "flex";
    clear();
    var type = "RptPaySlip";
    var vSalaryType = $("input[name='vSalaryType']:checked").val();

    $("#type").val(type);
    if (type != "") {
        getMonth(type, vSalaryType);
    }
}
function RptBankAdviceWithForwardingLetterWork() {

    document.getElementById('pDate').style.display = "flex";
    document.getElementById('pMonthId').style.display = "flex"
    document.getElementById('pBankId').style.display = "flex";
    document.getElementById('pBankBranchId').style.display = "flex";
    document.getElementById('pDesignation').style.display = "flex";
    document.getElementById('comAccountNo').style.display = "flex";
    document.getElementById('pAddress').style.display = "flex";
    document.getElementById('comReferenceNo').style.display = "flex";
    document.getElementById('rdoBankTypeId').style.display = "flex";
    document.getElementById('pSalaryHoldStatus').style.display = "flex";
    clear();
    var type = "RptBankAdviceWithForwardingLetter";
    $("#type").val(type);
    if (type != "") {
        getMonth(type, "0");
    }
}
function RptBonusAdviceWork() {

    document.getElementById('pDate').style.display = "flex";
    document.getElementById('pMonthId').style.display = "flex"
    document.getElementById('pBankId').style.display = "flex";
    document.getElementById('pBankBranchId').style.display = "flex";
    document.getElementById('pDesignation').style.display = "flex";
    document.getElementById('comAccountNo').style.display = "flex";
    document.getElementById('pAddress').style.display = "flex";
    document.getElementById('comReferenceNo').style.display = "flex";
    document.getElementById('rdoBankTypeId').style.display = "flex";
    clear();
    var type = "RptBonusAdvice";
    $("#type").val(type);
    if (type != "") {
        getMonth(type, "0");
    }
}


function RptNoteRequisitionWork() {
    document.getElementById('pDate').style.display = "flex";
    document.getElementById('pMonthId').style.display = "flex"
    document.getElementById('pDesignation').style.display = "flex";
    document.getElementById('pBankId').style.display = "flex";
    document.getElementById('pBranchName').style.display = "flex";
    document.getElementById('pAddress').style.display = "flex";
    document.getElementById('comAccountNo').style.display = "flex";

    clear();
    var type = "RptNoteRequisition";
    $("#type").val(type);
    if (type != "") {
        getMonth(type, "0");
    }
}

function RptSummaryReportOfSalaryWork() {
    document.getElementById('pMonthId').style.display = "flex";
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    clear();
    var type = "RptSummaryReportOfSalary";
    $("#type").val(type);
    if (type != "") {
        getMonth(type, "0");
    }
}
function RptIncomeTaxWork() {
    document.getElementById('comFiscYear').style.display = "flex";
    document.getElementById('comEmployeeId').style.display = "flex";
    clear();
    var type = "RptIncomeTax";
    $("#type").val(type);
    if (type != "") {
        getFiscalYear(type);
    }
}
function RptIncomeTaxSummaryWork() {
    document.getElementById('comFiscYear').style.display = "flex";
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    document.getElementById('comEmployeeId').style.display = "flex";
    clear();
    var type = "RptIncomeTaxSummary";
    $("#type").val(type);
    if (type != "") {
        getFiscalYear(type);
    }
}
function RptIncomeTaxCalculationWork() {
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    document.getElementById('comEmployeeId').style.display = "flex";
    document.getElementById('divSalaryMonth').style.display = "flex";
    document.getElementById('divTotalBonusYear').style.display = "flex";

    clear();
    var type = "RptIncomeTaxCalculation";
    $("#type").val(type);
    if (type != "") {
        getUnit(type, "0", "0", "0", "0", "0", "0");
    }
}


function RptSalaryCertificateWork() {
    document.getElementById('pDate').style.display = "flex";
    document.getElementById('pMonthId').style.display = "flex";
    document.getElementById('comEmployeeId').style.display = "flex";
    document.getElementById('comCertifiedBy').style.display = "flex";
    document.getElementById('comDesignation').style.display = "flex";
    document.getElementById('comContact').style.display = "flex";
    clear();
    var type = "RptSalaryCertificate";
    var vSalaryType = $("input[name='vSalaryType']:checked").val();

    $("#type").val(type);
    if (type != "") {
        getMonth(type, '0');
        getCertifiedBy(type);
    }
}


function RptOtherEarningWork() {
    document.getElementById('pMonthId').style.display = "flex";
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    document.getElementById('comEmployeeId').style.display = "flex";
    clear();
    var type = "RptOtherEarning";
    $("#type").val(type);
    if (type != "") {
        getMonth(type, "0");
    }
}

function RptOtherDeductionWork() {
    document.getElementById('pMonthId').style.display = "flex";
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    document.getElementById('comEmployeeId').style.display = "flex";
    clear();
    var type = "RptOtherDeduction";
    $("#type").val(type);
    if (type != "") {
        getMonth(type, "0");
    }
}
function RptMobileExtraWork() {
    document.getElementById('pMonthId').style.display = "flex";
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    document.getElementById('comEmployeeId').style.display = "flex";
    clear();
    var type = "RptMobileExtra";
    $("#type").val(type);
    if (type != "") {
        getMonth(type, "0");
    }
}



/*Salary Report Data Load Action Start*/

/*OT Report Data Load Action Start*/
function RptMonthWiseOfStatementWork() {
    document.getElementById('pMonthId').style.display = "flex";
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    clear();
    var type = "RptMonthWiseOfStatement";
    $("#type").val(type);
    if (type != "") {
        getMonth(type, "0");
    }
}
/*OT Report Data Load Action End*/

/*Loan Report Data Load Action Start*/
function RptLoanApplicationWork() {
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('comEmployeeId').style.display = "flex";
    document.getElementById('comApplicationDate').style.display = "flex";
    ;
    clear();
    var type = "RptLoanApplication";
    $("#type").val(type);
    if (type != "") {
        getUnit(type, "0", "0", "0", "0", "0");
    }

}
function RptIndividualLoanStatementWork() {
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('comEmployeeId').style.display = "flex";
    document.getElementById('fromDate').style.display = "flex";
    document.getElementById('comLoanStatus').style.display = "flex"
    /*   document.getElementById('toDate').style.display = "flex";*/

    clear();
    var type = "RptIndividualLoanStatement";
    $("#type").val(type);
    if (type != "") {
        getUnit(type, "0", "0", "0", "0", "0");
    }
}
function RptLoanRegisterWork() {
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    document.getElementById('comEmployeeId').style.display = "flex";
    document.getElementById('fromDate').style.display = "flex";
    document.getElementById('comLoanStatus').style.display = "flex"

    clear();
    var type = "RptLoanRegister";
    $("#type").val(type);
    if (type != "") {
        getUnit(type, "0", "0", "0", "0", "0");
    }
}
function RptAdvanceSalaryLoanWork() {
    document.getElementById('pMonthId').style.display = "flex";
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    document.getElementById('comEmployeeId').style.display = "flex";
    clear();
    var type = "RptAdvanceSalaryLoan";
    $("#type").val(type);
    if (type != "") {
        getMonth(type, "0");
    }
}
function RptAdvanceSalaryLoanRegisterWork() {
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    document.getElementById('comEmployeeId').style.display = "flex";
    document.getElementById('fromDate').style.display = "flex";
    document.getElementById('comLoanStatus').style.display = "flex"
    clear();
    var type = "RptAdvanceSalaryLoanRegister";
    $("#type").val(type);
    if (type != "") {
        getUnit(type, "0", "0", "0", "0", "0");

    }
}

/*Loan Report Data Load Action End*/

/*Leave Report Data Load Action Start*/
function RptLeaveApplicationWork() {
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('comEmployeeId').style.display = "flex";
    document.getElementById('comApplicationDate').style.display = "flex";
    clear();
    var type = "RptLeaveApplication";
    $("#type").val(type);
    if (type != "") {
        getUnit(type, "0", "0", "0", "0", "0");
    }
}
function RptLeaveRegisterWork() {
    document.getElementById('comYear').style.display = "flex";
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    clear();
    var type = "RptLeaveRegister";
    $("#type").val(type);
    var inpYear = $("#inpYear").val();
    if (type != "") {
        getUnit(type, "0", "0", "0", "0", "0", "0", "0", "0", "0", "0", "0");
    }
}
function LeaveEncashmentWork() {
    document.getElementById('comYear').style.display = "flex";
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    clear();
    var type = "RptLeaveEncashment";
    $("#type").val(type);
    var inpYear = $("#inpYear").val();
    if (type != "") {
        getUnit(type, "0", "0", "0", "0", "0", "0", "0", "0", "0", "0", "0");
    }
}

function RptIndividualLeaveRegisterWork() {
    document.getElementById('comYear').style.display = "flex";
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    document.getElementById('comEmployeeId').style.display = "flex";
    clear();
    var type = "RptIndividualLeaveRegister";
    $("#type").val(type);
    var inpYear = $("#inpYear").val();
    if (type != "") {
        getUnit(type, "0", "0", "0", "0", "0", "0", "0", "0", "0", "0", "0");
    }
}

/*Leave Report Data Load Action End*/

/*Other Report Data Load Action Start*/
function RptItemDistrubationReportWork() {
    document.getElementById('comItem').style.display = "flex";
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    document.getElementById('comApplicationDate').style.display = "flex";
    clear();
    var type = "RptItemDistrubationReport";
    $("#type").val(type);
    if (type != "") {
        getUnit(type, "0", "0", "0", "0", "0", "0", "0", "0", "0", "0", "0");
    }
}
function RptIncrementProposalWork() {
    document.getElementById('pIncrementProposal').style.display = "flex";
    document.getElementById('comYear').style.display = "flex";
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    document.getElementById('comEmployeeId').style.display = "flex";
    clear();
    var type = "RptIncrementProposal";
    var vIncrementProposal = $("input[name='vIncrementProposal']:checked").val();
    var inpYear = $("#inpYear").val();
    $("#type").val(type);
    if (type != "") {
        getUnit(type, inpYear, "0", "0", "0", "0", "0", "0", "0", vIncrementProposal);
    }
}


function RptRptIncrementReportWork() {
    document.getElementById('comYear').style.display = "flex";
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    document.getElementById('comEmployeeId').style.display = "flex";
    clear();
    var type = "RptIncrementReport";
    var inpYear = $("#inpYear").val();
    $("#type").val(type);
    if (type != "") {
        getUnit(type, inpYear, "0", "0", "0", "0", "0", "0", "0", "0", "0");
    }
}
function RptSalaryIncrementStatementWork() {
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    document.getElementById('comEmployeeId').style.display = "flex";
    document.getElementById('comServiceStatus').style.display = "flex";

    clear();
    var type = "RptSalaryIncrementStatement";
    $("#type").val(type);
    if (type != "") {
        getUnit(type, "0", "0", "0", "0", "0", "0", "0", "0", "0");
    }
}
function RptEmployeePromotionReportWork() {
    document.getElementById('pDate').style.display = "flex";
    document.getElementById('comYear').style.display = "flex";
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    document.getElementById('comEmployeeId').style.display = "flex";

    clear();
    var type = "RptEmployeePromotionReport";
    var inpYear = $("#inpYear").val();
    $("#type").val(type);
    if (type != "") {
        getUnit(type, inpYear, "0", "0", "0", "0", "0", "0", "0", "0", "0");
    }
}
function RptContributionAndProfitStatementWork() {
    document.getElementById('comYear').style.display = "flex";
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    document.getElementById('comEmployeeId').style.display = "flex";
    clear();
    var type = "RptContributionAndProfitStatement";
    var inpYear = $("#inpYear").val();
    $("#type").val(type);
    if (type != "") {
        getUnit(type, inpYear, "0", "0", "0", "0", "0", "0", "0", "0");
    }
}
function RptContributionAndProfitSummaryWork() {
    document.getElementById('comYear').style.display = "flex";
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    document.getElementById('comEmployeeId').style.display = "flex";
    document.getElementById('comServiceStatus').style.display = "flex";
    clear();
    var type = "RptContributionAndProfitSummary";
    var inpYear = $("#inpYear").val();
    $("#type").val(type);
    if (type != "") {
        getUnit(type, inpYear, "0", "0", "0", "0", "0", "0", "0", "0");
    }
}
function RptContributionAndProfitDetailsWork() {
    document.getElementById('comYear').style.display = "flex";
    document.getElementById('pUnitId').style.display = "flex";
    document.getElementById('pDepartmentId').style.display = "flex";
    document.getElementById('pSectionId').style.display = "flex";
    document.getElementById('comEmployeeId').style.display = "flex";
    document.getElementById('comServiceStatus').style.display = "flex";
    clear();
    var type = "RptContributionAndProfitDetails";
    var inpYear = $("#inpYear").val();
    $("#type").val(type);
    if (type != "") {
        getUnit(type, inpYear, "0", "0", "0", "0", "0", "0", "0", "0");
    }
}
function Orientation() {
    document.getElementById('pDate').style.display = "flex";
    document.getElementById('comTo').style.display = "flex";
    clear();
    var type = "RptOrientation";
    var dDate = getBdToDbFormat($("#dDate").val());
    $("#type").val(type);
    if (type != "") {
        getTo(type, dDate);
    }
}

/*Other Report Data Load Action End*/

// action for option group, select option, Radio etc action Start
function othersAction() {
    var vType = "";
    $('input[type=radio][name=vStatus]').change(function () {
        vType = $("#type").val();
        var vStatus = $("input[name='vStatus']:checked").val();

        if (vType != "") {
            if (vStatus == "Active") {
                vStatus = "1";
            }
            else if (vStatus == "Inactive") {
                vStatus = "0";
            }
            else if (vStatus == "All") {
                vStatus = "%";
            }
            if (vType == "RptEmployeeList") {
                getUnit(vType, "0", "0", vStatus, "0", "0", "0", "0", "0");
            }
        }
    });

    $('input[type=radio][name=vReportType]').change(function () {
        type = $("#type").val();
        var vReportType = $("input[name='vReportType']:checked").val();
        var inpFromDateTo = getBdToDbFormat($("#inpFromDateTo").val());
        var inpToDateTo = getBdToDbFormat($("#inpToDateTo").val());
        if (type != "") {

            if (type == "RptConfirmationJoiningLeftList") {
                if (inpFromDateTo != "" && inpFromDateTo != "") {
                    getCategory(type, vReportType, inpFromDateTo, inpToDateTo);
                }
            }
        }

    });

    $('input[type=radio][name=vIncrementProposal]').change(function () {
        type = $("#type").val();
        var vIncrementProposal = $("input[name='vIncrementProposal']:checked").val();
        var inpYear = $("#inpYear").val();
        if (type != "") {

            if (type == "RptIncrementProposal") {
                if (inpYear != "" && inpYear != "") {
                    getUnit(type, inpYear, "0", "0", "0", "0", "0", "0", "0", vIncrementProposal);
                }
            }
        }

    });

    $("#dDate").change(function () {
        var dDate = getBdToDbFormat($("#dDate").val());
        var type = $("#type").val();
        if (type != "") {
            if (isValidDate(dDate)) {
                if (
                    type == "RptDailyAttendanceStatement" || type == "RptDailyAbsentStatement" || type == "RptAttendanceDailyMovement" ||
                    type == "RptDailyLateInEmployeeList" || type == "RptDailyEarlyOutEmployeeList"
                ) {
                    getUnit(type, dDate, "0", "0", "0");
                    $('#vUnitId').focus();
                }
                else (type == "RptOrientation")

                {
                    getTo(type, dDate);
                    $('#vTo').focus();
                }
            }
        }
    });

    $("#inpYear").keyup(function () {
        var type = $("#type").val();
        var vIncrementProposal = $("input[name='vIncrementProposal']:checked").val();
        var inpYear = $("#inpYear").val();
        if (type == "RptIncrementProposal") {
            if (inpYear != "" && inpYear != "0") {
                getUnit(type, inpYear, "0", "0", "0", "0", "0", "0", "0", vIncrementProposal);
            }
        }
        else if (type == "RptIncrementReport" || type == "RptEmployeePromotionReport") {
            if (inpYear != "" && inpYear != "0") {
                getUnit(type, inpYear, "0", "0", "0", "0", "0", "0", "0", "0", "0");

            }
        }
        else if (type == "RptLeaveRegister" || type == "RptLeaveEncashment") {
            if (inpYear != "" && inpYear != "0") {
                getUnit(type, inpYear, "0", "0", "0", "0", "0", "0", "0", "0", "0");
            }
        }
        else if (type == "RptIndividualLeaveRegister") {
            if (inpYear != "" && inpYear != "0") {
                getUnit(type, inpYear, "0", "0", "0", "0", "0", "0", "0", "0", "0");
            }
        }
        else if (type == "RptContributionAndProfitStatement" || type == "RptContributionAndProfitStatement"
            || type == "RptContributionAndProfitDetails") {
            if (inpYear != "" && inpYear != "0") {
                getUnit(type, inpYear, "0", "0", "0", "0", "0", "0", "0", "0");
            }
        }
    });

    $('input[type=radio][name=vSalaryType]').change(function () {
        vType = $("#type").val();
        var vSalaryType = $("input[name='vSalaryType']:checked").val();

        if (vType != "") {
            if (vSalaryType != "") {
                getMonth(vType, vSalaryType);
            }
        }
    });
    $('input[type=radio][name=vAttendanceType]').change(function () {
        vType = $("#type").val();
        var vAttendanceType = $("input[name='vAttendanceType']:checked").val();

        if (vType != "") {
            if (vAttendanceType != "") {
                getMonth(vType, vAttendanceType);
            }
        }
    });

    $("#inpFromDateTo").change(function () {
        var type = $("#type").val();
        var vReportType = $("input[name='vReportType']:checked").val();
        var inpFromDateTo = getBdToDbFormat($("#inpFromDateTo").val());
        var inpToDateTo = getBdToDbFormat($("#inpToDateTo").val());
        if (type != "") {
            if (type == "RptConfirmationJoiningLeftList") {
                if (inpFromDateTo != "" && inpToDateTo != "") {
                    getCategory(type, vReportType, inpFromDateTo, inpToDateTo);
                    $('#vCategory').focus();
                }
            }
        }
    });

    $("#inpToDateTo").change(function () {
        var type = $("#type").val();
        var vReportType = $("input[name='vReportType']:checked").val();
        var inpFromDateTo = getBdToDbFormat($("#inpFromDateTo").val());
        var inpToDateTo = getBdToDbFormat($("#inpToDateTo").val());
        if (type != "") {
            if (type == "RptConfirmationJoiningLeftList") {
                if (inpFromDateTo != "" && inpToDateTo != "") {
                    getCategory(type, vReportType, inpFromDateTo, inpToDateTo);
                    $('#vCategory').focus();
                }
            }
        }
    });

    $("#vMonth").change(function () {
        var type = $("#type").val();
        var vSalaryType = $("input[name='vSalaryType']:checked").val();
        var vMonth = $("#vMonth").val();
        var vAttendanceType = $("input[name='vAttendanceType']:checked").val();
        if (type != "") {
            if (vMonth != "" && vMonth != "0") {
                if (type == "RptMonthlySalary" || type == "RptPaySlip" || type == "RptBonus") {
                    getUnit(type, "0", vMonth, "0", vSalaryType, "0", "0");
                }
                else if (type == "RptMonthWiseOfStatement" || type == "RptSummaryReportOfSalary") {
                    getUnit(type, "0", vMonth, "0", "0", "0", "0");
                }
                else if (
                    type == "RptIndividualEmployeeAttendance" || type == "RptMonthlyAttendanceSummary" || type == "RptShortViewOfAttendance" ||
                    type == "RptMonthlyDutyRoster" || type == "RptInLieu" || type == "RptAdvanceSalaryLoan"
                    || type == "RptOtherEarning" || type == "RptOtherDeduction" || type == "RptMobileExtra"
                    || type == "RptIncompleteAttendanceList") {
                    getUnit(type, "0", vMonth, "0", "0", "0", "0");
                }
                else if (type == "RptMonthlyAttendanceSummaryManual" || type == "RptMonthlyMealInformation") {
                    getUnit(type, "0", vMonth, "0", vAttendanceType, "0", "0");
                }
                else if (type == "RptBankAdviceWithForwardingLetter" || type == "RptNoteRequisition" || type == "RptBonusAdvice") {
                    getBank(type, vMonth);
                }
                else if (type == "RptSalaryCertificate") {
                    getEmployee(type, "0", "0", vMonth, "0", "0", "0", "0", "0", "0", "0", "0", "0");
                }
            }
        }
    });

    $("#vCertifiedById").change(function () {
        var type = $("#type").val();
        var vCertifiedById = $("#vCertifiedById").val();

        if (type != "") {
            if (vCertifiedById != "" && vCertifiedById != "0") {
                if (type == "RptCertification" || type == "RptSalaryCertificate") {
                    getDesignation(type, vCertifiedById)
                }
            }
        }
    });

    $("#vBankId").change(function () {
        var type = $("#type").val();
        var vMonth = $("#vMonth").val();
        var vBankId = $("#vBankId").val();
        if (type != "") {
            if (vMonth != "" && vMonth != "0" && vBankId != "" && vBankId != "0") {
                if (
                    type == "RptBankAdviceWithForwardingLetter" || type == "RptNoteRequisition" || type == "RptBonusAdvice"
                ) {
                    getBankBranch(type, vMonth, vBankId);
                }
            }
        }
    });

    $("#vItemName").change(function () {
        var type = $("#type").val();
        var vUnitId = $("#vUnitId").val();
        var vDepartmentId = $("#vDepartmentId").val();
        var vSectionId = $("#vSectionId").val();
        var vItemName = $("#vItemName").val();

        if (type == "RptItemDistrubationReport") {
            if (vUnitId != "" && vUnitId != "0") {
                if (vDepartmentId != "" && vDepartmentId != "0") {
                    if (vSectionId != "" && vSectionId != "0") {
                        if (vItemName != "" && vItemName != "0") {
                            getApplicationDate(type, vUnitId, vDepartmentId, vSectionId, "0", vItemName);
                        }
                    }
                }
            }
        }
    });

    $("#vCategory").change(function () {
        var type = $("#type").val();
        var inpFromDateTo = getBdToDbFormat($("#inpFromDateTo").val());
        var inpToDateTo = getBdToDbFormat($("#inpToDateTo").val());
        var vCategory = $("#vCategory").val();
        var vReportType = $("input[name='vReportType']:checked").val();
        if (type == "RptConfirmationJoiningLeftList") {
            if (vCategory != "" && vCategory != "0") {
                getUnit(type, "0", "0", "0", "0", vCategory, vReportType, inpFromDateTo, inpToDateTo, "0", "0");
            }
        }
        else if (type == "RptLengthOfService" || type == "RptEmployeeList") {
            if (vCategory != "" && vCategory != "0") {
                getUnit(type, "0", "0", "0", "0", vCategory, "0", "0", "0", "0", "0", "0");
            }
        }
    });

    $("#vFiscalYear").change(function () {
        var type = $("#type").val();
        var vFiscalYear = $("#vFiscalYear").val();

        if (type != "") {
            if (vFiscalYear != "" && vFiscalYear != "0") {
                if (type == "RptIncomeTax") {
                    getEmployee(type, "0", "0", "0", "0", "0", "0", "0", "0", "0", "0", "0", "0", "0", vFiscalYear);
                    $('#vEmployeeId').focus();
                }
                if (type == "RptIncomeTaxSummary") {
                    getUnit(type, "0", "0", "0", "0", "0", "0", "0", "0", "0", "0", vFiscalYear);
                    //type, dDate, vMonth, vStatus, vSalaryType, vCategory, vReportType, inpFromDateTo, inpToDateTo, vIncrementProposal, vItemName, vFiscalYear
                    $('#vUnitId').focus();
                }
            }
        }
    });
    $("#vUnitId").change(function () {
        var type = $("#type").val();
        var dDate = $("#dDate").val();
        var vMonth = $("#vMonth").val();
        var inpFromDateTo = getBdToDbFormat($("#inpFromDateTo").val());
        var inpToDateTo = getBdToDbFormat($("#inpToDateTo").val());
        var vItemName = $("#vItemName").val();
        var vCategory = $("#vCategory").val();
        var vReportType = $("input[name='vReportType']:checked").val();
        var vIncrementProposal = $("input[name='vIncrementProposal']:checked").val();
        var inpYear = $("#inpYear").val();
        var vFiscalYear = $("#vFiscalYear").val();
        var vUnitId = $("#vUnitId").val();
        var vStatus = $("input[name='vStatus']:checked").val();
        if (vStatus == "Active") {
            vStatus = "1";
        }
        else if (vStatus == "Inactive") {
            vStatus = "0";
        }
        else if (vStatus == "All") {
            vStatus = "%";
        }
        var vSalaryType = $("input[name='vSalaryType']:checked").val();
        var vAttendanceType = $("input[name='vAttendanceType']:checked").val();
        var vMoneyTransferType = $("input[name='vMoneyTransferType']:checked").val();

        if (type != "") {
            if (type == "RptLoanRegister" || type == "RptAdvanceSalaryLoanRegister") {
                if (vUnitId != "" && vUnitId != "0") {
                    getDepartment(type, "0", "0", vUnitId, vStatus, "0", "0", "0", "0", "0");
                }
            }

            else if (type == "RptAdvanceSalaryLoanRegister") {
                console.log("getDepartment", Hello)
                if (vUnitId != "" && vUnitId != "0") {
                    getDepartment(type, "0", "0", vUnitId, "0", "0", "0", "0", "0", "0");
                }
            }

            else if (type == "RptIdCard" || type == "RptItemDistrubationReport" || type == "RptIncomeTaxCalculation") {
                if (vUnitId != "" && vUnitId != "0") {
                    getDepartment(type, "0", "0", vUnitId, "0", "0", "0", "0", "0", "0");
                }
            }
            else if (type == "RptConfirmationJoiningLeftList") {
                if (vCategory != "" && vCategory != "0" && vUnitId != "" && vUnitId != "0") {
                    getDepartment(type, "0", "0", vUnitId, "0", "0", vCategory, vReportType, inpFromDateTo, inpToDateTo, "0", "0");
                }

            }
            else if (type == "RptEmployeeList" || type == "RptLengthOfService") {
                if (vCategory != "" && vCategory != "0" && vUnitId != "" && vUnitId != "0") {
                    getDepartment(type, "0", "0", vUnitId, "0", "0", vCategory, "0", "0", "0");
                }

            }
            else if (type == "RptDailyAttendanceStatement" || type == "RptDailyAbsentStatement" || type == "RptAttendanceDailyMovement" ||
                type == "RptDailyLateInEmployeeList" || type == "RptDailyEarlyOutEmployeeList") {
                if ((dDate != "" && dDate != "0") && (vUnitId != "" && vUnitId != "0")) {
                    var dDate = getBdToDbFormat(dDate);
                    getDepartment(type, dDate, "0", vUnitId, "0", "0", "0", "0", "0", "0");
                }
            }
            else if (type == "RptMonthlySalary" || type == "RptPaySlip" || type == "RptBonus") {
                if ((vMonth != "" && vMonth != "0") && (vUnitId != "" && vUnitId != "0")) {
                    getDepartment(type, "0", vMonth, vUnitId, "0", vSalaryType);
                }
            }
            else if (type == "RptMonthWiseOfStatement" || type == "RptSummaryReportOfSalary") {
                if ((vMonth != "" && vMonth != "0") && (vUnitId != "" && vUnitId != "0")) {
                    getDepartment(type, "0", vMonth, vUnitId, "0", "0", "0", "0", "0", "0");
                }
            }
            else if (type == "RptLoanApplication" || type == "RptIndividualLoanStatement" || type == "RptLeaveApplication") {
                if ((vUnitId != "" && vUnitId != "0")) {
                    getEmployee(type, "0", "0", "0", vUnitId, "0", "0", "0", "0", "0", "0", "0", "0");
                }
            }
            else if (type == "RptLeaveRegister" || type == "RptIndividualLeaveRegister" || type == "RptLeaveEncashment") {
                if ((vUnitId != "" && vUnitId != "0")) {
                    getDepartment(type, inpYear, "0", vUnitId, "0", "0", "0", "0", "0", "0", "0", "0", "0");
                }
            }
            else if (type == "RptIndividualEmployeeAttendance" || type == "RptMonthlyAttendanceSummary" ||
                type == "RptShortViewOfAttendance" || type == "RptMonthlyDutyRoster" || type == "RptInLieu"
                || type == "RptAdvanceSalaryLoan"
                || type == "RptOtherEarning" || type == "RptOtherDeduction" || type == "RptMobileExtra") {
                if ((vMonth != "" && vMonth != "0") && (vUnitId != "" && vUnitId != "0")) {
                    getDepartment(type, "0", vMonth, vUnitId, "0", "0", "0", "0", "0", "0");
                }
            }

            else if (type == "RptShiftInfo" || type == "RptRamadan") {
                if ((vUnitId != "" && vUnitId != "0")) {
                    getDepartment(type, "0", "0", vUnitId, "0", "0", "0", "0", "0", "0");
                }
            }

            else if (type == "RptMonthlyAttendanceSummaryManual" || type == "RptMonthlyMealInformation" ||
                type == "RptIncompleteAttendanceList") {
                if ((vMonth != "" && vMonth != "0") && (vUnitId != "" && vUnitId != "0")) {
                    getDepartment(type, "0", vMonth, vUnitId, "0", vAttendanceType);
                }
            }
            else if (type == "RptIncrementProposal") {
                if ((inpYear != "" && inpYear != "0") && (vUnitId != "" && vUnitId != "0")) {
                    getDepartment(type, inpYear, "0", vUnitId, "0", "0", "0", "0", "0", "0", vIncrementProposal);
                }
            }

            else if (type == "RptContributionAndProfitStatement" || type == "RptContributionAndProfitSummary"
                || type == "RptContributionAndProfitDetails") {
                if ((inpYear != "" && inpYear != "0") && (vUnitId != "" && vUnitId != "0")) {
                    getDepartment(type, inpYear, "0", vUnitId, "0", "0", "0", "0", "0", "0", "0", "0", "0");
                }
            }

            else if (type == "RptIncrementReport" || type == "RptEmployeePromotionReport") {
                if ((inpYear != "" && inpYear != "0") && (vUnitId != "" && vUnitId != "0")) {
                    getDepartment(type, inpYear, "0", vUnitId, "0", "0", "0", "0", "0", "0", "0", "0", "0");
                }
            }
            else if (type == "RptSalaryIncrementStatement") {
                if (vUnitId != "" && vUnitId != "0") {
                    getDepartment(type, "0", "0", vUnitId, "0", "0", "0", "0", "0", "0", "0", "0", "0");
                }
            }
            else if (type == "RptIncomeTaxSummary") {
                if (vFiscalYear != "" && vFiscalYear != "0" && vUnitId != "" && vUnitId != "0") {
                    getDepartment(type, "0", "0", vUnitId, "0", "0", "0", "0", "0", "0", "0", "0", vFiscalYear);
                }
            }
        }
    });

    $("#vDepartmentId").change(function () {
        var type = $("#type").val();
        var dDate = $("#dDate").val();
        var vMonth = $("#vMonth").val();
        var inpFromDateTo = getBdToDbFormat($("#inpFromDateTo").val());
        var inpToDateTo = getBdToDbFormat($("#inpToDateTo").val());
        var vItemName = $("#vItemName").val();
        var vCategory = $("#vCategory").val();
        var vReportType = $("input[name='vReportType']:checked").val();
        var vIncrementProposal = $("input[name='vIncrementProposal']:checked").val();
        var inpYear = $("#inpYear").val();
        var vFiscalYear = $("#vFiscalYear").val();
        var vUnitId = $("#vUnitId").val();
        var vDepartmentId = $("#vDepartmentId").val();
        var vStatus = $("input[name='vStatus']:checked").val();
        if (vStatus == "Active") {
            vStatus = "1";
        }
        else if (vStatus == "Inactive") {
            vStatus = "0";
        }
        else if (vStatus == "All") {
            vStatus = "%";
        }
        var vSalaryType = $("input[name='vSalaryType']:checked").val();
        var vAttendanceType = $("input[name='vAttendanceType']:checked").val();


        if (type != "") {
            if (type == "RptLoanRegister" || type == "RptAdvanceSalaryLoanRegister") {
                if ((vDepartmentId != "" && vDepartmentId != "0") && (vUnitId != "" && vUnitId != "0")) {
                    getSection(type, "0", "0", vUnitId, vDepartmentId, vStatus, vSalaryType, "0", "0", "0", "0");
                }
            }
            else if (type == "RptIdCard" || type == "RptItemDistrubationReport" || type == "RptIncomeTaxCalculation") {
                if ((vDepartmentId != "" && vDepartmentId != "0") && (vUnitId != "" && vUnitId != "0")) {
                    getSection(type, "0", "0", vUnitId, vDepartmentId, "0", "0", "0", "0", "0", "0");
                }
            }
            /*  vCategory, vReportType, inpFromDateTo, inpToDateTo*/

            else if (type == "RptConfirmationJoiningLeftList") {
                if ((vCategory != "" && vCategory != "0") && (vDepartmentId != "" && vDepartmentId != "0") && (vUnitId != "" && vUnitId != "0")) {
                    getSection(type, "0", "0", vUnitId, vDepartmentId, "0", "0", vCategory, vReportType, inpFromDateTo, inpToDateTo, "0", "0");
                }
            }

            else if (type == "RptEmployeeList" || type == "RptLengthOfService") {
                if ((vCategory != "" && vCategory != "0") && (vDepartmentId != "" && vDepartmentId != "0") && (vUnitId != "" && vUnitId != "0")) {

                    var vSectionId = $("#vSectionId").val();

                    getSection(type, "0", "0", vUnitId, vDepartmentId, "0", "0", vCategory, "0", "0", "0");

                    if (vSectionId == "%") {
                        console.log("vSectionId: ", vSectionId);
                        $("#vSectionId").val(vSectionId).trigger('change');
                    }
                }
            }

            else if (
                type == "RptDailyAttendanceStatement" || type == "RptDailyAbsentStatement" || type == "RptAttendanceDailyMovement" ||
                type == "RptDailyLateInEmployeeList" || type == "RptDailyEarlyOutEmployeeList"

            ) {

                if (
                    (dDate != "" && dDate != "0") && (vUnitId != "" && vUnitId != "0") && (vDepartmentId != "" && vDepartmentId != "0")
                ) {
                    var dDate = getBdToDbFormat(dDate);
                    getSection(type, dDate, "0", vUnitId, vDepartmentId, "0", "0", "0", "0", "0", "0");
                }
            }
            else if (type == "RptMonthlySalary" || type == "RptPaySlip" || type == "RptBonus") {
                if ((vMonth != "" && vMonth != "0") && (vUnitId != "" && vUnitId != "0") && (vDepartmentId != "" && vDepartmentId != "0")) {
                    getSection(type, "0", vMonth, vUnitId, vDepartmentId, "0", vSalaryType);
                }
            }
            else if (type == "RptMonthWiseOfStatement" || type == "RptSummaryReportOfSalary") {
                if ((vMonth != "" && vMonth != "0") && (vUnitId != "" && vUnitId != "0") && (vDepartmentId != "" && vDepartmentId != "0")) {
                    getSection(type, "0", vMonth, vUnitId, vDepartmentId, "0", "0", "0", "0", "0", "0");
                }
            }
            else if (type == "RptIndividualEmployeeAttendance" || type == "RptMonthlyAttendanceSummary" || type == "RptShortViewOfAttendance"
                || type == "RptMonthlyDutyRoster" || type == "RptInLieu" || type == "RptAdvanceSalaryLoan" || type == "RptOtherEarning"
                || type == "RptOtherDeduction" || type == "RptMobileExtra") {
                if ((vMonth != "" && vMonth != "0") && (vUnitId != "" && vUnitId != "0") && (vDepartmentId != "" && vDepartmentId != "0")) {
                    getSection(type, "0", vMonth, vUnitId, vDepartmentId, "0", "0", "0", "0", "0", "0");
                }
            }

            else if (type == "RptShiftInfo" ) {
                if ((vUnitId != "" && vUnitId != "0") && (vDepartmentId != "" && vDepartmentId != "0")) {
                    getSection(type, "0", "0", vUnitId, vDepartmentId, "0", "0", "0", "0", "0", "0");
                }
            }
            
            else if (type == "RptRamadan") {
                if ((vUnitId != "" && vUnitId != "0") && (vDepartmentId != "" && vDepartmentId != "0")) {
                    getSection(type, "0", "0", vUnitId, vDepartmentId, "0", "0", "0", "0", "0", "0");
                }
            }

            else if (type == "RptMonthlyAttendanceSummaryManual" || type == "RptMonthlyMealInformation" || type == "RptIncompleteAttendanceList") {
                if ((vMonth != "" && vMonth != "0") && (vUnitId != "" && vUnitId != "0") && (vDepartmentId != "" && vDepartmentId != "0")) {
                    getSection(type, "0", vMonth, vUnitId, vDepartmentId, "0", vAttendanceType, "0", "0", "0", "0");
                }
            }

            else if (type == "RptLeaveRegister" || type == "RptIndividualLeaveRegister" || type == "RptLeaveEncashment") {
                if ((inpYear != "" && inpYear != "0") && (vUnitId != "" && vUnitId != "0") && (vDepartmentId != "" && vDepartmentId != "0")) {
                    getSection(type, inpYear, "0", vUnitId, vDepartmentId, "0", "0", "0", "0", "0", "0", "0");
                }
            }
            else if (type == "RptIncrementProposal") {
                if ((inpYear != "" && inpYear != "0") && (vUnitId != "" && vUnitId != "0") && (vDepartmentId != "" && vDepartmentId != "0")) {
                    getSection(type, inpYear, "0", vUnitId, vDepartmentId, "0", "0", "0", "0", "0", "0", vIncrementProposal);
                }
            }

            else if (type == "RptIncrementReport" || type == "RptEmployeePromotionReport") {
                if ((inpYear != "" && inpYear != "0") && (vUnitId != "" && vUnitId != "0") && (vDepartmentId != "" && vDepartmentId != "0")) {
                    getSection(type, inpYear, "0", vUnitId, vDepartmentId, "0", "0", "0", "0", "0", "0", "0");
                }
            }
            else if (type == "RptSalaryIncrementStatement")
            {
                if ((vUnitId != "" && vUnitId != "0") && (vDepartmentId != "" && vDepartmentId != "0")) {
                    getSection(type, "0", "0", vUnitId, vDepartmentId, "0", "0", "0", "0", "0", "0", "0");
                }
            }
            else if
            (
                type == "RptContributionAndProfitStatement" || type == "RptContributionAndProfitSummary" || type == "RptContributionAndProfitDetails"
            )
            {
                if ((inpYear != "" && inpYear != "0") && (vUnitId != "" && vUnitId != "0") && (vDepartmentId != "" && vDepartmentId != "0")) {
                    getSection(type, inpYear, "0", vUnitId, vDepartmentId, "0", "0", "0", "0", "0", "0", "0");
                }
            }
            else if (type == "RptIncomeTaxSummary") {
                if ((vFiscalYear != "" && vFiscalYear != "0") && (vUnitId != "" && vUnitId != "0") && (vDepartmentId != "" && vDepartmentId != "0")) {
                    getSection(type, inpYear, "0", vUnitId, vDepartmentId, "0", "0", "0", "0", "0", "0", "0", "0", vFiscalYear);
                }
            }
        }
    });

    $("#vSectionId").change(function () {
        var type = $("#type").val();
        var vMonth = $("#vMonth").val();
        var vCategory = $("#vCategory").val();
        var vReportType = $("input[name='vReportType']:checked").val();
        var inpFromDateTo = getBdToDbFormat($("#inpFromDateTo").val());
        var inpToDateTo = getBdToDbFormat($("#inpToDateTo").val());
        var vIncrementProposal = $("input[name='vIncrementProposal']:checked").val();
        var inpYear = $("#inpYear").val();
        var vFiscalYear = $("#vFiscalYear").val();
        var vUnitId = $("#vUnitId").val();
        var vDepartmentId = $("#vDepartmentId").val();
        var vSectionId = $("#vSectionId").val();
        var vStatus = $("input[name='vStatus']:checked").val();
        var dDate = $("#dDate").val();

        if (vStatus == "Active") {
            vStatus = "1";
        }
        else if (vStatus == "Inactive") {
            vStatus = "0";
        }
        else if (vStatus == "All") {
            vStatus = "%";
        }

        var vSalaryType = $("input[name='vSalaryType']:checked").val();
        var vAttendanceType = $("input[name='vAttendanceType']:checked").val();


        if (type != "") {
            if (type == "RptLoanRegister" || type == "RptAdvanceSalaryLoanRegister") {
                if ((vUnitId != "" && vUnitId != "0") && (vDepartmentId != "" && vDepartmentId != "0") && (vSectionId != "" && vSectionId != "0")) {
                    getEmployee(type, vStatus, "0", vMonth, vUnitId, vDepartmentId, vSectionId, "0", "0", "0", "0", "0", "0");
                }
            }
            else if (type == "RptIdCard" || type == "RptIncomeTaxCalculation") {
                if ((vDepartmentId != "" && vDepartmentId != "0") && (vUnitId != "" && vUnitId != "0") && (vSectionId != "" && vSectionId != "0")) {
                    getEmployee(type, "0", "0", "0", vUnitId, vDepartmentId, vSectionId, "0", "0", "0", "0", "0", "0");
                }
            }
            else if (type == "RptConfirmationJoiningLeftList") {
                if ((vCategory != "" && vCategory != "0") && (vUnitId != "" && vUnitId != "0") && (vDepartmentId != "" && vDepartmentId != "0") && (vSectionId != "" && vSectionId != "0")) {
                    getNewDesignation(type, vUnitId, vDepartmentId, vCategory, vReportType, inpFromDateTo, inpToDateTo, vSectionId);
                }
            }
            else if (type == "RptLengthOfService") {
                if ((vCategory != "" && vCategory != "0") && (vUnitId != "" && vUnitId != "0") &&
                    (vDepartmentId != "" && vDepartmentId != "0") &&
                    (vSectionId != "" && vSectionId != "0")) {
                    getEmployee(type, "0", "0", "0", vUnitId, vDepartmentId, vSectionId, "0", "0", vCategory,
                        "0", "0", inpToDateTo);
                }
            }
            else if (type == "RptMonthlySalary" || type == "RptPaySlip" || type == "RptBonus") {
                if (
                    (vMonth != "" && vMonth != "0") && (vUnitId != "" && vUnitId != "0") && (vDepartmentId != "" && vDepartmentId != "0") &&
                    (vSectionId != "" && vSectionId != "0") && (vSalaryType != "" && vSalaryType != "0")
                ) {
                    getEmployee(type, "0", "0", vMonth, vUnitId, vDepartmentId, vSectionId, vSalaryType, "0", "0", "0", "0", "0");
                }
            }
            else if (type == "RptIndividualEmployeeAttendance" || type == "RptMonthlyAttendanceSummary" || type == "RptShortViewOfAttendance"
                || type == "RptMonthlyDutyRoster" || type == "RptInLieu" || type == "RptAdvanceSalaryLoan" || type == "RptOtherEarning" ||
                type == "RptOtherDeduction" || type == "RptMobileExtra") {
                if (
                    (vMonth != "" && vMonth != "0") && (vUnitId != "" && vUnitId != "0") &&
                    (vDepartmentId != "" && vDepartmentId != "0") &&
                    (vSectionId != "" && vSectionId != "0")
                ) {
                    getEmployee(type, "0", "0", vMonth, vUnitId, vDepartmentId, vSectionId, "0", "0", "0", "0", "0", "0");
                }
            }
            else if (type == "RptMonthlyAttendanceSummaryManual" || type == "RptMonthlyMealInformation") {
                if (
                    (vMonth != "" && vMonth != "0") && (vUnitId != "" && vUnitId != "0") && (vDepartmentId != "" && vDepartmentId != "0") && (vSectionId != "" && vSectionId != "0")
                ) {
                    getEmployee(type, "0", "0", vMonth, vUnitId, vDepartmentId, vSectionId, vAttendanceType, "0", "0", "0", "0", "0");
                }
            }
            else if
                (
                type == "RptDailyAttendanceStatement" || type == "RptDailyAbsentStatement" || type == "RptAttendanceDailyMovement" ||
                type == "RptDailyLateInEmployeeList" || type == "RptDailyEarlyOutEmployeeList"
            ) {
                if (
                    (dDate != "" && dDate != "0") && (vUnitId != "" && vUnitId != "0") && (vDepartmentId != "" && vDepartmentId != "0") && (vSectionId != "" && vSectionId != "0")
                ) {
                    var dDate = getBdToDbFormat(dDate);
                    getDesignationList(type, dDate, vUnitId, vDepartmentId, vSectionId);
                }
            }

            else if (type == "RptIncompleteAttendanceList")
            {
                if (
                    (dDate != "" && dDate != "0") && (vUnitId != "" && vUnitId != "0") && (vDepartmentId != "" && vDepartmentId != "0") &&
                    (vSectionId != "" && vSectionId != "0")
                ) {
                    var dDate = getBdToDbFormat(dDate);
                    getServiceType(type, "0", vUnitId, vDepartmentId, vSectionId, "0",vMonth);
                }
            }

            else if (type == "RptIndividualLeaveRegister") {
                if ((inpYear != "" && inpYear != "0") && (vUnitId != "" && vUnitId != "0") && (vDepartmentId != "" && vDepartmentId != "0") && (vSectionId != "" && vSectionId != "0")) {
                    getEmployee(type, "0", inpYear, "0", vUnitId, vDepartmentId, vSectionId, "0", "0", "0", "0", "0", "0", "0");
                }
            }
            else if (type == "RptIncrementProposal") {
                if ((inpYear != "" && inpYear != "0") && (vUnitId != "" && vUnitId != "0") && (vDepartmentId != "" && vDepartmentId != "0") && (vSectionId != "" && vSectionId != "0")) {
                    getEmployee(type, "0", inpYear, "0", vUnitId, vDepartmentId, vSectionId, "0", "0", "0", "0", "0", "0", vIncrementProposal);
                }
            }

            else if (type == "RptIncrementReport" || type == "RptEmployeePromotionReport") {
                if ((inpYear != "" && inpYear != "0") && (vUnitId != "" && vUnitId != "0") && (vDepartmentId != "" && vDepartmentId != "0") && (vSectionId != "" && vSectionId != "0")) {
                    getEmployee(type, "0", inpYear, "0", vUnitId, vDepartmentId, vSectionId, "0", "0", "0", "0", "0", "0", "0");
                }
            }
            else if (type == "RptSalaryIncrementStatement") {
                if ((vUnitId != "" && vUnitId != "0") && (vDepartmentId != "" && vDepartmentId != "0") &&
                    (vSectionId != "" && vSectionId != "0")) {
                    getEmployee(type, "0", "0", "0", vUnitId, vDepartmentId, vSectionId, "0", "0", "0", "0", "0", "0", "0");
                }
            }
            else if (type == "RptItemDistrubationReport") {
                if ((vUnitId != "" && vUnitId != "0") && (vDepartmentId != "" && vDepartmentId != "0") && (vSectionId != "" && vSectionId != "0")) {
                    getItem(type, vUnitId, vDepartmentId, vSectionId);
                }
            }

            else if (type == "RptContributionAndProfitStatement" || type == "RptContributionAndProfitSummary"
                || type == "RptContributionAndProfitDetails") {
                if ((inpYear != "" && inpYear != "0") && (vUnitId != "" && vUnitId != "0") && (vDepartmentId != "" && vDepartmentId != "0")
                    && (vSectionId != "" && vSectionId != "0")) {
                    getEmployee(type, "0", inpYear, "0", vUnitId, vDepartmentId, vSectionId, "0", "0", "0", "0", "0", "0", "0");
                }
            }

            else if (type == "RptIncomeTaxSummary") {
                if ((vFiscalYear != "" && vFiscalYear != "0") && (vUnitId != "" && vUnitId != "0") && (vDepartmentId != "" && vDepartmentId != "0")
                    && (vSectionId != "" && vSectionId != "0")) {
                    getEmployee(type, "0", "0", "0", vUnitId, vDepartmentId, vSectionId, "0", "0", "0", "0", "0", "0", "0", vFiscalYear);
                }
            }
        }
    });

    $("#vDesignationId").change(function () {
        var type = $("#type").val();
        var vCategory = $("#vCategory").val();
        var vReportType = $("input[name='vReportType']:checked").val();
        var inpFromDateTo = getBdToDbFormat($("#inpFromDateTo").val());
        var inpToDateTo = getBdToDbFormat($("#inpToDateTo").val());

        var dDate = $("#dDate").val();
        var vUnitId = $("#vUnitId").val();
        var vDepartmentId = $("#vDepartmentId").val();
        var vSectionId = $("#vSectionId").val();
        var vDesignationId = $("#vDesignationId").val();

        if (type != "") {
            if (type == "RptConfirmationJoiningLeftList") {
                if (vCertifiedById != "" && vCertifiedById != "0") {
                    if ((vCategory != "" && vCategory != "0") && (vUnitId != "" && vUnitId != "0") &&
                        (vDepartmentId != "" && vDepartmentId != "0") && (vSectionId != "" && vSectionId != "0")
                        && (vDesignationId != "" && vDesignationId != "0")) {
                        getReligion(type, vCategory, vReportType, vUnitId, vDepartmentId, vSectionId, inpFromDateTo, inpToDateTo, vDesignationId)
                    }
                }
            }
            else if (
                type == "RptDailyAttendanceStatement" || type == "RptDailyAbsentStatement" || type == "RptAttendanceDailyMovement" ||
                type == "RptDailyLateInEmployeeList" || type == "RptDailyEarlyOutEmployeeList"
            ) {
                if (
                    (dDate != "" && dDate != "0") && (vUnitId != "" && vUnitId != "0") && (vDepartmentId != "" && vDepartmentId != "0") &&
                    (vSectionId != "" && vSectionId != "0") && (vDesignationId != "" && vDesignationId != "0")
                ) {
                    var dDate = getBdToDbFormat(dDate);
                    getServiceType(type, dDate, vUnitId, vDepartmentId, vSectionId, vDesignationId);
                }
            }
        }
    });
/*    type, vMonth, vUnitId, vDepartmentId, vSectionId, vSalaryType, vEmployeeId*/
    $("#vEmployeeId").change(function () {
        var type = $("#type").val();
        var vCategory = $("#vCategory").val();
        var vReportType = $("input[name='vReportType']:checked").val();
        var inpFromDateTo = getBdToDbFormat($("#inpFromDateTo").val());
        var inpToDateTo = getBdToDbFormat($("#inpToDateTo").val());
        var vSalaryType = $("input[name='vSalaryType']:checked").val();
        var vMonth = $("#vMonth").val();
        var vUnitId = $("#vUnitId").val();
        var vDepartmentId = $("#vDepartmentId").val();
        var vSectionId = $("#vSectionId").val();
        var vEmployeeId = $("#vEmployeeId").val();

        if (type == "RptLoanApplication" || type == "RptLeaveApplication") {
            if ((vUnitId != "" && vUnitId != "0") && (vEmployeeId != "" && vEmployeeId != "0")) {
                getApplicationDate(type, "0", "0", "0", vEmployeeId, "0");
            }
        }
        if (type == "RptBonus") {
            if ((vMonth != "" && vMonth != "0") &&
                (vUnitId != "" && vUnitId != "0") && (vDepartmentId != "" && vDepartmentId != "0") &&
                (vSectionId != "" && vSectionId != "0")) {
                getOccasion(type, vSalaryType, vMonth, vUnitId, vDepartmentId, vSectionId, vEmployeeId);
            }
        }
    });

    $("#chkAllRank").click(function () {
        var select = $('#chkAllRank').prop('checked');
        var element = document.querySelectorAll("#gridRank tr td .chkRank");
        for (var i = 0; i < element.length; i++) {
            $('#' + element[i].id).prop('checked', select);
        }
    });
    $("#chkAllDesignation").click(function () {
        var select = $('#chkAllDesignation').prop('checked');
        var element = document.querySelectorAll("#gridDesignation tr td .chkDesignation");
        for (var i = 0; i < element.length; i++) {
            $('#' + element[i].id).prop('checked', select);
        }
    });
    $("#chkAllServiceStatus").click(function () {
        var select = $('#chkAllServiceStatus').prop('checked');
        var element = document.querySelectorAll("#gridServiceStatus tr td .chkServiceStatus");
        for (var i = 0; i < element.length; i++) {
            $('#' + element[i].id).prop('checked', select);
        }
    });
}
// action for option group, select option, Radio etc action End

/*Data Load Action Start*/

function getMonth(type, vSalaryType) {
    var vMonth = $("#vMonth").val();

    var url = "/Payroll/PayrollReport/getMonth?type=" + type + "&vSalaryType=" + vSalaryType;
    console.log("getMonth " + type + " : " + commonUrl + url);
    $("#vMonth").val(0).trigger('change');
    $.getJSON(url, function (data) {
        var item = "";
        item += '<option value="' + '0' + '">==Choose a Month==</option>'
        $("#vMonth").html(item);
        $.each(data, function (i, opt) {
            item += '<option value="' + opt.value + '">' + opt.text + '</option>'
        });
        $("#vMonth").html(item);

        if (vMonth != undefined && !isEmpty(vMonth)) {
            $("#vMonth").val(vMonth).trigger('change.select2');
        }
    });
}
function getFiscalYear(type) {
    var vFiscalYear = $("#vFiscalYear").val();

    var url = "/Payroll/PayrollReport/getFiscalYear?type=" + type;
    console.log("getYear " + type + " : " + commonUrl + url);
    $("#vFiscalYear").val(0).trigger('change');
    $.getJSON(url, function (data) {
        var item = "";
        item += '<option value="' + '0' + '">==Choose a Fiscal Year==</option>'
        $("#vFiscalYear").html(item);
        $.each(data, function (i, opt) {
            item += '<option value="' + opt.value + '">' + opt.text + '</option>'
        });
        $("#vFiscalYear").html(item);

        if (vFiscalYear != undefined && !isEmpty(vFiscalYear)) {
            $("#vFiscalYear").val(vFiscalYear).trigger('change.select2');
        }
    });
}


function getItem(type, vUnitId, vDepartmentId, vSectionId) {
    var vItemName = $("#vItemName").val();
    var url = "/Payroll/PayrollReport/getItem?type=" + type + "&vUnitId=" + vUnitId + "&vDepartmentId=" + vDepartmentId + "&vSectionId=" + vSectionId;

    console.log("getItem " + type + " : " + commonUrl + url);
    $("#vItemName").val(0).trigger('change');
    $.getJSON(url, function (data) {
        var item = "";
        item += '<option value="' + '0' + '">==Choose a Item==</option>'
        /* item += '<option value="' + '%' + '">All</option>'*/
        $("#vItemName").html(item);
        $.each(data, function (i, opt) {
            item += '<option value="' + opt.value + '">' + opt.text + '</option>'
        });
        $("#vItemName").html(item);

        if (vItemName != undefined && !isEmpty(vItemName)) {
            $("#vItemName").val(vItemName).trigger('change.select2');
        }
    });
}
function getCategory(type, vReportType, inpFromDateTo, inpToDateTo) {
    var vCategory = $("#vCategory").val();
    var url = "/Payroll/PayrollReport/getCategory?type=" + type + "&vReportType=" + vReportType + "&inpFromDateTo=" + inpFromDateTo +
        "&inpToDateTo=" + inpToDateTo;
    $("#vCategory").val(0).trigger('change');
    $.getJSON(url, function (data) {
        var item = "";
        item += '<option value="' + '0' + '">==Choose a Category==</option>'
        item += '<option value="' + '%' + '">All</option>'
        $("#vCategory").html(item);
        $.each(data, function (i, opt) {
            item += '<option value="' + opt.value + '">' + opt.text + '</option>'
        });
        $("#vCategory").html(item);

        if (vCategory != undefined && !isEmpty(vCategory)) {
            $("#vCategory").val(vCategory).trigger('change.select2');
        }
    });
}
function getUnit(type, dDate, vMonth, vStatus, vSalaryType, vCategory, vReportType, inpFromDateTo, inpToDateTo,
    vIncrementProposal, vItemName, vFiscalYear) {
    var vUnitId = $("#vUnitId").val();
    var url = "/Payroll/PayrollReport/getUnit?type=" + type + "&dDate=" + dDate + "&vMonth=" + vMonth + "&vStatus=" + vStatus +
        "&vSalaryType=" + vSalaryType + "&vCategory=" + vCategory + "&vReportType=" + vReportType + "&inpFromDateTo=" + inpFromDateTo +
        "&inpToDateTo=" + inpToDateTo + "&vIncrementProposal=" + vIncrementProposal + "&vItemName=" + vItemName + "&vFiscalYear=" + vFiscalYear;
    console.log("getUnit " + type + " : " + commonUrl + url);

    $("#vUnitId").val(0).trigger('change');
    $.getJSON(url, function (data) {
        var item = "";
        item += '<option value="' + '0' + '">==Choose a Unit==</option>'
        $("#vUnitId").html(item);
        $.each(data, function (i, opt) {
            item += '<option value="' + opt.value + '">' + opt.text + '</option>'
        });
        $("#vUnitId").html(item);

        if (vUnitId != undefined && !isEmpty(vUnitId)) {
            $("#vUnitId").val(vUnitId).trigger('change.select2');
        }
    });
}
function getDepartment(type, dDate, vMonth, vUnitId, vStatus, vSalaryType, vCategory, vReportType, inpFromDateTo, inpToDateTo,
    vIncrementProposal, vItemName, vFiscalYear) {
    var vDepartmentId = $("#vDepartmentId").val();
    var url = "/Payroll/PayrollReport/getDepartment?type=" + type + "&dDate=" + dDate + "&vMonth=" + vMonth + "&vUnitId=" + vUnitId + "&vStatus=" +
        vStatus + "&vSalaryType=" + vSalaryType + "&vCategory=" + vCategory + "&vReportType=" + vReportType +
        "&inpFromDateTo=" + inpFromDateTo + "&inpToDateTo=" + inpToDateTo +
        "&vIncrementProposal=" + vIncrementProposal + "&vItemName=" + vItemName + "&vFiscalYear=" + vFiscalYear;
    console.log("getDepartment " + type + " : " + commonUrl + url);
    $("#vDepartmentId").val(0).trigger('change');
    $.getJSON(url, function (data) {
        var item = "";
        item += '<option value="' + '0' + '">==Choose a Department==</option>'
        if (type != "RptIdCard" || type != "RptIncomeTaxCalculation") {
            item += '<option value="' + '%' + '">All</option>'
        }
        $("#vDepartmentId").html(item);
        $.each(data, function (i, opt) {
            item += '<option value="' + opt.value + '">' + opt.text + '</option>'
        });

        $("#vDepartmentId").html(item);

        ///For Multiple Select
        //$("#vDepartmentId").select2({
        //    multiple: true
        //});

        if (vDepartmentId != undefined && !isEmpty(vDepartmentId)) {
            $("#vDepartmentId").val(vDepartmentId).trigger('change.select2');
        }
    });
}

function getSection(type, dDate, vMonth, vUnitId, vDepartmentId, vStatus, vSalaryType, vCategory, vReportType,
    inpFromDateTo, inpToDateTo, vIncrementProposal, vItemName, vFiscalYear) {
    var vSectionId = $("#vSectionId").val();

    var url = "/Payroll/PayrollReport/getSection?type=" + type + "&dDate=" + dDate + "&vMonth=" + vMonth + "&vUnitId=" + vUnitId + "&vDepartmentId=" +
        vDepartmentId + "&vStatus=" + vStatus + "&vSalaryType=" + vSalaryType + "&vCategory=" + vCategory + "&vReportType="
        + vReportType + "&inpFromDateTo=" + inpFromDateTo + "&inpToDateTo=" + inpToDateTo +
        "&vIncrementProposal=" + vIncrementProposal + "&vItemName=" + vItemName + "&vFiscalYear=" + vFiscalYear;
    console.log("getSection " + type + " : " + commonUrl + url);
    $("#vSectionId").val(0).trigger('change');
    $.getJSON(url, function (data) {
        var item = "";
        item += '<option value="' + '0' + '">==Choose a Section==</option>'
        item += '<option value="' + '%' + '">All</option>'
        $("#vSectionId").html(item);
        $.each(data, function (i, opt) {
            item += '<option value="' + opt.value + '">' + opt.text + '</option>'
        });
        $("#vSectionId").html(item);

        if (vSectionId != undefined && !isEmpty(vSectionId)) {
            $("#vSectionId").val(vSectionId).trigger('change.select2');
        }
    });
}
function tableClearRank(start) {
    var tableRank = document.getElementById('gridRank');
    var rowCount = tableRank.rows.length;
    for (var i = start; i < rowCount; i++) {
        tableRank.deleteRow(start);
    }
}
function getRankTableData() {
    var url = "/Payroll/PayrollReport/getRankTableData";
    $.getJSON(url, function (data) {
        x = 0;
        tableClearRank(1);
        $.each(data, function (i, opt) {
            x = x + 1;
            addRowRank(x);
            $("#lblRankId" + x).text(opt.value);
            $("#lblRankName" + x).text(opt.text);
        });
    });
}
function addRowRank(x) {
    var tableArrayRank = new Array();
    tableArrayRank = ['#', 'Rank', 'SysId'];

    var gridRank = document.getElementById('gridRank');
    var rowCount = gridRank.rows.length;
    var tr = gridRank.insertRow(rowCount);
    tr = gridRank.insertRow(rowCount);
    for (var c = 0; c < tableArrayRank.length; c++) {
        var td = document.createElement('td');
        td = tr.insertCell(0);
        if (c == 2) {
            var ele = document.createElement('input');
            ele.setAttribute('class', 'chkRank');
            ele.setAttribute('type', 'checkbox');
            ele.setAttribute('id', 'chkRank' + x);
            td.appendChild(ele);
        }
        if (c == 1) {
            var ele = document.createElement('label');
            ele.setAttribute('class', 'lblRankName');
            ele.setAttribute('id', 'lblRankName' + x);
            td.appendChild(ele);
        }
        if (c == 0) {
            var ele = document.createElement('label');
            ele.setAttribute('class', 'lblRankId');
            ele.setAttribute('id', 'lblRankId' + x);
            ele.style.display = 'none';
            td.appendChild(ele);
        }
    }
}

function tableClearDesignation(start) {
    var tableDesignation = document.getElementById('gridDesignation');
    var rowCount = tableDesignation.rows.length;
    for (var i = start; i < rowCount; i++) {
        tableDesignation.deleteRow(start);
    }
}
function getDesignationTableData() {
    var url = "/Payroll/PayrollReport/getDesignationTableData";
    $.getJSON(url, function (data) {
        x = 0;
        tableClearDesignation(1);
        $.each(data, function (i, opt) {
            x = x + 1;
            addRowDesignation(x);
            $("#lblDesignationId" + x).text(opt.value);
            $("#lblDesignationName" + x).text(opt.text);
        });
    });
}
function addRowDesignation(x) {
    var tableArrayDesignation = new Array();
    tableArrayDesignation = ['#', 'Designation', 'SysId'];

    var gridDesignation = document.getElementById('gridDesignation');
    var rowCount = gridDesignation.rows.length;
    var tr = gridDesignation.insertRow(rowCount);
    tr = gridDesignation.insertRow(rowCount);
    for (var c = 0; c < tableArrayDesignation.length; c++) {
        var td = document.createElement('td');
        td = tr.insertCell(0);
        if (c == 2) {
            var ele = document.createElement('input');
            ele.setAttribute('class', 'chkDesignation');
            ele.setAttribute('type', 'checkbox');
            ele.setAttribute('id', 'chkDesignation' + x);
            td.appendChild(ele);
        }
        if (c == 1) {
            var ele = document.createElement('label');
            ele.setAttribute('class', 'lblDesignationName');
            ele.setAttribute('id', 'lblDesignationName' + x);
            td.appendChild(ele);
        }
        if (c == 0) {
            var ele = document.createElement('label');
            ele.setAttribute('class', 'lblDesignationId');
            ele.setAttribute('id', 'lblDesignationId' + x);
            ele.style.display = 'none';
            td.appendChild(ele);
        }
    }
}

function tableClearServiceStatus(start) {
    var tableServiceStatus = document.getElementById('gridServiceStatus');
    var rowCount = tableServiceStatus.rows.length;
    for (var i = start; i < rowCount; i++) {
        tableServiceStatus.deleteRow(start);
    }
}
function getServiceStatusTableData() {
    var url = "/Payroll/PayrollReport/getServiceStatusTableData";
    $.getJSON(url, function (data) {
        x = 0;
        tableClearServiceStatus(1);
        $.each(data, function (i, opt) {
            x = x + 1;
            addRowServiceStatus(x);
            $("#lblServiceStatusName" + x).text(opt.text);
        });
    });
}
function addRowServiceStatus(x) {
    var tableArrayServiceStatus = new Array();
    tableArrayServiceStatus = ['#', 'ServiceStatus'];

    var gridServiceStatus = document.getElementById('gridServiceStatus');
    var rowCount = gridServiceStatus.rows.length;
    var tr = gridServiceStatus.insertRow(rowCount);
    tr = gridServiceStatus.insertRow(rowCount);
    for (var c = 0; c < tableArrayServiceStatus.length; c++) {
        var td = document.createElement('td');
        td = tr.insertCell(0);
        if (c == 1) {
            var ele = document.createElement('input');
            ele.setAttribute('class', 'chkServiceStatus');
            ele.setAttribute('type', 'checkbox');
            ele.setAttribute('id', 'chkServiceStatus' + x);
            td.appendChild(ele);
        }
        if (c == 0) {
            var ele = document.createElement('label');
            ele.setAttribute('class', 'lblServiceStatusName');
            ele.setAttribute('id', 'lblServiceStatusName' + x);
            td.appendChild(ele);
        }
    }
}

function getNewDesignation(type, vUnitId, vDepartmentId, vCategory, vReportType, inpFromDateTo, inpToDateTo, vSectionId) {
    var vDesignationId = $("#vDesignationId").val();
    var url = "/Payroll/PayrollReport/getNewDesignation?type=" + type + "&vUnitId=" + vUnitId + "&vDepartmentId=" +
        vDepartmentId + "&vCategory=" + vCategory + "&vReportType=" + vReportType + "&inpFromDateTo=" + inpFromDateTo +
        "&inpToDateTo=" + inpToDateTo + "&vSectionId=" + vSectionId;
    console.log("getSection " + type + " : " + commonUrl + url);
    $("#vDesignationId").val(0).trigger('change');
    $.getJSON(url, function (data) {
        var item = "";
        item += '<option value="' + '0' + '">==Choose a Section==</option>'
        item += '<option value="' + '%' + '">All</option>'
        $("#vDesignationId").html(item);
        $.each(data, function (i, opt) {
            item += '<option value="' + opt.value + '">' + opt.text + '</option>'
        });
        $("#vDesignationId").html(item);

        if (vDesignationId != undefined && !isEmpty(vDesignationId)) {
            $("#vDesignationId").val(vDesignationId).trigger('change.select2');
        }
    });
}

function getEmployee(type, vStatus, dDate, vMonth, vUnitId, vDepartmentId, vSectionId, vSalaryType, vFromDate, vCategory, vReportType,
    inpFromDateTo, inpToDateTo, vIncrementProposal,vFiscalYear) {
    var vEmployeeId = $("#vEmployeeId").val();

    var url = "/Payroll/PayrollReport/getEmployee?type=" + type + "&vStatus=" + vStatus + "&dDate=" + dDate + "&vMonth=" + vMonth + "&vUnitId=" + vUnitId +
        "&vDepartmentId=" + vDepartmentId + "&vSectionId=" + vSectionId + "&vSalaryType=" + vSalaryType +
        "&vFromDate=" + vFromDate + "&vCategory=" + vCategory + "&vReportType=" + vReportType + "&inpFromDateTo=" + inpFromDateTo +
        "&inpToDateTo=" + inpToDateTo + "&vIncrementProposal=" + vIncrementProposal + "&vFiscalYear=" + vFiscalYear;
    console.log("getEmployee " + type + " : " + commonUrl + url);
    $('#vEmployeeId').val(0).trigger('change');
    $.getJSON(url, function (data) {
        var item = "";
        $("#vEmployeeId").empty();
        item += '<option value="' + '0' + '">==Choose a Employee==</option>'
        if (
            type == "RptEmployeeList" || type == "RptMonthlyAttendanceSummary" || type == "RptShortViewOfAttendance" || type == "RptMonthlySalary" ||
            type == "RptPaySlip" || type == "RptMonthlyDutyRoster" || type == "RptInLieu" || type == "RptMonthlyAttendanceSummaryManual" ||
            type == "RptMonthlyMealInformation" || type == "RptLoanRegister" || type == "RptConfirmationJoiningLeftList" || type == "RptLengthOfService" ||
            type == "RptIncrementProposal" || type == "RptContributionAndProfitSummary" || type == "RptContributionAndProfitDetails" ||
            type == "RptIncrementReport" || type == "RptSalaryIncrementStatement" || type == "RptIdCard" || type == "RptEmployeePromotionReport" ||
            type == "RptBonus" || type == "RptAdvanceSalaryLoanRegister" || type == "RptOtherEarning" || type == "RptOtherDeduction" ||
            type == "RptMobileExtra" || type == "RptIncomeTaxSummary" || type == "RptIncomeTaxCalculation"
        ) {
            item += '<option value="' + '%' + '">All</option>'
        }
        $("#vEmployeeId").html(item);
        $.each(data, function (i, opt) {
            item += '<option value="' + opt.value + '">' + opt.text + '</option>'
        });
        $("#vEmployeeId").html(item);

        if (vEmployeeId != undefined && !isEmpty(vEmployeeId)) {
            $("#vEmployeeId").val(vEmployeeId).trigger('change.select2');
        }
    });
}
function getServiceType(type, dDate, vUnitId, vDepartmentId, vSectionId, vDesignationId,vMonth) {
    var vServiceType = $("#vServiceType").val();
    var url = "/Payroll/PayrollReport/getServiceType?type=" + type + "&dDate=" + dDate + "&vUnitId=" + vUnitId + "&vDepartmentId=" + vDepartmentId +
        "&vSectionId=" + vSectionId + "&vDesignationId=" + vDesignationId + "&vMonth=" + vMonth;

    console.log("getServiceType " + type + " : " + commonUrl + url);
    $('#vServiceType').val(0).trigger('change');
    $.getJSON(url, function (data) {
        var item = "";
        $("#vServiceType").empty();
        item += '<option value="' + '0' + '">==Choose a Service Type==</option>'
        if (type == "RptDailyAttendanceStatement" || type == "RptDailyAbsentStatement" || type == "RptAttendanceDailyMovement" ||
            type == "RptDailyLateInEmployeeList" || type == "RptDailyEarlyOutEmployeeList" || type == "RptMonthlyAttendanceSummaryManual") {
            item += '<option value="' + '%' + '">All</option>'
        }
        $("#vServiceType").html(item);
        $.each(data, function (i, opt) {
            item += '<option value="' + opt.value + '">' + opt.text + '</option>'
        });
        $("#vServiceType").html(item);

        if (vServiceType != undefined && !isEmpty(vServiceType)) {
            $("#vServiceType").val(vServiceType).trigger('change.select2');
        }
    });
}
/*type, vMonth, vUnitId, vDepartmentId, vSectionId, vSalaryType, vEmployeeId)*/
function getOccasion(type, vSalaryType,vMonth, vUnitId, vDepartmentId, vSectionId, vEmployeeId) {
    var vOccasion = $("#vOccasion").val();

    var url = "/Payroll/PayrollReport/getOccasion?type=" + type +
        "&vSalaryType=" + vSalaryType +
        "&vMonth=" + vMonth +
        "&vUnitId=" + vUnitId +
        "&vDepartmentId=" + vDepartmentId +
        "&vSectionId=" + vSectionId +

        "&vEmployeeId=" + vEmployeeId;

    console.log("getOccasion " + type + " : " + commonUrl + url);

    $("#vOccasion").val(0).trigger('change');
    $.getJSON(url, function (data) {
        var item = "";
        item += '<option value="' + '0' + '">==Choose a Occassion==</option>'
        $("#vOccasion").html(item);
        $.each(data, function (i, opt) {
            item += '<option value="' + opt.value + '">' + opt.text + '</option>'
        });
        $("#vOccasion").html(item);

        if (vOccasion != undefined && !isEmpty(vOccasion)) {
            $("#vOccasion").val(vOccasion).trigger('change.select2');
        }
    });
}



function getApplicationDate(type, vUnitId, vDepartmentId, vSectionId, vEmployeeId, vItemName) {
    var employeeApplicationDate = $("#employeeApplicationDate").val();
    var url = "/Payroll/PayrollReport/getApplicationDate?type=" + type + "&vUnitId=" + vUnitId + "&vDepartmentId=" + vDepartmentId +
        "&vSectionId=" + vSectionId + "&vEmployeeId=" + vEmployeeId + "&vItemName=" + vItemName;
    console.log("getApplicationDate " + type + " : " + commonUrl + url);
    $("#employeeApplicationDate").val(0).trigger('change');
    $.getJSON(url, function (data) {
        var item = "";
        item += '<option value="' + '0' + '">==Choose a Date==</option>'
        $("#employeeApplicationDate").html(item);
        $.each(data, function (i, opt) {
            item += '<option value="' + opt.value + '">' + opt.text + '</option>'
        });
        $("#employeeApplicationDate").html(item);

        if (employeeApplicationDate != undefined && !isEmpty(employeeApplicationDate)) {
            $("#employeeApplicationDate").val(employeeApplicationDate).trigger('change.select2');
        }
    });
}





function getDesignation(type, vCertifiedById) {
    var url = "/Payroll/PayrollReport/getDesignation?type=" + type + "&vCertifiedById=" + vCertifiedById;
    console.log("getDesignation " + type + " : " + commonUrl + url);
    $.getJSON(url, function (data) {
        $.each(data, function (i, opt) {
            $('#inpDesignationCertifiedBy').val(opt.value);
            $('#inpContactNo').val(opt.text);
        });
    });
}
function getReligion(type, vCategory, vReportType, vUnitId, vDepartmentId, vSectionId, inpFromDateTo, inpToDateTo, vDesignationId) {
    var vReligion = $("#vReligion").val();
    var url = "/Payroll/PayrollReport/getReligion?type=" + type + "&vCategory=" + vCategory + "&vReportType=" + vReportType +
        "&vUnitId=" + vUnitId + "&vDepartmentId=" + vDepartmentId +
        "&vSectionId=" + vSectionId + "&inpFromDateTo=" + inpFromDateTo + "&inpToDateTo=" + inpToDateTo
        + "&vDesignationId=" + vDesignationId;

    $("#vReligion").val(0).trigger('change');
    $.getJSON(url, function (data) {
        var item = "";
        item += '<option value="' + '0' + '">==Choose a Religion==</option>'
        item += '<option value="' + '%' + '">All</option>'
        $("#vReligion").html(item);
        $.each(data, function (i, opt) {
            item += '<option value="' + opt.value + '">' + opt.text + '</option>'
        });
        $("#vReligion").html(item);

        if (vReligion != undefined && !isEmpty(vReligion)) {
            $("#vReligion").val(vReligion).trigger('change.select2');
        }
    });
}
function getDesignationList(type, dDate, vUnitId, vDepartmentId, vSectionId) {
    var vDesignationId = $("#vDesignationId").val();
    var url = "/Payroll/PayrollReport/getDesignationList?type=" + type + "&dDate=" + dDate + "&vUnitId=" + vUnitId +
        "&vDepartmentId=" + vDepartmentId + "&vSectionId=" + vSectionId;
    console.log("getDesignation " + type + " : " + commonUrl + url);

    $("#vDesignationId").val(0).trigger('change');
    $.getJSON(url, function (data) {
        var item = "";
        item += '<option value="' + '0' + '">==Choose a Designation==</option>'
        item += '<option value="' + '%' + '">All</option>'
        $("#vDesignationId").html(item);
        $.each(data, function (i, opt) {
            item += '<option value="' + opt.value + '">' + opt.text + '</option>'
        });
        $("#vDesignationId").html(item);

        if (vDesignationId != undefined && !isEmpty(vDesignationId)) {
            $("#vDesignationId").val(vDesignationId).trigger('change.select2');
        }
    });
}

function getBank(type, vMonth) {
    var vBankId = $("#vBankId").val();
    var url = "/Payroll/PayrollReport/getBank?type=" + type + "&vMonth=" + vMonth;
    console.log("getBank " + type + " : " + commonUrl + url);
    $("#vBankId").val(0).trigger('change');
    $.getJSON(url, function (data) {
        var item = "";
        item += '<option value="' + '0' + '">==Choose a Bank==</option>'
        $("#vBankId").html(item);
        $.each(data, function (i, opt) {
            item += '<option value="' + opt.value + '">' + opt.text + '</option>'
        });
        $("#vBankId").html(item);

        if (vBankId != undefined && !isEmpty(vBankId)) {
            $("#vBankId").val(vBankId).trigger('change.select2');
        }
    });
}
function getBankBranch(type, vMonth) {
    var mBranchId = $("#mBranchId").val();
    var url = "/Payroll/PayrollReport/getBankBranch?type=" + type + "&vMonth=" + vMonth
    console.log("getBankBranch " + type + " : " + commonUrl + url);
    $("#mBranchId").val(0).trigger('change');
    $.getJSON(url, function (data) {
        var item = "";
        item += '<option value="' + '0' + '">==Choose a Branch==</option>'
        $("#mBranchId").html(item);
        $.each(data, function (i, opt) {
            item += '<option value="' + opt.value + '">' + opt.text + '</option>'
        });

        $("#mBranchId").html(item);

        if (mBranchId != undefined && !isEmpty(mBranchId)) {
            $("#mBranchId").val(mBranchId).trigger('change.select2');
        }
    });
}
function getCertifiedBy(type) {
    var vCertifiedById = $("#vCertifiedById").val();
    var url = "/Payroll/PayrollReport/getCertifiedBy?type=" + type;
    console.log("getCertifiedBy " + type + " : " + commonUrl + url);
    $("#vCertifiedById").val(0).trigger('change');
    $.getJSON(url, function (data) {
        var item = "";
        item += '<option value="' + '0' + '">==Choose a Certified By==</option>'
        $("#vCertifiedById").html(item);
        $.each(data, function (i, opt) {
            item += '<option value="' + opt.value + '">' + opt.text + '</option>'
        });
        $("#vCertifiedById").html(item);

        if (vCertifiedById != undefined && !isEmpty(vCertifiedById)) {
            $("#vCertifiedById").val(vCertifiedById).trigger('change.select2');
        }
    });
}

function getTo(type, dDate) {
    var vTo = $("#vTo").val();
    var url = "/Payroll/PayrollReport/getTo?type=" + type + "&dDate=" + dDate;
    console.log("getTo " + type + " : " + commonUrl + url);

    $("#vTo").val(0).trigger('change');
    $.getJSON(url, function (data) {
        var item = "";
        item += '<option value="' + '0' + '">==Choose a To==</option>'

        if (type != "RptOrientation")
            item += '<option value="' + '%' + '">All</option>'
        $("#vTo").html(item);
        $.each(data, function (i, opt) {
            item += '<option value="' + opt.value + '">' + opt.text + '</option>'
        });
        $("#vTo").html(item);
        if (vTo != undefined && !isEmpty(vTo)) {
            $("#vTo").val(vTo).trigger('change.select2');
        }
    });
}


/*Data Load Action End*/

//Clear Function
function clear() {
    var date = getCDay() + '-' + getCMonth() + '-' + getCYear();
    $("#type").val("");
    $('#vEmployeeId').val('0').trigger('change');
    $('#vReligion').val('0').trigger('change');
    $('#vCategory').val('0').trigger('change');
    $('#vFiscalYear').val('0').trigger('change');
    $("input[name=vReportType][value='NewEmployee']").prop("checked", true);
    $("input[name=vStatus][value='Active']").prop("checked", true);
    $("input[name='vSalaryType']:checked").prop("checked", true);
    $("input[name=vEmployeeType][value='Present Employee']").prop("checked", true);
    $("input[name=vWithOrWithOutGross][value='Without Gross']").prop("checked", true);
    $("#vCertifiedById").val('0').trigger('change');
    $("#vUnitId").val('0').trigger('change');
    $("#vDesignationId").val('0').trigger('change');
    $("#employeeApplicationDate").val('0').trigger('change');
    $("#dDate").val(date);
    $("#vMonth").val('0').trigger('change');
    $("#vDepartmentId").val('0').trigger('change');
    $("#vDepartmentId").val('0').trigger('change');
    $("#vSectionId").val('0').trigger('change');
    $("#inpAccountNo").val("0051070206192");
    $("#inpAddress").val("O R Nizam Road Branch, Chattogram");
    $("#inpReferenceNo").val("");
    $("#inpYear").val(getCYear());
}
4