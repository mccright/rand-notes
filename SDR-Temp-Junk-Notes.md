
***Hardware: NESDR SMArt***  
Part of a new NooElec NESDR SMArt Bundle (Premium RTL-SDR w/ Aluminum Enclosure, 0.5PPM TCXO, SMA Input & 3 Antennas. RTL2832U & R820T2-Based, plus, re-designed antenna base, and 3 antenna masts).  
http://www.nooelec.com/store/sdr/sdr-receivers/nesdr/nesdr-smart.html  
   
I plugged in the device (Fedore 27) and it worked perfectly.  
  
SpyServer from: https://airspy.com/download/  
Then set up the Pi as an SDR streaming server: https://eliaselectronics.com/rtlsdr/2014/11/19/raspi-rtl-streaming-server.html  
  
**Planning for GPS reception**  
Antenna Notes:  
Here is a relevant blog: (https://eliaselectronics.com/rtlsdr/2015/04/26/crude-skewed-wheel-antenna-gps.html)[https://eliaselectronics.com/rtlsdr/2015/04/26/crude-skewed-wheel-antenna-gps.html]  
and for more detail, see Skew-Planar Wheel Antenna (http://www.slvrc.org/902band/skewplanar.htm)[http://www.slvrc.org/902band/skewplanar.htm]  
N.B. Testing and analysis has shown that the elements should be slightly more than one wavelength long ( WL x 1.0443 ).
The factors to use are:  31329 / F (centimeters) or 12334 / F (inches) long.  




***Originally had a DoA Device (below)***  
**Error Message Summary**  
From Fedora 27, Ubuntu 17.04, and Lubuntu 16.10 and on three different laptops, trying USB 1.1, 2.0, & 3.0 ports, I received the same series of usb device error messages:  
*  new full-speed USB device number <#> using uhci_hcd  
*  device descriptor read/64, error -71   
*  unable to enumerate USB device  
  
From Windows 10 Enterprise on an HP ZBook Workstation and Windows 10 Home on a 2015 Toshiba laptop with USB 3 and USB 2 ports, I received the same family of device error messages:  
*  Fail Unknown USB Device (Device Descriptor Request Failed)  
  
**Error Message Summary, Supporting Details**
From Fedora 27, Ubuntu 17.04, and Lubuntu 16.10 and on three different laptops, trying USB 1.1, 2.0, & 3.0 ports, I received the same series of usb device error messages:  

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
  
root@hostname:~ echo -1 >/sys/module/usbcore/parameters/autosuspend  
root@hostname:~ echo Y > /sys/module/usbcore/parameters/old_scheme_first  
  
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
    
Driver 'ohci-...' means it is USB 1.1 interface.  
Driver 'uhci-...' also means USB 1.1.  
USB 2.0 uses 'ehci-...' driver.   
USB 3.0 must use 'xhci_...' driver?  
I've read that some have addressed problems having this symptom by switching the IOMMU option to "enabled" (or the  "iommu=soft" option) and boot option to "legacy only."  Do I need to do that for this SDR hardware?  
  
root@hostname:~ grep -i usb /boot/config-$(uname -r) | grep -i rtl  
CONFIG_BT_HCIBTUSB_RTL=y  
CONFIG_USB_RTL8150=m  
CONFIG_USB_RTL8152=m  
CONFIG_RTLWIFI_USB=m  
CONFIG_DVB_USB_RTL28XXU=m  
root@hostname:~  grep -i sdr /boot/config-$(uname -r) | more  
CONFIG_MEDIA_SDR_SUPPORT=y  
CONFIG_DVB_RTL2832_SDR=m  
CONFIG_MMC_SDRICOH_CS=m  
root@hostname:~ grep -i dvb /boot/config-$(uname -r) | wc -l  
191  
root@hostname:~    
  
When the setting is y, it is built in the kernel, when set to m, it is a loadable module.  
  
  
**Toshiba Satellite S55-B5280 using Lubuntu 16.10**  
*Before plugging in the NESDR SMArt:*  
root@lubuntu:~ lsusb  
Bus 001 Device 002: ID 8087:8000 Intel Corp.   
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub  
Bus 002 Device 004: ID 04f2:b446 Chicony Electronics Co., Ltd   
Bus 002 Device 003: ID 8087:07dc Intel Corp.  
Bus 002 Device 002: ID 05dc:a710 Lexar Media, Inc.  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
root@lubuntu:~ lsusb  
*After plugging in the NESDR SMArt (it is still plugged into the USB slot):*  
root@lubuntu:~ lsusb  
Bus 001 Device 002: ID 8087:8000 Intel Corp.  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub  
Bus 002 Device 004: ID 04f2:b446 Chicony Electronics Co., Ltd   
Bus 002 Device 003: ID 8087:07dc Intel Corp.   
Bus 002 Device 002: ID 05dc:a710 Lexar Media, Inc.   
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
root@lubuntu:~  
  
*dmesg after pluging in the NESDR SMArt:*   
root@lubuntu:~ dmesg | tail -n 15  
[  113.598347] usb 2-3: new full-speed USB device number 5 using xhci_hcd  
[  113.710456] usb 2-3: device descriptor read/64, error -71  
[  113.926546] usb 2-3: device descriptor read/64, error -71  
[  114.142618] usb 2-3: new full-speed USB device number 6 using xhci_hcd  
[  114.254705] usb 2-3: device descriptor read/64, error -71  
[  114.470786] usb 2-3: device descriptor read/64, error -71  
[  114.686889] usb 2-3: new full-speed USB device number 7 using xhci_hcd  
[  114.687061] usb 2-3: Device not responding to setup address.  
[  114.891211] usb 2-3: Device not responding to setup address.  
[  115.095117] usb 2-3: device not accepting address 7, error -71  
[  115.207223] usb 2-3: new full-speed USB device number 8 using xhci_hcd  
[  115.207439] usb 2-3: Device not responding to setup address.  
[  115.411474] usb 2-3: Device not responding to setup address.  
[  115.615380] usb 2-3: device not accepting address 8, error -71  
[  115.615451] usb usb2-port3: unable to enumerate USB device  
root@lubuntu:~  
  
  
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
* R820T - Tuner 24MHz to 1850MHz.    

  
**Error Message Summary**  
From Fedora 27, Ubuntu 17.04, and Lubuntu 16.10 and on three different laptops, trying USB 1.1, 2.0, & 3.0 ports, I received the same series of usb device error messages:  
*  new full-speed USB device number <#> using uhci_hcd  
*  device descriptor read/64, error -71   
*  unable to enumerate USB device  
  
From Windows 10 Enterprise on an HP ZBook Workstation and Windows 10 Home on a 2015 Toshiba laptop with USB 3 and USB 2 ports, I received the same family of device error messages:  
*  Fail Unknown USB Device (Device Descriptor Request Failed)  
  
**Error Message Summary, Supporting Details**
From Fedora 27, Ubuntu 17.04, and Lubuntu 16.10 and on three different laptops, trying USB 1.1, 2.0, & 3.0 ports, I received the same series of usb device error messages:  

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
  
root@hostname:~ echo -1 >/sys/module/usbcore/parameters/autosuspend  
root@hostname:~ echo Y > /sys/module/usbcore/parameters/old_scheme_first  
    
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
  
  

