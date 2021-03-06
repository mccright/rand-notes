# Notes for PowerShell Scripts

I don't use PowerShell enough to remain literate.  These snippits help bootstrap my efforts to assemble utility code.  




## Set or get an environment variable  

### Create a script-local environment variable:  
```powershell
$env:JAVA_HOME = 'C:\Program Files\Java\jdk1.8.0_201'  
```

### Create a persistent system-wide environment variable:  
```powershell
[System.Environment]::SetEnvironmentVariable('ResourceGroup','AZ_Resource_Group')
```

### Query an environment variable:  
```powershell
$env:JAVA_HOME  
```
or  
```powershell
[System.Environment]::GetEnvironmentVariable('JAVA_HOME','machine')  
```
or
```powershell
Get-ChildItem -Path Env:JAVA_HOME  
```

### Check the path with:  
```powershell
Get-ChildItem -Path Env:\  
```

### Modify a persistent system-wide environment variable:  
```powershell
$TMPCLASSPATH = [Environment]::GetEnvironmentVariable('CLASSPATH', 'Machine')  
$NEWCLASSPATH = $TMPCLASSPATH + ';C:\dev\projectname\classes\'  
[Environment]::SetEnvironmentVariable("CLASSPATH", $NEWCLASSPATH, 'Machine')  
```

## Simplistic timing  
```powershell
$start = Get-Date  
# do the work that you care to time...  
$end = Get-Date  
$myCodeDuration = $end-$start  
Write-Output ('My code duration..... ' + $myCodeDuration + " or " + $myCodeDuration.TotalSeconds)  
```
or highlight the timing output
```powershell
Write-Host ('My code duration..... ' + $myCodeDuration + " or " + $myCodeDuration.TotalSeconds) -foregroundcolor DarkBlue -backgroundcolor Yellow  
```

## Using passed parameters (Active Directory example)  
```powershell
Param(
        [Parameter(Mandatory=$False, HelpMessage="Enter userName or emailAddress values")]
        [string]$user,
        [Parameter(Mandatory=$False, HelpMessage="Enter userName or emailAddress values")]
        [string]$email
        )

if ($user) {
  $mgrcn = Get-ADUser -Identity $user -Properties Manager | Select-Object -Property Manager
  $mgrcnstr = $mgrcn.Manager
  Get-ADUser -Filter {DistinguishedName -eq $mgrcnstr} -Properties DisplayName,UserPrincipalName,whenCreated,CanonicalName,City,LastLogonDate,mobile,MobilePhone,EmailAddress
}
if ($email) {
  $mgrcn = Get-ADUser -Filter {EmailAddress -eq $email} -Properties Manager | Select-Object -Property Manager
  $mgrcnstr = $mgrcn.Manager
  Get-ADUser -Filter {DistinguishedName -eq $mgrcnstr} -Properties DisplayName,UserPrincipalName,whenCreated,CanonicalName,City,LastLogonDate,mobile,MobilePhone,EmailAddress
}
else {
  Write-Host "Enter '-user' or '-email' values"
}
```
  
## Using passed parameters with an external application  
When your module will consume some passed parameters, some or all of which will be used by an external executable program, those parameters may require some special handling*.  This is especially true when you will pass a mix of variables and strings to the external executable program.  
```powershell
param([String]$debugFlag='False',[String]$inputFileName='theInput.txt',[String]$outputFileName='theOutput.txt')  
$outputPrefix = $Env:COMPUTERNAME  
$theOutputFile = $outputPrefix+"-"+$outputFileName  
$auditorName = "Alice"  
$executable = "C:\PROGRA~1\myApp\myAppVer6.exe"  
# Assemble the parameters:  
$executableParameters = '-quite', '-bom', '"full"', '-auditor', $auditorName, '-debug', $debugFlag, '-inFile', $inputFileName, '-reportName', $theOutputFile  
# Now use it:  
& $executable $executableParameters  
```
