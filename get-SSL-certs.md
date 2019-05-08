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

