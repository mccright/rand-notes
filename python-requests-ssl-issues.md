## INITIAL DRAFT: Dealing with SSL Issues when using Python requests  

In corporate environments, it is not unusual to have HTTP proxies and non-public Certificate Authorities that must be dealt with.  

One symptom of trouble is any error message that includes substrings like:  
```
urlopen error [SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed
```

When this happens, two common causes are https proxies, and cacerts files that are missing the CA for the local environment.  

Try updating you certificate store first -- because might get lucky & have this be a non-issue...  
```
pip install --upgrade certifi  
```

Then try executing your code again because you might have been missing a required-but-really-new certificate authority.  

If that does not work, get a known, working cacerts.pem file and copy it to:  
```
C:\Python<version>\Lib\site-packages\certifi\  
```
...or the equivilent location on your system.  

Then try executing your code again...  

If that does not do it, then explicitly set your proxy.  

# Method 1:  
Add a pair of proxy environment variables.  If your environment requires authentication, try:  
```
HTTPS_PROXY=http://<userName>:<passwd>@proxyhost.yourdomain.com:<port>
HTTP_PROXY=http://<userName>:<passwd>@proxyhost.yourdomain.com:<port>
```

or if authentication is not needed:  
```
HTTPS_PROXY=http://proxyhost.yourdomain.com:<port>
HTTP_PROXY=http://proxyhost.yourdomain.com:<port>
```

Try that...  

# Method 2:  
If you can't add new environment variables, you can add the proxy configuration to your source code.  It could look something like:  
```
# Start proxy modifications
s = requests.Session()
s.proxies = {
 "http": "http://<userName>:<passwd>@proxyhost.yourdomain.com:<port>,
 "https": "http://<userName>:<passwd>@proxyhost.yourdomain.com:<port>",
}
# End proxy modifications
# Remember to update my certificates so that requests knows about our proprietary CA
# copy <'good' cacerts.pem> C:\Python37-x86-64\Lib\site-packages\certifi
URL = "https://google.com"  # just an example...
# Dictionary of HTTP headers
s.headers = {'User-Agent': f'Your name (your@email.com)'} # or something else as appropriate
response = s.get(URL)
```

