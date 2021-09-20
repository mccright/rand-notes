# Ubuntu Updating Notes:  

## Kernel update results in broken WiFi
After updating kernel *5.11.0-34-generic* wireless driver failed to recognize my laptop's WiFi card.  

A quick search fount an Ubuntu bug report that had exactly my symptom, which looked like:  
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1938983](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1938983)  
```terminal
update-initramfs: Generating /boot/initrd.img-5.11.0-34-generic  
W: Possible missing firmware /lib/firmware/i915/skl_guc_49.0.1.bin for module i915  
W: Possible missing firmware /lib/firmware/i915/bxt_guc_49.0.1.bin for module i915  
W: Possible missing firmware /lib/firmware/i915/kbl_guc_49.0.1.bin for module i915  
...  
```

In [Comment #8](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1938983/comments/8) Luca Ferroni (liuck) offered a fix that looked practical -- and it worked for me.  Here is my version of his recommendation:  
```terminal  
cd /lib/firmware/i915/  

export url=https://anduin.linuxfromscratch.org/sources/linux-firmware/i915/  

/lib/firmware/i915$ wget --spider -r -l1 $url 2>&1 | grep '^--' | awk '{ print $3 }' | grep -v '\.\(css\|js\|png\|gif\|jpg\)$' > /tmp/binlist.txt  

/lib/firmware/i915$ cat ~/tmp/t.txt | while read a; do sudo wget $a; done  

/lib/firmware/i915$ sudo update-initramfs -u -k all  
```  

Thank you [Luca](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1938983/comments/8) for the idea.  
And thank you [Rob Wilkerson](https://stackoverflow.com/questions/2804467/spider-a-website-and-return-urls-only) for the download help.  



