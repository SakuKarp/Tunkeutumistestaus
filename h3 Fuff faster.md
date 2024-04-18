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

Alotin katsomalla Teron ohjeita https://terokarvinen.com/2022/cracking-passwords-with-hashcat/ ja seurasin niitä.

Aloitin päivittämällä ja asentamalla hashcattia


    sudo apt-get update # Päivittää paikalliset paketit
    sudo apt-get -y install hashid hashcat wget # asentaa paketit
    mkdir hashed # Luo hakemiston
    cd hashed # siirtyy hakemistoon
    wget https://github.com/danielmiessler/SecLists/raw/master/Passwords/Leaked-Databases/rockyou.txt.tar.gz # lataa tiedoston Gitistä 
    tar xf rockyou.txt.tar.gz # Purkaa tiedoston
    rm rockyou.txt.tar.gz # poistaa tiedoston
    head rockyou.txt # Tulostaa rivit tiedostosta 
    wc -l rockyou.txt # rivien lukumäärä

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/5d832ee9-69d1-4849-ae38-7af1143853a7)

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/8cbe9eb1-ec38-4724-bed8-e64f7c69545c)

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/422e0893-8b5a-4d15-b706-2133cfed5314)

    hashcat --example-hashes # näyttää listan erilaisista hasheista joita voi käyttää


![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/014cd143-beed-40a6-b2d0-8294ea25b74d)

hash typen katsominen

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/49100344-bf51-45f1-82ee-519bd1be74c7)

Haetaan hashcatillä hash id:n perusteella mikä halutaan murtaa ja tehdään se omaan filuun "solved"

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/20f17b2d-344e-478a-93b3-a9335f1709b9)

    cat solved # katsotaan salasana joka murrettiin







  
## b) Salainen, mutta ei multa. Ratkaise dirfuzt-1 artikkelista Karvinen 2023: Find Hidden Web Directories - Fuzz URLs with ffuf

Aloitin tekemällä tehtävää dirfutz-0 ohjeiden mukaan.cd

seurasin ohjeita ja lopputulos oli että löysin piilotetun ardminin sivustosta

Kuva vastauksesta:

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/8581e61c-7b59-406c-8d71-f9f4f736774e)

Aloitin tekemään Tehtävän challengea dirfuz-1.

Aloitin ottamalla paketin dirfuzt-1 teron sivuilta käyttäen

    wget https://terokarvinen.com/2023/fuzz-urls-find-hidden-directories/dirfuzt-1

Annoin oikeudet ja katsoin että se on päällä:

    chmod u+z dirfuzt-1
    ./dirfuzt-1

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/57ce6fa6-eb18-475b-9c47-55edde0995c3)


![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/8f2752e7-c2f5-4ef8-b6dd-30af238efb7e)

Avasin uuden shellin ja aloitin lataamaan fuffia

    $ wget https://github.com/ffuf/ffuf/releases/download/v2.0.0/ffuf_2.0.0_linux_amd64.tar.gz # lataa    
    tar -xf ffuf_2.0.0_linux_amd64.tar.gz # purkaa
    ./ffuf 

fuffi asennettu:

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/86392fa4-6890-406c-b94e-0465281cd539)

käytin Seclists by Daniel Miessler ja katsoin että se löytyy koneeltani.


![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/9f987b13-d8ad-411e-be77-31cd1b478fde)

Netistä pois ja jatkuu:

    ./ffuf -w common.txt -u http://127.0.0.2:8000/FUZZ -fs 154


![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/d105d0fc-9b10-4785-ab69-bd72c9e2810a)

fuzzauksessa tuli .git ja wp-admin esiin testasin ne URL ja löytyi:


![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/f10c79e8-771d-4dd8-a1ad-6838b3de33aa)


![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/3c03c223-423e-4909-975e-16fa0156baa8)

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
