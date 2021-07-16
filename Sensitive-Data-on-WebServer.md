## How to Protect Sensitive Data on a Web Server  

The best approach is to avoid locating any sensitive data on your web server.  

If that is not possible, configure your web server to explicitly deny access to that sensitive data.  

For this example, assume that the sensitive files are in a directory named 'sensitivefiles.'  

Below find one approach to denying access to the 'sensitivefiles' directory and its subdirectories on several different servers.  

### Lighttpd  
[https://redmine.lighttpd.net/projects/lighttpd/wiki/Docs_ModAccess](https://redmine.lighttpd.net/projects/lighttpd/wiki/Docs_ModAccess)  
[https://redmine.lighttpd.net/projects/1/wiki/docs_configurationoptions](https://redmine.lighttpd.net/projects/1/wiki/docs_configurationoptions)  
Enable the mod_access module:  
```
mod_accessserver.modules += ( "mod_access" )
```
Then deny access to the 'sensitivefiles' directory by adding the following to your lighttpd.conf:  
```
$HTTP["url"] =~ "^/sensitivefiles/" {
    url.access-deny = ("")
}
```
### Apache 2.2  
[https://httpd.apache.org/docs/2.2/mod/core.html#directorymatch](https://httpd.apache.org/docs/2.2/mod/core.html#directorymatch)  
Modify the httpd.conf:  
```
<DirectoryMatch "^/.*/sensitivefiles/">
   Order deny,allow
   Deny from all
</DirectoryMatch>
```

### Apache 2.4  
[https://httpd.apache.org/docs/2.4/mod/core.html#directorymatch](https://httpd.apache.org/docs/2.4/mod/core.html#directorymatch)  
Modify the httpd.conf:  
```
<DirectoryMatch "^/.*/sensitivefiles/">
    Require all denied
</DirectoryMatch>
```

### Nginx  
[https://www.nginx.com/resources/wiki/start/topics/examples/full/](https://www.nginx.com/resources/wiki/start/topics/examples/full/)  
[https://www.nginx.com/resources/wiki/start/topics/examples/server_blocks/](https://www.nginx.com/resources/wiki/start/topics/examples/server_blocks/)  
Add this code as the topmost chunk of the relevant (virtual) server-block in your nginx.conf:  
```
location ~ /sensitivefiles/ {
     deny all;
}
```
