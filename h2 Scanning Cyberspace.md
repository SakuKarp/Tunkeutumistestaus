# x) Lue/katso ja tiivistä. 

- Avoimet portit: Sovellukset ovat aktiivisia vastaanottamaan yhteyksiä

- Suljetut portit: Saavutettavissa, mutta ei kuuntele sovellusta

- Suodatetut portit: Pakettisuodatus estää Nmapin paketit

- Unfiltered: Portti on saavutettavissa, mutta tilaa ei voi määrittää

- Open|Filtered: Nmap ei voi varmasti sanoa, onko portti avoin/suodatettu

- Closed|Filtered: Nmap ei voi varmasti sanoa, onko portti suljettu/suodatettu


- -sS: SYN-skannaus, jossa skanneri lähettää SYN-paketteja määritellyille porteille. Vastauksen perusteella se voi päätellä portin tilan.

- -sT: TCP Connect -skannaus, jossa skanneri yrittää muodostaa oikean TCP-yhteyden tarkasteltavalle portille. Jos yhteys onnistuu, portti on avoin, muuten suljettu.

- -sU: UDP-skannaus, jossa skanneri lähettää UDP-paketteja määritellyille porteille. UDP-portit eivät välttämättä vastaa, joten tämä skannaus voi olla hidas ja epäluotettava.



# a) Asenna Kali virtuaalikoneeseen

Minulla oli Kali jo valmiiksi asennettu.

Asensin koneelleni Kalin sivustolta https://www.kali.org/get-kali/#kali-virtual-machines VirtualBoxille.

Asennus oli yksinkertainen ladattiin tiedosto, purin tiedoston ja lisäsin VirtualBoxiin. Pääsin kirjautumaan sisään

# b) Asenna Metasploitable 2 virtuaalikoneeseen

Aloitin etsimällä ohjeita ja löysin kyseisen ohjeen: https://www.geeksforgeeks.org/how-to-install-metasploitable-2-in-virtualbox/

Aloitin lataamalla tiedoston https://docs.rapid7.com/metasploit/metasploitable-2/ sivulta jonka jälkeen purkasin tiedoston.

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/ac481220-a0ef-4162-8d0d-519095febd4a)

Tämän jälkeen loin uuden koneen käyttäen Metasploitablea VirtualBoxissa 

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/55be5955-a62f-4521-ba1d-d82be6c9c2e0)

Käynnistin ja katsoin vielä että Login toimii

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/4fb2d2ef-b5f6-4bfc-a080-6ee56acc2cdb)

msfadminilla kirjautuminen:

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/f98fa0c5-7d5b-4542-9015-88d123b18062)



# c) Tee koneille virtuaaliverkko, jossa Kalin ja Metasploitablen välillä on host-only network, niin että porttiskannatessa ym. koneet on eristetty intenetistä, mutta ne saavat yhteyden toisiinsa  Osoita eri komennoilla, että Internet-yhteys katkeaa: 'ping 1.1.1.1'


Lisäsin molemmat Host-only verkkoon ja kirjauduin koneille sisään.

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/66669350-58a0-4d10-b0ab-2ee6c0cc852d)

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/a004d5fa-2b1e-4e91-86b3-a2863f9c9341)

Pingaus metalla ettei ole verkossa

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/462f8405-9457-413c-ba8d-0d0776c06ee6)

Pingaus kalilla ettei ole verkossa

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/2f764184-dccb-4ce2-bf97-b3dd1fbb644a)


ifconfig jolla katsoin inet addressin 

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/d2d552da-969a-4be4-9cf8-8cc4911201b1)

kalilla ip osoitteella metaan

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/0a383eab-0fb5-436a-8aa4-bb3c5723376a)


# d) Etsi Metasploitable porttiskannaamalla (db_nmap -sn). Tarkista selaimella, että löysit oikean IP:n - Metasploitablen weppipalvelimen etusivulla lukee Metasploitable. Katso, ettei skannauspaketteja vuoda Internetiin - kannattaa irrottaa koneet netistä skannatessa. Seuraa liikennettä snifferillä.

Aloitin etsimällä ohjeet db_nmapinkäyttöön ja löysin https://gist.github.com/fabionoth/ba46407d9cd03144150225715697c47f

Tämän jälkeen kun pääsin msf consoliin käytin komentoa :

    db_nmap -sn 192.168.56.101


![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/eebafde8-1722-4456-87fa-c45eb9365a99)

wireshark:

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/8249ce89-9741-4791-8527-5ce919d16fc5)






# e) Porttiskannaa Metasploitable huolellisesti (db_nmap -A -p0-). Analysoi tulos. Kerro myös ammatillinen mielipiteesi (uusi, vanha, tavallinen, erikoinen), jos jokin herättää ajatuksia. Seuraa liikennettä snifferillä.

Jatkoin tässä msf consolissa ja käytin komentoa: 

    db_nmap -A -p0- 192.168.56.101

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/dbc61d85-15ac-49c4-ac43-12768a695706)



ANALYSOIN TÄHÄN VIELÄ WIRESHARKISTA



# f) Tallenna portiskannauksen tulos tiedostoon käyttäen nmap:n omaa tallennusta (nmap -oA foo).


Tallensin tiedostot käyttäen komentoa:

    nmap -oA foo

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/3600a421-20b9-4d70-aafe-a93739f0f9eb)


# g) Tallenna shell-sessio tekstitiedostoon script-työkalulla (script -fa log001.txt)

Tallensin sen Script työkalulla

     script -fa log001.txt

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/60f77633-85ef-4a42-bec4-608eb4eed1c7)

Jonka jälkeen katsoin että se avautuu 

    micro log001.txt


![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/b0fd506c-bd15-4f52-b323-74ff80343a60)



# h) Etsi kaikki maininnat jostain osoitteesta, palvelusta tai vastaavasta kaikista tallennetuista tuloksista ja lokeista (grep -ir tero).



# i) Anna esimerkit nmap ajonaikaisista toiminnosta. (man nmap: runtime interaction)

Käytin tähän tehtävään https://nmap.org/book/man-runtime-interaction.html jossa kerrotaan hyvin mitä voi tehdä ajon aikana.

v / V
Lisää tai vähentää yksityiskohtaisuuden tasoa

d / D
Lisää tai vähentää vianjäljitystasoa

p / P
Kytkee päälle tai pois paketin jäljityksen

?
Tulosta toimintaohjeet käytön aikana

## References

https://terokarvinen.com/2024/eettinen-hakkerointi-2024/
https://gist.github.com/fabionoth/ba46407d9cd03144150225715697c47f
https://www.youtube.com/watch?v=klNl67MT1Eo
https://finlex.fi/fi/oikeus/kko/kko/2003/20030036
https://nmap.org/book/man-port-scanning-techniques.html
https://nmap.org/book/man-port-scanning-basics.html
