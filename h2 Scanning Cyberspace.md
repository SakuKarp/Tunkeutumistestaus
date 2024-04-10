x) Lue/katso ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva kustakin artikkelista. Kannattaa lisätä myös jokin oma ajatus, idea, huomio tai kysymys.)
Lyon 2009: Nmap Network Scanning: Chapter 15. Nmap Reference Guide:
Port Scanning Basics (opettele, mitä tarkoittavat: open, closed, filtered; muuten vain silmäily)
Port Scanning Techniques (opettele, mitä ovat: -sS -sT -sU; muuten vain silmäily)
KKO 2003:36. Alaikäinen tuomittiin Osuuspankkikeskuksen porttiskannaamisesta, korkeimman oikeuden ratkaisu.
Vapaavalintainen läpikävely 0xdf tai ippsec (Kannattaa valita helppo; esim "Base Points: Easy")




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
