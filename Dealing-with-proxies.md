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

### Java and Maven
There are a number of approaches to dealing with authenticating proxies in a Java/Maven environment.  Not every approach will be risk appropriate for every use case.  

Command line:

Environment variables:  

Configuration files:  


### Node and npm  



### Python and pip  



### dotNet and NuGet  



### Blocked by Vendor Policy  
There some use cases where a platform or vendor enables access via a permit list.  In that case, you need get the external IP address of the proxy approved.  The following commands can help and are script friendly:

**IP v4**  
* dig -4 TXT +short o-o.myaddr.l.google.com @ns1.google.com (when you use DNS server ns1.google.com, with the query "o-o.myaddr.l.google.com" it responds to that address query with the source IP of that request.  It is fast and the response is "wrapped" in double-quotes.)  
* curl https://ipecho.net/plain  
* curl http://checkip.amazonaws.com/  
* curl https://ifconfig.co  
* curl https://ifconfig.me  
* curl https://icanhazip.com  
* curl https://wtfismyip.com/text  
* curl https://ipv4.ident.me  
* curl https://ip4.seeip.org  
**IP v6**  
* dig -6 TXT +short o-o.myaddr.l.google.com @ns1.google.com (when you use DNS server ns1.google.com, with the query "o-o.myaddr.l.google.com" it responds to that address query with the source IP of that request.  It is fast and the response is "wrapped" in double-quotes.)  

```
$ curl https://ipecho.net/plain
173.18.133.212
```
