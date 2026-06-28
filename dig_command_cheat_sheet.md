# My dig Cheatsheet  

Dig (Domain Information Groper) is part of the BIND (Berkeley Internet Name Domain) suite of [DNS](https://en.wikipedia.org/wiki/Domain_Name_System) utilities. It queries [DNS](https://en.wikipedia.org/wiki/Domain_Name_System) name servers and shows [records](https://en.wikipedia.org/wiki/List_of_DNS_record_types) such as:  
* **A** record used to translate from a domain name to an IPv4 address  
* **AAAA** record used to translate from a domain name to an IPv6 address  
* **MX** record specifies the mail server used to handle mail for a domain specified in an e-mail address  
* **NS** record lists which name servers can answer lookups on a [DNS zone](https://en.wikipedia.org/wiki/DNS_zone)  
* **TXT** record (*Text record*) [RFC 1035](https://www.rfc-editor.org/info/rfc1035/), originally used for arbitrary human-readable text in a DNS record. Since the early 1990s, however, this record more often carries machine-readable data, such as specified by [RFC 1464](https://datatracker.ietf.org/doc/html/rfc1464)  
* **CNAME** record (*[Canonical name record](https://en.wikipedia.org/wiki/Canonical_name)*), Alias of one name to another: the DNS lookup will continue by retrying the lookup with the new name  
* **PTR** record  [RFC 1035](https://datatracker.ietf.org/doc/html/rfc1035). Pointer to a [canonical name](https://en.wikipedia.org/wiki/Canonical_name). Unlike a CNAME, DNS processing stops and just the name is returned. The most common use is for implementing [reverse DNS lookups](https://en.wikipedia.org/wiki/Reverse_DNS_lookup), but other uses include such things as [DNS-SD](https://en.wikipedia.org/wiki/DNS-SD)  

For a more comprehensive list of DNS record types see: [wikipedia.org/wiki/List_of_DNS_record_types](https://en.wikipedia.org/wiki/List_of_DNS_record_types)  





```/usr/bin/dig +short example.com```  
Usage: Collect the IP address or another specific record type without extra context, useful in some scripting use cases.  
Output: ```93.184.216.34```  

```/usr/bin/dig MX wellsfargo.com +short ```  
Usage: Collect the IP address(es) for the domain's mail server(s) without extra context, useful in some scripting use cases.  
Output: ```10 mxb-00004003.gslb.pphosted.com.
        10 mxa-00004003.gslb.pphosted.com.```  

```/usr/bin/dig MX wellsfargo.com ```  
Usage: Collect the IP address(es) for the domain's mail server(s) including context, useful in some troubleshooting use cases.  
Output: 
```Terminal
matt@host:~$ /usr/bin/dig MX wellsfargo.com

; <<>> DiG 9.20.18-1ubuntu2.1-Ubuntu <<>> MX wellsfargo.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 7557
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;wellsfargo.com.                        IN      MX

;; ANSWER SECTION:
wellsfargo.com.         353     IN      MX      10 mxb-00004003.gslb.pphosted.com.
wellsfargo.com.         353     IN      MX      10 mxa-00004003.gslb.pphosted.com.

;; Query time: 19 msec
;; SERVER: 10.255.255.254#53(10.255.255.254) (UDP)
;; WHEN: Sat Jun 27 17:24:01 CDT 2026
;; MSG SIZE  rcvd: 115

matt@host:~$
```


```/usr/bin/dig SOA wellsfargo.com ```  
Usage: Collect the hostname for the domain's SOA start of authority -- the authoritative DNS server server -- including context, useful in some troubleshooting use cases.  
Output: 
```Terminal
matt@host:~$ /usr/bin/dig SOA wellsfargo.com

; <<>> DiG 9.20.18-1ubuntu2.1-Ubuntu <<>> SOA wellsfargo.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 40856
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;wellsfargo.com.                        IN      SOA

;; ANSWER SECTION:
wellsfargo.com.         3600    IN      SOA     edns1.ultradns.com. hostmaster.wellsfargo.com. 2009396341 1800 900 2592000 300

;; Query time: 31 msec
;; SERVER: 10.255.255.254#53(10.255.255.254) (UDP)
;; WHEN: Sat Jun 27 17:33:32 CDT 2026
;; MSG SIZE  rcvd: 105

matt@host:~$
```

SOA – the start of authority, shows the authoritative DNS server. In this record, you see valuable information about the zone. There is only one SOA per zone.
``` /usr/bin/dig SOA wellsfargo.com +short ```  
Usage: Collect the hostname for the domain's SOA start of authority -- the authoritative DNS server server -- including context, useful in some troubleshooting use cases.  
Output: ```edns1.ultradns.com. hostmaster.wellsfargo.com. 2009396341 1800 900 2592000 300```  


Google DNS
dig @8.8.8.8
Cloudflare DNS
dig @1.1.1.1


https://www.cyberithub.com/20-dig-command-examples-in-linux-cheat-sheet/

https://www.dnsdingo.com/dns-commands.html

https://www.commandinline.com/cheat-sheet/dig/

https://www.cloudns.net/blog/linux-dig-command-install-use/

https://en.wikipedia.org/wiki/Domain_Name_System

https://github.com/geeek-khushi15/DIG-Commands-

https://linuxize.com/cheatsheet/dig/

https://linuxize.com/post/how-to-use-dig-command-to-query-dns-in-linux/

List of DNS record types
https://en.wikipedia.org/wiki/List_of_DNS_record_types


Chinese A.I. Models Close the Gap With Anthropic and OpenAI
Silicon Valley engineers recently flocked to new technology from a Chinese company, Z.ai, that is almost as good as its American competitors but much cheaper.
https://www.nytimes.com/2026/06/25/technology/zai-china-artificial-intelligence-models.html