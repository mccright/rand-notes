## What is the Current Operating System?  

In a large, busy environment, it is not uncommon to have quite a few terminal windows open.  

It is also common to have a range of operating systems and versions running.  

Sometimes it is very important to quickly know what OS is running.  

The following command helps me narrow down the environment type so that I can focus on troubleshooting the real problem rather than floundering around with commands that will not run right on the current OS.  

```
lsb_release -sdc
```
or just  
```
lsb_release -a
``` 
 
or  
 
```
cat /etc/os-release
```
 
or  
 
```
hostnamectl
```
or alias a one liner like:  

```python
python3 -c 'import platform;print(f"{platform.platform()} - {platform.version()}")'  
```
see also: [https://note.nkmk.me/en/python-platform-system-release-version/](https://note.nkmk.me/en/python-platform-system-release-version/)  

or  

add an alias for a Python script like: [https://github.com/easybuilders/easybuild/wiki/OS_flavor_name_version](https://github.com/easybuilders/easybuild/wiki/OS_flavor_name_version)  
