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

It is convenient to do your development and testing in Python virtual environments.  
`python3 -m venv env`  

In your virtual environment, your prompt will start with the venv name.  Using the example above, my prompt would look like:  
`(env) d:\PythonProjects\testprojOne>`  

Because we just set up a new `local` Python environment, we need to update the `local` cacert.pem.  

First backup the current cacert.pem.  
`move env\Lib\site-packages\pip\_vendor\certifi\cacert.pem env\Lib\site-packages\pip\_vendor\certifi\cacert.pem.backup`  

Now copy the master to your local environment.  
`copy C:\Users\%USERNAME%\.certificates\cacert.pem env\Lib\site-packages\pip\_vendor\certifi\cacert.pem`  

Some companies use proprietary certificates (maybe from an Active Directory CA infrastructure).  
If your organization uses proprietary certificates, then you will have to add the relevant certificates (root and signing CAs) to the shared cacerts.pem or cacerts.crt file.  

If you are behind an http/https proxy, this may require that you update the venv environment cert file:
# On Windows:  
`<currentDevDirectory>\<venvEnv>\Lib\site-packages\pip\_vendor\certifi\cacert.pem`  

# On Linux:  
`<currentDevDirectory>/<venvEnv>/Lib/site-packages/pip/_vendor/certifi/cacert.pem`  

Sometimes you are on a new system or a multi-user system that you have not used befor and things are just not working right.  

You might break down and `trust` pip's default component repositories.  

# On Windows:  
(`%USER%\pip\pip.ini`)  
```ini
[global]
trusted-host = pypi.python.org
               files.pythonhosted.org
               pypi.org

[install]
trusted-host = pypi.python.org
               files.pythonhosted.org
               pypi.org
```  

# On Linux:  
(`/etc/pip.conf`)  
```ini
[global]
trusted-host = pypi.python.org
               pypi.org
               files.pythonhosted.org

[install]
trusted-host = pypi.python.org
               pypi.org
               files.pythonhosted.org
```  


