# Trojan Source Vulnerability  

This is a reference to *recently* popularized abuse using invisible Unicode characters that mark source code to be right-to-left or left-to-right, enabling maliciously encoded sourcode that appears different to a compiler and to the human eye -- enabling the introductin and execution of arbitrary code.  

CVE: CVE-2021-42574 [https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-42574](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-42574)  

* Here is an example from 2017: [https://github.com/golang/go/issues/20209](https://github.com/golang/go/issues/20209)  
* Here is a recent Krebs article highlighing the scope and potential severity of this issue: [https://krebsonsecurity.com/2021/11/trojan-source-bug-threatens-the-security-of-all-code/](https://krebsonsecurity.com/2021/11/trojan-source-bug-threatens-the-security-of-all-code/)  
* Krebs references "Trojan Source: Invisible Vulnerabilities." By Nicholas Boucher and Ross Anderson: [https://www.trojansource.codes/trojan-source.pdf](https://www.trojansource.codes/trojan-source.pdf)  

---------------------

Table I from [https://www.trojansource.codes/trojan-source.pdf](https://www.trojansource.codes/trojan-source.pdf)  
## Unicode Directionalty Formatting Characters Relevant to Reordering Attacks.  
#### [See the BIDI Specification For the Complete List](https://www.unicode.org/reports/tr9/tr9-42.html).  

| Abbr.  | Code Point | Name | Description |
|--------|------------|-------------------------|-----------------------------------------------|
| LRE | U+202A | Left-to-Right Embedding | Try treating following text as left-to-right. |
| RLE | U+202B | Right-to-Left Embedding | Try treating following text as right-to-left. |
| LRO | U+202D | Left-to-Right Override | Force treating following text as left-to-right. |
| RLO | U+202E | Right-to-Left Override | Force treating following text as right-to-left. |
| LRI | U+2066 | Left-to-Right Isolate | Force treating following text as left-to-right without affecting adjacent text. |
| RLI | U+2067 | Right-to-Left Isolate | Force treating following text as right-to-left without affecting adjacent text. |
| FSI | U+2068 | First Strong Isolate | Force treating following text in direction indicated by the next character. |
| PDF | U+202C | Pop Directional Formatting | Terminate nearest LRE, RLE, LRO, or RLO. |
| PDI | U+2069 | Pop Directional Isolate | Terminate nearest LRI or RLI. |
