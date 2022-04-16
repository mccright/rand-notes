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
The secret textroot
```

### ToDo:  
* Encrypt/Decrypt a file  
* Encrypt/Decrypt a directory of files  
* Encrypt/Decrypt with a strong pass-phrase  
* Add bash scripting for these scenarios  
* Create a Python script to do the same using Python-native features  

