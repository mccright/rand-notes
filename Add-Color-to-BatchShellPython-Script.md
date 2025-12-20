# Using Color In Batch/CMD/Bash/Python Scripts  

I still use batch/cmd/bash scripts to help myself and others speed up repetitive tasks on Windows or Linux endpoints.  Yes, I understand that PowerShell, Python, and more exist, but I can code up many simple tasks with a batch/bash files much faster than with other languages.  If there is an important driver for one of those more powerfull languages, I use them, but economy drives to batch/bash for a range of repetitive activities.  Sometimes it is important to signal the user/operator about a notable event or condition and using color on the console/shell can help.  That is the rationale for this note.  

There are use cases where employing color can help users better understand any given utility's output.  

## Color Settings for your Bash Shell  
In the examples here, the script immediately below is named: terminal_colors.sh  
```bash
#!/bin/bash
### Script Name - terminal_colors.sh
### Common color codes - include them in other scripts.
# This list started with one I noticed in: 
# https://github.com/TheKevJames/tools/blob/master/docker-tuning-primer/root/tuning-primer.sh
# and broadened the supported spectrum.
export normal='\033[0m'
export black='\033[30m'
export boldblack='\033[1;0m'
export gray='\033[90m'
export graybg='\033[100m'
export lightgray='\033[37m'
export lightgraybg='\033[47m'
export white='\033[37m'
export lightwhite='\033[97m'
export lightwhitebg='\033[107m'
export boldwhite='\033[1;37m'
export red='\033[31m'
export boldred='\033[1;31m'
export redbg='\033[41m'
export lightred='\033[91m'
export lightredbg='\033[101m'
export boldred='\033[1;31m'
export green='\033[32m'
export greenbg='\033[42m'
export lightgreen='\033[92m'
export lightgreenbg='\033[102m'
export boldgreen='\033[1;32m'
export yellow='\033[33m'
export lightyellow='\033[93m'
export boldyellow='\033[1;33m'
export yellowbg='\033[43m'
export lightyellowbg='\033[103m'
export blue='\033[34m'
export bluebg='\033[44m'
export boldblue='\033[1;34m'
export lightblue='\033[94m'
export lightbluebg='\033[104m'
export magenta='\033[35m'
export boldmagenta='\033[1;35m'
export cyan='\033[36m'
export cyanbg='\033[46m'
export lightcyan='\033[96m'
export lightcyanbg='\033[106m'
export boldcyan='\033[1;36m'
export italic=='\033[1;3m'
export underline='\033[4;3m'
export inverse='\033[7;3m'
export strikethrough='\033[9;3m'

```

## Simple Bash example of using the 'common colors' above  
'source' the terminal_colors.sh script to get the color variables.  
```bash
#!/bin/bash
### Demonstrate using the codes above as an 'include'.
. ./terminal_colors.sh
SPACER='------------------------'
echo -e $white"This is white"$normal
echo -e $gray"This is gray"$normal
echo -e $lightgray"This is light gray"$normal
echo -e $blue"This is blue"$normal
echo -e $lightblue"This is Light blue"$normal
echo -e $cyan"This is cyan"$normal
echo -e $lightcyan"This is Light cyan"$normal
echo -e $green"This is Green"$normal
echo -e $lightgreen"This is Light Green"$normal
echo -e $yellow"This is Yellow"$normal
echo -e $lightyellow"This is Light Yellow"$normal
echo -e $red"This is Red"$normal
echo -e $lightred"This is Light Red"$normal
echo $SPACER
echo -e $white$bluebg"This is blue background / white foreground"$normal
echo -e $white$lightbluebg"This is Light blue background / white foreground"$normal
echo -e $black$cyanbg"This is cyan background / black foreground"$normal
echo -e $black$lightcyanbg"This is Light cyan background / black foreground"$normal
echo -e $black$graybg"This is gray background / black foreground"$normal
echo -e $black$lightgraybg"This is Light gray background / black foreground"$normal
echo -e $black$greenbg"This is green background"$normal
echo -e $black$lightgreenbg"This is Light Green background / black foreground"$normal
echo -e $black$yellowbg"This is Yellow background / black foreground"$normal
echo -e $black$lightyellowbg"This is Light Yellow background / black foreground"$normal
echo -e $white$redbg"This is Red background"$normal
echo -e $black$lightredbg"This is Light Red background"$normal

```

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


# Using Color In Python Console/Terminal Scripts  
* TINGE - Output colored text in terminal [https://pypi.org/project/Tinge/](https://pypi.org/project/Tinge/)  
* ansi-escape-room [https://pypi.org/project/ansi-escape-room/](https://pypi.org/project/ansi-escape-room/)  
* tcolopy is a Python library to apply true color for terminal text [https://pypi.org/project/tcolorpy/](https://pypi.org/project/tcolorpy/)  
* cs.ansi-colour: Convenience functions for ANSI terminal colour sequences [https://pypi.org/project/cs.ansi-colour/](https://pypi.org/project/cs.ansi-colour/)  
* pyout: Terminal styling for structured data, with color [https://github.com/pyout/pyout](https://github.com/pyout/pyout)  
* neotermcolor: ANSII Color formatting for output in terminal [https://pypi.org/project/neotermcolor/](https://pypi.org/project/neotermcolor/)  
* Blessed is a broad library for making terminal apps that includes an interface to colors [https://pypi.org/project/blessed/](https://pypi.org/project/blessed/)  
* rainbow can colorize commands output using patterns [https://github.com/nicoulaj/rainbow](https://github.com/nicoulaj/rainbow)  
* Chalk - A Light-weight python package for terminal output in color [https://github.com/anthonyalmarza/chalk](https://github.com/anthonyalmarza/chalk)  
