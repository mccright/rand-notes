### Libraries to Watch  
* CyberRadio - An SDR Based FM/AM Radio for your PC: https://github.com/luigifreitas/CyberRadio  
* dump1090: dump1090-fa is a ADS-B, Mode S, and Mode 3A/3C demodulator and decoder that will receive and decode aircraft transponder messages received via a directly connected software defined radio, or from data provided over a network connection. https://github.com/flightaware/dump1090  
* TheAirTraffic feed client - (https://theairtraffic.com/feed/ and https://grndcntrl.net/links/) - https://github.com/Jxck-S/tat-feeder and https://github.com/Jxck-S?tab=repositories  
* Useful references [https://github.com/kaltic/SDR-Notes](https://github.com/kaltic/SDR-Notes)  

### Hardware: NESDR SMArt  
Part of a new NooElec NESDR SMArt Bundle (Premium RTL-SDR w/ Aluminum Enclosure, 0.5PPM TCXO, SMA Input & 3 Antennas. RTL2832U & R820T2-Based, plus, re-designed antenna base, and 3 antenna masts).  
http://www.nooelec.com/store/sdr/sdr-receivers/nesdr/nesdr-smart.html  
   
I plugged in the device (Fedore 27) and it worked perfectly.  
  
SpyServer from: https://airspy.com/download/  
Then set up the Pi as an SDR streaming server: https://eliaselectronics.com/rtlsdr/2014/11/19/raspi-rtl-streaming-server.html  
  
### Planning for GPS reception  
The **U.S. Global Positioning System** (GPS) technology operates in [the following frequency bands](https://en.wikipedia.org/wiki/GPS_signals):  
* GPS L1 Band: 1575.42 MHz with a bandwidth of 15.345 MHz  
* GPS L2 Band: 1227.6 MHz with a bandwidth of 11 MHz  
* GPS L5 Band: 1176.45 MHz with a bandwidth of 12.5 MHz  

**Europe's Global Navigation Satellite System (GNSS) Galileo** technology operates in the following frequency bands:  
* Galileo E1 Band: 1559 MHz to 1591 MHz with a center frequency of 1575.42 MHz  
* Galileo E6 Band: 1260 MHz to 1300 MHz with a center frequency of 1278.75 MHz  
* Galileo E5 Band: 1164 MHz to 1214 MHz with a center frequency of 1189 MHz  
   * Galileo E5a Band: 1164 MHz to 1189 MHz with a center frequency of 1176.5 MHz  
   * Galileo E5b Band: 1189 MHz to 1214 MHz with a center frequency of 1201.5 MHz  

**[China's Global Navigation Satellite System](https://en.wikipedia.org/wiki/BeiDou_Navigation_Satellite_System) (GNSS) Beidou BDS-3** technology operates three open service signals in the following frequency bands:  
   * B1C:    1575.42 MHz with a bandwidth of 32.736 MHz  
   * B2a:    1176.45 MHz with  a bandwidth of 20.46 MHz  
   * B3I:     1268.52 MHz with a bandwidth of 20.46 MHz  

**[Japan's Quasi-Zenith Satellite System (QZSS)](https://en.wikipedia.org/wiki/Quasi-Zenith_Satellite_System)**:  

**[Indian Regional Navigation Satellite System](https://en.wikipedia.org/wiki/Indian_Regional_Navigation_Satellite_System)**:  

**[Russian Global Navigation Satellite System (GLONASS)](https://en.wikipedia.org/wiki/GLONASS)**:  
GLONASS open standard-precision signal [frequency-division multiple access (FDMA)]:  
* GLONASS L1OF Band: 15-channels spanning either side from 1602.0 MHz, the center frequency being 1602 MHz + n × 0.5625 MHz, where n is a satellite's frequency channel number.  
* GLONASS L2OF Band: 15-channels spanning either side from 1246.0 MHz, the center frequency being 1246 MHz + n × 0.4375 MHz, where n is a satellite's frequency channel number.  
GLONASS obfuscated high-precision signal:  
* GLONASS L1SF/L2SF.  GLONASS restricted-use codes are broadcast in the clear using only security through obscurity. The details of the high-precision signal have not been disclosed.  
GLONASS open standard-precision signal (*Newer* -- in testing or design phases [code-division multiple access (CDMA)]):  
* GLONASS L1OC/L1SC Band: 15-channels spanning either side from 1600.995 MHz, the center frequency being 1600.995 MHz + n × 0.5625 MHz, where n is a satellite's frequency channel number.  
* GLONASS L2OC/L2SC Band: 15-channels spanning either side from 1246.0 MHz, the center frequency being 1246 MHz + n × 0.4375 MHz, where n is a satellite's frequency channel number.  
* GLONASS L3OC/L3SVI Band: 15-channels spanning either side from 1202.025 MHz, the center frequency being 1202.025 MHz + n × 0.4375 MHz, where n is a satellite's frequency channel number.  
GLONASS obfuscated high-precision signal:  
* GLONASS obfuscated high-precision signal L1SC/L2SC/L3SVI.  GLONASS restricted-use codes are broadcast in the clear using only security through obscurity. The details of the high-precision signal have not been disclosed.

### Antenna Notes:  
See this general reference "Antennas, Aerials, & Propagation" [http://www.radio-electronics.com/info/antennas/](http://www.radio-electronics.com/info/antennas/)    
Calculating WaveLengths: Calculate Wavelength: [https://www.easycalculation.com/physics/electromagnetism/antenna-wavelength.php](https://www.easycalculation.com/physics/electromagnetism/antenna-wavelength.php), or [http://wxtofly.net/wavecalc.htm](http://wxtofly.net/wavecalc.htm)  
Calculating Antenna Lengths:  Monopole antennas: [https://itstillworks.com/calculate-monopole-length-8644948.html](https://itstillworks.com/calculate-monopole-length-8644948.html) and Dipole antennas: [http://www.radio-electronics.com/info/antennas/dipole/dipole.php](http://www.radio-electronics.com/info/antennas/dipole/dipole.php), or [http://www.westmountainradio.com/antenna_calculator.php?frequency=433](http://www.westmountainradio.com/antenna_calculator.php?frequency=433)  
Here is a relevant blog: [https://eliaselectronics.com/rtlsdr/2015/04/26/crude-skewed-wheel-antenna-gps.html](https://eliaselectronics.com/rtlsdr/2015/04/26/crude-skewed-wheel-antenna-gps.html)  
and for more detail, see Skew-Planar Wheel Antenna [http://www.slvrc.org/902band/skewplanar.htm](http://www.slvrc.org/902band/skewplanar.htm)  
N.B. Testing and analysis has shown that the elements should be slightly more than one wavelength long ( WL x 1.0443 ).
The factors to use are:  31329 / F (centimeters) or 12334 / F (inches) long.  

### Assembling an ADS-B Receiver  
First, where am I?  https://www.freemaptools.com/elevation-finder.htm  
**Virtually-Random Notes (*for now*)**  
TheAirTraffic feed client
    These scripts aid in setting up your current ADS-B receiver to feed TheAirTraffic.
    They will not disrupt any existing feed clients already present.
	Feed TheAirTraffic.com using an existing receiver running readsb / dump1090 / piaware / Raspbian / Linux. 
https://grndcntrl.net/links/
https://github.com/Jxck-S/tat-feeder
Find coordinates / elevation:
https://www.freemaptools.com/elevation-finder.htm
https://theairtraffic.com/feed/#scripts
https://theairtraffic.com/feed/
https://github.com/Jxck-S?tab=repositories
https://github.com/Jxck-S/tat-feeder
https://grndcntrl.net/falconlanding/
https://opensky-network.org/


Build your own Raspberry Pi flight tracker
https://www.raspberrypi.com/tutorials/build-your-own-raspberry-pi-flight-tracker/

dump1090-fa Debian/Raspbian packages
https://github.com/flightaware/dump1090

How to Track Local Airplanes with Raspberry Pi 
https://www.tomshardware.com/how-to/raspberry-pi-airplane-tracker
ADS-B Receiver Kit (Antenna and USB dongle)
How to Track Local Airplanes with Raspberry Pi 

1090MHz Antenna
Antennas that broadcast 1090MHz signals (the signal the antenna is receiving) are set up vertically and the best way to receive the signal is to align the antenna vertically, also.
1090 MHz Antenna
Regular price:    $49.99
https://flightaware.store/products/antenna-1090mhz
Specifically tuned for flight tracking of 1090 MHz ADS-B equipped aircraft. 
    Indoor/Outdoor (waterproof) 1090 MHz antenna
    Length 66cm/26in
    5.5 dBi gain
    N Type Termination
    2.5 cm to 4 cm diameter mounting bracket included
10m of LMR400 cable
 I saw an instant and dramatic improvement in reception range in comparison with a simple $8 wire antenna. I used the "MOOKEERF SMA to N Cable 25ft" to connect it to the Flightaware Pro.
 
Coaxial Cable 5 Meter
https://flightaware.store/products/coaxial-cable-5-meter
Regular price:   $35.25 
This coaxial cable is compatible with both our 1090MHz & 978MHz antenna and will plug directly into any of our Software Defined Radios (SDR).
    Low Loss RF Communication 50Ohms Impedance Cable
    17 AWG (0.056")
    ROHS compliant
    Impedance - 50 Ohms
    Capacitance - 24.2pF/foot
Coaxial Cable 10 Meter
https://flightaware.store/products/copy-of-coaxial-cable-10-meter
Regular price:   $48.25 

Do you want to build your own FlightAware PiAware ADS-B Ground Station? 
Get a free FlightAware Enterprise Account (USD89.95/mo value) 
Build a PiAware ADS-B Receiver
https://flightaware.com/adsb/piaware
https://flightaware.com/adsb/piaware/build/
View the PiAware installation page to install the latest version on your Pi: 
https://flightaware.com/adsb/piaware/install
 To build a PiAware, you must obtain the following components:
    Raspberry Pi 3 / 4 / Zero W
    Power supply for the Raspberry Pi
        5.1 Volts 2.5 Amps power supply recommended
    Micro SD Card (size: 8 GB or larger)
    Micro SD card reader
        If your computer does not have a built-in SD card reader/writer, you will need the optional USB SD card reader/writer.
    USB SDR ADS-B Receiver (FlightAware Pro Stick or Pro Stick Plus recommended)
        The USB SDR (Software Defined Radio) ADS-B (Automatic Dependent Surveillance-Broadcast) receiver translates the 1090 MHz radio signal into something the computer can understand
        Hint: If you are choosing between the FlightAware Pro Stick and the Pro Stick Plus remember the Plus has an on-board filter that works well in locations that have a lot of radio noise, such as urban environments.
    1090 MHz Antenna
        An indoor antenna can be purchased to start. If using the FlightAware USB adapter be sure the antenna has an SMA connector.
        If you use a telescoping mast antenna be sure to collapse it to a quarter wavelength of 1090 MHz (6.9 cm) to maximize reception.

1090MHz ADS-B Filtered Preamp
https://store.uputronics.com/index.php?route=product/product&path=59&product_id=50
    Brand: Uputronics
    Product Code: HAB-FPA1090SAW
    £43.19
	All our preamps are compatible with most USB SDR Dongles such as the RTL USB, Airspy, Fun Cube. You can power them from either bias tee (This item is 100% compatible with the Airspy bias-tee) or a simple USB-C cable (Not Supplied - See related items for a suitable USB Type A to C Cable).
	Bias-tee voltage input is 5V. Note: Unlike previous models, component supply issues mean bias-tee input voltage is 5V max. 
	This unit is a small filter and preamp designed to go between a software defined radio receiver and an antenna. Using a SAW bandpass filter and a low noise amplifier (LNA), it stops out of band intermodulation while providing additional gain for increased sensitivity. The LNA is before the SAW filter in this design to reduce the noise factor of the unit. This particular model is tuned for use with ADS-B frequencies (1090MHz).

The LNA used is a MiniCircuits PSA4-5043+ which provides about 16dB of gain @ 1090MHz.



### ANCIENT HISTORY: SDR startup at my house  
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
  
  

