## Selected Breach Lists  
*This is still an alpha document - no more than an idea that started with a question from a sibling.  I am not sure where it will go.*  

### Site/Domain based  
* [Have I Been Pwned (HIBP)](https://haveibeenpwned.com/) - list curated by Troy Hunt.  
* [Cloudbleed vulnerability list](https://github.com/pirate/sites-using-cloudflare) - Check the domains of any entries that appear in the Cloudbleed vulnerability list. This has potential to produce false positives due to the way this list was produced.  

### Username based  
* [Have I Been Pwned (HIBP)](https://haveibeenpwned.com/) - Check usernames against the Have I Been Pwned? list curated by [Troy Hunt](https://www.troyhunt.com/). If you will be automating this check, this service requires you to register for an API key via [https://haveibeenpwned.com/API/Key
](https://haveibeenpwned.com/API/Key), and an API key costs $3.50 US per month (Credit card required).  

### Password based  
* [Have I Been Pwned (HIBP)](https://haveibeenpwned.com/) - Another way to use a small portion of each password hash in HIBP and then check the full hash locally against the list of hashes returned by HIBP.  This is not ideal.  I would appreciate advice on a better path.  




### REFERENCES  
Andrew Schofield has a KeePass plug-in to automate this process [https://github.com/andrew-schofield/keepass2-haveibeenpwned](https://github.com/andrew-schofield/keepass2-haveibeenpwned)  