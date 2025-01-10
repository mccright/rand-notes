## Some Endpoint Admin Notes  

### If you need to open *lots of Terminals* at the same time in order to do your job  
How does this happen?  Maybe you need to support or administer multiple hosts, or maybe you need to routinely execute long-running commands.  In either use case, having a way to open multiple separate terminal instances within a single terminal window manager or physical terminal is a common way to satisfy your needs.  
[```screen```](https://github.com/mccright/rand-notes/blob/master/screen-and-tmux-cheat-sheet.md#screen-command-cheat-sheet) and [```tmux```](https://github.com/mccright/rand-notes/blob/master/screen-and-tmux-cheat-sheet.md#tmux-command-cheat-sheet) are a couple of the most popular tools for opening and managing multiple *terminals* from a single terminal session.  
Here are some useful ```screen``` and ```tmux``` resources:  
* The pair https://www.golinuxcloud.com/command-screen-linux/ and https://www.golinuxcloud.com/screen-command-in-linux/  
* https://phoenixnap.com/kb/how-to-use-linux-screen-with-commands  
* https://www.tecmint.com/screen-command-examples-to-manage-linux-terminals/  
* https://devhints.io/screen and https://devhints.io/tmux  
* Started with the list at: https://www.golinuxcloud.com/tmux-cheatsheet/  
* How-To page at: https://github.com/tmux/tmux/wiki  

Choosing the right [Window Manager](https://en.wikipedia.org/wiki/Window_manager) for yourself might also make you job easier.  There is a great list of window managers maintained at  [https://wiki.archlinux.org/title/Window_manager](https://wiki.archlinux.org/title/Window_manager) (*not just for Arch Linux*).  


### Understand the hardware that you are dealing with  
```inxi``` is a command line system information tool that can be as targeted or as comprehensive as is needed.  See: [https://github.com/smxi/inxi](https://github.com/smxi/inxi) and the documentation at: [https://smxi.org/docs/inxi-installation.htm](https://smxi.org/docs/inxi-installation.htm)  
On an Ubuntu 20.04 endpoint, I needed to install the ```inxi``` application and a collection of recommended utilities to squeeze out a full description of the hardware and setup...  
```terminal
sudo apt-get install --no-install-recommends inxi  

sudo apt-get install --no-install-recommends hddtemp ipmitool freeipmi-tools lm-sensors smartmontools glxinfo mesa-utils wmctrl libcpanel-json-xs-perl libjson-xs-perl libxml-dumper-perl hddtemp  
```
Then get an overview of the hardware with ```inxi -F``` and a more comprehensive view with ```inxi -v8```  

Another approach is to use ```cfg2html```: https://www.cfg2html.com/ and https://github.com/cfg2html/cfg2html  
```cfg2html``` output (*both html and text*) has an extensive hardware section.  

supportinfo
getsysinfo:  
* https://github.com/seocringe/getsysinfo  
* https://github.com/atayarani/getsysinfo  
* https://github.com/LumineonRL/GetSysInfo
get_config


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


### How to set up an SSD with the Raspberry Pi 4 (*or almost any other Debian-based Linux endpoint*)
By {The Pi Hut](https://thepihut.com/blogs/raspberry-pi-tutorials/how-to-set-up-an-ssd-with-the-raspberry-pi). You bought a new SSD and a USB3-to-SSD adapter cable and need to get it all set up...  If this was a new drive, in order to use it the SSD needs to have partition tables and partitions created, and these need to be 'mounted.' [This highly illustrated article](https://thepihut.com/blogs/raspberry-pi-tutorials/how-to-set-up-an-ssd-with-the-raspberry-pi) takes you through the detailed steps for getting that external SSD set up for use.  


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
To save time and storage space, see [https://github.com/basnijholt/rsync-time-machine.py](https://github.com/basnijholt/rsync-time-machine.py) "a Python port of the rsync-time-backup script, offering Time Machine-style backups using rsync. It creates incremental backups of files and directories to the destination of your choice. The backups are structured in a way that makes it easy to recover any file at any point in time."    


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


### Use find to identify all files in your home directory that are newer than "<filename>"    
```terminal
$ find ~ -type f -newer <filename>

```
### Use find to identify all files having a given filename pattern in your home directory that are newer than "<filename>"  
In this case, identify only those files with names matching the pattern ```-name "*.md"```.  
```terminal
$ find ~ -name "*.md" -type f -newer <filename>

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

### Chain Commands Where Practical  
| Description           |\: |&& |\|\| |\| |&  |
|:----------------------|:-:|:-:|:---:|:-:|:-:|
|Will the 2nd command execute if the first command has executed successfully?|Y |Y |N |Y |Y |
|Will the 2nd command execute if the 1st command failed? |Y |N |Y |Y |Y |
|Will the 2nd command execute only depending on the status of the 1st command? |N |Y |Y |N |N |
|Will the commands execute in parallel? |N |N |N |N |Y |
(*from page 68 Linux Format/LXF228 presenting content from www.linuxnix.com*)  


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
``sudo flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo ```  
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
Related References On This Topic:  
"[5 Best Ways to Generate QR Codes Using the PyQRCode Module in Python](https://blog.finxter.com/5-best-ways-to-generate-qr-codes-using-the-pyqrcode-module-in-python/)." March 8, 2024 by Emily Rosemary Collins  
Create QR Codes with PyQRCode: [https://pythonhosted.org/PyQRCode/create.html](https://pythonhosted.org/PyQRCode/create.html)  
Some history and background information about QRcodes: [https://www.qr-code-generator.com/qr-code-marketing/qr-codes-basics/](https://www.qr-code-generator.com/qr-code-marketing/qr-codes-basics/) and [https://www.qrcode.com/en/history/](https://www.qrcode.com/en/history/)  
Short overview of QRcode types: [https://www.qrcode.com/en/codes/](https://www.qrcode.com/en/codes/)  
[https://pythonhosted.org/PyQRCode/moddoc.html](https://pythonhosted.org/PyQRCode/moddoc.html)  


### Questions about what "*Office Suite*" of applications to use  
Over time, users will ask about options for full-featured word processor & spreadsheet applications.  I believe that [LibreOffice](https://www.libreoffice.org/) is an excellent response for broad swaths of user groups.  LibreOffice is compatible with other major office suites.  LibreOffice includes:  
* "[Writer](https://www.libreoffice.org/discover/writer/)" a word processor,  
* "[Calc](https://www.libreoffice.org/discover/calc/)" a powerful spreadsheet,  
* "[Impress](https://www.libreoffice.org/discover/impress/)" for creating presentations,  
* "[Draw](https://www.libreoffice.org/discover/draw/)" for diagrams and 2D/3D illustrations,  
* "[Base](https://www.libreoffice.org/discover/base/)" to deal with databases,  
* "[Math](https://www.libreoffice.org/discover/math/)" to create mathematical equations,  
* "[Charts](https://www.libreoffice.org/discover/charts/)" to create and embed charts within your documents.  
Why LibreOffice?  LibreOffice is free and open source software.  It is a successor to [OpenOffice](https://www.openoffice.org/product/index.html) which had its last major update in early 2014. LibreOffice has more than ten years of OpenOffice source code cleanup with the addition of mature, formal, manual and automated functionality and security testing. It [adds many extra features and improved](https://www.libreoffice.org/discover/libreoffice-vs-openoffice/) "[Microsoft Office](https://www.office.com/)" compatibility, has regular releases with security updates, and is released for desktop, mobile and cloud environments.  


## If you support Windows endpoints as well:  

### If you are just starting in this role  
...you might start with [PowerShell 101](https://learn.microsoft.com/en-us/powershell/scripting/learn/ps101/00-introduction?view=powershell-7.3)  
And "[Deep Dives](https://learn.microsoft.com/en-us/powershell/scripting/learn/deep-dives/overview?view=powershell-7.3)"  
And a collection of [sample scripts for system administration](https://learn.microsoft.com/en-us/powershell/scripting/samples/sample-scripts-for-administration?view=powershell-7.3)  

### Some Windows Endpoint Notes  
* See what is installed:  
  List apps for all users:  
    ```Get-AppxProvisionedPackage -Online | Select-Object DisplayName | Format-Table -HideTableHeaders```  
  List apps for all users and remove all Microsoft apps from the list:  
	```Get-AppxProvisionedPackage -Online | Select-Object DisplayName, PackageName | Select-String -Pattern 'Microsoft'  -NotMatch```  
  List apps for all users and present only apps from a specified vendor in the list (example 'Lenovo'):  
	```Get-AppxProvisionedPackage -Online | Select-Object DisplayName, PackageName | Select-String -Pattern 'lenovo'```  
  List apps for the current user:  
    ```Get-AppxPackage | Select-Object Name | Format-Table -HideTableHeaders```  
  List apps for the current user and remove all Microsoft apps from the list:  
    ```Get-AppxPackage | Select-Object Name, Publisher | Select-String -Pattern 'Microsoft'  -NotMatch```  
  List apps for the current user and present only apps from a specified vendor in the list (example 'Lenovo'):  
    ```Get-AppxPackage | Select-Object Name, Publisher | Select-String -Pattern 'lenovo'```  

#### Some Windows Event Messages for Monitoring -- Some Resources That Help You Search For What You Need:  
* [Basic security audit policy settings overview](https://learn.microsoft.com/en-us/windows/security/threat-protection/auditing/basic-security-audit-policy-settings)  
* [Audit logon events](https://learn.microsoft.com/en-us/windows/security/threat-protection/auditing/basic-audit-logon-events)  
* [Audit account logon events](https://learn.microsoft.com/en-us/windows/security/threat-protection/auditing/basic-audit-account-logon-events)  
* [Audit account management](https://learn.microsoft.com/en-us/windows/security/threat-protection/auditing/basic-audit-account-management)  
* [Audit object access](https://learn.microsoft.com/en-us/windows/security/threat-protection/auditing/basic-audit-object-access)  
* [Audit policy change](https://learn.microsoft.com/en-us/windows/security/threat-protection/auditing/basic-audit-policy-change)  
* [Audit process tracking](https://learn.microsoft.com/en-us/windows/security/threat-protection/auditing/basic-audit-process-tracking)  
* [Audit system events](https://learn.microsoft.com/en-us/windows/security/threat-protection/auditing/basic-audit-system-events)  
* [Advanced security auditing FAQ](https://learn.microsoft.com/en-us/windows/security/threat-protection/auditing/advanced-security-auditing-faq): This resource includes a long, helpful list of recommendations along with supporting details to assess your needs, and implementation (*as desired*)  

#### Some scripts to (*help*) set up a clean Windows 10/11 endpoint:  
* [https://github.com/Hecsall/clean-windows](https://github.com/Hecsall/clean-windows)  
And edit these to meet your needs:  
* https://github.com/Digressive/Remove-MS-Store-Apps/blob/master/Remove-MS-Store-Apps.ps1  
* https://github.com/UNC0V3R3D/resources/blob/main/remove_bloatware_regkeys.ps1  
* https://github.com/UNC0V3R3D/resources/blob/main/privacy.ps1  



### List the local Windows users:  
    `Get-LocalUser`

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

-----

# Now some temporary notes on monitoring my UPS:  

## APC UPS Monitoring -- apcupsd  
Manual:  

* http://www.apcupsd.org/manual/manual.html  
* https://wiki.debian.org/apcupsd  
* "Managing APC Brand Uninterruptible Power Supplies With apcupsd." https://wiki.ubuntu.com/apcupsd  
* Linux Magazine article -- "Monitoring Your UPS With apcupsd." by Riccardo Facchetti, on December 1, 2000. https://www.linuxjournal.com/article/4347  
* https://monsterb.github.io/notes/notes004.txt  
* "Manage your APC battery backup system with this Linux command." Protect yourself from power incidents by running a simple utility: apcupsd. 17 Dec 2021, By David Both. https://opensource.com/article/21/12/linux-apcupsd  
* "Configuring UPS/apcupsd." Jul 18, 2016. https://rmoff.net/2016/07/18/configuring-ups/apcupsd/  
* An example of using Python to drive your use of ```apcaccess```: https://github.com/yufushiro/munin-apcupsd-load-watts/blob/main/apcupsd_load_watts  
* Useful, simplistic model for building an sqlite database for apcusd data: https://github.com/bzsparks/apcupsd-alert/blob/master/createDB.py  
  * Useful example of fetching apcusbd data using Python: https://github.com/flyte/apcaccess  
  * or: https://github.com/noriah/den/blob/main/bin/apcaccess.py  
  * or: https://github.com/dev-bash/APC-ups-Home-Assistant/blob/main/apc.py  
  * or: https://github.com/smarthomeNG/plugins/blob/master/apcups/__init__.py  
  ```python
        command = '/sbin/apcaccess status {0}:{1}'.format(self._host, self._port)   # the command goes here
        output = subprocess.check_output(command.split(), shell=False)
        # decode byte string to string
        output = output.decode()
        for line in output.split('\n'):
            (key,spl,val) = line.partition(': ')
            key = key.rstrip().lower()
            val = val.strip()
  ```
  * or: https://github.com/jncronin/pymonitor/blob/master/apcaccess_interface.py  
  * or: https://github.com/HireChrisJohnston/nagios-apcupsd/blob/master/check_apcaccess.py  
  * or: https://github.com/tumtumtum/pymonitor/blob/master/apcaccess_interface.py  
  * or: https://github.com/randomstring/MQTTsensord/blob/master/mqttsensord.py  
  * another example: https://github.com/flyte/simple-http-db/blob/develop/server.py  
  * NOTE: [Check for better examples](https://github.com/search?q=apcaccess+language%3APython&type=code&l=Python&p=3)  
  * or try the same using fastapi: https://github.com/ChristopherGS/ultimate-fastapi-tutorial  
    * If you can't decide, see a simple comparison: https://github.com/ChristopherGS/python-api-examples  
* Get wattage from UPS unit (APC UPS) with Linux shell: https://github.com/noriah/den/blob/main/bin/upsinfo  


```apcupsd``` is the background daemon, and also includes a command line utility, "apcupsd", that allows you to send some commands to the UPS.  
```apcaccess``` is an additional utility that comes bundled with apcupsd, and is used to display current status information about the UPS.  
```apctest``` is an additional utility that comes bundled with apcupsd, and is used to modify the on-board EEPROM settings for the UPS itself.  
The configuration file is ```/etc/apcupsd/apcupsd.conf```  
The following commands start and enable apcupsd so that it will restart after reboots.  

```terminal
# systemctl start apcupsd ; systemctl enable apcupsd
```

Another console-based client is powerflute that can be used to monitor the UPS status continuously.  

Try using ```lsusb```:  

```terminal
root@proxmox01:/proc/bus# lsusb
[...]
Bus 003 Device 007: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
[...]
```

It’s also found using ```udev``` (per the ```apcupsd``` documentation - *maybe I shouldn’t be quite so rude about it*):  

```terminal
root@proxmox01:/proc/bus# udevadm info --attribute-walk --name=/dev/usb/hiddev0
[...]
  looking at parent device '/devices/pci0000:00/0000:00:14.0/usb3/3-2':
    KERNELS=="3-2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ...
    ATTRS{ltm_capable}=="no"
    ATTRS{manufacturer}=="American Power Conversion"
    ATTRS{removable}=="removable"
    ATTRS{idProduct}=="0002"
    ATTRS{bDeviceClass}=="00"
    ATTRS{product}=="Back-UPS CS 650 FW:817.v9.I USB FW:v9"
```

it’s also there under usb-devices:  

```terminal
root@proxmox01:/proc/bus# usb-devices
[...]
T:  Bus=03 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=  7 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=051d ProdID=0002 Rev=00.06
S:  Manufacturer=American Power Conversion
S:  Product=Back-UPS CS 650 FW:817.v9.I USB FW:v9
S:  SerialNumber=4B1517P07342
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
[...]
```

Try to start the daemon  
```terminal
$ sudo service apcupsd start
* Starting UPS monitor (for Network UPS) apcupsd    [ OK ]
* Starting UPS monitor (for Server UPS) apcupsd     [ OK ]
...sudo systemctl restart apcupsd.service
```

Check daemon status  
```terminal
$ service apcupsd status
* UPS monitor (for Network UPS) is running
* UPS monitor (for Server UPS) is running
```
The following commands start and enable apcupsd so that it will restart after reboots.  
```terminal
systemctl start apcupsd ; systemctl enable apcupsd
```
### apctest  
```apctest``` is a program that allows you to talk directly to your UPS and run certain low-level tests, adjust various settings such as the battery installation date and alarm behavior, and perform a battery runtime calibration.  
```apcupsd``` must be run at startup time, when the operating system services are loaded: in fact, apcupsd is just another OS service.  

```apcupsd```'s main init script file is installed in:  

```terminal
/sbin/init.d/apcupsd
```

This script is responsible for starting up apcupsd during system startup and shutting down apcupsd during system shutdown. It is also symbolically linked to these paths:  

```terminal
/sbin/init.d/rc2.d/K20apcupsd
/sbin/init.d/rc2.d/S20apcupsd
/sbin/init.d/rc3.d/K20apcupsd
/sbin/init.d/rc3.d/S20apcupsd
```

They are present only on runlevel 2 and 3 because apcupsd is run only in multiuser runlevels; that means runlevel 2 or 3 on SuSE Linux OS.  

To be able to shutdown the computer properly on power failures, apcupsd relies on its own service script located in:  

```terminal
/etc/apcupsd/apccontrol
```

and on a patched halt script. When apcupsd detects a situation that needs an emergency shutdown, it first creates two files called /etc/nologin and /etc/apcupsd/powerfail.  

...
## apcupsd Configuration  

Before running apcupsd it is necessary to configure the dæmon to work as needed with the local hardware configuration and the desired behavior. In a standard installation, the configuration file is in:  

```terminal
 /etc/apcupsd/apcupsd.conf
```

This file is a plain ASCII file that contains all the configuration directives needed by apcupsd.  

The directives must be properly configured before apcupsd can operate correctly. With these directives you specify the kind of cable, the model of UPS connected to the computer, the device where the UPS is connected, how to operate on power failures, logging options and much more.  

### Stand-Alone Configuration  

A typical stand-alone configuration includes a computer and a UPS connected to its serial port.  

Listing 2 shows a configuration file for a stand-alone SmartUPS connected to the first serial port of the computer. On power failure, apcupsd will shut down the computer when the battery level falls below 5% of full charge or the UPS remaining run-time falls below three minutes, whichever happens first. apcupsd will send messages to user consoles every five minutes sending the first message one minute after the power failure occurs. apcupsd will not disallow user logins during a power failure. UPS events are logged in /etc/apcupsd/apcupsd.events. The UPS status can be read from our CGI interface or from /etc/apcupsd/apcupsd.status, which is updated every minute.  

If, for example, you want to write your own routine for the on-battery action, you can write your own shell script, as shown in Listing 5, called onbattery and put it in the /etc/apcupsd/ directory. Doing so will run the customized script before the default action. In case you don't want the default action to be taken, terminate your customized script with an exit code of 99. If you want to write customized scripts to replace the default behavior, you are encouraged to edit the apccontrol script and at least mimic its behavior in your own script. Please be aware that writing faulty scripts may cause your system to crash during power failures.  

### "apcassess status"  

To ease UPS monitoring, apcupsd offers a number of client facilities.  As mentioned above, ```apcaccess``` is the main client tool for monitoring UPS status.  Example ```apcaccess``` output is in Listing 6 below.  



#### Listing 2. Configuration File for a Stand-alone SmartUPS  
(*Example config files*:  
* https://github.com/rpochet/apcupsd/blob/main/apcupsd.conf  
* https://github.com/lucboudreau/apcupsd2mqtt/blob/main/etc/apcupsd/apcupsd.conf  
* https://github.com/HireChrisJohnston/nagios-apcupsd/blob/master/etc/apcupsd/apcupsd2.conf )  

```terminal
## apcupsd.conf v1.1 ##
#
# ========= General configuration parameters ============
#
# defines the type of cable that you have.
UPSCABLE smart
#
# defines the type of UPS you have.
UPSTYPE smartups
#
# name of your serial port
DEVICE /dev/ttyS0
#
# path for serial port lock file
LOCKFILE /var/lock
#
# ===== configuration parameters used
# during power failures =============
#
# If during a power failure, the remaining battery
# percentage (as reported by the UPS) is below or
# equal to BATTERYLEVEL,
# apcupsd will initiate a system shutdown.
BATTERYLEVEL 5
#
# If during a power failure, the remaining runtime
# in minutes (as calculated internally by the UPS)
# is below or equal to MINUTES,
# apcupsd, will initiate a system shutdown.
MINUTES 3
#
# If during a power failure, the UPS has run on
# batteries for TIMEOUT many seconds or longer,
# apcupsd will initiate a system shutdown.
# A value of 0 disables this timer.
TIMEOUT 0
#
# Time in seconds between annoying users to signoff
# prior to system shutdown. 0 disables.
ANNOY 300
#
# Initial delay after power failure before warning
# users to get off the system.
ANNOYDELAY 60
#
# The condition which determines when users are
# prevented from logging in during a power failure.
NOLOGON disable
#
#==== Configuration statements the network
# information server======================
#
# information server. If netstatus is on, a network
# information server process will be started for
# serving the STATUS and EVENT data over the network
# (used by CGI programs).
NETSERVER on
#
# port to use for sending STATUS and EVENTS data
# over the network. It is not used unless NETSERVER
# is on. If you change this port, you will need to
# change the corresponding value in the
# cgi directory and rebuild the cgi programs.
SERVERPORT 7000
#
# If you want the last few EVENTS to be available
# over the network by the network information server,
# you must define an EVENTSFILE.
# Only the last 50 or so events are kept.
EVENTSFILE /etc/apcupsd/apcupsd.events
#
# ===== Configuration statements to control
# apcupsd system logging ==============
#
# Time interval in seconds between writing the
# STATUS file; 0 disables
STATTIME 60
#
# Location of STATUS file (written to only if
# STATTIME is nonzero)
STATFILE /etc/apcupsd/apcupsd.status
#
# You probably do not want this on.
LOGSTATS off
#
# Time interval in seconds between writing the DATA
# records to the log file. 0 disables.
DATATIME 0
#
# ===== Configuration statements used if sharing ====
# a UPS and controlling it via the network
#
# normally stand-alone unless you share a UPS with
# multiple machines.
UPSCLASS standalone
#
# Unless you want to share the UPS
# (power multiple machines).
# this should be disable
UPSMODE disable
#
# NETACCESS <string> [ true | false ]
# Enable Network Access Support
NETACCESS true
```



#### Table 3. Arguments apccontrol Recognizes  

```terminal
Keyword—Default Action

powerout -- `wall' a message telling `There are power problems'.
onbattery -- `wall' a message telling `System is on battery'.
failing -- `wall' a message telling `Battery power is failing'.
timeout -- `wall' a message telling `Timeout on Battery reached'.
loadlimit -- `wall' a message telling `Battery load limit reached'.
runlimit -- `wall' a message telling `Battery runtime limit reached'.
doreboot -- Begins the `shutdown--r' sequence.
doshutdown -- Begins the `shutdown--h' sequence.
mainsback -- Attempt to cancel a running `shutdown' sequence.
annoyme -- `wall' a message telling `Power problems, logoff now'.
emergency -- Begins an emergency `shutdown' sequence.
changeme -- `wall' a message telling `Battery failed, change them now'.
remotedown -- Begins the `shutdown' sequence, called from remote.
restartme -- Attempt to restart the apcupsd.
```

#### Listing 5. /ect/apcupsd/onbattery  

```bash
#!/bin/sh
#
# This shell script if placed in /etc/apcupsd
# will be called by /etc/apcupsd/apccontrol when the UPS
# goes on batteries.  We send an e-mail message to root
# to notify him.
#
SYSADMIN=root
MAIL="bin/mail"
HOSTNAME=`hostname`
#
echo "HOSTNAME Power Failure" >/tmp/$$
echo " " >>/tmp/$$
/sbin/apcaccess status 2>>/tmp/$$
cat /tmp/$$ | $MAIL -s "HOSTNAME Power Failure !!!" $SYSADMIN
exit 0
```


#### Listing 6. Output of “apcassess status”  

```terminal
APC      : 001,048,1088
DATE     : Fri Dec 03 16:49:24 EST 1999
HOSTNAME : daughter
RELEASE  : 3.7.2
CABLE    : APC Cable 940-0024C
MODEL    : APC Smart-UPS 600
UPSMODE  : Stand-alone
UPSNAME  : SU600
LINEV    : 122.1 Volts
MAXLINEV : 123.3 Volts
MINLINEV : 122.1 Volts
LINEFREQ : 60.0 Hz
OUTPUTV  : 122.1 Volts
LOADPCT  :  32.7 Percent Load Capacity
BATTV    : 26.6 Volts
BCHARGE  : 095.0 Percent
MBATTCHG : 15 Percent
TIMELEFT :  19.0 Minutes
MINTIMEL : 3 Minutes
SENSE    : Medium
DWAKE    : 000 Seconds
DSHUTD   : 020 Seconds
LOTRANS  : 106.0 Volts
HITRANS  : 129.0 Volts
RETPCT   : 010.0 Percent
STATFLAG : 0x08 Status Flag
STATUS   : ONLINE
ITEMP    : 34.6 C Internal
ALARMDEL : Low Battery
LASTXFER : Unacceptable Utility Voltage Change
SELFTEST : NO
STESTI   : 336
DLOWBATT : 05 Minutes
DIPSW    : 0x00 Dip Switch
REG1     : N/A
REG2     : N/A
REG3     : 0x00 Register 3
MANDATE  : 03/30/95
SERIALNO : 13035861
BATTDATE : 05/05/98
NOMOUTV  : 115.0
NOMBATTV :  24.0
HUMIDITY : N/A
AMBTEMP  : N/A
EXTBATTS : N/A
BADBATTS : N/A
FIRMWARE : N/A
APCMODEL : 6TD
END APC  : Fri Dec 03 16:49:25 EST 1999
```
