pip-setup-notes  
===============  

## Sometimes pip complains behind a proxy  

This will require that you configure access through that proxy.
Also, some companies use proprietary certificates (maybe from an Active Directory CA infrastructure).  If you have this issue, then you will have to add the relevant certificates (root and signing CAs) to the shared cacerts.pem or cacerts.crt file.  

# On Windows:  
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


# On Linux:  
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

This was a helpful link: [https://aafaqueabdullah.wordpress.com/2017/04/10/ssl-authentication/](https://aafaqueabdullah.wordpress.com/2017/04/10/ssl-authentication/)  


## Sometimes you use `venv` to manage your virtual environments  

Some companies use proprietary certificates (maybe from an Active Directory CA infrastructure).  
If your organization uses proprietary certificates, then you will have to add the relevant certificates (root and signing CAs) to the shared cacerts.pem or cacerts.crt file.  

If you are behind an http/https proxy, this may require that you update the venv environment cert file:
# On Windows:  
`<currentDevDirectory>\<venvEnv>\Lib\site-packages\pip\_vendor\certifi\cacert.pem`  

# On Linux:  
`<currentDevDirectory>/<venvEnv>/Lib/site-packages/pip/_vendor/certifi/cacert.pem`  
