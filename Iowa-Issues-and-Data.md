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
* Two weeks before the 2024 election, Iowa Secretary of State [Paul Pate released](https://desmoinesregister-ia.newsmemory.com?publink=08524e977_134d50a) a very low quality (*lots of known weaknesses at time of issue*) list of Iowa Residents that he suspected of voter crimes -- primarily of voting while being a non-citizen.  As county personnel were approaching maximum workload for the pending election, Pate required counties to act on his flawed list. This appeared to be little more than a public show of support to a Trumpist narrative of *massive illegal non-citizen voting*, as well as a tactic to add chaos into election activities, to sow doubt about the *integrity* of elections, to instill fear in legal voter populations who are also immigrants, and possibly to support the Trumpist narrative that voting is *bad* in the U.S. and should be replaced with something else.  County personnel identified lots of errors in Pate's list...  Pate's sloppy (*hostile?*) "research" to construct his list of 2000 voters who's citizenship must be challenged was quickly proven when, as [Brianne Pfannenstiel reported](https://desmoinesregister-ia.newsmemory.com?publink=08524e977_134d50a) in the Des Moines Register that "As part of the lawsuit from LULAC, the state filed a brief that said on Oct. 24, a U.S. Citizenship and Immigration Services agent contacted the secretary of state’s office and agreed to look up each of the 2,176 people on the list and confirm their citizenship. After reviewing the list, the agent told Pate’s office that 12% of the people were not citizens."  


### Water in Iowa  
* A [2019 University of Iowa study](https://desmoinesregister-ia.newsmemory.com?selDate=20221020&goTo=A007&artid=1) found Iowa leads the country in manure waste.  
* [751 rivers, streams, lakes, reservoirs and wetlands are considered impaired](https://desmoinesregister-ia.newsmemory.com?selDate=20221020&goTo=A007&artid=1) -- roughly half of Iowa’s waterways that were assessed.  
* In November 2024 the EPA was trying to get the Iowa DNR to add several rivers used as major sources of drinking water to their list of Impared waterways. Donnelle Eller [wrote in the Des Moines Register that](https://desmoinesregister-ia.newsmemory.com?publink=2876615d5_134d4ff):  
>States are required to evaluate their rivers, lakes, streams and reservoirs every two years to determine if they meet standards for drinking water, recreation, fishing and other uses. Then states are asked to put together water quality improvement plans. In 2022, Iowa had 597 impaired water segments.  
>The U.S. Environmental Protection Agency said Wednesday that the Iowa Department of Natural Resources should add seven segments of the Cedar, Des Moines, Iowa, Raccoon and South Skunk rivers due to high levels of nitrate, a form of nitrogen that can be released into water from manure and commercial fertilizers.  
>(The Iowaa DNR) submitted its list to the EPA in June, identifying 577 water segments with 746 impairments caused by a range of pollutants, including bacteria, animal waste and fertilizer spills.  The EPA said water samples taken from the seven segments it wants added exceeded federal nitrate limits 40 times, primarily from 2020 to 2022. The Cedar River segment flows into Cedar Rapids, the Raccoon River into Des Moines, the Des Moines River into Des Moines and Ottumwa, and the Iowa River into Iowa City.  
>Along with 12 other state and national groups, Food & Water Watch has asked the EPA to prohibit new or expanded livestock operations in northeast Iowa and investigate land-use practices that could cause contamination, among other actions (northeast Iowa’s karst region is characterized by a porous limestone geology which increases the risk of contaminants making their way into groundwater and aquifers that serve as drinking water for large populations).  “Big Ag is polluting our waterways with impunity — and we are paying for it with our health,” Michaelyn Mankel, an organizer for the group, said in a statement. “EPA must take emergency action to intervene in Iowa’s worsening nitrate contamination crisis.”


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


### Food/Hunger  
Food insecurity in Iowa by the numbers (*By F. Amanda Tugade, 01-12-2024, [The Des Moines Register](https://desmoinesregister-ia.newsmemory.com?publink=0114326e8_134d555)*)  
● The average cost of a meal in Iowa is $4.  
● More than 344,000 Iowans are food insecure. More than 30% — roughly 110,000 — are children.  
● 1 in 9 adults — and 1 in 6 children — do not have enough to eat or know where their next meal is coming from.  
● Families with children spend an average of $331 a week on groceries or 41% more than families without kids.  
● The average amount of extra money Iowans experiencing food insecurity need to cover food costs is roughly $245 million.  
● To qualify for any food assistance (*in Iowa*), a single person’s gross monthly limit is $1,632 (*$19,584/yr*), according to the Iowa Department of Health and Human Services.  


### Health Care  
In November 2024 [Michaela Ramm reported for the Des Moines Register](https://desmoinesregister-ia.newsmemory.com?publink=0e0ca3598_134d504) that:  
>"Forty-one hospitals — or about a third of Iowa’s hospitals — have shut down their labor and delivery units from 2000 to 2021, according to a state report. In many cases, these closures left a county without a birthing facility."  
In December 2024 [Clark Kauffman reported in the Iowa Capital Dispatch](https://iowacapitaldispatch.com/2024/12/04/ombudsmen-and-advocates-join-fight-over-nursing-home-staffing-levels/) that Iowa’s Brenna Bird and Kim Reynolds were attempting to block implementation of new nursing home staffing requirements even though:  
>According to data from the Centers for Medicare and Medicaid Services, 14% of Iowa’s 422 nursing facilities were cited for insufficient staffing in fiscal year 2023, before the new (*Biden administration*) requirements were enacted. That’s more than double the national average, which was 5.9%.  Only five other states – Hawaii, Michigan, Montana, New Mexico and Oregon – had a worse record of compliance with the staffing requirements in place at that time.  


### Banning Books  
In May 2023, Gov. [Kim Reynolds signed Senate File 496](https://www.legis.iowa.gov/legislation/BillBook?ba=SF%20496&ga=90), that bans books (except "*religious books*") depicting sex acts from public schools -- threatening teachers and administrators with harsh penalties for non-compliance -- and resulting in the removal of more than 1,300 books from Iowa public schools.  After a 5 month delay, the Iowa State Board of Education published a "Notice of Intended Action" -- under the heading of "Eliminating Achievement and Opportunity Gaps" -- of [changes to Iowa School rules for “General Accreditation Standards”](https://educate.iowa.gov/sites/default/files/2023-11/2023-11-15SBE-Rules-Chapter12.pdf) in November 2023.  
See the fruits of Iowa's book banning elected officials in the database "[Library books removed in Iowa school districts](https://databases.desmoinesregister.com/database-books-removed-from-libraries-in-iowa-school-districts/)." by Tim Webber, Samantha Hernandez and [The Des Moines Register](https://www.desmoinesregister.com).  As of 2024-03-17, The Des Moines Register database includes roughly 1,820 instances of banned "[books — 615 of which are unique titles — removed from schools since the law went into effect July 1 (2023)](https://www.desmoinesregister.com/story/news/politics/iowa-poll/2024/03/17/iowa-poll-half-say-new-book-ban-law-for-public-schools-goes-too-far-senate-file-496-lgbtq/72775250007/)."  


### Iowa Legislature's/Governor's "Don't say gay" Law  
In May 2023, Gov. [Kim Reynolds signed Senate File 496](https://www.legis.iowa.gov/legislation/BillBook?ba=SF%20496&ga=90), that prohibits "[instruction related to gender identity and sexual orientation](https://www.legis.iowa.gov/docs/publications/SJNL/1375335.pdf#page=4)"
in Iowa schools (*also see additional references on pages 1, 2, 3, 7, 11 and 13*). If any student "[requests an accommodation that is intended to affirm the student's gender identity](https://www.legis.iowa.gov/docs/publications/LGE/90/attachments/SF496_GovLetter.pdf#page=11)," their teacher (*or any "licensed practitioner employed by the school district"*) "[shall report the student's request to an administrator employed by the school district, and the administrator shall report the student's request to the student's parent or guardian.](https://www.legis.iowa.gov/docs/publications/LGE/90/attachments/SF496_GovLetter.pdf#page=11)"  The Governor's action also removed all mentions of "HPV," the availability of a "vaccine to prevent HPV," and references to "acquired immune deficiency syndrome" from the content required by "[health education](https://www.legis.iowa.gov/docs/publications/LGE/90/attachments/SF496_GovLetter.pdf#page=6)" and by "instruction in human growth and development](https://www.legis.iowa.gov/docs/publications/LGE/90/attachments/SF496_GovLetter.pdf#page=8)"  After a 5 month delay, the Iowa State Board of Education published a "Notice of Intended Action" -- under the heading of "Eliminating Achievement and Opportunity Gaps" -- of [changes to Iowa School rules for “General Accreditation Standards”](https://educate.iowa.gov/sites/default/files/2023-11/2023-11-15SBE-Rules-Chapter12.pdf) in November 2023.  


### Iowa Legislature's/Governor's "Don't Come Here" Law  
With [Senate File 2340](https://www.legis.iowa.gov/publications/search/document?fq=id:1448304&q=%22Senate+File+2340%22) the Iowa Legislature and Governor created a new crime of "illegal reentry into state by certain aliens."  It says that anyone who has previously been deported, removed or denied admission to the United States and then enters Iowa, can be sent to prison in Iowa for up to 10 years and the judge in the case would have to order the convicted person to return to "the country they had come from." It also requires that anyone convicted of "[Illegal reentry into state by certain aliens](https://www.legis.iowa.gov/publications/search/document?fq=id:1448304&q=%22Senate+File+2340%22)" "shall not be eligible for a deferred judgment, deferred sentence, or suspended sentence."  

While the new law says law enforcement officers can't arrest someone if that individual is in a school, a place of worship, a health care facility, or a facility for survivors of sexual assault, it also provides civil immunity from liability and indemnification for local law enforcement and other government officials along with contractors responsible for enforcing the measure. That immunity appears to support behaviors that make Iowa an unwelcoming place for all who do not emit the visual and audio queues that signal "Iowan" to state and local officials (*strongly suspect that means, for too many, "white without an accent"*).  


### Too Many Iowa Leaders Attack "Iowa Nice."  
If you have read down the page to this paragraph, you probably already know that [Iowa nice](https://en.wikipedia.org/wiki/Iowa_nice) is, at least in part, a myth...  
President-elect Trump recently said that he would deport everyone in the U.S. without up-to-date federal government permission to be in the country, including any of their children who were born in the U.S.  Iowa Gov. Kim Reynolds has been a Trump and Trumpism enthusiast after the arrival of Covid-19 in 2020 [*[except for a short infatuation with Ron DeSantis in the pre-caucus 2024 Presidential campaign](https://www.politico.com/news/magazine/2024/01/19/kim-reynolds-trump-endorsements-00136372)*].  She [sent](https://apnews.com/article/iowa-guard-troops-texas-border-ce4b6127b24ecef7be46feeeb16af2e4) Iowa National Guard troops to Texas twice (*along with smaller groups of Iowa Department of Public Safety officers and Iowa State Patrol troopers*) to help Gov. Greg Abbott drive up the rate of death and maiming among populations attempting to cross the Rio Grand river.  In mid-December 2024, Reynolds has pledged to [deploy "every tool"](https://desmoinesregister-ia.newsmemory.com?publink=1158e9da5_134d562) at her disposal to support Trump's (*and Tom Homan's*) mass deportation promises.  
["Iowa tees up for deportations -- Gov. promises to deploy 'every tool' for operation"](https://desmoinesregister-ia.newsmemory.com?publink=1158e9da5_134d562) by Sabine Martin.  


### School Absenteeism  
Chronic absenteeism is having missed at least 10% of school days or instructional hours.  In late 2024 the statewide average for chronic absenteeism in Iowa is [21% of the student population](https://desmoinesregister-ia.newsmemory.com?publink=031f19f7d_134d563) -- a number that represents additional challenges in the future for too many of those students, and illustrates weaknesses in student/family support systems.  During the 2024 legislative session, Iowa Republicans introduced [Senate File 2435](https://www.legis.iowa.gov/legislation/BillBook?ga=90&ba=SF2435) emphasizing charging and prosecuting parents of "Truant" students -- in Section 15, county attorneys are made responsible for enforcement of Iowa's truancy laws ("[has been absent from school, for any reason, for at least twenty percent of the days or hours in the grading period" [beginning on page 25](https://www.legis.iowa.gov/legislation/BillBook?ga=90&ba=SF2435).  


### Finding Information:  
* The Iowa Legislature [https://www.legis.iowa.gov/](https://www.legis.iowa.gov/)  
* Searching for what Iowa Legislators filed: [https://www.legis.iowa.gov/publications/search](https://www.legis.iowa.gov/publications/search)  
* Legiscan IA [https://legiscan.com/IA](https://legiscan.com/IA)  
* Iowa Data Center [https://www.iowadatacenter.org/index.php/quick-facts/iowa-quick-facts](https://www.iowadatacenter.org/index.php/quick-facts/iowa-quick-facts)  


### Other:  
* "the four biggest oil companies — Exxon Mobile, Shell, Chevron, and Total Energies — have made over $330 billion in profits in just the past three years." [By Jonas Magram, DMR, 2024-03-10, page F3](https://desmoinesregister-ia.newsmemory.com?selDate=20240310&goTo=F003&artid=2&editionStart=Des%20Moines%20Register)  
* "Tuition alone at Iowa State University has risen 236% since 2001; inflation in that period is 73%. Iowa students have some of the worst loan debt burdens in the nation." [By Lucas Grundmeier, DMR, 2024-03-10, page F1](https://desmoinesregister-ia.newsmemory.com?selDate=20240310&goTo=F001&artid=2&editionStart=Des%20Moines%20Register)  
* Since 2001, the Federal Crop Insurance Program’s "total payments to Iowa farmers have grown by over 630%, from about $3 billion a year to over $19 billion in 2022." [By Jonas Magram, DMR, 2024-03-10, page F3](https://desmoinesregister-ia.newsmemory.com?selDate=20240310&goTo=F003&artid=2&editionStart=Des%20Moines%20Register)  
