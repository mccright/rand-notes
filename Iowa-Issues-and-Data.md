# Iowa Issues and Data  
*This is an early draft of topics of concern.*  

## Internet Connectivity  
I read wildly varying characterizations of Internet connectivity across the state of Iowa.  Because Internet connectivity is an important input to the success of education, business, and governing (democracy) of the state, it is critical that we have an unambiguous, trustworthy, shared understanding of its current state.  
'Ookla for Good' maintains an open data set that includes data on *Intetnet speeds* and *coverage* across the United States, including Iowa for both mobile and fixed Internet connections.  They gather their data via their *speedtest* application. Using this link: [https://www.ookla.com/ookla-for-good/open-data](https://www.ookla.com/ookla-for-good/open-data) narrow the scope to "Iowa, United States" and choose a data set.  When comparing Q3 2023 (similar to Q4 2021) fixed and mobile Internet coverage data for Iowa against Missouri, Wisconsin or Illinois (*or a number of other states*), too much of Iowa that is outside urban areas still looks like a digital wasteland. 	
  * Not only is connectivity **coverage** limited in Iowa, **upload/download speeds** are limited as well.  In Q3 2023 Iowa was 36th for mobile and 44th for fixed connection download speeds (*mobile speeds being far, far below measured speeds in Illinois, Minnesota, and Missouri, and fixed speeds falling even below Nebraska, South Dakota, Mississippi, West Virginia, and Maine*). In Q4 2023 Iowa dropped to 37th for median download speeds (in Q4 2021 Iowa was also 44th, *8th from the slowest*, in the nation with median download speed of 38.81 Mbps and median upload 7.72 Mbps).   [https://www.speedtest.net/global-index/united-states#market-analysis](https://www.speedtest.net/global-index/united-states#market-analysis).  This connectivity sloth is in spite of Iowa Governor Reynolds saying for years that Internet access is a priority for her administration...  
  * Why use Ookla?  Given their descriptions of their data, it seems like a useful source for Internet connectivity data.  "Every day, over ten million unique tests are actively initiated by our users in the locations and at the times when their connectivity matters to them. Since our founding in 2006, an unparalleled total of more than 40 billion tests have been taken with Speedtest." [https://www.speedtest.net/about](https://www.speedtest.net/about) and "Hundreds of millions of people worldwide use Speedtest® to measure their internet connection. With over 18 million consumer-initiated tests taken daily and billions of data points gathered, Ookla® data paints a clear picture of the performance, quality, and availability of virtually every network in the world." [https://www.ookla.com/ookla-for-good](https://www.ookla.com/ookla-for-good)  
  * Raw data: "Speedtest by Ookla Global Fixed and Mobile Network Performance Maps." "Global fixed broadband and mobile (cellular) network performance, allocated to zoom level 16 web mercator tiles (approximately 610.8 meters by 610.8 meters at the equator). Data is provided in both Shapefile format as well as Apache Parquet with geometries represented in Well Known Text (WKT) projected in EPSG:4326. Download speed, upload speed, and latency are collected via the Speedtest by Ookla applications for Android and iOS and averaged for each tile. Measurements are filtered to results containing GPS-quality location accuracy."  Updated quarterly. [https://registry.opendata.aws/speedtest-global-performance/](https://registry.opendata.aws/speedtest-global-performance/)  
  * The SpeedTest client apps [https://www.speedtest.net/apps/cli](https://www.speedtest.net/apps/cli)  
    * And some speedtest scripts of varying sophistication:  
      * Speedtest-cli Python module [https://github.com/sivel/speedtest-cli](https://github.com/sivel/speedtest-cli)  
      * Shell Scripts To Install Speedtest_Cli [https://github.com/Socerest2/speedtestcli-sh](https://github.com/Socerest2/speedtestcli-sh)   
      * [https://github.com/MegaMosquito/speed](https://github.com/MegaMosquito/speed)  
      * [https://github.com/cesarhdezap/ISP-speed-checker](https://github.com/cesarhdezap/ISP-speed-checker)  
      * [https://github.com/julianzue/SpeedtestCLI](https://github.com/julianzue/SpeedtestCLI/blob/main/speed.py)  
      * [https://github.com/JayRovacsek/speedtestcli-periodic](https://github.com/JayRovacsek/speedtestcli-periodic)  
      * [https://github.com/Brawn1/speedtestcli_db](https://github.com/Brawn1/speedtestcli_db)  
      * [https://github.com/search?l=Shell&q=speedtestcli&type=Code](https://github.com/search?l=Shell&q=speedtestcli&type=Code)  
      * [https://github.com/search?l=Shell&q=speedtestcli&type=Code](https://github.com/search?l=Shell&q=speedtestcli&type=Code) and [https://github.com/search?l=Python&q=speedtestcli&type=Code](https://github.com/search?l=Python&q=speedtestcli&type=Code)  
  * Install SpeedTest for Terminal on Linux: 
You can get the 'official' version from speedtest.net: [https://www.speedtest.net/apps/cli](https://www.speedtest.net/apps/cli)  
* Another approach is to use https://github.com/sivel/speedtest-cli/ from Matt Martz:  
(Noticed this utility at: https://francoconidi.it/speedtest-cli-failed-su-debian-10/)  
```terminal
sudo apt-get install python3-pip
wget https://raw.github.com/sivel/speedtest-cli/master/speedtest.py
chmod a+rx speedtest.py
sudo mv speedtest.py /usr/local/bin/speedtest-cli
sudo chown root:root /usr/local/bin/speedtest-cli
sudo speedtest-cli
```

  * If **SpeedTest* is just wrong for you (*for any reason*), you might try [fast](https://fast.com/) from [NetFlix](https://netflixtechblog.com/building-fast-com-4857fe0f8adb). [https://fast.com/](https://fast.com/)


### Elections  
A non-scientific review of Iowa legislator's recently filed legislation tagged as about "elections" shows that the following topics (*in no particular order*) were topics that legislators were attempting to change: ```boards, commissions, and councils, elections and politics, government entities, voting, absentee voting, ballots, canvasses of votes, canvassing for votes, proxy voting, runoff elections, voter registration, voting systems examiners board, voting and write-in voting```.  

* Iowa legislators showed **a lot** of interest in mucking with elections in 2021-2022 sessions.  A [search of their "Legislative Documents" site](https://www.legis.iowa.gov/publications/search?tab=true&rows=10&start=0&sort=score%20desc&q=elections&fq=-status%3A%22Reserved%22%20AND%20-status%3A%22Repealed%22%20AND%20-status%3A%22Rescinded%22&fq=(l1%3A%22leg%3A0978%7C89th%20GA%202nd%20Session%22%20OR%20l1%3A%22leg%3A0979%7C89th%20GA%201st%20Session%22)) shows **855** individual pieces of legislation filed in one status or another (*many of those did not pass in the 2021-2022 sessions*). For example, here are three at *random*:  
	* [SJR9](https://legiscan.com/IA/bill/SJR9/2021):	A joint resolution proposing an amendment to the Constitution of the State of Iowa relating to the qualifications of electors. (Formerly SSB 1083.)	2022-06-21. Proof of publication certified. S.J. 943.  
	* [SF413](https://legiscan.com/IA/bill/SF413/2021):	A bill for an act relating to the conduct of elections, including absentee ballots and voter list maintenance activities, making penalties applicable, and including effective date and applicability provisions. (Formerly SSB 1199.)  
	* [SF568](https://legiscan.com/IA/bill/SF568/2021):	A bill for an act relating to the conduct of elections, including nominations, procedures for proposed amendments to the Iowa Constitution, and absentee voting, and including effective date provisions. (Formerly SSB 1237.)  
* Iowa legislators again showed **a lot** of interest in mucking with elections in 2023.  A [search of their "Legislative Documents" site](https://www.legis.iowa.gov/publications/search?tab=true&rows=10&start=0&sort=score%20desc&q=elections&fq=-status%3A%22Reserved%22%20AND%20-status%3A%22Repealed%22%20AND%20-status%3A%22Rescinded%22&fq=(l1%3A%22leg%3A0976%7C90th%20GA%202nd%20Session%22%20OR%20l1%3A%22leg%3A0977%7C90th%20GA%201st%20Session%22)) shows **644** individual pieces of legislation filed in one status or another (*many of those did not pass in 2023*).  


### Water in Iowa  
* A [2019 University of Iowa study](https://desmoinesregister-ia.newsmemory.com?selDate=20221020&goTo=A007&artid=1) found Iowa leads the country in manure waste.  
* [751 rivers, streams, lakes, reservoirs and wetlands are considered impaired](https://desmoinesregister-ia.newsmemory.com?selDate=20221020&goTo=A007&artid=1) -- roughly half of Iowa’s waterways that were assessed.  


### Lead Poisoning  
The CDC says there is no safe level for lead in blood. Exposure at any level has been shown to cause irreversible harm to children, including damage to the brain and nervous systems, slowed growth and development, learning and behavior problems, and hearing and speech difficulty.  

Nearly 70% of homes in Iowa were built before 1978, when the toxic lead paint was banned for residential use, a proportion far larger than in most other states. Children in low-income families and children of color are most at risk for lead exposure, according to several studies.  

A 2021 study by Quest Diagnostics and Boston Children’s Hospital found that nearly 2% of U.S. children had lead in their blood at or above the 5-microgram action level. It found that in Iowa, the figure was much higher: 3.6%, the ninth-largest proportion among U.S. states.  

Iowa has the nation’s fourth-highest percentage of children under 6 who have detectable levels of lead in their blood — 76%, according to a study published in the Journal of Pediatrics in September 2021 that looked at blood tests from 1.14 million children under 6.  

At the same time, he said, enforcement “is weakening or absent in most parts of the state.”  

FROM: " Few options exist to remove lead paint, despite risk to kids." By Lee Rood, [https://desmoinesregister-ia.newsmemory.com?selDate=20221023&goTo=A001&artid=1](https://desmoinesregister-ia.newsmemory.com?selDate=20221023&goTo=A001&artid=1)  


### Housing  
(September 2022) Polk County is seeing a rise in the number of people who are homeless. According to a point-in-time count conducted by Homeward, the county’s homelessness planning organization, the population increased by 23% in the last year. And the number of people who are unsheltered in Polk County has nearly doubled since January. 
https://desmoinesregister-ia.newsmemory.com?selDate=20221030&goTo=A001&artid=0  
(October 2022 - Polk County) 521 households are on the waitlist to find affordable housing in the county. 
https://desmoinesregister-ia.newsmemory.com?selDate=20221030&goTo=A001&artid=0  


### Banning Books  
In May 2023, Gov. [Kim Reynolds signed Senate File 496](https://www.legis.iowa.gov/legislation/BillBook?ba=SF%20496&ga=90), that bans books (except "*religious books*") depicting sex acts from public schools -- threatening teachers and administrators with harsh penalties for non-compliance -- and resulting in the removal of more than 1,300 books from Iowa public schools.  After a 5 month delay, the Iowa State Board of Education published a "Notice of Intended Action" -- under the heading of "Eliminating Achievement and Opportunity Gaps" -- of [changes to Iowa School rules for “General Accreditation Standards”](https://educate.iowa.gov/sites/default/files/2023-11/2023-11-15SBE-Rules-Chapter12.pdf) in November 2023.  
See the fruits of Iowa's book banning elected officials in the database "[Library books removed in Iowa school districts](https://databases.desmoinesregister.com/database-books-removed-from-libraries-in-iowa-school-districts/)." by Tim Webber, Samantha Hernandez and [The Des Moines Register](https://www.desmoinesregister.com).  As of 2024-03-17, The Des Moines Register database includes roughly 1,820 instances of banned "[books — 615 of which are unique titles — removed from schools since the law went into effect July 1 (2023)](https://www.desmoinesregister.com/story/news/politics/iowa-poll/2024/03/17/iowa-poll-half-say-new-book-ban-law-for-public-schools-goes-too-far-senate-file-496-lgbtq/72775250007/)."  


### Iowa Legislature's/Governor's "Don't say gay" Law  
In May 2023, Gov. [Kim Reynolds signed Senate File 496](https://www.legis.iowa.gov/legislation/BillBook?ba=SF%20496&ga=90), that prohibits "[instruction related to gender identity and sexual orientation](https://www.legis.iowa.gov/docs/publications/SJNL/1375335.pdf#page=4)"
in Iowa schools (*also see additional references on pages 1, 2, 3, 7, 11 and 13*). If any student "[requests an accommodation that is intended to affirm the student's gender identity](https://www.legis.iowa.gov/docs/publications/LGE/90/attachments/SF496_GovLetter.pdf#page=11)," their teacher (*or any "licensed practitioner employed by the school district"*) "[shall report the student's request to an administrator employed by the school district, and the administrator shall report the student's request to the student's parent or guardian.](https://www.legis.iowa.gov/docs/publications/LGE/90/attachments/SF496_GovLetter.pdf#page=11)"  The Governor's action also removed all mentions of "HPV," the availability of a "vaccine to prevent HPV," and references to "acquired immune deficiency syndrome" from the content required by "[health education](https://www.legis.iowa.gov/docs/publications/LGE/90/attachments/SF496_GovLetter.pdf#page=6)" and by "instruction in human growth and development](https://www.legis.iowa.gov/docs/publications/LGE/90/attachments/SF496_GovLetter.pdf#page=8)"  After a 5 month delay, the Iowa State Board of Education published a "Notice of Intended Action" -- under the heading of "Eliminating Achievement and Opportunity Gaps" -- of [changes to Iowa School rules for “General Accreditation Standards”](https://educate.iowa.gov/sites/default/files/2023-11/2023-11-15SBE-Rules-Chapter12.pdf) in November 2023.  


### Finding Information:  
* The Iowa Legislature [https://www.legis.iowa.gov/](https://www.legis.iowa.gov/)  
* Legiscan IA [https://legiscan.com/IA](https://legiscan.com/IA)  
* Iowa Data Center [https://www.iowadatacenter.org/index.php/quick-facts/iowa-quick-facts](https://www.iowadatacenter.org/index.php/quick-facts/iowa-quick-facts)  

### Other:  
* "the four biggest oil companies — Exxon Mobile, Shell, Chevron, and Total Energies — have made over $330 billion in profits in just the past three years." [By Jonas Magram, DMR, 2024-03-10, page F3](https://desmoinesregister-ia.newsmemory.com?selDate=20240310&goTo=F003&artid=2&editionStart=Des%20Moines%20Register)  
* "Tuition alone at Iowa State University has risen 236% since 2001; inflation in that period is 73%. Iowa students have some of the worst loan debt burdens in the nation." [By Lucas Grundmeier, DMR, 2024-03-10, page F1](https://desmoinesregister-ia.newsmemory.com?selDate=20240310&goTo=F001&artid=2&editionStart=Des%20Moines%20Register)  
* Since 2001, the Federal Crop Insurance Program’s "total payments to Iowa farmers have grown by over 630%, from about $3 billion a year to over $19 billion in 2022." [By Jonas Magram, DMR, 2024-03-10, page F3](https://desmoinesregister-ia.newsmemory.com?selDate=20240310&goTo=F003&artid=2&editionStart=Des%20Moines%20Register)  
