# Using Color In Batch/CMD/Bash Scripts  

I still use batch/cmd/bash scripts to help myself and others speed up repetitive tasks on Windows or Linux endpoints.  Yes, I understand that PowerShell, Python, and more exist, but I can code up many simple tasks with a batch/bash files much faster than with other languages.  If there is an important driver for one of those more powerfull languages, I use them, but economy drives to batch/bash for a range of repetitive activities.  Sometimes it is important to signal the user/operator about a notable event or condition and using color on the console/shell can help.  That is the rationale for this note.  

There are use cases where employing color can help users better understand any given utility's output.  

## Batch file investigating how given codes will look on your endpoint.  
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
  
## Simple Bash version of the same
```bash
#!/bin/bash
### Demonstrate how given codes will look on your endpoint.
# Colors from:
# https://www.codeproject.com/Tips/5255355/How-to-put-color-on-Windows-console
# Thank you Tiago Cavalcante Trindade
SPACER='------------------------'
echo -e "\e[34mThis is blue\e[0m"
echo -e "\e[94mThis is Light blue\e[0m"
echo -e "\e[36mThis is cyan\e[0m"
echo -e "\e[96mThis is Light cyan\e[0m"
echo -e "\e[32mThis is Green\e[0m"
echo -e "\e[92mThis is Light Green\e[0m"
echo -e "\e[33mThis is Yellow\e[0m"
echo -e "\e[93mThis is Light Yellow\e[0m"
echo -e "\e[31mThis is Red\e[0m"
echo -e "\e[91mThis is Light Red\e[0m"
echo $SPACER
echo -e "\e[44mThis is blue background\e[0m"
echo -e "\e[104mThis is Light blue background\e[0m"
echo -e "\e[30m\e[46mThis is cyan background / black foreground\e[0m"
echo -e "\e[30m\e[106mThis is Light cyan background / black foreground\e[0m"
echo -e "\e[30m\e[100mThis is gray background / black foreground\e[0m"
echo -e "\e[30m\e[47mThis is Light gray background / black foreground\e[0m"
echo -e "\e[42mThis is green background\e[0m"
echo -e "\e[30m\e[102mThis is Light Green background / black foreground\e[0m"
echo -e "\e[30m\e[43mThis is Yellow background / black foreground\e[0m"
echo -e "\e[30m\e[103mThis is Light Yellow background / black foreground\e[0m"
echo -e "\e[41mThis is Red background\e[0m"
echo -e "\e[101mThis is Light Red background\e[0m"

```

## References  
If this resonates with you, there are some useful resources to build on this idea:  
* Wikipedia: [https://en.wikipedia.org/wiki/ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code)  
* Colorpedia: [https://github.com/joowani/colorpedia/](https://github.com/joowani/colorpedia/)
