## Sharing Information at Home  
Is it prudent to donate everything you share around the house with your ISP, your email provider, and your chosen social media provider?  I don't think so.  As a result, I have begun experimenting with some simple, isolated information sharing platforms for around the house.  

**Simple** is important to me.  Simple, even primitive, seems best for most of our family information sharing -- most of which is transient.  Simple text and lists will get us far.  I don't have a *favorite* platform in mind and need to look around for options and experiment.  

### An Experiment with openNAMU  
openNAMU is a Korean wiki that is relatively immature and in active development.  It is also not a highly secure or self-defensive platform.  But it IS simple:  

* cd ~/github  
* git clone -b stable https://github.com/openNAMU/openNAMU.git  
* cd openNAMU/  
* python3 -m venv env  
* source env/bin/activate  
* python -m pip install --upgrade pip  
* python -m pip install --upgrade setuptools wheel  
* python -m pip install -r requirements.txt  
* python3 ./app.py  
    * It will prompt for the TCP port
* permit traffic through your firewall:  
    * <IP_ADDRESS> <port>/tcp ALLOW <LOCAL_SEGMENT>/ <SUBNET_MASK>  
    * and DENY all traffic from your router  
* Point your browser at http://localhost:<port>/  
* Use the Admin menu to create users, administer roles (grant Admin to one or more users)  
* Pick a template, edit page headers & footers as needed.
Done.  
* Use the system as a wiki or as highly asynchronous *instant* messaging on your local home network segment.  

Scripting startup thereafter is easy:
```terminal
#!/bin/bash 
cd ~/github/openNAMU/
source env/bin/activate
python3 ./app.py
```
It requires users write in HTML, which will be a turn-off for some (it is not at my home for this use case).  It appears to have no concept of https/TLS communications yet, so it is not appropriate for unsafe networks.  The authors have produced a good start.  I'll keep looking for now.  


### Next An Experiment with _________  
CS Class Chat app using Flask
[https://github.com/saarikabhasi/Chat-application](https://github.com/saarikabhasi/Chat-application)  


### Candidates for Review  
* SoapBox  
* GNU Social  
* RocketChat [https://github.com/RocketChat/Rocket.Chat](https://github.com/RocketChat/Rocket.Chat)  
* Zulip [https://github.com/zulip/zulip](https://github.com/zulip/zulip) [use this version [https://github.com/zulip/docker-zulip](https://github.com/zulip/docker-zulip)]  
* RevoltChat [https://github.com/revoltchat/](https://github.com/revoltchat/)  
* HubZilla
* Este es el repositorio de los contenidos de la Wiki de Python Argentina? [https://github.com/PyAr/wiki](https://github.com/PyAr/wiki)  

* Rūrusetto (ルールセット)  
[https://github.com/Rurusetto/rurusetto](https://github.com/Rurusetto/rurusetto)  
* Passing on Okuna - it is interesting, but looks *too big* and likely too much work for my home environment needs [https://github.com/OkunaOrg/okuna-api](https://github.com/OkunaOrg/okuna-api)  

* This is not core to the mission above, but maybe experiment with [Funkwhale](https://funkwhale.audio/) [https://dev.funkwhale.audio/funkwhale/funkwhale](https://dev.funkwhale.audio/funkwhale/funkwhale), [https://blog.funkwhale.audio/](https://blog.funkwhale.audio/), and   
  * Docker image from Ned Kelley: [https://github.com/ultimate-pms/ultimate-media-server-core/tree/master/dockerfiles/server/docker-funkwhale](https://github.com/ultimate-pms/ultimate-media-server-core/tree/master/dockerfiles/server/docker-funkwhale)  
  *  funkwhale music import script from Ned Kelley: [https://github.com/ultimate-pms/ultimate-media-server-core/blob/master/scripts/funkwhale/funkwhale_bump-files.sh](https://github.com/ultimate-pms/ultimate-media-server-core/blob/master/scripts/funkwhale/funkwhale_bump-files.sh)  

