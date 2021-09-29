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
