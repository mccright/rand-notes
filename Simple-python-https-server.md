# Simple python https server  

## Simple python https server creator for testing.  
One common use case is to quickly set up a web server on one side of a firewall so that you can test connectivity from the other.  
There is a resource for this use case at: [https://github.com/talhasch/pyhttps](https://github.com/talhasch/pyhttps) that I sometimes employ.  
*CAUTION:* Without some caution, this can be a high risk scenario.  Use this only if you have high confidence that you know what you are doing.  

## For Linux:  
Installation with pip  
```    pip install pyhttps```  

Installation from source:  
    Clone repo: ```git clone https://github.com/talhasch/pyhttps && cd pyhttps```   
    Run: ```python setup.py install```   

Usage:  
Run ```pyhttps``` in the terminal.  

It requires that openssl is installed.  

Then test with:  
```    curl --noproxy localhost --insecure https://localhost:4443```  


## For Windows 10:  
```
git clone https://github.com/talhasch/pyhttps 
cd pyhttps
python setup.py install
pip3 install pyhttps
```
Then just run pyhttps....  

...and point your local browser to:  
[https://localhost:4443/](https://localhost:4443/)  
or in a terminal:  
```curl --noproxy localhost --insecure https://localhost:4443```  

## ADVANCED USAGE:  
You can expose the server to the network:  
```    pyhttps --host <ServerHostName> --port 4443```  
Then point your browser on any other endpoint to:  
```    https://<remoteServerHostName>:4443/ ```  


## Windows OpenSSL Troubleshooting:  
```
D:\project\testing>pyhttps
INFO:root:pyhttps 0.0.3
ERROR:root:openssl executable not found!

D:\project\testing>
```

## Fetch OpenSSL binaries:  
OpenSSL Binaries: [https://wiki.openssl.org/index.php/Binaries](https://wiki.openssl.org/index.php/Binaries) 
OpenSSL for Microsoft Windows from FireDaemon:
[https://kb.firedaemon.com/support/solutions/articles/4000121705](https://kb.firedaemon.com/support/solutions/articles/4000121705)   
Pre-compiled x86 (32-bit) and x64 (64-bit) 1.1.1 libraries with dependency on the Visual Studio 2019 runtime (binary-compatible with Visual Studio 2015 and 2017). Primarily built for FireDaemon Fusion, but may be used for any Windows application. The OpenSSL DLL and EXE files are digitally code-signed 'FireDaemon Technologies Limited'.  

This version also has some third party dependencies:  
Get the latest supported Visual C++ downloads (current back through VS 2008):  
[https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads)   
Download the Microsoft Visual C++ Redistributable for Visual Studio 2015, 2017 and 2019.
x64: ```vc_redist.x64.exe``` [https://aka.ms/vs/16/release/vc_redist.x64.exe](https://aka.ms/vs/16/release/vc_redist.x64.exe)  

I put a copy in:  
```\\server\Utils\openssl-1.1``` so you just need to add the following to your ```%PATH%```:  
```<DriveLetter>:\Utils\openssl-1.1\x64\bin```
