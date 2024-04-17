## x) Lue/katso ja tiivistä.


Karvinen 2023: Find Hidden Web Directories - Fuzz URLs with ffuf:

- Fuff: työkalu jolla haetaan piilotettuja hakemistoja ja muita verkon resursseihin liittyviä haavoittuvuus tarkastuksia/testejä.

- Fuffin käyttö ilman internettiä

- Artikkelissa kerrotaan hyvin miten Fuff toimii automaattisesti hakemaan eri poluista. (/secret, /.svn /admin)


Karvinen 2022: Cracking Passwords with Hashcat

- Hashcat: salasanojen murtamistyökalu, jolla pystyy purkamaan eri salasanoja ja niiden hash-arvoja.

- Artikkelissa ohjeistetaan miten Hashcattiä käytetään.

- Sanakirja: tiedosto joka sisältää paljon sanoja tai eri merkkijonoja.


Karvinen 2023: Crack File Password With John

- John the ripper: Avoimen lähdekoodin salasanan murtamistyökalu

- Artikkelissa ohjeistetaan miten John the ripperiä käytetään.


## a) Asenna Hashcat ja testaa sen toiminta murtamalla esimerkkisalasana.
  
## b) Salainen, mutta ei multa. Ratkaise dirfuzt-1 artikkelista Karvinen 2023: Find Hidden Web Directories - Fuzz URLs with ffuf

## c) Asenna John the Ripper ja testaa sen toiminta murtamalla jonkin esimerkkitiedoston salasana.
  
## d) Fuffme. Asenna Ffufme harjoitusmaali paikallisesti omalle koneellesi. Ratkaise tehtävät (kaikki paitsi ei "Content Discovery - Pipes")
Basic Content Discovery
Content Discovery With Recursion
Content Discovery With File Extensions
No 404 Status
Param Mining
Rate Limited
Subdomains - Virtual Host Enumeration


## e) Tee msfvenom-työkalulla haittaohjelma, joka soittaa kotiin (reverse shell). Ota yhteys vastaan metasploitin multi/handler -työkalulla.
Haittaohjelma ei saa olla automaattisesti leviävä. Msfvenom tekee tunnilla opetelluilla asetuksilla ohjelman, joka avaa reverse shellin, kun sen ajaa, mutta joka ei leviä eikä tee muutenkaan mitään itsestään.
Raporttiin riittävät pelkät komennot haitakkeen tekemiseen, itse binääriä ei ole pakko laittaa verkkoon. Mikäli laitat binäärin verkkoon, pakkaa se salakirjoitettuun zip-pakettiin ja laita salasanaksi "infected". 
Latauslinkin yhteydessä on oltava selkeä varoitus siitä, että binääriä ei tule ajaa oikeilla koneilla. Salasanan voit halutessasi kertoa varoitusten yhteydessä.

## f) Asenna Windows virtuaalikoneeseen. Voi olla esimerkiksi Metasploitable 3 tai Microsoftin sivuilta saatava ilmainen kokeiluversio.

## g) Ota Windowsiin graafinen etähallintayhteys Linuxista. Käytä RDP:tä eli Remote Desktop Protocol.

# References
https://terokarvinen.com/2024/eettinen-hakkerointi-2024/
https://terokarvinen.com/2023/fuzz-urls-find-hidden-directories/
https://terokarvinen.com/2022/cracking-passwords-with-hashcat/
https://terokarvinen.com/2023/crack-file-password-with-john/
