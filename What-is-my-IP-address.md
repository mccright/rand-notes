## What is my IP address?  

### External IP address  

When you are on a virtual server, deep within some vendor's infrastructure, or you are behind NAT'ing carrier/business infrastructure, or when you are being blocked because you are not on the *permit-list*, there are terminal/script/console friendly ways to identify your external IP address.  Here are a few that work for me:

*IP v4*  
* dig -4 TXT +short o-o.myaddr.l.google.com @ns1.google.com (when you use DNS server ns1.google.com, with the query "o-o.myaddr.l.google.com" it responds to that address query with the source IP of that request.  It is highly-available, fast and the response is "wrapped" in double-quotes.)  
* dig -4 +short myip.opendns.com @resolver1.opendns.com (not as fast as above, but an option)  
* curl https://ipecho.net/plain  
* curl http://checkip.amazonaws.com/ (highly-available)  
* curl https://ifconfig.co  
* curl https://ifconfig.me  
* curl https://icanhazip.com  
* curl https://wtfismyip.com/text  
* curl https://ident.me or https://v4.ident.me  
* curl https://ipv4bot.whatismyipaddress.com/  
* curl https://ip4.seeip.org  
* curl https://api.ipify.org/
*IP v6*  
* dig -6 TXT +short o-o.myaddr.l.google.com @ns1.google.com (when you use DNS server ns1.google.com, with the query "o-o.myaddr.l.google.com" it responds to that address query with the source IP of that request.  It is fast and the response is "wrapped" in double-quotes.)  

```
$ curl https://ipecho.net/plain
173.18.133.212
```


### Local IP address(es)  

TLDR: Windows - ipconfig.exe; Linux - ifconfig.

On Linux or Windows Linux Subsystem, you can identify the IP address on all local interfaces with a single command:
```bash
/sbin/ifconfig |grep -B1 "inet\|inet6" |awk '{ if ( $1 == "inet" || $1 == "inet6" ) { print "  ",$2 } else if ( $1 != "inet" && $1 != "inet6" ) { print $1 } }'  
```
Make it a function in your Bash shell:
```bash
function intips { /sbin/ifconfig |grep -B1 "inet\|inet6" |awk '{ if ( $1 == "inet" || $1 == "inet6" ) { print "  ",$2 } else if ( $1 != "inet" && $1 != "inet6" ) { print $1 } }'; }
```
*The function above is a copy from: https://www.if-not-true-then-false.com/2010/linux-get-ip-address/.  Thank you JR.*

Or sometimes it is important to get the interface in the default route:

```bash
/sbin/route | awk '/default/ {print $8}'
```
Depending on your platform, you may need to fiddle with the awk command to capture the correct column.

Or if you are just going to iterate through each address and don't care about the interface:
```bash
hostname -I
```
