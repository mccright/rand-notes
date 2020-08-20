# Using Color In Batch/CMD files  

I still use batch/cmd files to help myself and others speed up repetitive tasks on Windows endpoints.  Yes, I understand that PowerShell, Python, and more exist, but I can code up many tasks with a batch file much faster than with other languages.  If there is an important driver for one of those more powerfull languages, I use them, but economy drives to batch for a range of repetitive activities.  

There are use cases where employing color can help users better understand any given utility's output.  

### Batch file for seeing how given codes will look on your endpoing.  
```batch
@ECHO OFF
@REM Colors from:
@REM https://www.codeproject.com/Tips/5255355/How-to-put-color-on-Windows-console
@REM Thank you Tiago Cavalcante Trindade
SET SPACER="------------------------"
echo [34mThis is blue[0m
echo [94mThis is Light blue[0m
echo [36mThis is cyan[0m
echo [96mThis is Light cyan[0m
echo [32mThis is Green[0m
echo [92mThis is Light Green[0m
echo [33mThis is Yellow[0m
echo [93mThis is Light Yellow[0m
echo [31mThis is Red[0m
echo [91mThis is Light Red[0m
echo %SPACER%
echo [44mThis is blue background[0m
echo [104mThis is Light blue background[0m
echo [30m[46mThis is cyan background / black foreground[0m
echo [30m[106mThis is Light cyan background / black foreground[0m
echo [30m[100mThis is gray background / black foreground[0m
echo [30m[47mThis is Light gray background / black foreground[0m
echo [42mThis is green background[0m
echo [30m[102mThis is Light Green background / black foreground[0m
echo [30m[43mThis is Yellow background / black foreground[0m
echo [30m[103mThis is Light Yellow background / black foreground[0m
echo [41mThis is Red background[0m
echo [101mThis is Light Red background[0m

```

