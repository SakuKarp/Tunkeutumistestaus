x) Lue/katso ja tiivistä. 

Avoimet portit: Sovellukset ovat aktiivisia vastaanottamaan yhteyksiä
Suljetut portit: Saavutettavissa, mutta ei kuuntele sovellusta
Suodatetut portit: Pakettisuodatus estää Nmapin paketit
Unfiltered: Portti on saavutettavissa, mutta tilaa ei voi määrittää
Open|Filtered: Nmap ei voi varmasti sanoa, onko portti avoin/suodatettu
Closed|Filtered: Nmap ei voi varmasti sanoa, onko portti suljettu/suodatettu

-sS: SYN-skannaus, jossa skanneri lähettää SYN-paketteja määritellyille porteille. Vastauksen perusteella se voi päätellä portin tilan.
-sT: TCP Connect -skannaus, jossa skanneri yrittää muodostaa oikean TCP-yhteyden tarkasteltavalle portille. Jos yhteys onnistuu, portti on avoin, muuten suljettu.
-sU: UDP-skannaus, jossa skanneri lähettää UDP-paketteja määritellyille porteille. UDP-portit eivät välttämättä vastaa, joten tämä skannaus voi olla hidas ja epäluotettava.



a) Asenna Kali virtuaalikoneeseen



b) Asenna Metasploitable 2 virtuaalikoneeseen

c) Tee koneille virtuaaliverkko, jossa Kalin ja Metasploitablen välillä on host-only network, niin että porttiskannatessa ym. koneet on eristetty intenetistä, mutta ne saavat yhteyden toisiinsa 
Osoita eri komennoilla, että Internet-yhteys katkeaa: 'ping 1.1.1.1', 'ping www.google.com', 'curl www.google.com'
Vapaaehtoisena lisänä: Kali saa yhteyden Internettiin, mutta sen voi laittaa pois päältä.

d) Etsi Metasploitable porttiskannaamalla (db_nmap -sn). Tarkista selaimella, että löysit oikean IP:n - Metasploitablen weppipalvelimen etusivulla lukee Metasploitable. Katso, ettei skannauspaketteja vuoda Internetiin - kannattaa irrottaa koneet netistä skannatessa. Seuraa liikennettä snifferillä.

e) Porttiskannaa Metasploitable huolellisesti (db_nmap -A -p0-). Analysoi tulos. Kerro myös ammatillinen mielipiteesi (uusi, vanha, tavallinen, erikoinen), jos jokin herättää ajatuksia. Seuraa liikennettä snifferillä.

f) Tallenna portiskannauksen tulos tiedostoon käyttäen nmap:n omaa tallennusta (nmap -oA foo).

g) Tallenna shell-sessio tekstitiedostoon script-työkalulla (script -fa log001.txt)

h) Etsi kaikki maininnat jostain osoitteesta, palvelusta tai vastaavasta kaikista tallennetuista tuloksista ja lokeista (grep -ir tero).

i) Anna esimerkit nmap ajonaikaisista toiminnosta. (man nmap: runtime interaction)
