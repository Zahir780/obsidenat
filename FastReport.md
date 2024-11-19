# FastReport এ level condition দিতে গেলে,

[IIf([Table.vLeaveTypeName]=="Casual Leave","Total Leave","")]

# FastReport এ data তে condition দিতে গেলে,
[IIf([Table.vLeaveTypeName]=="Casual Leave",[Table1.iLeaveDays],"")]
