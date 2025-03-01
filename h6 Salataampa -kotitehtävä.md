# h6 - Salataampa 

## Raportti kotitehtävistä.  

**Tehtävänannot:  
(https://terokarvinen.com/linux-palvelimet/#h6-salataampa)

## Sisällys  

x) Tiivistelmät  
Let's Encrypt 2024: How It Works  
Lange 2024: Lego: Obtain a Certificate: Using an existing, running web server  
The Apache Software Foundation 2025: Apache HTTP Server Version 2.4 [Official]  
Documentation: SSL/TLS Strong Encryption: How-To: Basic Configuration Example  
a) Let's. Hanki ja asenna palvelimellesi ilmainen TLS-sertifikaatti Let's Encryptilta. Osoita, että se toimii.  
b) A-rating. Testaa oma sivusi TLS jollain yleisellä laadunvarmistustyökalulla, esim. SSLLabs (Käytä vain tavanomaisia tarkistustyökaluja, ei tunkeutumistestausta eikä siihen liittyviä työkaluja)
c) Vapaaehtoinen: Tee weppilomake, jossa on käyttäjätunnus ja salasana. Käytä salaamatonta http-yhteyttä.  
Sieppaa liikennettä (esim. Wireshark, ngrep). Mitä havaitset? Mitä vaikutuksia tällä on tietoturvaan?  

## Raportti  
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

## x) Tiivistelmät  

**Let's Encrypt 2024: How It Works**  

Tarkoituksena hankkia varmenne HTTPS-palvelimen luomiseksi automaattisesti.  
- Palvelu Let`s Encrypt tunnistaa palvelimen ylläpitäjän julkisen avaimen avulla.  
- Agentti luo avainparin ja todistaa hallitsevansa sivustoa DNS-tietueella tai HTTPS- 
 tiedostolla. Tämän jälkee CA tarkistaa ja hyväksyy validoinnin.  
- Agentti voi pyytää, uusia ja peruuttaa varmenteita valtuutetulla avainparilla. CA tarkistaa ja myöntää varmenteet, jotka tallennetaan CT-lokeihin.  
- Agentti lähettää peruutuspyynnön, CA merkitsee varmenteen peruutetuksi ja julkaisee tiedon OCSP-palveluun.  

**Agentti** = Ohjelmisto, joka hallinnoi varmenteita palvelimella.  
Se todistaa domainin hallinnan, pyytää, uusii ja peruuttaa varmenteita (esim. Certbot).  

**CA (Certificate Authority)** = Varmentajaorganisaatio, joka myöntää, tarkistaa ja peruuttaa varmenteita.  
Let's Encrypt on yksi CA.  

**CT (Certificate Transparency)** = Julkinen lokijärjestelmä, johon varmenteet tallennetaan.  
Se lisää läpinäkyvyyttä ja estää luvattomia varmenteita.  

**OCSP (Online Certificate Status Protocol)** = Protokolla, jolla selaimet ja muut järjestelmät tarkistavat, onko  varmenne peruutettu.  

**Lange 2024: Lego: Obtain a Certificate: Using an existing, running web server**  

**Varmenne web-palvelimen kautta**: Komento = **lego --email="you@example.com" --domains="example.com" --http run**, varmenteet tallennetaan .lego-kansioon.  

**DNS-palveluntarjoajan kautta**: Jos web-palvelinta ei voi käyttää, varmennus onnistuu DNS-palvelun avulla (esim. 
 Gandi: lego --dns gandi).  

Usean SOA-alueen tapauksessa: Määritä ulkoinen nimipalvelin **--dns.resolvers-parametrilla**.  

Olemassa olevan CSR:n käyttö: Jos sinulla on jo CSR, voit käyttää sitä --csr-valitsimella.

Olemassa olevan web-palvelimen kanssa: Määritä --http.webroot, jotta varmennuksen haaste tallennetaan oikeaan  hakemistoon.  

Skriptin suorittaminen varmenteen hankinnan jälkeen: Käytä --run-hook="./myscript.sh" automatisoimaan sertifikaatin 
 asennus muille palveluille (esim. Postfixille).  

## a) Ilmaisen TLS-sertifikaatin asentaminen Let's Encryptilta  

Aloitin tehtävän lukemalla Tero Karvisen tekemää tehtävänantoa.  

- Potkaise demonia = ok  
- kokeile, että weppisivut toimivat = ok  
  
  Komento: **Sudo apt-get install lego**  

Legon asentamisen jälkeen katselin pitkää lego-komentoa ja huomasin siinä olevat kohdat, jotka tulisi vaihtaa omaan   palvelimeeni sopiviksi.  
  
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

- ota sertifikaatti käyttöön name based virtual host -asetuksissa (esimerkki alla). Muista potkaista demonia.  

 <img width="509" alt="image" src="https://github.com/user-attachments/assets/cefa51ed-78be-4be8-a831-501bf1a22f37" />  

- sudo a2ensite joonalindholm.me.conf = OK  
- sudo a2enmod ssl = OK  
- sudo apache2ctl configtest = OK  
- tee reikä muuriin, 443/tcp = OK  

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

## b) SSLabs  
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
Vanhentuneet ja vähemmän turvalliset selaimet ja käyttöjärjestelmät eivät pääse sivustolleni.  

Palvelimeltani puuttuu myös DNS CAA, joka valvoo, että vain tietyt varmentajat saavat antaa sertifikaatin.  
Tämä estää vääriä sertifikaatteja. Tämä olisi varmasti hyvä joskus päivittää.  

## c) http-weppilomake, jossa on käyttäjätunnus ja salasana sekä liikenteen sieppaus.  



**Lähdeluettelo**  

https://letsencrypt.org/how-it-works/  
https://go-acme.github.io/lego/usage/cli/obtain-a-certificate/index.html#using-an-existing-running-web-server  
https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html#configexample  
https://httpd.apache.org/docs/2.4/mod/mod_alias.html#redirect
https://www.ssllabs.com/ssltest/
https://blog.ise.io/blog/the-dangers-of-cbc-mode



