# Notes for Configuring New Kali Hosts:  
  
1. Add a new non-root user.  
2. Set the user's password.  
3. Add that user to:  
  * the sudo group.  
  * the lpadmin group.  
4. Change default shell to bash.  
5. Login as that user and change the password.  
6. Update the host.

```
 useradd -m username
 passwd username
 usermod -a -G sudo username
 usermod -a -G lpadmin username
 chsh -s /bin/bash username 
```
Now logout.  Then login as *username* and change the password:  
```
passwd username
```
Update the sources.list file to use https instead of http:
```
sudo vi /etc/apt/sources.list
```
Add ```deb https://mirrors.ocf.berkeley.edu/kali kali-rolling main non-free contrib``` to the sources.list file as well.  

Update the host's software:
```
sudo apt update
sudo apt upgrade -y
```
or  
```
sudo apt full-upgrade
```
then  
```
sudo apt dist-upgrade
sudo apt autoremove
```

## http Proxy Support 
If you are in an environment isolated from the Internet via an http proxy:  
  
Add this to /etc/bash.bashrc  
```
function setproxy(){
        read -ep "Username: " proxusername
        read -esp "Password: " proxpassword
        encodedpassword=`echo -ne $proxpassword | hexdump -v -e '/1 "%02x"' | sed 's@\(..\)@%\1@g'`
        export http_proxy="http://$proxusername:$encodedpassword@proxyname.domain.com:80"
        export https_proxy="http://$proxusername:$encodedpassword@proxyname.domain.com:80"
        export ftp_proxy="http://$proxusername:$encodedpassword@proxyname.domain.com:80"
        }
function rmproxy(){
        unset http_proxy https_proxy ftp_proxy
        }
function lsproxy(){
        echo -e "$http_proxy\n$https_proxy\n$ftp_proxy"
        }
```
Add a 20proxy.conf file to help apt package manager understand how to contact the Kali repos:  
```
vi /etc/apt/apt.conf.d/20proxy.conf
```
Then in that file:  
```
Acquire {
  HTTP::proxy "http://user:password@proxyname.domain.com:port";
  HTTPS::proxy "http://user:password@proxyname.domain.com:port";
  }
```
