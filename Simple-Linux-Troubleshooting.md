## Some Simple Linux Troubleshooting Reminders  

### What happened last boot?  
"*dmesg vs journalctl*"  
Remember that *dmesg* is so 1990s...  
```terminal
dmesg | grep theError
```

Now we use journalctl -b  
```terminal
journalctl -b | grep theError
```
*journalctl -b -0* for the current boot, *journalctl -b -1* for the one before, etc.  

or, *-g* or *--grep=PATTERN* to show entries with MESSAGE matching PATTERN (*this can be any string/sub-string and is case insensitive*)  
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


or  
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
