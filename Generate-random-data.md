1000 bytes:
```  
$ dd if=/dev/urandom bs=1000 count=1 of=targetFile.dat  
```  
  
1000 bytes, base64'd, 77 character lines:
```  
$ head -c 1k /dev/urandom | base64 > targetFile.dat  
```  
  
1000 bytes, base64'd, one line [tr used to remove CRLFs]:
```  
$ head -c 1k /dev/urandom | base64 | tr -cd '[[:alnum:]]' > targetFile.dat  
```  
  
2000 bytes, base64'd, one line, trimmed to 1000 characters:
```  
$ head -c 2k /dev/urandom | base64 | tr -cd '[[:alnum:]]' | head -c 1k > targetFile.dat  
```  

Create a random password where the permitted character set is "_A-Za-z0-9!@#$%^&*()[]{},.=+~":  
```  
cat /dev/urandom | tr -dc '_A-Za-z0-9!@#$%^&*()[]{},.=+~' | head -c${1:-10};echo;  
```  
Edit the character set as needed for your system.  
  
NOTE: This is only pseudo-random, but good-enough for many purposes.  
If more highly random data is required, use Crypto classes in Java or .NET.
