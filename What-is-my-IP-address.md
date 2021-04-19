## What is my IP address?  

When you are on a virtual server, deep within some vendor's infrastructure, or you are behind NAT'ing carrier/business infrastructure, or when you are being blocked because you are not on the *permit-list*, there are terminal/script/console friendly ways to identify your external IP address.  Here are a few that work for me:

* dig -6 TXT +short o-o.myaddr.l.google.com @ns1.google.com (when you use DNS server ns1.google.com, with the query "o-o.myaddr.l.google.com" it responds to that address query with the source IP of that request.  It is highly-available, fast and the response is "wrapped" in double-quotes.)  
* dig +short myip.opendns.com @resolver1.opendns.com (not as fast as above, but an option)  
* curl https://ipecho.net/plain  
* curl http://checkip.amazonaws.com/ (highly-available)  
* curl https://ifconfig.co  
* curl https://ifconfig.me  
* curl https://icanhazip.com  
* curl https://wtfismyip.com/text  
* curl https://ident.me or https://v4.ident.me  
* curl https://ipv4bot.whatismyipaddress.com/  
* curl https://ip4.seeip.org  
*IP v6*  
* dig -6 TXT +short o-o.myaddr.l.google.com @ns1.google.com (when you use DNS server ns1.google.com, with the query "o-o.myaddr.l.google.com" it responds to that address query with the source IP of that request.  It is fast and the response is "wrapped" in double-quotes.)  

```
$ curl https://ipecho.net/plain
173.18.133.212
```
