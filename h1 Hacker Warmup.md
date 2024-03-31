# h1 Hacker Warmup

x) Lue/katso ja tiivistä ranskalaisilla viivoilla. (Video & teksti linkattu lähteisiin)

- Port scanning : Järjestelmän tai verkon skannaaminen, avoimien porttien löyträminen ja eri hyökkäysreittien löytäminen.
- Service enumeration : kun portit on tunnistettu, niistä voi kerätä tietoa eri palveluista esim. vesriotiedostoista ja konfiguraatioista.
- vulnerability scanning : järjestelmän tai verkon skannaamminen haavoittuvuuksille esim. puuttuvat tietoturvapäivityksett tai väärät konffat
- Web service review : tällä yleensä meinataan ohjelmiston, alustan tai työkalujen arviointiin. Tarkastellaan ominaisuuksia , surituskykyä ja turvallisuutta.
- työkalut : Nmap (versatail & stable) , masscan (fastest), udpprotoscanner (fast UDP port scanner)
- Network Vulnerability scanners: OpenVas, Nessus, Nexpose, Qualys
- Web vulnerability scanners: Nikto, wpScan, SQLMap, Burp Suite, Zed attack Proxy
- Incident Response: Tapa regoida ja käsitellä eri tietoturvaepäiltyjä esim. tietomurto ja hyökkäykset organisaatioissa.
- Intrusion Detection: Prosessi jolla tunnistetaan epäilyttävä tai haitallinen toiminta verkossa tai järjestelmässä
- Intelligence: Tiedustelutieto jolla kerätään ja analysoidaan tunnistamaan uhat ja haavoittuvuudet
- Threat: mahdollinen riski tai vaara
- APT: Edistynyt ja pitkäaikainen uhka.
- Computer Network Defense: Tietoverkon "puolustus" jolla suojataan verkkoja ja järjestelmiä



a) Ratkaise Over The Wire: Bandit kolme ensimmäistä tasoa (0-2).

b) Asenna WebGoat ja kokeile, että pääset kirjautumaan sisään.

c) Ratkaise WebGoatista tehtävät "HTTP Basics" ja "Developer tools". Katso vinkit alta.

d) Ratkaise ja selitä PortSwigger Labs: Lab: SQL injection vulnerability in WHERE clause allowing retrieval of hidden data. (Edellyttää ilmaista rekisteröitymistä. 
Tehtävän voi ratkaista pelkästään selaimen osoitekenttää muokkaamalla.) Selitä, mitä tekniikoita kokeilit, ja mitä hyökkäyksesi eri osat tekevät.

e) Asenna Linux virtuaalikoneeseen. Suosittelen joko Kali (viimeisin versio) tai Debian 12-Bookworm.

f) Porttiskannaa 1000 tavallisinta tcp-porttia omasta koneestasi (localhost). Analysoi tulokset.

g) Porttiskannaa kaikki koneesi (localhost) tcp-portit. Analysoi tulokset. (Edellisissä kohdissa mainittuja analyyseja ei tarvitse toistaa, voit vain viitata niihin ja keskittyä eroihin).

h) Tee laaja porttiskanaus (nmap -A) omalle koneellesi (localhost), kaikki portit. Selitä, mitä -A tekee. Analysoi tulokset. (Edellisissä kohdissa mainittuja analyyseja ei tarvitse toistaa, voit vain viitata niihin ja keskittyä eroihin.).

i) Asenna demoni tai pari (esim Apache ja SSH). Vertaile, miten localhost:n laajan porttiskannauksen tulos eroaa.

j) Kokeile ja esittele jokin avointen lähteiden tiedusteluun sopiva weppisivu tai työkalu. 
Hyviä esimerkkejä löytyy Bazzel: IntelTechniques: Tools ja Bellingcat: Resources, voit myös käyttää muuta itse valitsemaasi työkalua. Työkalua pitää siis myös kokeilla, pelkkä nimen mainitseminen ei riitä. Pidä esimerkit harmittomina, älä julkaise kenenkään henkilökohtaisia salaisuuksia raportissasi.

#references

https://learning.oreilly.com/videos/the-art-of/9780135767849/9780135767849-SPTT_04_00/
https://terokarvinen.com/2024/eettinen-hakkerointi-2024/
