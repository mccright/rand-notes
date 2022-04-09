## Some Endpoint Admin Notes  

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



#### Use find to execute command on files  
Delete files that have not been modified in the last 30 days:  
```  
$ find ~/tmp -type f -mtime +30 -exec rm {} +  
```  
  
Delete files that have not been accessed in the last 30 days:  
```  
$ find ~/tmp -type f -atime +30 -exec rm {} +  
```  
  
Delete files larger than 100MB:  
```  
$ find ~/tmp -type f -size +100M -exec rm {} +  
```  
  
NOTE: Some home directories are mounted with the *noatime* directive to speed up file usage.


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

If you use Solid State Drives (SSDs) (standard in modern computers), USB *thumb* drives, or SD cards/flash memory cards do not use the approach described above. Secure deletion on SSD storage media is a challenge because they use *wear leveling*, a technology that attempts to spread data evenly across all of the media so that any one part of that storage will not be overwritten too many times -- so that the storage device will last longer.  Wear leveling interferes with secure erase programs, which deliberately try to overwrite sensitive files with junk data in order to permanently erase them. As a result, it is better to use full-disk encryption. Encryption avoids the difficulty of secure erasing by making any file on the drive difficult to recover without the required secret.
