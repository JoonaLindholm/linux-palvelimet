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

## Tiivistelmät  

**Let's Encrypt 2024: How It Works**  

Tarkoituksena hankkia varmenne HTTPS-palvelimen luomiseksi automaattisesti.  
- Palvelu Let`s Encrypt tunnistaa palvelimen ylläpitäjän julkisen avaimen avulla.  
- Agentti luo avainparin ja todistaa hallitsevansa sivustoa DNS-tietueella tai HTTPS- 
 tiedostolla. Tämän jälkee CA tarkistaa ja hyväksyy validoinnin.  
- Agentti voi pyytää, uusia ja peruuttaa varmenteita valtuutetulla avainparilla. CA tarkistaa ja myöntää varmenteet, jotka tallennetaan CT-lokeihin.
- Agentti lähettää peruutuspyynnön, CA merkitsee varmenteen peruutetuksi ja julkaisee tiedon OCSP-palveluun.

**Agentti** = Ohjelmisto, joka hallinnoi varmenteita palvelimella. Se todistaa domainin hallinnan, pyytää, uusii ja peruuttaa varmenteita (esim. Certbot).  

**CA (Certificate Authority)** = Varmentajaorganisaatio, joka myöntää, tarkistaa ja peruuttaa varmenteita. Let's Encrypt on yksi CA.  

**CT (Certificate Transparency)** = Julkinen lokijärjestelmä, johon varmenteet tallennetaan. Se lisää läpinäkyvyyttä ja estää luvattomia varmenteita.  

**OCSP (Online Certificate Status Protocol)** = Protokolla, jolla selaimet ja muut järjestelmät tarkistavat, onko varmenne peruutettu.  

**Lange 2024: Lego: Obtain a Certificate: Using an existing, running web server**  

**Varmenne web-palvelimen kautta**: Komento = **lego --email="you@example.com" --domains="example.com" --http run**, varmenteet tallennetaan .lego-kansioon.

**DNS-palveluntarjoajan kautta**: Jos web-palvelinta ei voi käyttää, varmennus onnistuu DNS-palvelun avulla (esim. Gandi: lego --dns gandi).

Usean SOA-alueen tapauksessa: Määritä ulkoinen nimipalvelin **--dns.resolvers-parametrilla**.

Olemassa olevan CSR:n käyttö: Jos sinulla on jo CSR, voit käyttää sitä --csr-valitsimella.

Olemassa olevan web-palvelimen kanssa: Määritä --http.webroot, jotta varmennuksen haaste tallennetaan oikeaan hakemistoon.

Skriptin suorittaminen varmenteen hankinnan jälkeen: Käytä --run-hook="./myscript.sh" automatisoimaan sertifikaatin asennus muille palveluille (esim. Postfixille).

**Lähdeluettelo**  

https://letsencrypt.org/how-it-works/  
https://go-acme.github.io/lego/usage/cli/obtain-a-certificate/index.html#using-an-existing-running-web-server  
https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html#configexample  




