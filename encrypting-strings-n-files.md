# Notes on Encrypting Strings and Files  

Anyone involved in non-public work will need to communicate secrets from time to time.  

Because of the fluid nature of the employment marketplace and the reliance on contingent employees as well as service providers who staff with *next available*, it is important to have safe-enough ways to share secrets without proprietary tooling.  This page is a place to document some simple, on-demand ways to share secrets with those whom you don't share technology infrastructure and whom may have severe constraints on their ability to introduce new crypto tooling into their environment(s).  

In each case, I assume that the secret will be shared out-of-band in a manner that minimizes the opportunities for unauthorized access.  The nature of your use case will determine the level of rigor required to meet your *safe-enough* threshold.  

## Using openssl  
Openssl is available across many environments.  Here are a couple common ways to use openssl to support our mission (*above*):  

The **source** actor encrypts and base64-encodes a string with pre-shared password hosted in an environment variable.  
```terminal
user@demohost:~# echo -n "The secret text"|openssl enc -e -aes-256-ecb -a -salt -k $ENC_VAR
U2FsdGVkX18bV/Clc1Y5I94C9RwTy+mJ9sKCv2fWV2A=
```

The **destination** actor base-64 decodes and decrypts message with the pre-shared password hosted in an environment variable.  
```terminal
echo "U2FsdGVkX18bV/Clc1Y5I94C9RwTy+mJ9sKCv2fWV2A=" | openssl enc -d -base64 -aes-256-ecb -k $ENC_VAR
The secret text
```

In a second scenario the **source** actor encrypts and base64-encodes a text file with pre-shared password hosted in an environment variable.  
```terminal
user@demohost:~# openssl enc -e -aes-256-ecb -a -salt -k $ENC_VAR < 100-Notable-Books-of-2020.txt > tmp.enc
user@demohost:~#
```

The **destination** actor base-64 decodes and decrypts the encrypted file with the pre-shared password hosted in an environment variable.  
```terminal
user@demohost:~# openssl enc -d -base64 -aes-256-ecb -k $ENC_VAR < tmp.enc
The original file contents in clear text...
user@demohost:~#
```


### Research These:  
* **[RFC 9180 Hybrid public-key encryption (HPKE)](https://datatracker.ietf.org/doc/html/rfc9180)**   See a useful overview from CloudFlare: [https://blog.cloudflare.com/hybrid-public-key-encryption/](https://blog.cloudflare.com/hybrid-public-key-encryption/).  
  * "[TL;DR - Hybrid Public Key Encryption.](https://www.franziskuskiefer.de/p/tldr-hybrid-public-key-encryption/)"  
  * "[Hybrid Public Key Encryption: My Involvement in Development and Analysis of a Cryptographic Standard](https://www.benjaminlipp.de/p/hpke-cryptographic-standard/)."  
  * "[An Analysis of Hybrid Public Key Encryption.](https://www.semanticscholar.org/paper/An-Analysis-of-Hybrid-Public-Key-Encryption-Lipp/d8627eb52a4211e59ec897f1a10dd15c96ff7311)" 
  * And some Python implementations of *[draft version 1](https://datatracker.ietf.org/doc/html/draft-barnes-cfrg-hpke-01)* at: [https://github.com/dwd/crypto-examples/blob/master/hpke.py](https://github.com/dwd/crypto-examples/blob/master/hpke.py); and others at [https://github.com/dajiaji/pyhpke](https://github.com/dajiaji/pyhpke), [https://github.com/nymble/hpke](https://github.com/nymble/hpke) and [https://github.com/ctz/hpke-py](https://github.com/ctz/hpke-py), or just check GitHub again: [https://github.com/search?q=HPKE&type=Repositories](https://github.com/search?q=HPKE&type=Repositories).  
* The activity around hpke continues.  For a current view on github, use: [https://github.com/search?q=hpke&type=repositories](https://github.com/search?q=hpke&type=repositories) and for only Python implementations, [https://github.com/search?q=hpke+language%3APython+&type=repositories](https://github.com/search?q=hpke+language%3APython+&type=repositories)  
* or broaden your search with: [https://github.com/search?q=cryptography&type=repositories](https://github.com/search?q=cryptography&type=repositories)  

### ToDo:  
* Encrypt/Decrypt a file - Done  
* Encrypt/Decrypt a directory of files  
* Encrypt/Decrypt with a strong pass-phrase  
* Add bash scripting for these scenarios  
* Create a Python script to do the same using Python-native features  

