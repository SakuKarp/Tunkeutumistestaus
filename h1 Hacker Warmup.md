# h1 Hacker Warmup


# x) Lue/katso ja tiivistä ranskalaisilla viivoilla. (Video & teksti linkattu lähteisiin)

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



# a) Ratkaise Over The Wire: Bandit kolme ensimmäistä tasoa (0-2). 

tehtävät:
https://overthewire.org/wargames/bandit/bandit0.html

Level 0-2

Otin ssh yhteyden 

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/957403f6-3867-4479-a4a0-9858770bf0e6)

Tämän jälkeen käytin komentoja

    ls
    cat readme

Löysin tiedoston ja katsoin mitä se pitää sisällään

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/c128b628-807b-4f8e-be63-f94fee7977ff)

Tämän jälkeen otin ssh yhteyden bandit1 käyttämällä salasanaa jonka löysin readme filestä

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/3889dbc1-1136-48aa-8de6-674badbab241)



![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/02cd52e6-0bf4-4383-a30b-382e47ade962)

Tein saman kirjautumalla bandit2 käyttämällä salasanaa jonka löysin - kansiosta.

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/e3a51628-d4f2-45a1-b9cd-1b35c42dd819)


![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/4a3fa42a-b94d-464d-ac75-494060068fb1)





# b) Asenna WebGoat ja kokeile, että pääset kirjautumaan sisään.

Alotin asentamalla javaa käyttäen Teron ohjeita Install Webgoat 8 - Learn Web Pentesting.

    sudo apt-get update
    sudo apt-get -y install openjdk-17-jre ufw wget bash-completion
    wget https://terokarvinen.com/2020/install-webgoat-web-pentest-practice-target/webgoat-server-8.0.0.M26.jar
    java -jar webgoat-server-8.0.0.M26.jar

Tämän jälkeen rekisteröin ja kirjauduin WebvGoattiin http://localhost:8080/WebGoat/

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/8fb2c90d-5c6e-4f1e-aaf4-9302553d5db6)


# c) Ratkaise WebGoatista tehtävät "HTTP Basics" ja "Developer tools". Katso vinkit alta.
Aloitin lisäämällä nimen


http basics tehtävät:

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/40e054b8-3ab5-4933-b78b-75a77d0db832)



Alotin avaamalla F12 dev toolin kirjoitin "GET ja POST" etsin attacking ja avasin sen Requestit

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/4e2c6ec3-64ec-441b-bf73-1b440958ed98)

Löysin sieltä vastaukset: 

magic_num "83"
Answer: "post"
magic_answer "get"

Developer tools tehtävät:

Aloitin tekemään DDeveloper Tools tehtävää ja alussa luin ohjeita ja tein mitä sivulla käskettiin. 

Testataan consolia

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/f025e347-6d7d-4f4e-ae2f-4b6b3cf2d7cb)

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/ee3bb83b-0caa-4e95-977f-57e9cdd3c138)

kutsuttiin numero käyttämällä webgoat.customjs.phoneHome()

Saatiin numero ja tehtävä läpi

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/c920c6c7-38d1-4c23-acb9-bf2e3b49b236)


Aloitin painamalla "Go" näppäintä joka lähetti pyynnön. Filen type oli network avasin sen ja request osiossa näkyi vastaus netWorkNum "98.86567958895161".


![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/b5f0e7ac-f4ff-4188-8828-2ce65e0c3ad3)

Molemmat osiot ovat tehty

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/7bdb6cb4-8f79-41bc-8ca7-b29637af8dab)



# d) Ratkaise ja selitä PortSwigger Labs: Lab: SQL injection vulnerability in WHERE clause allowing retrieval of hidden data. (Edellyttää ilmaista rekisteröitymistä. Tehtävän voi ratkaista pelkästään selaimen osoitekenttää muokkaamalla.) Selitä, mitä tekniikoita kokeilit, ja mitä hyökkäyksesi eri osat tekevät.

Aloitin kirjautumalla sisään Labiin ja aloitin tutkimaan miten tämän tehtävän voisi suorittaa. Katsoin community videot miten tämän tehävän voi ratkaistaan. 

Käytin videota https://www.youtube.com/watch?v=alTceRdSxS0 tehtävän tekemiseen joka oli Community osiossa "Intigriti" henkilön tekijältä.

Url loppu osaan categoria osiossa lisäsin +or+1=1-- ja tämä antoi kaikki tuotteet näkyville

En hirveesti itse saanut tästä tehtävästä selvää miten ja miksi nämä toimivat näin.

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/9079b327-13b0-4049-b62c-1bd4267588fd)



# e) Asenna Linux virtuaalikoneeseen. Suosittelen joko Kali (viimeisin versio) tai Debian 12-Bookworm.

Asensin koneelleni Kalin sivustolta https://www.kali.org/get-kali/#kali-virtual-machines VirtualBoxille.

Asennus oli yksinkertainen ladattiin tiedosto:

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/8ff6099c-253c-4952-a9b1-b2e67d46fa7b)

Purin tiedoston ja lisäsin VirtualBoxiin. Pääsin kirjautumaan sisään 

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/899ef2d2-7bab-42b8-806a-1b9f8cdaf609)


# f) Porttiskannaa 1000 tavallisinta tcp-porttia omasta koneestasi (localhost). Analysoi tulokset.

porttiskannasin käyttämällä

    nmap -p -1000 localhost komentoa

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/85e064d2-87be-4fa2-bf0c-8c8a68a9b816)
                                                           
Scannaus kertoo:

Start ajan

Reportin localhostista

Host on päällä

Muut osoitteet mitä ei skannattu

kaikki 1000 porttia ovat ignore tilassa

Ei näytä 1000 suljettua porttia

# g) Porttiskannaa kaikki koneesi (localhost) tcp-portit. Analysoi tulokset. (Edellisissä kohdissa mainittuja analyyseja ei tarvitse toistaa, voit vain viitata niihin ja keskittyä eroihin).

porttiskannasin käyttämällä eikä siinä näkynyt eroja

    nmap -p- localhost

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/c2bc7797-2dd1-4bb5-a8ef-cfb8eaae5ba9)



# h) Tee laaja porttiskanaus (nmap -A) omalle koneellesi (localhost), kaikki portit. Selitä, mitä -A tekee. Analysoi tulokset. (Edellisissä kohdissa mainittuja analyyseja ei tarvitse toistaa, voit vain viitata niihin ja keskittyä eroihin.).


porttiskannasin käyttämällä ja erot mitä näin oli "fingerprint" sekä "network distance". -A lisää käyttöjärjestelmän tunnistamisen, version ja reitityksen seurannan.

    nmap -A localhost

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/ef4904d1-3b5f-4576-a3f0-bd73fc4f2550)





# i) Asenna demoni tai pari (esim Apache ja SSH). Vertaile, miten localhost:n laajan porttiskannauksen tulos eroaa.

asensin apachen ja ssh käyttämällä jonka jälkeen tein porttiskannauksen Nmap -A localhost mutta mitään erikoista ei siihen tullut? en tiedä syytä. (en startannut niitä)

    sudo apt install openssh-server
    sudo apt install apache2

kuva vielä skannauksesta:

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/d9059d90-10f7-41bb-ba2c-ee9895c604ea)




# j) Kokeile ja esittele jokin avointen lähteiden tiedusteluun sopiva weppisivu tai työkalu.


Tutkin netistä erilaisia tiedusteluun sopivia websivuja ja löysin https://checkusernames.com/

Siellä voi etsiä Käyttäjänimellä millä alustoilla on samalla nimellä käyttäjiä.

Käytin haku nimeksi test123 jotta se ei keneenkään kohdistu. Kuvassa näkyy haku.

![image](https://github.com/SakuKarp/Tunkeutumistestaus/assets/148875105/d2e09a96-325f-44d8-899f-b934caeccc2f)



## references

https://checkusernames.com/

https://portswigger.net/web-security/sql-injection/lab-retrieve-hidden-data

https://www.kali.org/get-kali/#kali-virtual-machines

https://terokarvinen.com/2020/install-webgoat-web-pentest-practice-target/

https://overthewire.org/wargames/bandit/bandit0.html

https://learning.oreilly.com/videos/the-art-of/9780135767849/9780135767849-SPTT_04_00/

https://terokarvinen.com/2024/eettinen-hakkerointi-2024/
