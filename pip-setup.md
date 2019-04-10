pip-setup-notes  
===============  

##Sometimes pip complains behind a proxy  

#On Windows:  
Create a file: `%USER%\pip\pip.ini`  

In that file, include:
```ini
[global]
cert = C:\users\<username>\.certificates\<aUsableCAbundle.crt>
PIP_CERT = C:\users\<username>\.certificates\<aUsableCAbundle.crt>
HTTPS_PROXY = http://<user>:<passwd>@<proxy>:<port>
HTTP_PROXY = http://<user>:<passwd>@<proxy>:<port>
 
[install]
cert = C:\users\<username>\.certificates\<aUsableCAbundle.crt>
PIP_CERT = C:\users\<username>\.certificates\<aUsableCAbundle.crt>
HTTPS_PROXY = http://<user>:<passwd>@<proxy>:<port>
HTTP_PROXY = http://<user>:<passwd>@<proxy>:<port>
```
Create a directory: `%USER%\.certificates`
Copy a useful CA certificate bundle into the `%USER%\.certificates` directory


#On Linux:  
Add the following to your `/etc/pip.conf` file:
```ini
[global]
PIP_CERT = /home/<userName>/.certificates/<aUsableCAbundle.crt>
HTTPS_PROXY = http://<user>:<passwd>@<proxy>:<port>
HTTP_PROXY = http://<user>:<passwd>@<proxy>:<port>
 
[install]
PIP_CERT = /home/<userName>/.certificates/<aUsableCAbundle.crt>
HTTPS_PROXY = http://<user>:<passwd>@<proxy>:<port>
HTTP_PROXY = http://<user>:<passwd>@<proxy>:<port>
```

Create a directory: `~/.certificates`
Copy a useful CA certificate bundle into the `~/.certificates` directory

