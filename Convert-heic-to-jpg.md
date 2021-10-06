# Use libheif to Convert iOS heif images to jpg format  

Apple products that emit images default to heif format, that is still unfriendly in some endpoint and server environments.  That leaves conversion a regular duty.  

leibheif is at [https://github.com/strukturag/libheif](https://github.com/strukturag/libheif)  

Install it on Ubuntu spins with:  
```terminal
sudo apt-get install libheif-examples
```

If you need to convert a single file:  
```terminal
/usr/bin/heif-convert -q 100 [original-file-name] [file-name-with-jpg-or-png-extension] 
```

If you have a collection of heic files, use a script that automates this process.  
It seems like most recommendations use a for loop like:  
```terminal
for file in *.heic; do heif-convert -q 100 $file ${file/%.heic/.jpg}; done
```
One example (the one above) is at [https://lokarithm.com/2021/02/27/linux-how-to-convert-heic-files-to-jpg-or-png/](https://lokarithm.com/2021/02/27/linux-how-to-convert-heic-files-to-jpg-or-png/)  
And a more elaborate version of the same at: [https://github.com/lokarithm/HandyBashCommands/tree/main/heic-converter](https://github.com/lokarithm/HandyBashCommands/tree/main/heic-converter)  

Another example is at:  
[https://github.com/shellbro/dockerfile-heif-convert/blob/master/convert-all](https://github.com/shellbro/dockerfile-heif-convert/blob/master/convert-all)  
or 
[https://stuffjasondoes.com/2019/07/10/batch-convert-heic-to-jpg-in-linux/](https://stuffjasondoes.com/2019/07/10/batch-convert-heic-to-jpg-in-linux/)  

And some notes on how to navigate a collection of image files for processing at: [https://gist.github.com/bittercoder/f6601784ebe4f63e9b9e037e3344b960](https://gist.github.com/bittercoder/f6601784ebe4f63e9b9e037e3344b960)  
and  
[https://gist.github.com/mrmcwake/6d22eee12e8261e75743019c9219f4bc](https://gist.github.com/mrmcwake/6d22eee12e8261e75743019c9219f4bc)  