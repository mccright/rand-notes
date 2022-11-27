## Some Endpoint Admin Notes  

### Developers who want to expose their applications on their endpoint to the Internet
Consider **[ngrok](https://ngrok.com)**: ngrok is a globally distributed reverse proxy fronting your web services running on a given endpoint, or in any cloud or private network.  *Paid [ngrok](https://ngrok.com/pricing)* has additional features that support its promotion as "the programmable network edge that adds connectivity, security, and observability to your apps with no code changes."  Pay attention to the details of every request.  The free version may not be suitable for your business, your local environment, or your regulators/investors/customers.  

  
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

If you use Solid State Drives (SSDs) (standard in modern computers), USB *thumb* drives, or SD cards/flash memory cards do not use the approach described above. Secure deletion on SSD storage media is a challenge because they use *wear leveling*, a technology that attempts to spread data evenly across all of the media so that any one part of that storage will not be overwritten too many times -- so that the storage device will last longer.  Wear leveling interferes with secure erase programs, which deliberately try to overwrite sensitive files with junk data in order to permanently erase them. As a result, it is better to use full-disk encryption. Encryption avoids the difficulty of secure erasing by making any file on the drive difficult to recover without the required secret.

For more on this topic and about digital security more broadly, you might review: [https://icorn.org/digital-security](https://icorn.org/digital-security)  


### What Application is Using Given Ports  
If an application barks about not being able to use port *NN* (for example port 80 or 443), use the following to identify if the port is already *owned* by another application.
```terminal
sudo ss -tlpn | grep -E ":(80|443)"
```
[Based on a blog ](https://francoconidi.it/solved-certbot-error-could-not-bind-to-ipv4/)

### Some Simple Linux Troubleshooting Reminders  
I have been adding some simple Linux troubleshooting reminders to a different file in this repo.  See:  [https://github.com/mccright/rand-notes/blob/master/Simple-Linux-Troubleshooting.md](https://github.com/mccright/rand-notes/blob/master/Simple-Linux-Troubleshooting.md)  


### Some Flexible Linux Live Distributions  
* **Fedora Live**: Fedora Xfce Desktop is implemented to be fast and lightweight.  It is shipped as a live operating system.  It includes everything you need to try out Fedora's Xfce Desktop.  You don't have to erase anything on your current system to try it out, and it won't put your existing files at risk.  You can have the boot copy all files to RAM first so that it runs very fast using the ```rd.live.ram=1``` boot parameter (*press the TAB key at the grub boot menu*).  If you like it after a test drive, you can install it to a local hard drive from the Live Media desktop. [https://spins.fedoraproject.org/xfce/](https://spins.fedoraproject.org/xfce/)  

* **Lubuntu**:  Lubuntu is a fast and lightweight Ubuntu based operating system using the minimal desktop LXQT and a selection of light applications. Lubuntu has very low hardware requirements.  That said, it makes a lean platform on which to build a fast development endpoint.  [https://lubuntu.me/](https://lubuntu.me/)  

* **SysLinuxOS**: SysLinuxOS is a specialized Linux operating system for those in infrastructure roles and is currently based on Debian 11 bullseye and a modern kernel (*kernel 5.16-amd64 on 2022-09-03*).  It comes with a large, broad spectrum of applications and utilities installed that would support many categories of infrastructure, maintenance, and collaboration work.  There are two versions, one using the Mate desktop and the other using Gnome.  [https://syslinuxos.com](https://syslinuxos.com)  


### When Your AppImage-Delivered Application Does Not Work
Some applications are delivered via AppImage.  This can be a benefit, as you can be more confident that all the application dependencies are present and correct.  Unfortunately, just downloading the AppImage file may not be all that you need to do...  
In my experience, it can save you some time to verify that the <appName>.AppImage file is executable.  
```ls -al <appName>.AppImage```  
If it is not, set it so:  
```chmod +x <appName>.AppImage```  


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

### Some Windows Endpoint Notes  
* Some scripts to (*help*) set up a clean Windows 10 endpoint: [https://github.com/Hecsall/clean-windows](https://github.com/Hecsall/clean-windows)  

### Some Mobile Device Endpoint Notes  
* When you have a business or social visitor who needs Internet access via your WiFi...  This situation can appear as part of a large number of use cases.  Even when you have a dedicated *visitor* SSID set up, getting your visitor's phone or tablet configured requires sharing one or more secrets -- which is not ideal.  Most of us don't have easy-to-use [one-time-password](https://en.wikipedia.org/wiki/One-time_password) systems available for these situations, so sharing secrets can involve some material risks.  The simple act of having *eyes-friendly* passwords laying around, or voicing WiFi connection secrets to those who need them, increases the likelihood of *leakage.*  One simple way to reduce (*not to eliminate*) some of those risks is to have the mobile endpoint configuration details coded into a QR code.  They are not very *eyes-friendly,* but still require careful handling throughout their lifecycle.  
The Linux utility "qrencode" is one way to generate QR code for your mobile endpoint WiFi configuration details.  For example:
```terminal
user@host:~/QR$qrencode -s 9 -l H -o "<QRcodeFileName>.png" "WIFI:S:<theTargetSSID>;T:WPA2;P:<thePassword>;;"
```
Replace `<theTargetSSID>` with your visitor SSID and `<thePassword>` with your visitor WiFi password, and name the file something that does not give away the secrets.  When the mobile endpoint WiFi configuration details are needed, bring up the `<QRcodeFileName>.png` file in your browser and have the visitor scan the QR code on your screen with their mobile device.  *Use this idea only in the "access to visitor/guest WiFi networks.  This approach is NOT risk-appropriate for providing access to high security networks.*  

