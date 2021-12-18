## Log4Shell -- log4j Vulnerability Notes  

If you have not yet started your upgrade(s), upgrade to 2.16.x.  
If you upgraded to 2.15.0, upgrade again, to 2.16.x.

Why should I care a vulnerable log4j component?  Sonatype recorded that:  

* The affected versions were downloaded 28.6 M times in the last 4 months  
* Log4j-core is in the top 0.1% percentile measured by download volume  
* Log4j is seen as a dependency in almost 7,000 open source projects  

### What is the vulnerability?  
* "New Log4j Vulnerability CVE-2021-44228: Info and Remediation." By Daniel Elkabes
[https://www.whitesourcesoftware.com/resources/blog/log4j-vulnerability-cve-2021-44228](https://www.whitesourcesoftware.com/resources/blog/log4j-vulnerability-cve-2021-44228)  
* [https://www.lunasec.io/docs/blog/log4j-zero-day/](https://www.lunasec.io/docs/blog/log4j-zero-day/)  
* [https://www.lunasec.io/docs/blog/log4shell-live-patch-technical/](https://www.lunasec.io/docs/blog/log4shell-live-patch-technical/)  
* [https://www.lunasec.io/docs/blog/log4j-zero-day-severity-of-cve-2021-45046-increased/](https://www.lunasec.io/docs/blog/log4j-zero-day-severity-of-cve-2021-45046-increased/)  
* [https://logging.apache.org/log4j/2.x/security.html](https://logging.apache.org/log4j/2.x/security.html)  
* And for an illustration of attacker activity: [https://thehackernews.com/2021/12/apache-log4j-vulnerability-log4shell.html](https://thehackernews.com/2021/12/apache-log4j-vulnerability-log4shell.html)    
* CVE-2021-44228 Detail: [https://www.cve.org/CVERecord?id=CVE-2021-44228](https://www.cve.org/CVERecord?id=CVE-2021-44228) or [https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-44228](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-44228)  
* CVE-2021-45046 Detail: [https://www.cve.org/CVERecord?id=CVE-2021-45046](https://www.cve.org/CVERecord?id=CVE-2021-45046) or [https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-45046](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-45046)  


*So, ask yourself:*  
* Do we have this Log4j vulnerability exposed to potential attack/exploit?  
* If yes, where?  
* How quickly should we get fixes in place?  


### Apache Log4j Vulnerability Guidance  
[https://www.cisa.gov/uscert/apache-log4j-vulnerability-guidance](https://www.cisa.gov/uscert/apache-log4j-vulnerability-guidance)  
CISA and its partners, through the Joint Cyber Defense Collaborative, are responding to active, widespread exploitation of a critical remote code execution (RCE) vulnerability (CVE-2021-44228) in Apache’s Log4j software library, versions 2.0-beta9 to 2.14.1, known as "Log4Shell" and "Logjam." Log4j is very broadly used in a variety of consumer and enterprise services, websites, and applications—as well as in operational technology products—to log security and performance information. An unauthenticated remote actor could exploit this vulnerability to take control of an affected system.  

Apache initially recommended that all versions of Log4J be upgraded to Log4J 2.15.0, but a new denial of service vulnerability in 2.15.0 led to release of log4j 2.16.0 which has a more conservative default configuation.  If you have not begun your 2.15.0 upgrade work, it will make sense for most to implement 2.16.0.

If you are unsure where log4j is referenced within your application, the Maven dependency tree command will output evidence or your dependencies within your application. Be sure to search for the existence of Log4j in that Maven dependency tree output.

### What about Log4J 1.x?
Continuing to use Log4j 1.x brings evidence-based vulnerabilities:

* "Deserialization of Untrusted Data" CVS 9.8 https://security.snyk.io/vuln/SNYK-JAVA-LOG4J-572732 and
* "Remote Code Execution (RCE)" CVS 6.6 https://security.snyk.io/vuln/SNYK-JAVA-LOG4J-2316893 and
* The discussion starting at https://github.com/apache/logging-log4j2/pull/608#issuecomment-991723301 appears to offer evidence that the log4j 1.x source code includes support for a jndi:ldap approach to exploits.

If you work in global financial services, there seem to be risks that normal (or hostile) regulator, partner, customer, or prospect reviews or risk management inquiries will discover your doing business using of these increasingly ancient and unsupported components.  It seems like any global financial services enterprise in this state could expect some level of negative impact because this behavior seems increasingly misaligned with generally-accepted expectations.

Making tight and legalistic connections between CVE-2021-44228 and log4j 1.x seem unproductive in the context of the broader risks that these components bring with their use.

Updating dependencies with Maven: [https://www.baeldung.com/maven-dependency-latest-version](https://www.baeldung.com/maven-dependency-latest-version)  

#### CISA Log4j (CVE-2021-44228) Vulnerability Guidance  
* CISA [https://github.com/cisagov/log4j-affected-db](https://github.com/cisagov/log4j-affected-db)  
* Netherlands National Cyber Security Center (NCSC) Log4j Vulnerability (CVE-2021-44228) Resources  [https://github.com/NCSC-NL/log4shell](https://github.com/NCSC-NL/log4shell)  

"Apache takes off, nukes insecure feature at the heart of Log4j from orbit with v2.16." [https://www.theregister.com/2021/12/14/apache_log4j_v2_16_jndi_disabled_default/](https://www.theregister.com/2021/12/14/apache_log4j_v2_16_jndi_disabled_default/)  


*Log4j 2.15.0 and previously suggested mitigations may not be enough*  
[https://isc.sans.edu/diary/rss/28134](https://isc.sans.edu/diary/rss/28134)  
Published: 2021-12-14  
Last Updated: 2021-12-14 20:55:02 UTC  
by Renato Marinho (Version: 1)  
