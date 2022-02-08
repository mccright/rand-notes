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

or
```terminal
journalctl -b -g theError
```
or  
```terminal
systemctl list-units --failed
```
to see what might have failed to start.  

****
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
