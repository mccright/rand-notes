Some time ago I started experiencing long delays/timeouts whenever I installed Python modules.  They succeeded, but took a long time.  
After some initial troubleshooting, I just started changing my behavior -- reading the news while pip did its thing, rather than waiting and getting mad.  
But that approach was not durable...  I can see that my connectivity to Python component repositories is broken:  
```terminal
ltuser@laptop:~$ curl -v -I -6 https://pypi.python.org/
*   Trying 2a04:4e42:58::223:443...
* TCP_NODELAY set
* Immediate connect fail for 2a04:4e42:58::223: Network is unreachable
* Closing connection 0
curl: (7) Couldn't connect to server

ltuser@laptop:~$ curl -v -I -6 https://pypi.org/
*   Trying 2a04:4e42::223:443...
* TCP_NODELAY set
* Immediate connect fail for 2a04:4e42::223: Network is unreachable
*   Trying 2a04:4e42:400::223:443...
* TCP_NODELAY set
* Immediate connect fail for 2a04:4e42:400::223: Network is unreachable
*   Trying 2a04:4e42:200::223:443...
* TCP_NODELAY set
* Immediate connect fail for 2a04:4e42:200::223: Network is unreachable
*   Trying 2a04:4e42:600::223:443...
* TCP_NODELAY set
* Immediate connect fail for 2a04:4e42:600::223: Network is unreachable
* Closing connection 0
curl: (7) Couldn't connect to server
ltuser@laptop:~$ 
```
That sure looked like a routing issue.  I opened the administrative interface to my router and ensured that IPv6 support was turned on.  It was.  I had set it to configure via DHCP, as my ISP required (mediacom, ug).  
Back to the PC to see if I had messed up the configuration.  I am running Lubuntu 20.04.  
```terminal  
ltuser@laptop:~$ ip -6 route
::1 dev lo proto kernel metric 256 pref medium
fe80::/64 dev wlp3s0 proto kernel metric 600 pref medium
ltuser@laptop:~$ ip -4 route
default via 192.168.1.1 dev wlp3s0 proto dhcp metric 600 
172.17.0.0/16 dev docker0 proto kernel scope link src 172.17.0.1 linkdown 
192.168.1.0/24 dev wlp3s0 proto kernel scope link src 192.168.1.140 metric 600 
ltuser@laptop:~$ 
```
That fe80::/64 address looked OK as it indicates a private network (not routable on the open Internet), but I expected it to be associated with an interface.  
After some searches, I tried the tests hosted at [https://test-ipv6.com/](https://test-ipv6.com/).  They reported that mediacom is not supporting IPv6 for me.  

Rather than burn hours attempting to get mediacom support to do anything that might light up IPv6 support for me, I decided to turn off dns support for IPv6 on my PC (only a temporary *fix* until I get the energy to fight mediacom or switch to another ISP).  

My avahi-deamon was set up to try IPv6, then fall back to IPv4 addresses (the Lubuntu installation default), so I uncommented the mDNS line line entry in /etc/nsswitch.conf:  
```terminal
hosts:          files mdns4_minimal [NOTFOUND=return] dns
```
Then restarted the avahi service with:  
```terminal
sudo service avahi-daemon restart
```
Now I am back to *fast* pip installs -- at least no *gasping* delays while IPv6 addresses for component repositories time out.  
```terminal
(env) ltuser@laptop:/tmp$ time pip install numpy
Collecting numpy
  Downloading numpy-1.21.2-cp38-cp38-manylinux_2_12_x86_64.manylinux2010_x86_64.whl (15.8 MB)
     |████████████████████████████████| 15.8 MB 113 kB/s 
Installing collected packages: numpy
Successfully installed numpy-1.21.2

real    0m33.406s
user    0m5.703s
sys     0m1.768s
(env) ltuser@laptop:/tmp$
```

Helpful references:  
* [https://unix.stackexchange.com/questions/586334/how-to-enable-mdns-for-ipv6-on-ubuntu-and-debian](https://unix.stackexchange.com/questions/586334/how-to-enable-mdns-for-ipv6-on-ubuntu-and-debian)  
* [https://ipv6-or-no-ipv6.blogspot.com/2009/02/enabling-ipv6-support-in-avaha.html](https://ipv6-or-no-ipv6.blogspot.com/2009/02/enabling-ipv6-support-in-avaha.html)  
* [https://mediacomcc.custhelp.com/app/social/questions/detail/qid/138/~/ipv6-settings/session/](https://mediacomcc.custhelp.com/app/social/questions/detail/qid/138/~/ipv6-settings/session/)
