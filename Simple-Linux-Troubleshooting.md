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
sane-find-scanner
```
Then ensure that the ATTR{idVendor} and ATTR{idProduct} in /etc/udev/??-scanner.rules match what it finds. And that you are in the GROUP:="groupName" listed there as well.  

