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
or
```terminal
journalctl -b -g theError
```

