# x) Lue/katso ja tiivistä. 

Avoimet portit: Sovellukset ovat aktiivisia vastaanottamaan yhteyksiä

Suljetut portit: Saavutettavissa, mutta ei kuuntele sovellusta

Suodatetut portit: Pakettisuodatus estää Nmapin paketit

Unfiltered: Portti on saavutettavissa, mutta tilaa ei voi määrittää

Open|Filtered: Nmap ei voi varmasti sanoa, onko portti avoin/suodatettu

Closed|Filtered: Nmap ei voi varmasti sanoa, onko portti suljettu/suodatettu


-sS: SYN-skannaus, jossa skanneri lähettää SYN-paketteja määritellyille porteille. Vastauksen perusteella se voi päätellä portin tilan.

-sT: TCP Connect -skannaus, jossa skanneri yrittää muodostaa oikean TCP-yhteyden tarkasteltavalle portille. Jos yhteys onnistuu, portti on avoin, muuten suljettu.

-sU: UDP-skannaus, jossa skanneri lähettää UDP-paketteja määritellyille porteille. UDP-portit eivät välttämättä vastaa, joten tämä skannaus voi olla hidas ja epäluotettava.



# a) Asenna Kali virtuaalikoneeseen

Minulla oli Kali jo valmiiksi asennettu.

Asensin koneelleni Kalin sivustolta https://www.kali.org/get-kali/#kali-virtual-machines VirtualBoxille.

Asennus oli yksinkertainen ladattiin tiedosto, purin tiedoston ja lisäsin VirtualBoxiin. Pääsin kirjautumaan sisään

# b) Asenna Metasploitable 2 virtuaalikoneeseen

Aloitin etsimällä ohjeita ja löysisin kyseisen ohjeen: https://www.geeksforgeeks.org/how-to-install-metasploitable-2-in-virtualbox/

Aloitin lataamalla tiedoston https://docs.rapid7.com/metasploit/metasploitable-2/ sivulta jonka jälkeen purkasin tiedoston.

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/ac481220-a0ef-4162-8d0d-519095febd4a)

Tämän jälkeen loin uuden koneen käyttäen Metasploitablea VirtualBoxissa 

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/55be5955-a62f-4521-ba1d-d82be6c9c2e0)

Käynnistin ja katsoin vielä että Login toimii

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/4fb2d2ef-b5f6-4bfc-a080-6ee56acc2cdb)

msfadminilla kirjautuminen:

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/f98fa0c5-7d5b-4542-9015-88d123b18062)



# c) Tee koneille virtuaaliverkko, jossa Kalin ja Metasploitablen välillä on host-only network, niin että porttiskannatessa ym. koneet on eristetty intenetistä, mutta ne saavat yhteyden toisiinsa 
Osoita eri komennoilla, että Internet-yhteys katkeaa: 'ping 1.1.1.1', 'ping www.google.com', 'curl www.google.com'
Vapaaehtoisena lisänä: Kali saa yhteyden Internettiin, mutta sen voi laittaa pois päältä.





# d) Etsi Metasploitable porttiskannaamalla (db_nmap -sn). Tarkista selaimella, että löysit oikean IP:n - Metasploitablen weppipalvelimen etusivulla lukee Metasploitable. Katso, ettei skannauspaketteja vuoda Internetiin - kannattaa irrottaa koneet netistä skannatessa. Seuraa liikennettä snifferillä.

# e) Porttiskannaa Metasploitable huolellisesti (db_nmap -A -p0-). Analysoi tulos. Kerro myös ammatillinen mielipiteesi (uusi, vanha, tavallinen, erikoinen), jos jokin herättää ajatuksia. Seuraa liikennettä snifferillä.

# f) Tallenna portiskannauksen tulos tiedostoon käyttäen nmap:n omaa tallennusta (nmap -oA foo).

# g) Tallenna shell-sessio tekstitiedostoon script-työkalulla (script -fa log001.txt)

# h) Etsi kaikki maininnat jostain osoitteesta, palvelusta tai vastaavasta kaikista tallennetuista tuloksista ja lokeista (grep -ir tero).


# i) Anna esimerkit nmap ajonaikaisista toiminnosta. (man nmap: runtime interaction)


## References

https://finlex.fi/fi/oikeus/kko/kko/2003/20030036
https://nmap.org/book/man-port-scanning-techniques.html
https://nmap.org/book/man-port-scanning-basics.html
