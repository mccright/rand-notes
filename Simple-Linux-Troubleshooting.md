## Some Simple Linux Troubleshooting Reminders  

### What happened last boot?  
"*dmesg vs journalctl*"  
Remember that ```dmesg``` is *so* 1990s...  
```terminal
dmesg | grep -i theError
```

*Now* we use ```journalctl -b``` -- building on our habits learned with dmesg:  
```terminal
journalctl -b | grep theError
```
*journalctl -b -0* for the current boot, *journalctl -b -1* for the one before, etc.  

or -- *shedding some of our old habits and joining the 21st century* -- *-g* or *--grep=PATTERN* to show entries with MESSAGE matching PATTERN (*this can be any string/sub-string and is case insensitive*)  
```terminal
journalctl -b -g theError
```

or maybe you only care about the last hour (*and don't yet know exactly what you are looking for*)  
```terminal
journalctl --since -1h
```
or
```terminal
journalctl --since 1 hour
```
and if you didn't guess the time right..
```terminal
journalctl --since today
```

or, if you know the name of the service that is the target of your investigation, *-u* shows logs from the specified service and *-x* will add message explanations where available.  
```terminal
journalctl -b -1 -xu the.service
```

Find all entries of priority level range error or higher since booting:
```terminal
journalctl -b -p error
```

or, if you find yourself thinking that you need to ```tail -f``` your log(s) and watch for an error...  
Open two terminals, in the first:  
```terminal
journalctl -f 
```
and then go to the second terminal and perform the action that you suspect is causing the problem at hand, while watching the ```journalctl``` output in the other terminal.  

or, using a completely different approach...  
```terminal
systemctl list-units --failed
```
to see what might have failed to start.  

****
### What is my hardware?  
Sometimes software that is new to you may have hardware constraints.  For example, is my NVIDIA controller supported?  In order to answer that question it is generally important to know the model and version of that device.  'lspci' can reveal those types of information with:  
```terminal
lspci -vmmnn
```

### Where is my scanner?  
```terminal
scanimage -L
```
Run the scanimage command as root (sudo) and as a normal user.  If it only works as root, there must be a permission problem.  Maybe you need to add yourself to the scanner group?  
If the path outlined above is not relevant, then try:
```terminal
sane-find-scanner
```
Then ensure that the ATTR{idVendor} and ATTR{idProduct} in /etc/udev/??-scanner.rules match what it finds. And that you are in the GROUP:="groupName" listed there as well.  

### All the advice I get says my file system is filled -- but it isn't.  What's up?  
If your file systems still have pleanty of free space:  
```terminal
df -k
```
Then maybe you are out of inodes.  Check that with 'df' as well:  
```terminal
df -i
```
Or a tool that can show you what directories are consuming the most space:  
```terminal
ncdu
```
It will take a **long** time if you use it at the root (/).

### My (hardware) device is not working   
Is it a device that requires a firmware file?  
```terminal
dmesg | grep -i firmware
```
You can *follow* log messages with (example watching for USB plug-in details)  
```terminal
dmesg --follow | grep -e sd | grep -e usb
```
or
```terminal
journalctl --follow | grep -e sd | grep -e usb
```
or
```terminal
journalctl -w | grep -e sd | grep -e usb
```

### The OS resists my urge to remove my USB thumb drive  
```terminal
/usr/bin/lsof | grep media/theUSBdrive
```
and if nothing appears, try the same with root to see if it is a system process or the activity of another user causing the problem  
```terminal
sudo /usr/bin/lsof | grep media/theUSBdrive
```

### Someone says they are sending me traffic, and I see no evidence of it.  
One approach is to '*listen*' to the network interface that *should* be receiving that traffic.  One of the most portable ways to approach this task is with ```tcpdump```.  See:  
* "A tcpdump Primer with Examples." [https://danielmiessler.com/study/tcpdump/](https://danielmiessler.com/study/tcpdump/)  
* "Tcpdump usage examples." [http://www.rationallyparanoid.com/articles/tcpdump.html](http://www.rationallyparanoid.com/articles/tcpdump.html)  
* Network Traffic Analysis [http://sleepyhead.de/howto/?href=network#traffic](http://sleepyhead.de/howto/?href=network#traffic)  
* And a close relative, tstat, "TCP STatistic and Analysis Tool." [http://tstat.tlc.polito.it/](http://tstat.tlc.polito.it/)  


### An endpoint was returned to you -- *or you just found one of your 'old' PCs and want to use it again* -- and you don't have access to root  
An easy approach is to press ```e``` when the GRUB menu appears (*or ESC if the boot is silent*) and edit the boot menu.  
Edit the line starting with ```linux``` or add a new one and comment out the old.  It needs to include ```init=/bin/bash```.  That will tell the kernel to run a Bash shell without running any other services.  Only the ```/``` root file system is mounted.  Set the root password with ```$ passwd root``` and then reboot.  You are good to go...   ***If the root filesystem mount read-only***: You also need to add ```rootflags=rw``` to the Grub menu that you initially edited above.  
