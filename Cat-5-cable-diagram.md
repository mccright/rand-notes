

## RJ45 ethernet connection pinouts:  

Connect your computer to your router or your switch using a straight-through cable. I have read that EIA/TIA T568B is the most popular standard used for straight-through LAN cables.  
There are two main standards for attaching connectors onto *Cat-5 RJ45 cable wiring*: EIA/TIA 568A and EIA/TIA 568B. Both are correct. In the context of straight-through cables, use either of the EIA/TIA 568 A or B standards consistently throughout any given installation.  
*Cat-5 RJ45 Ethernet cabling* has 8 color coded wires. In the EIA/TIA 568 A or B specifications, they are twisted into 4 pairs of wires. For any given RJ45 connector, a given cable pair is used for pins 1 and 2; another for pins 3 and 6, another for pins 4 and 5, and another for pins 7 and 8.  The difference between EIA/TIA 568A and EIA/TIA 568B standards is that they specify the colors to use for each of those pairs.  

Here is an illustration of a straight-through Ethernet cable:
<a href="https://www.makeuseof.com/cat-5e-wiring-diagram/"><img src="https://static1.makeuseofimages.com/wordpress/wp-content/uploads/2023/05/03-image-showing-the-pinout-diagram-of-a-straight-through-ethernet-cable.jpg"></a>  
From: <a href="https://www.makeuseof.com/cat-5e-wiring-diagram/">"Cabling Your Home Network? Here’s a Helpful Cat 5e Wiring Diagram" 
By Arjun Vishnu, 2023-06-03</a>  


### EIA/TIA 568-A Ethernet UTP cable wiring diagram  

|Pin |Signal |Description |Wire color |Pin |
|:--:|:-----:|:----------:|:---------:|:--:|
| 1 |TX+ pair 1 |Transmit Data+ |White with green strip  |1 |
| 2 |TX- pair 1 |Transmit Data- |Green with white stripe or solid green |2 |
| 3 |RX+ pair 2 |Receive Data+ |White with orange stripe |3 |
| 4 |BI+ pair 3 |Bi-directional+ |Blue with white stripe or solid blue |4 |
| 5 |BI- pair 3 |Bi-directional- |White with blue stripe |5 |
| 6 |RX- pair 2 |Receive Data- |Orange with white stripe or solid orange |6 |
| 7 |BI+ pair 4 |Bi-directional+ |White with brown strip |7 |
| 8 |BI- pair 4 |Bi-directional- |Brown with white stripe or solid brown |8 |


### EIA/TIA 568-B Ethernet UTP cable wiring diagram  

|Pin |Signal |Description |Wire color |Pin |
|:--:|:-----:|:----------:|:---------:|:--:|
| 1 |TX+ pair 1 |Transmit Data+ |White with orange stripe |1 |
| 2 |TX- pair 1 |Transmit Data- |Orange with white stripe or solid orange |2 |
| 3 |RX+ pair 2 |Receive Data+ |White with green stripe |3 |
| 4 |BI+ pair 3 |Bi-directional+ |Blue with white stripe or solid blue |4 |
| 5 |BI- pair 3 |Bi-directional- |White with blue stripe |5 |
| 6 |RX- pair 2 |Receive Data- |Green with white stripe or solid |6 |
| 7 |BI+ pair 4 |Bi-directional+ |White with brown strip |7 |
| 8 |BI- pair 4 |Bi-directional- |Brown with white stripe or solid brown |8 |
  
#### Do I Care About the Differences in Cat-5, Cat-6, or Other Twisted Pair *Standards* for Home Ethernet Wiring?  
If you are connecting a couple devices and the cable lengths will be less than 165 feet (50 meters) then, probably not too much.  If your cable runs are between 165 and 325 feet (100 meters), then pay more attention to the fine points of your cable specification as well as the specs of your Ethernet endpoints.  Some people (*including sales-people*) speak of *standard* 100 meter cable length support without consideration of the actual cable in question.  Use some caution if purchasing twisted pair cabling for runs longer than 165 feet (50 meters).  
Category 5 cable, commonly known as Cat 5, is an unshielded twisted pair cable type designed for high signal integrity and has been used for Ethernet network infrastructure since at least the early 1990s.  Unshielded twisted pair cables depend on the quality of the twists to protect from [eletromagnetic interference](https://en.wikipedia.org/wiki/Electromagnetic_interference) or [crosstalk](https://en.wikipedia.org/wiki/Crosstalk).  The *Category 5* standards have evolved over time and changes they specify support higher speed communications -- for example [Category 5e]().  If you know you will be *living with* your cabling for a long time (*possibly decades*) you may want to use cabling certified as Category 6 -- which should support much higher data communications throughputs -- to avoid the possibility of having to replace your cabling infrastructure in the future.  
In a home Ethernet implementation there are some other issues that may matter a lot.  Will your cabling be exposed to UV light (*for example, sunlight*), or high heat in an attic or other high-temp location, or strong radio frequency (RF) energy?  Issues like those may force the use of cable products having specialized capabilities (*as opposed to the first spool available*).  
