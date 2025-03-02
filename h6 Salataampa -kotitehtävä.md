# h6 - Salataampa 

### Raportti h6-kotitehtävistä  

**Tehtävänannot:**  

(https://terokarvinen.com/linux-palvelimet/#h6-salataampa)

### Sisällysluettelo  

**x) Let's Encrypt 2024: How It Works**  

**x) Lange 2024: Lego: Obtain a Certificate: Using an existing, running web server  
The Apache Software Foundation 2025: Apache HTTP Server Version 2.4 [Official]**  

**x) Documentation: SSL/TLS Strong Encryption: How-To: Basic Configuration Example**  

**a) Let's. Hanki ja asenna palvelimellesi ilmainen TLS-sertifikaatti Let's Encryptilta. Osoita, että se toimii.**  

**b) A-rating. Testaa oma sivusi TLS jollain yleisellä laadunvarmistustyökalulla, esim. SSLLabs (Käytä vain tavanomaisia tarkistustyökaluja, ei tunkeutumistestausta eikä siihen liittyviä työkaluja)**  

**c) Vapaaehtoinen: Tee weppilomake, jossa on käyttäjätunnus ja salasana. Käytä salaamatonta http-yhteyttä.  
Sieppaa liikennettä (esim. Wireshark, ngrep). Mitä havaitset? Mitä vaikutuksia tällä on tietoturvaan?**  

---

### x) Tiivistelmät  

### Let's Encrypt 2024: How It Works  

Tarkoituksena hankkia varmenne HTTPS-palvelimen luomiseksi automaattisesti.  
- Palvelu Let`s Encrypt tunnistaa palvelimen ylläpitäjän julkisen avaimen avulla.  
- Agentti luo avainparin ja todistaa hallitsevansa sivustoa DNS-tietueella tai HTTPS- 
 tiedostolla. Tämän jälkee CA tarkistaa ja hyväksyy validoinnin.  
- Agentti voi pyytää, uusia ja peruuttaa varmenteita valtuutetulla avainparilla. CA tarkistaa ja myöntää varmenteet, jotka tallennetaan CT-lokeihin.  
- Agentti lähettää peruutuspyynnön, CA merkitsee varmenteen peruutetuksi ja julkaisee tiedon OCSP-palveluun.  

**Agentti** = Ohjelmisto, joka hallinnoi varmenteita palvelimella.  
Se todistaa domainin hallinnan, pyytää, uusii ja peruuttaa varmenteita (esim. Certbot tai lego).  

**CA (Certificate Authority)** = Varmentajaorganisaatio, joka myöntää, tarkistaa ja peruuttaa varmenteita.  
Let's Encrypt on yksi CA.  

**CT (Certificate Transparency)** = Julkinen lokijärjestelmä, johon varmenteet tallennetaan.  
Se lisää läpinäkyvyyttä ja estää luvattomia varmenteita.  

**OCSP (Online Certificate Status Protocol)** = Protokolla, jolla selaimet ja muut järjestelmät tarkistavat, onko  varmenne peruutettu.  

---

### Lange 2024: Lego: Obtain a Certificate: Using an existing, running web server  

Sertifikaatti luodaan komennolla (Tiedot korvataan omilla)  

lego --email="you@example.com" --domains="example.com" --http run  

Sertifikaattitiedostot sijaitsevat lego/certificates/ kansiossa:  

- example.com.crt = Palvelimen sertifikaatti (sisältää myös CA:n sertifikaatin)  
- example.com.key = Yksityinen avain  
- example.com.issuer.crt = Myöntäjän (CA) sertifikaatti. Esim. Let`s Encrypt  
- example.com.json = JSON-metatiedot  
  
Wildcard-sertifikaatit (*.example.com) tallentuvat _.example.com.crt -nimellä.  

.crt ja .key tiedostot ovat PEM-muotoisia x509-sertifikaatteja ja yksityisiä avaimia.  

---

### Documentation: SSL/TLS Strong Encryption: How-To: Basic Configuration Example  

Konfiguraatio-tiedoston pitää sisältää minimissään seuraavat kohdat:    

LoadModule ssl_module modules/mod_ssl.so  
Tämä korvattiin tehtävänannossa komennolla: **sudo a2enmod ssl**  

Konfiguraatio -esimerkki:  

<VirtualHost *:443>  
    ServerName www.example.com  
    SSLEngine on  
    SSLCertificateFile "/path/to/www.example.com.cert"  
    SSLCertificateKeyFile "/path/to/www.example.com.key"  
</VirtualHost>  

Selitykset kohdille:  
- ServerName = Määrittää verkkosivun nimen.  
- SSLEngine on = Aktivoi SSL:n.  
- SSLCertificateFile = Viittaa palvelimen sertifikaattiin.  
- SSLCertificateKeyFile = Viittaa palvelimen yksityiseen avaimeen.  

---

### Raportti kotitehtävistä  

Aloitin tehtävien suorittamisen 28.2. klo 18.  
Tein tehtäviä 28.2. - 2.3. välisenä aikana.  

**Tietokoneen resurssit:**  

- Windows 11 pro x64 -käyttöjärjestelmä  
- B550M-ITX/ac -emolevy  
- Amd Ryzen 7 5800X3D -prosessori  
- 32 gb -ram muistia  
- Noin 2 tb ssd -levytilaa  
- 3060ti 8GB GDDR6 -näytönohjain  

**VM Linuxin resurssit ja asetukset:**  

![image](https://github.com/user-attachments/assets/7990b8ca-0601-4e51-8877-15d8fc3b5325)  

---

### a) Ilmaisen TLS-sertifikaatin asentaminen Let's Encryptilta   

Aloitin tehtävän lukemalla Tero Karvisen tehtävänantoa ja vinkkejä.  

- Potkaise demonia = ok  
- kokeile, että weppisivut toimivat = ok  

Legon asennus:  
Komento: **Sudo apt-get install lego**  

Lego oli siis työkalu, joka haki varmeenteen CA:lta eli tässä tapauksessa CA oli Let`s Encrypt.  

Legon asentamisen jälkeen katselin pitkää lego-komentoa ja huomasin siinä olevat kohdat, jotka tulisi vaihtaa omaan  palvelimeeni sopiviksi.  
  
Komento:    
--server=https://acme-staging-v02.api.letsencrypt.org/directory  
--accept-tos  
--**email="ishouldchangesamplevalues@example.com"**  
--**domains="tero.example.com" --domains="www.tero.example.com"**  
--**http --http.webroot="/home/tero/public_sites/tero.example.com/"**  
--**path="/home/tero/lego/certificates/"**  
--pem  
run  

Kävin luomassa lego kansion käyttäjä-kansioon.   
Kansion luomisen jälkeen ajoin lego-komennon testiympäristössä eli staging-ympäristössä.  

Komento:  
**lego --server=https://acme-staging-v02.api.letsencrypt.org/directory \  
--accept-tos \  
--email="sähköposti" \  
--domains="joonalindholm.me" --domains="www.joonalindholm.me" \  
--http --http.webroot="/home/joona/publicsites/joonalindholm.me" \  
--path="/home/joona/lego/certificates/" \  
--pem \  
run**  
 
<img width="971" alt="image" src="https://github.com/user-attachments/assets/91e79773-ead6-49a2-82d3-8b4686cd003c"/>  
Staging meni maaliin ja sertifikaatin saaminen onnistui.  

Tämän jälkeen katsoin Teron vinkkejä ja siellä luki, että pitää poistaa testin luoma kansio.  
**--path="/home/joona/lego/certificates/" \**  
Käytin komentoa: **rm -rf certificates** lego kansiossa.  
Tämä komento poisti kansion sisältöineen.  

Tämän jälkeen olin valmis oikeaan komentoon:  

**lego   
--accept-tos \  
--email="sähköposti" \  
--domains="joonalindholm.me" --domains="www.joonalindholm.me" \  
--http --http.webroot="/home/joona/publicsites/joonalindholm.me" \  
--path="/home/joona/lego/certificates/" \  
--pem \  
run**  
  
<img width="971" alt="image" src="https://github.com/user-attachments/assets/4a3c57f4-f602-4b27-98f8-35a512d83f81" />

Sertifikaatin hakeminen onnistui.  
Katselin tehtävänantoa ja noudatin vinkkejä.  

Tehtävänannossa luki: "ota sertifikaatti käyttöön name based virtual host -asetuksissa (esimerkki alla). Muista potkaista demonia."  

 <img width="509" alt="image" src="https://github.com/user-attachments/assets/cefa51ed-78be-4be8-a831-501bf1a22f37" />  

- sudo a2ensite joonalindholm.me.conf = OK  / uusi konfiguraatio aktiiviseksi  
- sudo a2enmod ssl = OK  / SSL asetukset aktiiviseksi  
- sudo apache2ctl configtest = OK  / Palvelimen testaus  
- tee reikä muuriin, 443/tcp = OK  / Reikä palomuuriin HTTPS-yhteydelle  

https://www.joonalindholm.me toimi ja sivu oli suojattu.  
Alisivut eivät kuitenkaan olleet suojattuja, vaan avautuivat perus http-versioina.  

Lähdin googlailemaan ongelmaa ja lopulta päädyin apache2 omaan ohjeeseen osoitteessa:  

https://httpd.apache.org/docs/2.4/mod/mod_alias.html#redirect  

Sivulta löytyi ohjeet redirect riville konfiguraatio-tiedostoon.  

<img width="472" alt="image" src="https://github.com/user-attachments/assets/29bb208d-773f-4a22-8935-795e6a44c604" />  

Korjasin konfiguraation ja ajoin komennot uudestaan.  
**sudo a2ensite joonalindholm.me.conf**  
**sudo systemctl restart apache2**  
Nyt sivuni toimivat oikein.  

<img width="356" alt="image" src="https://github.com/user-attachments/assets/3b8a1a46-81e8-40b7-8d5b-14871840f2bb" />  

<img width="443" alt="image" src="https://github.com/user-attachments/assets/c899c275-9e39-4668-b190-938b3dc3daac" />  

<img width="438" alt="image" src="https://github.com/user-attachments/assets/6aa83dc1-ee5b-4436-9dfd-133c9173164f" />  

<img width="240" alt="image" src="https://github.com/user-attachments/assets/dea8c989-7ca5-4161-b734-838735e528b9" />  

---

### b) SSLabs  
Tehtävässä piti testata sivut TLS laadunvarmistustyökalulla.  
Käytin tehtävänannon työkalua SSLLabs.  
**(https://www.ssllabs.com/ssltest/)**  

Laitoin osoitteeni Hostname kenttään.  

<img width="664" alt="image" src="https://github.com/user-attachments/assets/43dd368b-e7ab-4cd9-9971-3f4bdc8f87b5" />  

Testissä meni noin minuutti tai kaksi ja lopulta avautui tulokset.  

<img width="812" alt="image" src="https://github.com/user-attachments/assets/72fe0bd3-111c-4621-8454-929168bf8aef" />  

Tulokset vaikuttivat hyviltä. Sivua alaspäin skrollatessa sai nähdä tarkempia tietoja.  
Keräsin kaikki kohdat, jotka eivät vaikuttaneet hyviltä, vaikka arvosana sivulle olikin "A".  

<img width="666" alt="image" src="https://github.com/user-attachments/assets/369d133a-d176-45d4-9f14-d40faf4ef030" />  

<img width="344" alt="image" src="https://github.com/user-attachments/assets/c5a2ccac-de1d-4379-a048-0878131a6e2b" />  

Katsellessani oransseja kohtia Cipher Suites tuloksissa huomasin, että niissä kaikissa oli CBC-moodi.  
Ilmeisesti CBC ei ole enää turvallinen vaihtoehto. CBC ei googlauksen mukaan ollut hyvä padding oracle hyökkäystä kohtaan, jossa käytetään salauksen virheitä CBC-moodia vastaan.  

**https://blog.ise.io/blog/the-dangers-of-cbc-mode**  

Sivuni ei ole myöskään yhteensopiva windows xp:n ja chrome 49 kanssa. Tämä on varmaankin hyvä asia turvallisuuden kannalta.  
Vanhentuneet ja vähemmän turvalliset selaimet ja käyttöjärjestelmät eivät siis pääse sivustolleni, koska handshake ei onnistu.    

Palvelimeltani puuttuu myös DNS CAA, joka valvoo, että vain tietyt varmentajat saavat antaa sertifikaatin.  
Tämä estää vääriä sertifikaatteja. Tämä olisi varmasti hyvä joskus päivittää, mutta jos käyttää Let`s Encryptiä niin onko se tarpeen.  

---

### c) http-weppilomake, jossa on käyttäjätunnus ja salasana sekä liikenteen sieppaus.  

Aloitin tehtävän 2.3.2025 klo 10:30.  
Tehtäväni oli luoda weppilomake, johon kirjaudutaan käyttäjätunnuksella ja salasanalla.  
Tämän lisäksi pitäisi kaapata liikennettä ja analysoida sitä.  

Aloitin tehtävän googlailemalla, kuinka luodaan weppilomake html-rakenteeseen.  
Päädyin sivulle:  
**https://genuineproductdigital.medium.com/how-to-build-a-login-page-using-html-a-step-by-step-guide-9654b4c279d2**  

Kopioin sivun rakenteen oman etusivuni html-tiedostoon.  

<img width="479" alt="image" src="https://github.com/user-attachments/assets/c2ec7163-8852-4cd1-80cf-a08ac593b7b4" />  

Päätin kokeilla tehtävänannossa mainittua ngrep-ohjelmaa verkkoliikenteen tutkimiseen.    
Komento: **sudo apt-get install ngrep**  

Seuraavaksi minun piti saada konfiguroitua sivuni takaisin http-muotoon.  
Tallensin https-konfiguraationi notepadiin, että voin myöhemmin palauttaa sen takaisin.  

- Poistin kaikki redirect rivit  
- Tein komennot sudo a2ensite joonalindholm.me.conf, sudo systemctl restart apache2  
- Menin puhelimella sivuilleni. Sivut olivat taas not secure.  

Http-säätöjen jälkeen aloin tutkimaan kuinka ngrep toimii.
Löysin googlaamalla sivun:  
**https://www.geeksforgeeks.org/ngrep-network-packet-analyzer-for-linux/**

Kokeilin ohjeessa esiintyvää komentoa: **sudo ngrep port 80**  
Eli halusin kuunnella porttia 80, jota http-protokolla käyttää.  

Tämän jälkeen odottelin jonkun aikaa kunnes kokeilin itse luoda toimintaa porttiin 80.  
Kirjoittelin jotain siansaksaa käyttäjänimeeni ja salasanaani, jolloin huomasin, että nämä tiedot olivat selvästi luettavissa ngrepissa.  

Kokeilin seuraavia tietoja:  
testikayttaja
testisalasana

<img width="644" alt="image" src="https://github.com/user-attachments/assets/01b27fe3-a1f9-4f99-9dc1-f40c9d85929e" />  

Kokeilin samaa https-sivuilla testiksi.  
Korjasin konfiguraationi takaisin https-muotoon.  

Komento: **sudo ngrep port 443**  

<img width="647" alt="image" src="https://github.com/user-attachments/assets/104b64ff-f9f6-487f-9bab-601fe29eaf6a" />

Kaikki tiedot olivat salattuja.

Eli, jos hyökkääjä pääsisi verkkooni, se voisi kaapata kirjautumistietoni, jos sivuni olisivat http-muodossa.  
Hyökkäyksiä, joille olisin haavoittuvainen: Man In The Middle, ARP-spoofing ja pakettien sniffaus esimerkiksi ngrepillä.  

**ARP-spoofing**: Hyökkääjä huijaa verkon laitteita, että hänen MAC-osoitteensa kuuluu reitittimelle. Tämän avulla liikenne kulkee hyökkääjän kautta.    
**Man-in-the-Middle**: Hyökkääjä menee käyttäjän ja palvelimen väliin. Näin hän voi lukea tai muokata salaamatonta liikennettä.  
**Pakettien sniffaus**: Ohjelmat (esim. ngrep, tcpdump ja Wireshark) mahdollistavat verkon liikenteen seuraamisen ja arkaluonteisten tietojen etsimisen.  

---

**Lähdeluettelo**  

Let`s Encryptin esittely  
https://letsencrypt.org/how-it-works/  

Sertifikaatti -ohjeet  
https://go-acme.github.io/lego/usage/cli/obtain-a-certificate/index.html#using-an-existing-running-web-server  

SSL konfiguraatio -ohjeet  
https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html#configexample  

Http -> Https redirect -ohjeet
https://httpd.apache.org/docs/2.4/mod/mod_alias.html#redirect  

SSLLabsin ssl -testi  
https://www.ssllabs.com/ssltest/  

CBC -moodin ongelmat  
https://blog.ise.io/blog/the-dangers-of-cbc-mode  

Ngrep -ohjeet  
https://www.geeksforgeeks.org/ngrep-network-packet-analyzer-for-linux/  

