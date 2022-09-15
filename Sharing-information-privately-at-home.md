## Sharing Information at Home  
Is it prudent to donate everything you share around the house with your ISP, your email provider, and your chosen social media provider?  I don't think so.  As a result, I have begun experimenting with some simple, isolated information sharing platforms for around the house.  

**Simple** is important to me.  Simple, even primitive, seems best for most of our family information sharing -- most of which is transient.  Simple text and lists will get us far.  I don't have a *favorite* platform in mind and need to look around for options and experiment.  
**Cleanup** is also important to me.  If any of these experiments really *sticks* then it will accumulate non-public data.  At some point I'll need to *securely* erase that data.  (shred, wipe, srm (secure-delete))  
```terminal
shred -zvu -n 5 <filename>
```
Then confirm your work:  
```terminal
hexdump < <filename>
```
You might see: [https://icorn.org/digital-security](https://icorn.org/digital-security) for more information about digital security  


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
* **Use a local Matrix server:**  
* Here is a description of installing the Element Matrix server using Docker: [https://github.com/vector-im/element-web#running-from-docker](https://github.com/vector-im/element-web#running-from-docker)  
* Matrix (An open network for secure, decentralized communication) server setup using Ansible and Docker [https://github.com/spantaleev/matrix-docker-ansible-deploy](https://github.com/spantaleev/matrix-docker-ansible-deploy)  
* Dockerising a full Matrix server with Element (Riot) messaging, coTURN NAT traversal and Traefik(v2.2) proxy on RancherOS and Digital Ocean (*which violates my "at home" mandate, but may be a template for this target*) [https://github.com/b-venter/Matrix-Docker-install](https://github.com/b-venter/Matrix-Docker-install)  
  * Admin Support: This is a simple library for functions that I use with my Matrix-Server [https://github.com/btesteracc/matrix_admin](https://github.com/btesteracc/matrix_admin)  
* And maybe -- A "lightweight (but full-featured) Matrix server, written in Go language, which has ease of deployment. The implementation is aimed specifically to HOMEservers (which are usually small, for example, Raspberry Pi)" [https://github.com/signaller-matrix/signaller](https://github.com/signaller-matrix/signaller)  

* ChatServer: JustSaying [https://github.com/subhashi31/ChatServer](https://github.com/subhashi31/ChatServer)  
* Minimalist Notepad [https://github.com/pereorga/minimalist-web-notepad/](https://github.com/pereorga/minimalist-web-notepad/)  
* editPad (*self-hosted*) [https://github.com/shweshi/editpad](https://github.com/shweshi/editpad)  
* SoapBox  
* GNU Social  
* RocketChat [https://github.com/RocketChat/Rocket.Chat](https://github.com/RocketChat/Rocket.Chat)  
* Zulip [https://github.com/zulip/zulip](https://github.com/zulip/zulip) [use this version [https://github.com/zulip/docker-zulip](https://github.com/zulip/docker-zulip)]  
* RevoltChat [https://github.com/revoltchat/](https://github.com/revoltchat/)  
* HubZilla 
* TalkTalkTalk single-page chat room [https://github.com/josephernest/talktalktalk](https://github.com/josephernest/talktalktalk); My initial experimentation leads me to believe that its Python 2 code is not going to work in a Python 3 world without some material upgrading.  I am setting this option aside for now.  
* Este es el repositorio de los contenidos de la Wiki de Python Argentina? [https://github.com/PyAr/wiki](https://github.com/PyAr/wiki)  
* Another Python 2 chat system: [https://github.com/illBeRoy/secured-chat-server](https://github.com/illBeRoy/secured-chat-server)  
* surevine / web-chat [https://github.com/surevine/web-chat](https://github.com/surevine/web-chat)  
* hedgedoc [https://github.com/hedgedoc/hedgedoc](https://github.com/hedgedoc/hedgedoc) and [https://docs.hedgedoc.org/setup/docker/](https://docs.hedgedoc.org/setup/docker/)  
* MatterMost [https://github.com/mattermost/mattermost-server](https://github.com/mattermost/mattermost-server)  
  * or one of the other XMPP servers listed at: [https://en.wikipedia.org/wiki/Comparison_of_XMPP_server_software](https://en.wikipedia.org/wiki/Comparison_of_XMPP_server_software)  

* Rūrusetto (ルールセット)  
[https://github.com/Rurusetto/rurusetto](https://github.com/Rurusetto/rurusetto)  
* Passing on Okuna - it is interesting, but looks *too big* and likely too much work for my home environment needs [https://github.com/OkunaOrg/okuna-api](https://github.com/OkunaOrg/okuna-api)  

* This is not core to the mission above, but maybe experiment with [Funkwhale](https://funkwhale.audio/) [https://dev.funkwhale.audio/funkwhale/funkwhale](https://dev.funkwhale.audio/funkwhale/funkwhale), [https://blog.funkwhale.audio/](https://blog.funkwhale.audio/), and   
  * Docker image from Ned Kelley: [https://github.com/ultimate-pms/ultimate-media-server-core/tree/master/dockerfiles/server/docker-funkwhale](https://github.com/ultimate-pms/ultimate-media-server-core/tree/master/dockerfiles/server/docker-funkwhale)  
  *  funkwhale music import script from Ned Kelley: [https://github.com/ultimate-pms/ultimate-media-server-core/blob/master/scripts/funkwhale/funkwhale_bump-files.sh](https://github.com/ultimate-pms/ultimate-media-server-core/blob/master/scripts/funkwhale/funkwhale_bump-files.sh)  

* Also a little off-topic, but still relevant to the *privately sharing information* mission -- SecretShare, A *simple* library implementing Adi Shamir's "How to share a secret" algorithm written in Python: [https://github.com/HacKanCuBa/secretshare-py](https://github.com/HacKanCuBa/secretshare-py)  
