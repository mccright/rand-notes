pip-setup-notes  
===============  

## Maybe pip is not the answer  
I have been using Ubuntu & Lubuntu 20.04 for a while now and just can't stand how slow pip is -- and how it agressively attempts to get me to use the keyring when for my development context it is not needed.  This odd feature is better described as an issue:  

[pip issue 8719](https://github.com/pypa/pip/issues/8719): "Keyring support is enabled silently when the keyring module is installed in the user's system. There's no way for the user to say whether or not they want keyring support, or to turn it off when it causes an issue. The pip tests don't test the behaviour of the keyring module (just the integration) and there have been a number of issues reported which are down to keyring behaviour: [#8634](https://github.com/pypa/pip/issues/8634), [#8485](https://github.com/pypa/pip/issues/8485), [#8443](https://github.com/pypa/pip/issues/8443), [#8090](https://github.com/pypa/pip/issues/8090)." Thank you [Paul Moore](https://github.com/pfmoore/).  
While I don't have any hard data, it seems reasonable to assume that, globally, this [issue](https://github.com/pypa/pip/issues/8719) has wasted a fantastic amount of developer's time and ought to be a higher priority.  

In practice this feature/issue generates user prompts and results in Warnings for a behavior that unnecessary for a big chunk of humanity, here is an example from my home PC, moments ago:
```term
matt@silt:~/testProj$ python3 --version
Python 3.8.5
matt@silt:~/testProj$ python3 -m pip install --upgrade pip
WARNING: Keyring is skipped due to an exception: Failed to unlock the keyring!
WARNING: Keyring is skipped due to an exception: Failed to unlock the keyring!
WARNING: Keyring is skipped due to an exception: Failed to open keyring: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken..
WARNING: Keyring is skipped due to an exception: Failed to unlock the keyring!
Collecting pip
  WARNING: Keyring is skipped due to an exception: Failed to unlock the keyring!
  Using cached pip-21.0.1-py3-none-any.whl (1.5 MB)
Installing collected packages: pip
Successfully installed pip-21.0.1
matt@silt:~/testProj$ ^C
````
In a pinch, exporting `PYTHON_KEYRING_BACKEND=keyring.backends.null.Keyring` will stop the prompting, which can help in a headless, or Docker context.  

As for the 'speed:'  
```term
matt@silt:~/testProj$ time sudo python3 -m pip install --upgrade pip
Requirement already satisfied: pip in /usr/local/lib/python3.8/dist-packages (21.0.1)

real    1m21.422s
user    0m0.916s
sys     0m0.077s
matt@silt:~/testProj$ time python3 -m pip install --upgrade pip
Defaulting to user installation because normal site-packages is not writeable
Requirement already satisfied: pip in /home/mattm/.local/lib/python3.8/site-packages (21.0.1)

real    1m1.034s
user    0m0.777s
sys     0m0.059s
matt@silt:~/testProj$
```

Other references:  
* "Every single command from pip runs super slow #8485" [https://github.com/pypa/pip/issues/8485](https://github.com/pypa/pip/issues/8485)  
* "Pip install block waiting forever for a keyring to unlock #7883" [https://github.com/pypa/pip/issues/7883](https://github.com/pypa/pip/issues/7883)  
* "Keyring support should require an --enable-keyring flag #8719" [https://github.com/pypa/pip/issues/8719](https://github.com/pypa/pip/issues/8719)  


# In some contexts you will have to use pip, in that case:  

## Sometimes pip complains behind a proxy  

This will require that you configure access through that proxy.
Also, some companies use proprietary certificates (maybe from an Active Directory CA infrastructure).  If you have this issue, then you will have to add the relevant certificates (root and signing CAs) to the shared cacerts.pem or cacerts.crt file.  

# On Windows:  
Create a file: `%USERPROFILE%\pip\pip.ini`  

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
Add the following to your `$HOME/.config/pip/pip.conf` file:
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
[https://docs.python.org/3/library/venv.html](https://docs.python.org/3/library/venv.html)  

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

Sometimes you are on a new system or a multi-user system that you have not used before and things are just not working right.  

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
(`$HOME/.config/pip/pip.conf`)  
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


