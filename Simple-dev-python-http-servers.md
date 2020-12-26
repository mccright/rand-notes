## Simple python http server options for development [EARLY DRAFT].  
*Again, this is mostly a reminder for my own work.*  
One common use case is to quickly set up a web server to host your app at various stages of development.  
 
### Gunicorn [https://gunicorn.org/](https://gunicorn.org/)  
---

Gunicorn is a Python [WSGI HTTP Server](https://en.wikipedia.org/wiki/Web_Server_Gateway_Interface) for UNIX.  

Install using pip  

```bash  
$ pip3 install gunicorn  
```

Start the app using gunicorn:    
```bash  
$ gunicorn --bind 0.0.0.0:8001 run:app  
```

Point your browser at `http://localhost:8001`.  
  
 
### Waitress [https://docs.pylonsproject.org/projects/waitress/en/stable/](https://docs.pylonsproject.org/projects/waitress/en/stable/)  
---

Waitress (think *Gunicorn for Windows*), a production-quality pure-Python WSGI server.  It has no dependencies outside the Python standard library.  

Install using pip  

```bash  
$ pip3 install waitress  
```
Start the app using [waitress-serve](https://docs.pylonsproject.org/projects/waitress/en/stable/runner.html)  

```bash  
$ waitress-serve --port=8001 run:app    
```

Point your browser at `http://localhost:8001`.  
  
 
### uWSGI [http://uwsgi-docs.readthedocs.org/en/latest/](http://uwsgi-docs.readthedocs.org/en/latest/)  
---

uWSGI, performant [WSGI server](https://en.wikipedia.org/wiki/Web_Server_Gateway_Interface) implementation for UNIX.  

Install using pip  

*Install the latest stable release:*   
```bash
$ pip3 install uwsgi   
```
*Or install the latest LTS (long term support) release:*   
```
pip3 install https://projects.unbit.it/downloads/uwsgi-lts.tar.gz  
```
[Start uWSGI to run an HTTP server/router passing requests to your Flask application](https://uwsgi-docs.readthedocs.io/en/latest/WSGIquickstart.html#deploying-flask):  

```bash  
uwsgi --http 127.0.0.1:8001 --wsgi-file myflaskapp.py --callable app  
```
*Or start uWSGI to run an HTTP server/router passing requests to your native WSGI application:*  
```bash  
$ uwsgi --http 127.0.0.1:8001 --wsgi-file helloworld.py  
```

Point your browser at `http://localhost:8001`.  
  
uWSGI has lots of startup options to enhance performance and production readiness.  See:  
* The WSGI [QuickStart](https://uwsgi-docs.readthedocs.io/en/latest/WSGIquickstart.html) for some of them: [https://uwsgi-docs.readthedocs.io/en/latest/WSGIquickstart.html](https://uwsgi-docs.readthedocs.io/en/latest/WSGIquickstart.html)  
* Another primer: [https://www.digitalocean.com/community/tutorials/how-to-serve-flask-applications-with-uswgi-and-nginx-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-serve-flask-applications-with-uswgi-and-nginx-on-ubuntu-18-04)  

