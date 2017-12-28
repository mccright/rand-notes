
***Hardware: NESDR SMArt***  
Part of a new NooElec NESDR SMArt Bundle (Premium RTL-SDR NESDR SMArt plus 3 antenna)  
 
**Error Message Summary**  
From Fedora 27, Ubuntu 16.10, and Lubuntu 16.10 and on three different laptops, trying USB 1.1, 2.0, & 3.0 ports, I received the same series of usb device error messages:  
*  new full-speed USB device number <#> using uhci_hcd  
*  device descriptor read/64, error -71   
*  unable to enumerate USB device  
  
From Windows 10 Enterprise on an HP ZBook Workstation and Windows 10 Home on a 2015 Toshiba laptop with USB 3 and USB 2 ports, I received the same family of device error messages:  
*  Fail Unknown USB Device (Device Descriptor Request Failed)  
  
**Error Message Summary, Supporting Details**
From Fedora 27, Ubuntu 16.10, and Lubuntu 16.10 and on three different laptops, trying USB 1.1, 2.0, & 3.0 ports, I received the same series of usb device error messages:  

***From dmesg***  
[    1.664555] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3  
[    1.664660] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001  
[    1.664662] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1  
[    1.664664] usb usb3: Product: UHCI Host Controller  
[    1.664666] usb usb3: Manufacturer: Linux 4.9.0-kali4-686-pae uhci_hcd  
[    1.664668] usb usb3: SerialNumber: 0000:00:1d.0  
[    1.665024] hub 3-0:1.0: USB hub found  
...  
[    2.288075] usb 3-2: new full-speed USB device number 2 using uhci_hcd  
[    2.416164] usb 3-2: device descriptor read/64, error -71  
[    2.652159] usb 3-2: device descriptor read/64, error -71  
[    2.880218] usb 3-2: new full-speed USB device number 3 using uhci_hcd  
[    3.008081] usb 3-2: device descriptor read/64, error -71  
[    3.244217] usb 3-2: device descriptor read/64, error -71  
[    3.472062] usb 3-2: new full-speed USB device number 4 using uhci_hcd  
[    3.888041] usb 3-2: device not accepting address 4, error -71  
[    4.012257] usb 3-2: new full-speed USB device number 5 using uhci_hcd  
[    4.432082] usb 3-2: device not accepting address 5, error -71  
[    4.432214] usb usb3-port2: unable to enumerate USB device  
  
root@kali1520:~# echo -1 >/sys/module/usbcore/parameters/autosuspend  
root@kali1520:~# echo Y > /sys/module/usbcore/parameters/old_scheme_first  
  
Then tried it later in the next port:  
[ 1283.632194] usb 3-1: new full-speed USB device number 6 using uhci_hcd  
[ 1284.048199] usb 3-1: device not accepting address 6, error -71  
[ 1284.168253] usb 3-1: new full-speed USB device number 7 using uhci_hcd  
[ 1284.584109] usb 3-1: device not accepting address 7, error -71  
[ 1284.704258] usb 3-1: new full-speed USB device number 8 using uhci_hcd  
[ 1284.832262] usb 3-1: device descriptor read/64, error -71  
[ 1285.068116] usb 3-1: device descriptor read/64, error -71  
[ 1285.296156] usb 3-1: new full-speed USB device number 9 using uhci_hcd  
[ 1285.424154] usb 3-1: device descriptor read/64, error -71  
[ 1285.660163] usb 3-1: device descriptor read/64, error -71  
[ 1285.768137] usb usb3-port1: unable to enumerate USB device  
  

**HP ZBook 17, Windows 10 Enterprise: Fail Unknown USB Device (Device Descriptor Request Failed)**
Device USB\VID_0000&PID_0002\5&6a10740&0&6 was configured.

Driver Name: usb.inf
Class Guid: {36FC9E60-C465-11CF-8056-444553540000}
Driver Date: 06/21/2006
Driver Version: 10.0.14393.1794
Driver Provider: Microsoft
Driver Section: BADDEVICE.Dev.NT
Driver Rank: 0xFF0000
Matching Device Id: USB\DEVICE_DESCRIPTOR_FAILURE
Outranked Drivers: usb.inf:USB\DEVICE_DESCRIPTOR_FAILURE:00FF2000
Device Updated: false
Parent Device: USB\ROOT_HUB30\4&2f849cbc&0&0

Device USB\VID_0000&PID_0002\5&6a10740&0&6 had a problem starting.

Driver Name: usb.inf
Class Guid: {36FC9E60-C465-11CF-8056-444553540000}
Service: 
Lower Filters: 
Upper Filters: 
Problem: 0x2B
Problem Status: 0x0
  
  
***SDR Temp Junk Notes***


Hardware: NESDR SMArt  
* RTL2382U - The ADC and USB data pump. It is mated with one of the following three tuner chips.  
* E4000 - Tuner. 60MHz to 1700MHz  
Big List of SDR Applications: https://wiki.radioreference.com/index.php/SDR_Software_Applications and (dated) https://www.rtl-sdr.com/big-list-rtl-sdr-supported-software/, & http://www.chace-ortiz.org/umc/software.html  
Try SDRSharp, SDRConsole, CubicSDR, SDR#, SDR-Radio, HDSDR, Unitrunker, & For aircraft, try RTL1090 plus Virtual Radar Server.  
•	SDRSharp: http://www.airspy.com  
•	SDRConsole  
•	CubicSDR  
•	SDR#  
•	SDR-Radio   
•	HDSDR  
•	PDW (Paging decoder for monitoring POCSAG, FLEX, ACARS, MOBITEX & ERMES pager traffic): http://www.discriminator.nl/pdw/index-en.html and https://github.com/Discriminator/PDW  
•	Unitrunker: http://www.unitrunker.com/ (pager RF-to-text?).  Manuals at: http://utahradio.org/mediawiki/index.php/UniTrunker_Guide and http://www.unitrunker.com/windows.html and http://www.unitrunker.com/realtek.html  
Supported protocols (definitions at: http://wiki.radioreference.com/):  
o	APCO P25  
o	EDACS 4800  
o	EDACS 9600  
o	Motorola  
o	MPT1327  
•	SDRTrunk   
•	DMRDecode  
•	?? Digital Speech Decoder (software package)  

Think about directional antennas and band-specific antennas…  

Getting started on Linux: http://osmocom.org/projects/sdr/wiki/rtl-sdr  
GETTING THE RTL-SDR TO WORK IN WINDOWS 10: https://www.rtl-sdr.com/getting-the-rtl-sdr-to-work-on-windows-10/ 
And https://www.reddit.com/r/RTLSDR/comments/3fx5t4/windows_10_and_rtl2832r820t_quick_and_frustration/ 
USB Troubleshooting: http://www.unitrunker.com/zadig.html  
https://github.com/keenerd/rtl-sdr  
Check http://m3ghe.blogspot.com/p/adding-support-for-rtl-sdr-usb-dongles.html and http://m3ghe.blogspot.co.uk/p/installing-rtl-dongle-sdr-driver-using.html and https://answers.microsoft.com/en-us/windows/forum/windows_10-hardware/realtek-rtl2832u-tv-usb-dongle-not-working-with/d464f6e4-426a-4cde-bbee-0d270659af30?auth=1 for driver help.  
And Why isn't Windows finding my device? (Applies to Windows 10 also) http://windows.microsoft.com/en-US/windows-8/why-isnt-windows-finding-device .  

TRY: Search Windows settings for "Device Installation Settings" and turn Win 10 device driver auto updates off.  Turning it off stops Windows continually overwriting correct working drivers with wrong not working drivers.  

If the Windows update has failed to register and download the requisite drivers for the device, you can also use the vendor id of the device and look for it in the PCI Vendor and Device Lists.  FAQ: http://www.pcidatabase.com/  

Plug in the NESDR Smart and Windows 10 presents the following:  
 
Quick Start Guide: https://www.rtl-sdr.com/rtl-sdr-quick-start-guide/ 
 https://www.rtl-sdr.com/tag/zadig/ 
and https://airspy.com/quickstart/  
* SDRSharp: https://airspy.com/download/  
* CUBIC SDR: https://github.com/cjcliffe/CubicSDR/ 

Installing the NESDR Smart: http://www.nooelec.com/store/qs/  
Download and install ZADIAG  
Driver Installation Procedure:  
1.    Plug your NESDR into an available USB port
2.    Open the 'NESDR Driver Installer', Zadig  
3.    Select 'List All Devices' from the 'Options' menu in Zadig  
4.    From the main dropdown, select the NESDR   
5.    Confirm the selected device has a USB ID of '0BDA 2838'  
6.    Press the big button to install drivers--button will either say 'Install Driver' or 'Replace Driver', depending on your Windows environment and settings. Either is fine  
VID: 0x0bda, PID: 0x2838, Tuner: E4000 (60MHz to 1700MHz), Device Name: ezcap USB 2.0 DVB-T/DAB/FM dongle (http://rtlsdr.org/hardware-usb)  

The Chips  
RTL2382U - The ADC and USB data pump. It is mated with one of the following three tuner chips.   
Elonics 4000 - Tuner. 60MHz to 1700MHz;  
FC0012 - Tuner 50MHz to 1000MHz ; Fitipower - no public information available.  
FC0013 - Tuner 50MHz to 1700MHz ; Fitipower - no public information available.  
R820T - Tuner 24MHz to 1850MHz ; Now the E4000 has gone this is the tuner to get as it's comparable in performance. It also seems to be cheaper overall.  

The RTL2832U  
The RTL2832U outputs 8-bit I/Q-samples, and the highest theoretically possible sample-rate is 3.2 MS/s, however, the highest sample-rate without lost samples that has been tested so far is 2.56 MS/s. The frequency range is highly dependent of the used tuner, dongles that use the Elonics E4000 offer the widest possible range.  RTL2382U driver source code: http://cgit.osmocom.org/rtl-sdr/tree/src.  Device driver header definitions, see rtl-sdr in: http://cgit.osmocom.org/rtl-sdr/tree/include/.   

The E4000  
“The E4000 is a highly integrated multi‐band RF tuner IC implemented in CMOS, ideal for digital TV and radio broadcast receiver solutions. The digitally programmable multi‐band tuner architecture allows the user to re‐configure the RF front end for different broadcast standards.”  
Data sheet: http://www.superkuh.com/gnuradio/Elonics-E4000-Low-Power-CMOS-Multi-Band-Tunner-Datasheet.pdf.  Elonics E4000 tuner driver source: http://cgit.osmocom.org/rtl-sdr/tree/src/tuner_e4k.c.  Device driver header definitions: http://cgit.osmocom.org/rtl-sdr/tree/include/tuner_e4k.h  
•	DVB‐T (174‐240MHz, 470‐858MHz)  
•	CMMB Terrestrial (470‐858MHz)  
•	D‐TMB (174‐240MHz, 1452‐1492MHz)  
•	ISDB‐T (470 – 862MHz)  
•	DVB‐H (470 – 858MHz, 1672‐1678MHz)  
•	T‐DMB (174 – 240MHz, 1452 – 1492MHz)  
•	DAB/DAB+ (174 – 240MHz, 1452 – 1492MHz)  
•	GPS L1 band (1575MHz) – (with additional LNA)  
•	FM radio (64 – 108MHz)  


Ultimately, the device may show up under different names -- as R820T Generic RTL2832U OEM (0) in SDRSharp, RTL2838UHIDI in HDSDR and EZCAP USB 2.0 RTL2838UHIDIR R820T in SDR Console.  
Active SDR Blog: http://www.superkuh.com/rtlsdr.html (RTL-SDR and GNU Radio)  
rtlsdr.org wiki: http://rtlsdr.org/   
osmocom.org git repositories: http://cgit.osmocom.org/.   
Welle.io DAB/DAB+ Receiver  
ModeSDeco2 ADS-B/Mode-S Decoder from Sergey Serov  
ACARS Decoder from Thierry Leconte  
Linrad from Leif Asbrink SM5BSZ  
Simon Brown’s SDR-Console  
HDSDR  
GQRX  
Unitrunker  
ExtIO Plugin by Andrea Montefusco IW0HDV  
GNU Radio Live DVD (AirSpy support based on Ubuntu Linux 14.04.4 LTS, 64-bit edition)  
SDRdaemon Utility to send I/Q samples read from a SDR device over the network via UDP  
GNU Radio Win64 binaries with airspy support see also build scripts on github  
SDR-J DAB, WFM and SDR programs with airspy support  
URH Universal Radio Hacker (The Ultimate Radio Hacker Tool with native AirSpy support since 21 April 2017)  
https://forums.radioreference.com/  
 
Get SDRSharp from AirSpy Downloads: https://airspy.com/download/  
See the section: “Windows SDR Software Package”  
 This repository contains the history of the pci.ids file, which is automatically generated from the PCI ID Database at http://pci-ids.ucw.cz/: https://github.com/pciutils/pciids   
https://answers.microsoft.com/en-us/windows/forum/windows_10-hardware/realtek-rtl2832u-tv-usb-dongle-not-working-with/d464f6e4-426a-4cde-bbee-0d270659af30?auth=1  

***SDR on Linux***  
Get started using a NooElec NESDR SMArt on a computer running Ubuntu 17.04.  
  
The first thing to do after you have your NESDR SMArt plugged into your Ubuntu computer is to run the command lsusb.     This will list all of the USB devices attached to the computer.  
If things are working as they should be, you will see the NESDR SMArt listed as:   
Realtek Semiconductor Corp. RTL2838 DVB-T.   
  
The DVB-T is the telling part. It means that the operating system has recognized the device and loaded, what it believes to be, the correct driver, since the default use of the device is to receive television broadcasts.  
   
Confirm this using the command:   
  
lsmod | grep dvb  
  
... which lists the loaded modules (drivers) and filters them to just show the ones that have the letters dvb in them.    
  
What we need to do now is remove those modules (drivers) and load the ones dedicated to using the device as an SDR.
We start by “blacklisting” the default drivers. This is done by editing the file  
 
/etc/modprobe.d/blacklist-dvb.conf  
  
Add the following to the file:   
blacklist dvb_usb_rtl28xxu  
, save, and close it  
  
rtl_fm -f 95.3e6 -M wbfm -s 200000 -r 48000 – | aplay -r 48k -f S16_LE  
  
To install the current Osmocom library for rtl-sdr under Linux one can use the following set of commands:  
  
   rm -r /usr/src/rtl-sdr*  
   cd /usr/src  
   git clone git://git.osmocom.org/rtl-sdr.git  
   mkdir build  
   cd build  
   cmake ../rtl-sdr  
   make  
   make install  
  
Two routines need to be changed to get the results demonstrated on this page: librtlsdr.c and tuner_e4k.c. October 18 2012 they differ from the original library as can be seen in this diff file: linrad-oct18.diff (10267 bytes) The diff might be useful to get the Linrad modifications into newer versions of the library. The source code of the modified library as of Oct 18 2012 is contained here rtl-sdr-linrad1.tbz (875606 bytes)  
  
  
rtl_test  
rtl_sdr  
rtl_tcp  
  
Example: to start a tcp erver with default parameters of tuning to 88.5Mhz and sample rate of 2.4Mhz
https://inst.eecs.berkeley.edu/~ee123/fa12/rtl_sdr.html  
  
>> rtl_tcp -s 2400000 -f 88500000  
Found 1 device(s).  
Found Elonics E4000 tuner  
Using ezcap USB 2.0 DVB-T/DAB/FM dongle  
Tuned to 88500000 Hz.  
listening...   
Use the device argument 'rtl_tcp=127.0.0.1:1234' in OsmoSDR (gr-osmosdr) source to receive samples in GRC and control rtl_tcp parameters (frequency, gain, ...).  
https://inst.eecs.berkeley.edu/~ee123/fa12/rtl_sdr.html  

Using rtl_sdr to capture to a file  
Example: to tune to 88.5Mhz and set the sample rate to 2.4Mhz use:  
  
>> rtl_sdr  -s 2400000 -f 88500000  capture.bin  
Use crtl-c to break the capture. Warning… the file will grow very quickly.  
  
Because of the automatic gain, in many cases the first couple of seconds of capture will not be useful. You should therefore discard them. An alternative is to use manual gain, but you have to be careful not to overrange when the signal is strong. The Supported gain values (18): -1.0 1.5 4.0 6.5 9.0 11.5 14.0 16.5 19.0 21.5 24.0 29.0 34.0 42.0 43.0 45.0 47.0 49.0.  
  
Example: to tune to 88.5Mhz and set the sample rate to 2.4Mhz and maximum gain use:  
  
>> rtl_sdr -s 2400000 -f 88500000 -g 49.0  capture.bin  
https://inst.eecs.berkeley.edu/~ee123/fa12/rtl_sdr.html  


gqrx  /bin/gqrx  

quisk /bin/quisk  

gnu-radio  

gr-rds GNU Radio FM RDS Receiver  

grig  A Ham Radio Control GUI  

idp  IBP beacons http://www.ncdxf.org/beacons.html  

tlp-rdw Radio Device Wizard for TLP  

tucnak2  VHF/UHF/SHF log for ham radio contests.  

unixcw  Set of utilities for Morse Code  

urh -- The Universal Radio Hacker is a software for investigating unknown wireless protocols. https://github.com/jopohl/urh  

gqrx -- Gqrx is a software defined radio receiver powered by the GNU Radio SDR framework and the Qt graphical toolkit.    

  
**Error Message Summary**  
From Fedora 27, Ubuntu 16.10, and Lubuntu 16.10 and on three different laptops, trying USB 1.1, 2.0, & 3.0 ports, I received the same series of usb device error messages:  
*  new full-speed USB device number <#> using uhci_hcd  
*  device descriptor read/64, error -71   
*  unable to enumerate USB device  
  
From Windows 10 Enterprise on an HP ZBook Workstation and Windows 10 Home on a 2015 Toshiba laptop with USB 3 and USB 2 ports, I received the same family of device error messages:  
*  Fail Unknown USB Device (Device Descriptor Request Failed)  
  
**Error Message Summary, Supporting Details**
From Fedora 27, Ubuntu 16.10, and Lubuntu 16.10 and on three different laptops, trying USB 1.1, 2.0, & 3.0 ports, I received the same series of usb device error messages:  

***From dmesg***  
[    1.664555] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3  
[    1.664660] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001  
[    1.664662] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1  
[    1.664664] usb usb3: Product: UHCI Host Controller  
[    1.664666] usb usb3: Manufacturer: Linux 4.9.0-kali4-686-pae uhci_hcd  
[    1.664668] usb usb3: SerialNumber: 0000:00:1d.0  
[    1.665024] hub 3-0:1.0: USB hub found  
...  
[    2.288075] usb 3-2: new full-speed USB device number 2 using uhci_hcd  
[    2.416164] usb 3-2: device descriptor read/64, error -71  
[    2.652159] usb 3-2: device descriptor read/64, error -71  
[    2.880218] usb 3-2: new full-speed USB device number 3 using uhci_hcd  
[    3.008081] usb 3-2: device descriptor read/64, error -71  
[    3.244217] usb 3-2: device descriptor read/64, error -71  
[    3.472062] usb 3-2: new full-speed USB device number 4 using uhci_hcd  
[    3.888041] usb 3-2: device not accepting address 4, error -71  
[    4.012257] usb 3-2: new full-speed USB device number 5 using uhci_hcd  
[    4.432082] usb 3-2: device not accepting address 5, error -71  
[    4.432214] usb usb3-port2: unable to enumerate USB device  
  
root@kali1520:~# echo -1 >/sys/module/usbcore/parameters/autosuspend  
root@kali1520:~# echo Y > /sys/module/usbcore/parameters/old_scheme_first  
  
Then tried it later in the next port:  
[ 1283.632194] usb 3-1: new full-speed USB device number 6 using uhci_hcd  
[ 1284.048199] usb 3-1: device not accepting address 6, error -71  
[ 1284.168253] usb 3-1: new full-speed USB device number 7 using uhci_hcd  
[ 1284.584109] usb 3-1: device not accepting address 7, error -71  
[ 1284.704258] usb 3-1: new full-speed USB device number 8 using uhci_hcd  
[ 1284.832262] usb 3-1: device descriptor read/64, error -71  
[ 1285.068116] usb 3-1: device descriptor read/64, error -71  
[ 1285.296156] usb 3-1: new full-speed USB device number 9 using uhci_hcd  
[ 1285.424154] usb 3-1: device descriptor read/64, error -71  
[ 1285.660163] usb 3-1: device descriptor read/64, error -71  
[ 1285.768137] usb usb3-port1: unable to enumerate USB device  
  

**HP ZBook 17, Windows 10 Enterprise: Fail Unknown USB Device (Device Descriptor Request Failed)**
Device USB\VID_0000&PID_0002\5&6a10740&0&6 was configured.

Driver Name: usb.inf
Class Guid: {36FC9E60-C465-11CF-8056-444553540000}
Driver Date: 06/21/2006
Driver Version: 10.0.14393.1794
Driver Provider: Microsoft
Driver Section: BADDEVICE.Dev.NT
Driver Rank: 0xFF0000
Matching Device Id: USB\DEVICE_DESCRIPTOR_FAILURE
Outranked Drivers: usb.inf:USB\DEVICE_DESCRIPTOR_FAILURE:00FF2000
Device Updated: false
Parent Device: USB\ROOT_HUB30\4&2f849cbc&0&0

Device USB\VID_0000&PID_0002\5&6a10740&0&6 had a problem starting.

Driver Name: usb.inf
Class Guid: {36FC9E60-C465-11CF-8056-444553540000}
Service: 
Lower Filters: 
Upper Filters: 
Problem: 0x2B
Problem Status: 0x0
  
  

