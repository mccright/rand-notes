Fetching SSL Certificate Chains  
===============================  

# Use openssl  

Open a command prompt on a machine with openssl available.  
Any Linux machine should work, or on Windows the "Git Bash" prompt also has openssl available.  
Execute the command:  

`openssl s_client -connect <fullyQualifiedHostname>:443 -showcerts`  

Then copy the certificates that you need into your cacerts.pem file(s).  

...all the content between: 

```
-----BEGIN CERTIFICATE-----
MIIHHzCCBgegAwIBAgIKHh84ewABAAA6wjANBgkqhkiG9w0BAQUFADBRMQswCQYD
VQQGEwJVUzEiMCAGA1UEChMZUHJpbmNpcGFsIEZpbmFuY2lhbCBHcm91cDEeMBwG
...(content removed here)
l4p19OP2yW9dNP1m5tQ7UB/vxF88UvvLAOVmFiZeoaS5UB3vXjJMdL1QEID4vioU
8ey9lvD7hRcsI71XdSd4a096jLUbz78oyLiM9MoYSBb8h/Q1IxOBio7OCk8GZecR
2dkz
-----END CERTIFICATE-----
```

# Notes:  

`-showcerts` Displays the server certificate list as sent by the server.  It only consists of certificates the server has sent (in the order the server has sent them). It is not a verified chain.  
There will be a summary first with the DN for each certificate, then details for each certificate in the chain.
Additional openssl command line parameters at: https://www.openssl.org/docs/man1.1.0/man1/openssl-s_client.html#OPTIONS  
