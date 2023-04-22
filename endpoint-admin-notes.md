## Some Endpoint Admin Notes  

### If you need to open *lots of Terminals* at the same time in order to do your job  
How does this happen?  Maybe you need to support or administer multiple hosts, or maybe you need to routinely execute long-running commands.  In either use case, having a way to open multiple separate terminal instances within a single terminal window manager or physical terminal is a common way to satisfy your needs.  
[```screen```](https://github.com/mccright/rand-notes/blob/master/screen-and-tmux-cheat-sheet.md#screen-command-cheat-sheet) and [```tmux```](https://github.com/mccright/rand-notes/blob/master/screen-and-tmux-cheat-sheet.md#tmux-command-cheat-sheet) are a couple of the most popular tools for opening and managing multiple *terminals* from a single terminal session.  
Here are some useful ```screen``` resources:  
* The pair https://www.golinuxcloud.com/command-screen-linux/ and https://www.golinuxcloud.com/screen-command-in-linux/  
* https://phoenixnap.com/kb/how-to-use-linux-screen-with-commands  
* https://www.tecmint.com/screen-command-examples-to-manage-linux-terminals/  
* https://devhints.io/screen and https://devhints.io/tmux  
* Started with the list at: https://www.golinuxcloud.com/tmux-cheatsheet/  
* How-To page at: https://github.com/tmux/tmux/wiki  



### Understand the hardware that you are dealing with  
**inxi** is a command line system information tool that can be as targeted or as comprehensive as is needed.  See: [https://github.com/smxi/inxi](https://github.com/smxi/inxi) and the documentation at: [https://smxi.org/docs/inxi-installation.htm](https://smxi.org/docs/inxi-installation.htm)  
On an Ubuntu 20.04 endpoint, I needed to install the ```inxi``` application and a collection of recommended utilities to squeeze out a full description of the hardware and setup...  
```terminal
sudo apt-get install --no-install-recommends inxi  

sudo apt-get install --no-install-recommends hddtemp ipmitool freeipmi-tools lm-sensors smartmontools glxinfo mesa-utils wmctrl libcpanel-json-xs-perl libjson-xs-perl libxml-dumper-perl hddtemp  
```
Then get an overview of the hardware with ```inxi -F``` and a more comprehensive view with ```inxi -v8```  


### Don't forget that Microsoft PowerShell runs on Linux  
[https://github.com/PowerShell/PowerShell](https://github.com/PowerShell/PowerShell)  
Binary packages are available for some distributions, and [documentation for a range of distributions is available](https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell-on-linux?view=powershell-7.3).  You can also [install PowerShell from the Snap store](https://learn.microsoft.com/en-us/powershell/scripting/install/install-other-linux?source=recommendations&view=powershell-7.3#installation-via-snap):  
```terminal
sudo snap install powershell --classic  
```
Then use ```pwsh``` to open PowerShell.  


### Set your timesource to a credible reference  
Use the NTP protocol.  
In the U.S., the global address ```time.nist.gov``` is resolved to all of the server addresses listed in the first table at [https://tf.nist.gov/tf-cgi/servers.cgi](https://tf.nist.gov/tf-cgi/servers.cgi) in a round-robin sequence to equalize the load across all of the servers.  Outside North America, see the list of time source maintainers [here](https://webtai.bipm.org/ftp/pub/tai/annual-reports/bipm-annual-report/TIMESERVICES/timeservices.pdf).  It is a bad practice to "hard-code" a particular server name or IP address into an endpoint as this infrastructure incorporates maintenance and evolves...  Also, never query a server more frequently than once every 4 seconds because systems that exceed this rate will be refused service by NIST and possibly be identified as a DoS source.  
Do not use the ancient and expensive "TIME" (port 37) or "DAYTIME" (port 13) protocols.  

### Developers who want to expose their applications on their endpoint to the Internet  
First, this ```idea``` may not be appropriate for any of your developers.  Exposing developer endpoints to inbound Internet traffic necessarily involves risks -- and under many circumstances, business-inappropriate risks.  
If you ***must*** do this, consider **[ngrok](https://ngrok.com)**: ngrok is a globally distributed reverse proxy fronting your web services running on a given endpoint, or in any cloud or private network.  *Paid [ngrok](https://ngrok.com/pricing)* has additional features that support its promotion as "the programmable network edge that adds connectivity, security, and observability to your apps with no code changes."  Pay attention to the details of every request.  The free version may not be suitable for your business, your local environment, or your regulators/investors/customers.  

  
### Booting a PC from a USB drive  
Many PCs have a configuration screen to select the boot drive/media.  
It is often accessed by pressing a key while powering on the PC.  See a nearby file for some [Vendor / Key combinations](https://github.com/mccright/rand-notes/blob/master/Boot-PC-from-a-USB-drive.md) in this repository.  


### Backup with rsync  
rsync synchronizes sets of files.  
Backup to a local destination file system:  
```terminal
rsync -a ~/sourcefiles/ ~/destinationfiles/
```
or  
Backup to a remote destination file system:  
```terminal
rsync -a ~/sourcefiles/ <user>@<host>:destinationfiles/
```
The *-a* preserves timestamps, file ownerships, permissions and recursive scanning.  The trailing slash means to copy the contents of the source directory, but not the directory name itself.  
rsync compares the files in the source and destination and then copies only those source files that are missing or different from the destination.  
Add *--delete* option if you also need to remove destination files when they are no longer on the source.  

Use [https://crontab-generator.org/](https://crontab-generator.org/) to help get your crontab entries perfect...  


### Use find to help copy collections of files  
Copy all the files in a given directory (*source_directory*) to a different target directory (*target_directory*).  
```terminal
find source_directory -type f -exec cp {} target_directory \;
```
If you are concerned about duplicate file names, one approach is to add a ```-i``` to the copy command.  That will tell the ```cp``` command to stop and prompt you for input before overwriting any files:  
```terminal
find source_directory -type f -exec cp -i {} target_directory \;
```

### Use find to help move collections of files  
This approach deals with duplicates by including a description of the directory tree in each file name by replacing the ```'/'``` character with an alternative that is appropriate for file names (*in this example, the dash ```'-'``` character*)  
```terminal
find source_directory -type f | while read F; do mv "$F" "target_directory/${F//\//-}" done
```


### Use find to execute command on files  
Delete files that have not been modified in the last 30 days:  
```  
$ find ~/tmp -type f -mtime +30 -exec rm {} +  
```  
  
Delete files that have not been accessed in the last 30 days:  
```  
$ find ~/tmp -type f -atime +30 -exec rm {} +  
```  
NOTE: Some home directories are mounted with the *noatime* directive to speed up file usage.
  
Delete files larger than 100MB:  
```  
$ find ~/tmp -type f -size +100M -exec rm {} +  
```  

### Use find to delete all files in a directory structure  
```terminal
$ find /home/<username>/directory/start/deletes/here -delete
```

### Securely Delete Files  
Endpoints accumulate non-public data.  At some point you will need to *securely* erase that data.  If you still use traditional hard drives (that have spinning disks), tools like shred, wipe, srm (secure-delete) should work well.  
```terminal
shred -zvu -n 5 <filename>
```
Then confirm your work:  
```terminal
hexdump < <filename>
```
You might also use BleachBit to clean up as well: 
[https://www.bleachbit.org/download/linux](https://www.bleachbit.org/download/linux)  
Or better, see: [https://securityinabox.org/en/files/destroy-sensitive-information/](https://securityinabox.org/en/files/destroy-sensitive-information/)  

### A collection of one-liners  
[https://github.com/jlevy/the-art-of-command-line#one-liners](https://github.com/jlevy/the-art-of-command-line#one-liners)  
And The Art of Command Line from the same author: [https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line)  

**If you use Solid State Drives (SSDs)** (standard in modern computers), USB *thumb* drives, or SD cards/flash memory cards do not use the approach described above. Secure deletion on SSD storage media is a challenge because they use *wear leveling*, a technology that attempts to spread data evenly across all of the media so that any one part of that storage will not be overwritten too many times -- so that the storage device will last longer.  Wear leveling interferes with secure erase programs, which deliberately try to overwrite sensitive files with junk data in order to permanently erase them. As a result, it is better to use full-disk encryption. Encryption avoids the difficulty of secure erasing by making any file on the drive difficult to recover without the required secret.

For more on this topic and about digital security more broadly, you might review: [https://icorn.org/digital-security](https://icorn.org/digital-security)  


### What Application is Using Given Ports  
If an application barks about not being able to use port *NN* (for example port 80 or 443), use the following to identify if the port is already *owned* by another application.
```terminal
sudo ss -tlpn | grep -E ":(80|443)"
```
[Based on a blog ](https://francoconidi.it/solved-certbot-error-could-not-bind-to-ipv4/)  

If that gives some evidence that an application is using a given TCP port, but leaves the root problem dangling, then we might need to *see* the network traffic...  One approach is to '*listen*' to the network interface that *should* be receiving that traffic.  One of the most portable ways to approach this task is with ```tcpdump```.  See:  
* "A tcpdump Primer with Examples." [https://danielmiessler.com/study/tcpdump/](https://danielmiessler.com/study/tcpdump/)  
* "Tcpdump usage examples." [http://www.rationallyparanoid.com/articles/tcpdump.html](http://www.rationallyparanoid.com/articles/tcpdump.html)  
* Network Traffic Analysis [http://sleepyhead.de/howto/?href=network#traffic](http://sleepyhead.de/howto/?href=network#traffic)  
* And a close relative, tstat, "TCP STatistic and Analysis Tool." [http://tstat.tlc.polito.it/](http://tstat.tlc.polito.it/)  

### Some Simple Linux Troubleshooting Reminders  
I have been adding some simple Linux troubleshooting reminders to a different file in this repo.  See:  [https://github.com/mccright/rand-notes/blob/master/Simple-Linux-Troubleshooting.md](https://github.com/mccright/rand-notes/blob/master/Simple-Linux-Troubleshooting.md)  


### Some Flexible Linux Live Distributions  
* **Fedora Live**: Fedora Xfce Desktop is implemented to be fast and lightweight.  It is shipped as a live operating system.  It includes everything you need to try out Fedora's Xfce Desktop.  You don't have to erase anything on your current system to try it out, and it won't put your existing files at risk.  You can have the boot copy all files to RAM first so that it runs very fast using the ```rd.live.ram=1``` boot parameter (*press the TAB key at the grub boot menu*).  If you like it after a test drive, you can install it to a local hard drive from the Live Media desktop. [https://spins.fedoraproject.org/xfce/](https://spins.fedoraproject.org/xfce/)  

* **Lubuntu**:  Lubuntu is a fast and lightweight Ubuntu based operating system using the minimal desktop LXQT and a selection of light applications. Lubuntu has very low hardware requirements.  That said, it makes a lean platform on which to build a fast development endpoint.  [https://lubuntu.me/](https://lubuntu.me/)  
  * NOTE: Starting with Ubuntu 22.04 some legacy behaviors have changed. When you customize audio playback options using Audio Playback Devices (*for example, using the speakers on a non-default HDMI display*), the configuration is changed back to defaults after the endpoint system returns from being in *sleep* mode.  Use pavucontrol (*install the **pavucontrol-qt** package*) to set the default and fallback audio outputs, and they will remain as you expect with legacy expectations. [*this fix was explained by Neil Bothwick in the December 2022 Linux Format, page 11*]  

* **SysLinuxOS**: SysLinuxOS is a specialized Linux operating system for those in infrastructure roles and is currently based on Debian 11 bullseye and a modern kernel (*kernel 5.16-amd64 on 2022-09-03*).  It comes with a large, broad spectrum of applications and utilities installed that would support many categories of infrastructure, maintenance, and collaboration work.  There are two versions, one using the Mate desktop and the other using Gnome.  [https://syslinuxos.com](https://syslinuxos.com)  


### When Your AppImage-Delivered Application Does Not Work
Some applications are delivered via AppImage.  This can be a benefit, as you can be more confident that all the application dependencies are present and correct.  Unfortunately, just downloading the AppImage file may not be all that you need to do...  
In my experience, it can save you some time to verify that the <appName>.AppImage file is executable.  
```ls -al <appName>.AppImage```  
If it is not, set it so:  
```chmod +x <appName>.AppImage```  
See also, "Updating your menu manually" section below if your issue is that a given AppImage-delivered application is not available in your menu...  

### Install a Given Flatpack-Packaged Application  
Assume -- *for this example* -- what we need Flatpak because that is how Github Desktop is distributed.  
1. Install Flatpak (once)  
```sudo apt install flatpak -y```  
Then, before you proceed, reboot your system, or else you will have issues such as applications icons not appearing.  
```reboot```  
2. Enable Flatpack using the following command in your terminal (once).  
``sudo flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo```  
3.  Now install Github Desktop with the following flatpak command:  
```flatpak install flathub io.github.shiftey.Desktop -y```  
You can launch GitHub Desktop with:  
```flatpak run io.github.shiftey.Desktop```  
Or use your menu:  
```Activities > Show Applications > Github Desktop```  
4. Periodically, update/upgrade Github Desktop  
For Flatpak, run the following command to check in your terminal for upgrades.  
```flatpak update```  
See also, "Updating your menu manually" section below if your issue is that a given Flatpack-delivered application is not available in your menu...   

### Updating your menu manually  
System-wide desktop configuration files are in ```/usr/share/applications/```.  User desktop configuration files are in ```$HOME/.local/share/applications```.  Check there for a ```.desktop``` file associated with the one you want to appear in the menu.  ToDo: Explain how to fix it, or to create a new one...  

### Writing and Reading Bootable USB Drives  
* USBImager is a simple GUI application that writes compressed disk images to USB drives and creates backups. Available platforms: Windows, MacOSX and Linux. [https://bztsrc.gitlab.io/usbimager/](https://bztsrc.gitlab.io/usbimager/) and source at [https://gitlab.com/bztsrc/usbimager](https://gitlab.com/bztsrc/usbimager)  
* Etcher  
* Gnome Disks  
* SUSE Imagewriter  
* dd  
* *to be continued*

### My Host has Hundreds of Processes Running. What the hell?
It is common for Linux hosts to run a lot of processes.  ps and top may help, but their ability to visualize what is going on is limited.  
One tool that has helped me better understand some of what is going on is **[pscircle](https://gitlab.com/mildlyparallel/pscircle).**  
Another tool that gets positive reviews is **[bpytop](https://github.com/aristocratos/bpytop)**, resource monitor that shows usage and stats for processor, memory, disks, network and processes.  

### Some Mobile Device Endpoint Notes  
* When you have a business or social visitor who needs Internet access via your WiFi...  This situation can appear as part of a large number of use cases.  Even when you have a dedicated *visitor* SSID set up, getting your visitor's phone or tablet configured requires sharing one or more secrets -- which is not ideal.  Most of us don't have easy-to-use [one-time-password](https://en.wikipedia.org/wiki/One-time_password) systems available for these situations, so sharing secrets can involve some material risks.  The simple act of having *eyes-friendly* passwords laying around, or voicing WiFi connection secrets to those who need them, increases the likelihood of *leakage.*  One simple way to reduce (*not to eliminate*) some of those risks is to have the mobile endpoint configuration details coded into a QR code.  They are not very *eyes-friendly,* but still require careful handling throughout their lifecycle.  
The Linux utility "qrencode" is one way to generate QR code for your mobile endpoint WiFi configuration details.  For example:
```terminal
user@host:~/QR$qrencode -s 9 -l H -o "<QRcodeFileName>.png" "WIFI:S:<theTargetSSID>;T:WPA2;P:<thePassword>;;"
```
Replace `<theTargetSSID>` with your visitor SSID and `<thePassword>` with your visitor WiFi password, and name the file something that does not give away the secrets.  When the mobile endpoint WiFi configuration details are needed, bring up the `<QRcodeFileName>.png` file in your browser and have the visitor scan the QR code on your screen with their mobile device.  *Use this idea only in the "access to visitor/guest WiFi networks.  This approach is NOT risk-appropriate for providing access to high security networks.*  


## If you support Windows endpoints as well:  

### If you are just starting in this role  
...you might start with [PowerShell 101](https://learn.microsoft.com/en-us/powershell/scripting/learn/ps101/00-introduction?view=powershell-7.3)  
And "[Deep Dives](https://learn.microsoft.com/en-us/powershell/scripting/learn/deep-dives/overview?view=powershell-7.3)"  
And a collection of [sample scripts for system administration](https://learn.microsoft.com/en-us/powershell/scripting/samples/sample-scripts-for-administration?view=powershell-7.3)  

### Some Windows Endpoint Notes  
* Some scripts to (*help*) set up a clean Windows 10 endpoint: [https://github.com/Hecsall/clean-windows](https://github.com/Hecsall/clean-windows)  

### Searching for user details in Active Directory using PowerShell  
 * If you know the login name: All the details that you are permitted to see  
     `$user="\<userName\>"`  
     `Get-ADUser -Identity $user -Properties *`  
 * If you only know the email address: All the details that you are permitted to see   
     `$emailAddr="<Email_Address\>"`  
     `Get-ADUser -Filter {EmailAddress -eq $emailAddr} -Properties *`  
 * If you want to know information about the manager of a given user  
     `$user="\<userName\>"`  
     `$mgrcn = Get-ADUser -Identity $user -Properties Manager | Select-Object -Property Manager`  
     `$mgrcnstr = $mgrcn.Manager`  
     `Get-ADUser -Filter {DistinguishedName -eq $mgrcnstr} -Properties DisplayName,UserPrincipalName,whenCreated,CanonicalName,City,LastLogonDate,mobile,MobilePhone,EmailAddress`  

  
### List all the Windows Domain Controllers and Sites within a given Domain  
At a command prompt:  
`c:\windows\system32\nltest.exe /DCLIST:<domainName>`  
  
### Simple way to temporarily bypass PowerShell execution policy
 * From the run dialog (or command prompt) just execute “powershell –ExecutionPolicy Bypass” and it will start a PowerShell session that allows for running scripts and keeps the lowered permissions isolated to just the current running process.  
      `C:\> powershell –ExecutionPolicy Bypass [command] [parameters]`  

