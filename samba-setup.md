## Share a drive or directory on your home network -- Samba Setup  

Sometimes it would be convenient to share some files on your home network.

If you need to share files on your Linux host with Windows endpoints, [Samba](https://en.wikipedia.org/wiki/Samba_(software)) is an easy option.  

This write-up is only risk-appropriate on a trusted network -- like the *safe* segment of my home network.  Consider your environment before using this approach.  

Assume that you want to share a directory called *~/Documents/eBooks* on an Ubuntu host.

Install Samba.
```console
sudo apt install samba
```
Set up the Samba configuration file.
```console
sudo vi /etc/samba/smb.conf
```
Then add the following to the file:
```console
[shared]
  comment = The eBook share
  path = /home/<username>/Documents/eBooks
  read only = yes
  browsable = yes
```

Now that you have told Samba what to do, restart the Samba service so it will pick up your demands and tell the firewall to permit samba traffic.
```console
sudo service smbd restart
sudo ufw allow samba
```
Even on a *safe* network, add a Samba password to each user account that will access the share.
```console
sudo smbpasswd -a <username>
```




[https://en.wikipedia.org/wiki/Samba_(software)](https://en.wikipedia.org/wiki/Samba_(software).  

