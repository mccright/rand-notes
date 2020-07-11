## DNS Services  

Here is a list of DNS servers having a range of characteristics:  

* [Alternate DNS](https://alternate-dns.com/): 198.101.242.72 and 23.253.163.53 & IPv6 2001:4800:780e:510:a8cf:392e:ff04:8982 and 2001:4801:7825:103:be76:4eff:fe10:2e49  
* [AdGuard DNS](https://adguard.com/en/adguard-dns/overview.html): 176.103.130.130 and 176.103.130.131 & IPv6 2a00:5a60::ad1:0ff and 2a00:5a60::ad2:0ff  
* [Cloudflare](https://www.cloudflare.com/dns/): 1.1.1.1 and 1.0.0.1  
* [Comodo Secure](https://www.comodo.com/secure-dns): 8.26.56.26 and 8.20.247.20  
* [DNS.Watch](https://dns.watch/index):* 84.200.69.80 and 84.200.70.40& IPv6 2001:1608:10:25::1c04:b12f and 2001:1608:10:25::9249:d69b  
* [FreeDNS](https://freedns.zone/en/):* 45.33.97.5 and 37.235.1.174  
* [Google Public DNS](https://developers.google.com/speed/public-dns/): 8.8.8.8 and 8.8.4.4  
* [OpenDNS](https://www.opendns.com/)/Cisco: 208.67.222.222, 208.67.220.220 and 208.67.222.123  
* [OpenNIC](https://www.opennic.org/): 94.247.43.254 and 192.71.245.208 & IPv6 2a00:dcc0:eda:88:245:71:858e:a15 and 2a00:f826:8:1::254  
* [Quad9](https://www.quad9.net/)/IBM: 9.9.9.9 and 149.112.112.112  
* [UltraDNS](https://www.publicdns.neustar/)/Neustar: 156.154.70.5 and 156.154.71.5 or with some threats blocked 156.154.70.2 and 156.154.71.2 & IPv6 2610:a1:1018::5 and 2610:a1:1019::5 or with some threats blocked 2610:a1:1018::2 and 2610:a1:1019::2   
* [UncensoredDNS](https://blog.uncensoreddns.org/):* 198.180.150.12, 91.239.100.100 and 89.233.43.71 & IPv6 2001:67c:28a4:: and 2a01:3a0:53:53::  
* [Verisign Public DNS](https://www.verisign.com/en_US/security-services/public-dns/index.xhtml): 64.6.65.6 and 64.6.64.6 & IPv6 2620:74:1b::1:1 and 2620:74:1c::2:2  
[*] No logging

### Then test your performance:  
1. dig @8.8.8.8 www.nytimes.com  
2. Or a Linux-based open source DNS Performance Test, a shell script named [DNSPerfTest](https://github.com/cleanbrowsing/dnsperftest).  
3. If you can't run dig, you can use the [Geektools Dig](http://www.geektools.com/digtool.php) webpage to run the same queries.  
