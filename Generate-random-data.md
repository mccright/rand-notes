## Generate some random data  

/dev/urandom (present since Linux 1.3.30) provides an interface to the kernel's random number generator.  The  random number generator gathers environmental noise from device drivers and other sources into an entropy pool.  The generator also keeps an estimate of the number of bits of noise in the entropy pool.  From this entropy pool, random numbers are created. 
/dev/urandom will emit data only when sufficient entropy is available -- but that is most of the time on our endpoints and servers (*see: [CSPRNG](https://en.wikipedia.org/wiki/Cryptographically_secure_pseudorandom_number_generator) and  https://words.filippo.io/dispatches/linux-csprng/*).  

### In a Bash environment  
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

Create a 13 character random password where the permitted character set is "_A-Za-z0-9!@#$%^&*,.=+~":  
```  
$ head -c${1:-100} /dev/urandom | tr -dc '_A-Za-z0-9!@#$%^&*,.=+~' | head -c${1:-13};echo;  
```  
or, add a function to your ~/.bashrc:
```  
function randpass(){  < /dev/urandom  tr -dc '_A-Za-z0-9!@#$%^&*,.=+~' | head -c${1:-13};echo;}  
```  

Edit the character set as needed for your system.  

### In a Python environment  
I have some ```random``` string examples at: [https://github.com/mccright/PythonStuff/blob/main/createRandomStrings.py](https://github.com/mccright/PythonStuff/blob/main/createRandomStrings.py)  

Generate psudo-random integers within your Python script:   
```python
# Generate a list of 10 random integers between 0 and 1024
import random
list_random_ints = [random.randint(0, 1024) for i in range(10)]
# list_random_ints contained 
# [11, 757, 247, 724, 882, 74, 596, 874, 991, 565]
# in my sample run.
```
Or, if you need the numbers to resist attack, use Python ```secrets``` [https://docs.python.org/3/library/secrets.html](https://docs.python.org/3/library/secrets.html)  
```python
import secrets
list_random_ints = [secrets.randbelow(1024) for i in range(10)]
# list_random_ints contained 
# [208, 247, 662, 687, 361, 217, 67, 795, 465, 227]
# in my sample run.
```

In the **old days**, we did stuff like this:  
```
$ echo 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'| sed 's/./&\n/g' | shuf | tr -d "\n"
```
or
```
$ echo 'ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789'| sed 's/./&\n/g' | shuf | tr -d "\n"
```
or for some "*really hard-to-guess*" strings:  
```
$ echo 'AaBbCcDdEeFfGgHhIiJjKkLlMmNnOoPpQqRrSsTtUuVvWwXxYyZz0123456789@!#$^_.'| sed 's/./&\n/g' | shuf | tr -d "\n"
```

  
NOTE: Unless otherwise noted, these examples are only pseudo-random, but good-enough for many purposes.  In a Python environment, the ```ramdom``` module uses the 'current system time' as the seed, so a hostile party may have a well-defined attack surface (*including a related timestamp, or other temporal indicator*) making it unsuitable for security-sensitive use cases.  
If more highly random data is required, use crypto-grade classes in Python, Java or .NET.

