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

    ./ffuf -w common.txt -u http://127.0.0.2:8000/FUZZ # näyttää kaikki
    
    ./ffuf -w common.txt -u http://127.0.0.2:8000/FUZZ -fs 154 # poistaa 154 kokoiset paketit


![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/d105d0fc-9b10-4785-ab69-bd72c9e2810a)

fuzzauksessa tuli .git ja wp-admin esiin testasin ne URL ja löytyi:


![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/f10c79e8-771d-4dd8-a1ad-6838b3de33aa)


![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/3c03c223-423e-4909-975e-16fa0156baa8)

## c) Asenna John the Ripper ja testaa sen toiminta murtamalla jonkin esimerkkitiedoston salasana.

Aloitin tehtävän käyttäen teron ohjeita John the ripperistä

komentoja joita käytin:

    sudo apt-get update # päivittää paketit
    sudo apt-get -y install micro bash-completion git build-essential libssl-dev zlib1g zlib1g-dev zlib-gst libbz2-1.0 libbz2-dev atool zip wget # lataa työkalut joita tarvitsee
    git clone --depth=1 https://github.com/openwall/john.git # cloonaa gitin
    cd john/src/ # siirtyy hakemistoon
    ./configure # ( en ole varma) 
    wget https://TeroKarvinen.com/2023/crack-file-password-with-john/tero.zip # otaa teron zipin netistä
    unzip tero.zip # unzippaa teron tiedoston
    zip2john tero.zip >tero.zip.hash # exractaa paketin uuteen tiedostoon zip hashhiin
    john tero.zip.hash # john työstää tiedostoa
    cat secretFiles/SECRET.md # cat katsoo tulostaa filen sisällön
    

kloonasin gitin:


![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/676f14a9-b87a-442a-a1a6-79aeeca1e5fa)

menin john/src osioon ja conffasin sen:


![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/2bacbecd-d102-451a-85d6-6d683a2f241f)


latasin teron zippi tiedoston


![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/9c12629b-94a5-4319-9935-1969b6fe443f)

yritin unzipata sen ja se kysy salasanaa jota minulla ei ollut 



![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/bcb845ed-9e7d-4dfa-81e7-d5313459a18c)

käytin johnia joka antoi salasanan butterfly : 



![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/c869375c-595f-46c5-a291-f42f91cd8a7e)

unzippasin uudestaan salasanalla butterfly ja catti comennolla katsoin SECRET.md

You've found the secret, well done!

You have now completed the tutorial. 

Did you know that Jumbo John can handle many other file formats, too [1]?

[1] https://TeroKarvinen.com/2023/crack-file-password-with-john/



![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/9f49741e-25ab-417a-996c-d8956696cc10)


  
## d) Fuffme. Asenna Ffufme harjoitusmaali paikallisesti omalle koneellesi. Ratkaise tehtävät (kaikki paitsi ei "Content Discovery - Pipes")


- Aloitin tekemään content discovery – basic
![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/07238012-6985-42c7-bde1-50bafcf8e4db)

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/2ff5c3f4-7a88-477a-9baa-7b8b31869c0c)

 
Löysin 2 poikkeavaa tiedostoa class ja development.log

- Content Discovery With Recursion
  
 ![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/cc4dbdde-3e89-41b0-a9f2-9f9d15697ee5)


Tästä osioista löysyin 3 eri poikkeavaa tiedostoa admin, admin/users ja /admin/users/96

- Content Discovery With File Extensions
 
![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/83ac3f84-8891-4151-a00e-9b2354d4bea3)

Tästä osiosta löytyi users.log

- No 404 Status
 

tässä osiossa löytyi secret
![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/9ed46106-dcd1-445a-9bff-0ef5abbfce38)


- Param Mining
 
![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/4134ec48-8993-46f8-a00a-0471d7401f6a)

tässä osiossa löytyi debug


- Rate Limited

Tässä osiossa testasin molemmat mutta timeout oli liian pitkä ja tässä olisi kestänyt ikuisuus joten siirryin seuraavaan osioon.

- Subdomains - Virtual Host Enumeration

tässä osiossa hain kaikki ensin ja sitten filtteröin kaikki 1495 pois ja sain 
 
![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/04b2b1ff-515d-4a04-950d-efb4c08e07f9)




## e) Tee msfvenom-työkalulla haittaohjelma, joka soittaa kotiin (reverse shell). Ota yhteys vastaan metasploitin multi/handler -työkalulla.
Haittaohjelma ei saa olla automaattisesti leviävä. Msfvenom tekee tunnilla opetelluilla asetuksilla ohjelman, joka avaa reverse shellin, kun sen ajaa, mutta joka ei leviä eikä tee muutenkaan mitään itsestään.
Raporttiin riittävät pelkät komennot haitakkeen tekemiseen, itse binääriä ei ole pakko laittaa verkkoon. Mikäli laitat binäärin verkkoon, pakkaa se salakirjoitettuun zip-pakettiin ja laita salasanaksi "infected". 
Latauslinkin yhteydessä on oltava selkeä varoitus siitä, että binääriä ei tule ajaa oikeilla koneilla. Salasanan voit halutessasi kertoa varoitusten yhteydessä.

## f) Asenna Windows virtuaalikoneeseen. Voi olla esimerkiksi Metasploitable 3 tai Microsoftin sivuilta saatava ilmainen kokeiluversio.

Aloitin asentamalla iso tiedostoa 

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/566d24b0-5368-4875-a180-92da8b16dcb9)

avasin tiedoston virtualboxissa ja asensin sen siihen.

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/f0cc96a6-1f43-4379-8227-31965e088911)

kuva työpöydältä:

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/bd7e2acf-11a6-4322-8c9e-1f94b5432b18)



## g) Ota Windowsiin graafinen etähallintayhteys Linuxista. Käytä RDP:tä eli Remote Desktop Protocol.

aloitin lataamalla reminan kalille:

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/2b8f480e-b664-4770-b39b-958b6f6c9d82)


Syötin koneen ip osoitteen Quick Connectiin ja pääsin koneelle.

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/30a9c2b5-620e-4a9f-bde2-0a52dbd04b6f)


# References
https://www.microsoft.com/en-us/software-download/windows10
https://terokarvinen.com/2024/eettinen-hakkerointi-2024/
https://terokarvinen.com/2023/fuzz-urls-find-hidden-directories/
https://terokarvinen.com/2022/cracking-passwords-with-hashcat/
https://terokarvinen.com/2023/crack-file-password-with-john/
