4# Ram এর manufacture and Name জানার জন্য cmd(WIN+r)
wmic memorychip get Manufacturer
wmic memorychip get Speed

# Ram কয়টা আছে পিসির মধ্যে তার জন্য 
Get-WmiObject Win32_PhysicalMemory | Measure-Object4