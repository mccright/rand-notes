Using bash scripts in Termux  
===============================  

# Use the termux-fix-shebang utility  

Reusing & morphing other's bash scripts keeps the earth rotating.  

Reusing other's bash scripts in the Termux environment in the Android subsystem on a Chromebook requires an additional step.  

The standard `/bin/bash` isn't present in Termux so all those shebangs are broken.  
When I do a `which bash` the output looks like:

`/data/data/com.termux/files/usr/bin/bash`

The Termux environment includes a script to fix those broken shebangs.  

Here is the full lifecycle:  

Fetch that great script that you don't have to write yourself.  

`curl -o helloworld https://github.com/user/helloworld/blob/master/helloworld`

Or:  
Open a Termux shell.  
Open/create your new shell script with vi.  
Enter insert mode.  
Paste the copied script contents into the new file.  
Write, quit.

However you acquire the script,  
Change permissions on the script file so that it is executable.  
Either way, execute the command:  

`termux-fix-shebang helloworld`  

This will fix the shebang and your script should now work.  

My example helloworld now looks like:  

```
#!/data/data/com.termux/files/usr/bin/bash

limit=99
# outputfile=$(mktemp)

if [[ -z $* ]]
then
   echo "NO ARGUMENT!"
   echo "pease provide some hello world content as an argument to this script"
   echo "~/bin/helloworld Matt McCright"
   exit
fi

numinputs=$#

if [[ $numinputs -le $limit ]]
then
   echo $numinputs inputs

   for word in $*
      do
      echo hello $word
      done
fi
```

# Notes:  
For alternatives, see: [https://github.com/termux/termux-packages/issues/98](https://github.com/termux/termux-packages/issues/98)
