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

# Simplistic timing  
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

