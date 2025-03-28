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


### LocalSend May Be The One  
My testing between iOS and Windows seems to work as claimed.  
https://github.com/localsend/localsend/  
>"LocalSend is a free, open-source app that allows you to securely share files and messages with nearby devices over your local network, without needing an internet connection."  
>"About: LocalSend is a cross-platform app that enables secure communication between devices using a REST API and HTTPS encryption. Unlike other messaging apps that rely on external servers, LocalSend doesn't require an internet connection or third-party servers, making it a fast and reliable solution for local communication."  
>"All data is sent securely over HTTPS, and the TLS/SSL certificate is generated on the fly on each device, ensuring maximum security."  
This app is implemented to work on Windows, macOS, Linux, Android, iOS and Fire OS.  


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


### Next An Experiment with Convos  
https://github.com/convos-chat/convos  
Installation is a breeze, but I immediately learned that I had not carefully read the documentation.  
```terminal
curl https://convos.chat/install.sh | sh -
./convos/script/convos daemon
```

The script output showed that I was installing a Perl application -- something I had not done for years...  
In addition, the server appeared to work immediately, but the configuration showed me that this was not a local installation at all. I was using irc.libera.chat in the background.  
The documentation emphasized "[Convos is all about privacy](https://convos.by/)" This project is a web interface to global IRC.  Pretty neat, but not what I am looking for.   


### Next An Experiment with *CS Class Chat app using Flask*  
[https://github.com/saarikabhasi/Chat-application](https://github.com/saarikabhasi/Chat-application)  
My limited experimentation did not show this as a contender at test time.  


### Next An Experiment with *Workbase-server*   

The source code is at: https://github.com/wanglian/workbase-server/  
I tried the simple path and installed in on Ubuntu using snap -- https://snapcraft.io/workbase-server.  
```terminal
$ sudo snap install workbase-server
$ sudo snap run --shell workbase-server
# echo ROOT_URL=https://home.local > $SNAP_COMMON/root-url.env
# exit
$ sudo snap restart workbase-server
$ sudo ufw delete from <my_network_segment>/<its_netmask> to any port 3000 proto tcp
```
At that point it appeared to work.  Asking me to set up the initial (Admin) user.  Easy.  
I set up a second user and did some testing.   
The user interface is pretty crude and seems unfinished.  
But it does support interactive *chat-like* communication without hiccups.  
It is just not a pleasing experience and I get the sensation that catastrophe is nearby.  
I'll try something else.


### Other Candidates for Review  
* **Use a local Matrix server:**  
* A Matrix homeserver written in Rust  [https://github.com/social-network/conduit](https://github.com/social-network/conduit) and [https://hub.docker.com/r/matrixconduit/matrix-conduit](https://hub.docker.com/r/matrixconduit/matrix-conduit): "A fast Matrix homeserver that's easy to set up and just works. You can install it on a mini-computer like the Raspberry Pi to host Matrix for your family, friends or company."  Or clone the repo, build it with cargo build --release and call the binary (target/release/conduit) from somewhere like a systemd script. Read more [https://github.com/social-network/conduit/blob/master/DEPLOY_FROM_SOURCE.md](https://github.com/social-network/conduit/blob/master/DEPLOY_FROM_SOURCE.md)  
* Here is a description of installing the Element Matrix server using Docker: [https://github.com/vector-im/element-web#running-from-docker](https://github.com/vector-im/element-web#running-from-docker) or  
  * Synapse, reference impl of a Matrix homeserver -- matrixdotorg/synapse (Docker pulls 50M+) [https://hub.docker.com/r/matrixdotorg/synapse](https://hub.docker.com/r/matrixdotorg/synapse), [https://matrix.org/docs/projects/server/synapse](https://matrix.org/docs/projects/server/synapse) and 2020 instructions for installing it:  [https://linuxhandbook.com/install-matrix-synapse-docker/](https://linuxhandbook.com/install-matrix-synapse-docker/)  
  * And a web interface to your Matrix server - vectorim/element-web (Docker pulls 5M+) "A glossy Matrix collaboration client for the web." [https://hub.docker.com/r/vectorim/element-web](https://hub.docker.com/r/vectorim/element-web)  
* Matrix (An open network for secure, decentralized communication) server setup using Ansible and Docker [https://github.com/spantaleev/matrix-docker-ansible-deploy](https://github.com/spantaleev/matrix-docker-ansible-deploy)  
* Dockerising a full Matrix server with Element (Riot) messaging, coTURN NAT traversal and Traefik(v2.2) proxy on RancherOS and Digital Ocean (*which violates my "at home" mandate, but may be a template for this target*) [https://github.com/b-venter/Matrix-Docker-install](https://github.com/b-venter/Matrix-Docker-install)  
  * Admin Support: This is a simple library for functions that I use with my Matrix-Server [https://github.com/btesteracc/matrix_admin](https://github.com/btesteracc/matrix_admin)  
* And maybe -- A "lightweight (but full-featured) Matrix server, written in Go language, which has ease of deployment. The implementation is aimed specifically to HOMEservers (which are usually small, for example, Raspberry Pi)" [https://github.com/signaller-matrix/signaller](https://github.com/signaller-matrix/signaller)  

* ChatServer: JustSaying [https://github.com/subhashi31/ChatServer](https://github.com/subhashi31/ChatServer)  
* Minimalist Notepad [https://github.com/pereorga/minimalist-web-notepad/](https://github.com/pereorga/minimalist-web-notepad/) and a [model Docker config](https://github.com/pereorga/docker-php-test)  
* EtherPad (*self-hosted*) [https://etherpad.org/](https://etherpad.org/),  [https://github.com/ether/etherpad-lite/](https://github.com/ether/etherpad-lite/) and [https://github.com/ether/etherpad-lite/wiki/](https://github.com/ether/etherpad-lite/wiki/How-to-deploy-Etherpad-Lite-as-a-service)  
* editPad (*self-hosted*) [https://github.com/shweshi/editpad](https://github.com/shweshi/editpad)  
* SoapBox  
* GNU Social  
* RocketChat [https://github.com/RocketChat/Rocket.Chat](https://github.com/RocketChat/Rocket.Chat)  
* Zulip [https://github.com/zulip/zulip](https://github.com/zulip/zulip) [use this version [https://github.com/zulip/docker-zulip](https://github.com/zulip/docker-zulip)]  
* RevoltChat [https://github.com/revoltchat/](https://github.com/revoltchat/) and [https://github.com/revoltchat/self-hosted](https://github.com/revoltchat/self-hosted)  
* HubZilla 
* Este es el repositorio de los contenidos de la Wiki de Python Argentina? [https://github.com/PyAr/wiki](https://github.com/PyAr/wiki)  
* Another Python 2 chat system: [https://github.com/illBeRoy/secured-chat-server](https://github.com/illBeRoy/secured-chat-server)  
* hedgedoc [https://github.com/hedgedoc/hedgedoc](https://github.com/hedgedoc/hedgedoc) and [https://docs.hedgedoc.org/setup/docker/](https://docs.hedgedoc.org/setup/docker/)  
* MatterMost [https://github.com/mattermost/mattermost-server](https://github.com/mattermost/mattermost-server)  
  * or one of the other XMPP servers listed at: [https://en.wikipedia.org/wiki/Comparison_of_XMPP_server_software](https://en.wikipedia.org/wiki/Comparison_of_XMPP_server_software)  
* p2p https://briarproject.org/  
* ngIRCd - Internet Relay Chat Server [https://github.com/ngircd/ngircd](https://github.com/ngircd/ngircd)  
* https://github.com/georgeOsdDev/markdown-edit/  


* Rūrusetto (ルールセット)  
[https://github.com/Rurusetto/rurusetto](https://github.com/Rurusetto/rurusetto)  
* Passing on Okuna - it is interesting, but looks *too big* and likely too much work for my home environment needs [https://github.com/OkunaOrg/okuna-api](https://github.com/OkunaOrg/okuna-api)  
* TalkTalkTalk single-page chat room [https://github.com/josephernest/talktalktalk](https://github.com/josephernest/talktalktalk); My initial experimentation leads me to believe that its Python 2 code is not going to work in a Python 3 world without some material upgrading.  I am setting this option aside for now.  
* surevine / web-chat (*it requires a collection of distributed dependencies that does not fit my urge for external independence*) [https://github.com/surevine/web-chat](https://github.com/surevine/web-chat)  

* This is not core to the mission above, but maybe experiment with [Funkwhale](https://funkwhale.audio/) [https://dev.funkwhale.audio/funkwhale/funkwhale](https://dev.funkwhale.audio/funkwhale/funkwhale), [https://blog.funkwhale.audio/](https://blog.funkwhale.audio/), and   
  * Docker image from Ned Kelley: [https://github.com/ultimate-pms/ultimate-media-server-core/tree/master/dockerfiles/server/docker-funkwhale](https://github.com/ultimate-pms/ultimate-media-server-core/tree/master/dockerfiles/server/docker-funkwhale)  
  *  funkwhale music import script from Ned Kelley: [https://github.com/ultimate-pms/ultimate-media-server-core/blob/master/scripts/funkwhale/funkwhale_bump-files.sh](https://github.com/ultimate-pms/ultimate-media-server-core/blob/master/scripts/funkwhale/funkwhale_bump-files.sh)  

* If standing up your own is just too much work but you still want an easy-to-use primative, text-only chat interface, you might try [https://www.chatzy.com](https://www.chatzy.com/)  

* Also a little off-topic, but still relevant to the *privately sharing information* mission -- SecretShare, A *simple* library implementing Adi Shamir's "How to share a secret" algorithm written in Python: [https://github.com/HacKanCuBa/secretshare-py](https://github.com/HacKanCuBa/secretshare-py)  

https://github.com/miroslavpejic85/awesome-selfhosted-mirotalk#communication---irc  

https://github.com/topics/p2p-chat  

https://www.gutenberg.org/ebooks/70235  

Snapdrop: local file sharing in your browser. Inspired by Apple's Airdrop. https://github.com/RobinLinus/snapdrop  
