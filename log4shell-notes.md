## Log4Shell -- log4j Vulnerability Notes  

If you have not yet started your upgrade(s), upgrade to 2.16.x.  

Why should I care a vulnerable log4j component?  Sonatype recorded that:  

* The affected versions were downloaded 28.6 M times in the last 4 months  
* Log4j-core is in the top 0.1% percentile measured by download volume  
* Log4j is seen as a dependency in almost 7,000 open source projects  

### What is the vulnerability?  
* CVE-2021-44228 Detail: [https://www.cve.org/CVERecord?id=CVE-2021-44228](https://www.cve.org/CVERecord?id=CVE-2021-44228)  
* CVE-2021-45046 Detail: [https://www.cve.org/CVERecord?id=CVE-2021-45046](https://www.cve.org/CVERecord?id=CVE-2021-45046)  

So, ask yourself:  
* Do we have this Log4j vulnerability exposed to potential attack/exploit?  
* If yes, where?  
* How quickly can we get fixes in place?  


### Apache Log4j Vulnerability Guidance  
[https://www.cisa.gov/uscert/apache-log4j-vulnerability-guidance](https://www.cisa.gov/uscert/apache-log4j-vulnerability-guidance)  
CISA and its partners, through the Joint Cyber Defense Collaborative, are responding to active, widespread exploitation of a critical remote code execution (RCE) vulnerability (CVE-2021-44228) in Apache’s Log4j software library, versions 2.0-beta9 to 2.14.1, known as "Log4Shell" and "Logjam." Log4j is very broadly used in a variety of consumer and enterprise services, websites, and applications—as well as in operational technology products—to log security and performance information. An unauthenticated remote actor could exploit this vulnerability to take control of an affected system.  

#### CISA Log4j (CVE-2021-44228) Vulnerability Guidance  
* CISA [https://github.com/cisagov/log4j-affected-db](https://github.com/cisagov/log4j-affected-db)  
* Netherlands National Cyber Security Center (NCSC) Log4j Vulnerability (CVE-2021-44228) Resources  [https://github.com/NCSC-NL/log4shell](https://github.com/NCSC-NL/log4shell)  

"Apache takes off, nukes insecure feature at the heart of Log4j from orbit with v2.16." [https://www.theregister.com/2021/12/14/apache_log4j_v2_16_jndi_disabled_default/](https://www.theregister.com/2021/12/14/apache_log4j_v2_16_jndi_disabled_default/)  


*Log4j 2.15.0 and previously suggested mitigations may not be enough*  
[https://isc.sans.edu/diary/rss/28134](https://isc.sans.edu/diary/rss/28134)  
Published: 2021-12-14  
Last Updated: 2021-12-14 20:55:02 UTC  
by Renato Marinho (Version: 1)  
