## Notes on Dealing With Proxies  

#### HTTP proxies are a fact of life for almost anyone in business.  
I use a wide range of tooling, some of which require unique configuration to deal with HTTP proxies.  
These are my notes for dealing with some.  

### PowerShell and Azure  
Lots of businesses use proxies that require authentication.  In this use case, set the proxy environment variable:  

$env:HTTPS_PROXY = "http(s)://{username}:{password}@proxyName.domainName.com"  

It is important to encode *special* characters in your username and/or password.  For example:  

```   
!   is  %21  
#   is  %23  
$   is  %24  
(   is  %28  
)   is  %29  
@   is  %40  
:   is  %3A  
```  

### Blocked by Policy
There some use cases where a platform or vendor enables access via a permit list.  In that case, you need get the external IP address of the proxy approved.  The following commands can help and are script friendly:

* curl https://ipecho.net/plain  
* curl https://ifconfig.co  
* curl https://ifconfig.me  
* curl https://icanhazip.com  

```
$ curl https://ipecho.net/plain
173.18.133.212
```
