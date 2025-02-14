# h5-nimekäs  
Raportti kotitehtävistä.  

## Sisällys  

a) Nimi. Laita julkinen nimi osoittamaan omaan koneeseesi.  

b) Based. Laita Name Based Virtual Host näkymään uudessa nimessäsi. Kotisvuja pitää pystyä muokkaamaan ilman pääkäyttäjän oikeuksia.  

c) Kotisivu. Tee vähintään kolmen erillisen alasivun (esim. index.html, blog.html, projects.html)  

d) Alidomain. Tee kaksi uutta alidomainia, jotka osoittava omaan koneeseesi.  

e) Tutki jonkin nimen DNS-tietoja 'host' ja 'dig' -komennoilla.  

f) Vapaaehtoinen bonus: Aakkossalaattia sähköpostiin. Etsi palvelu, jonka DNS-tiedoissa on SPF ja DMARC.  


## Raportti  
Aloitin tehtävien suorittamisen 14.2. klo 17.  
Tein tehtäviä 14.2. - AIKA välisenä aikana.

**Tietokoneen resurssit:**  

- Windows 11 pro x64 -käyttöjärjestelmä  
- B550M-ITX/ac -emolevy  
- Amd Ryzen 7 5800X3D -prosessori  
- 32 gb -ram muistia  
- Noin 2 tb ssd -levytilaa  
- 3060ti 8GB GDDR6 -näytönohjain  

**VM Linuxin resurssit ja asetukset:**  

![image](https://github.com/user-attachments/assets/8cde2b9e-744b-4013-9fbe-b99cd7613f03)  

## a) ja b)  
**Nimi ja based**  

Olin tehnyt kotitehtävien kohdat a ja b vahingossa jo edellisissä kotitehtävissä.  
Seuraava osio jonka olen rajanuut viivalla on siis muistelu edellisistä kotitehtävistäni.  

***
**h4-Maailma kuulee**  
**Tehtävä e**  
https://github.com/JoonaLindholm/linux-palvelimet/blob/main/h4%20-%20Maailma%20kuulee.md  

Aloitin tämän tehtävän 9.2.2025. Alkaen noin klo 10 aamulla.  

Tämän jälkeen lähdin tutkimaan Name Based Virtual Hostia github educationista.
Sieltä löysin Namecheap kupongin, jolla saisin domain nimen vuodeksi veloituksetta.  

![image](https://github.com/user-attachments/assets/89cb0907-af73-434b-ae8e-fb6f340d5b03)  
  
![image](https://github.com/user-attachments/assets/2613fcc8-14aa-4894-a319-581dbd519fcb)  
  
![image](https://github.com/user-attachments/assets/a651d02a-2bf0-4fe5-ba8a-8c7be590c9ce)  

Etsin omalla nimelläni sopivan domainin ja painoin "ADD" -> "Confirm Order"  
Tämän jälkeen liitin viel github käyttäjäni namecheapin käyttäjään.  

![image](https://github.com/user-attachments/assets/d286d490-1205-467a-a828-69d37d634c04)  
  
![image](https://github.com/user-attachments/assets/554af77b-14f7-4c4b-bd87-c9105c488346)  

Kirjauduin sisään tililleni ja aktivoin tilini sähköpostin kautta.  
  
![image](https://github.com/user-attachments/assets/8b1c78c9-055e-4299-b554-889041253d39)  
  
![image](https://github.com/user-attachments/assets/6af79df7-ccbb-4064-a212-330badca6264)  
  
Jatkoin nimipalvelimen muokkausta Susanna Lehdon raportin mukaan ja lisäsin advanced DNS asetuksiin virtuaalipalvelimen ip-osoitteen.  
Postin myös vanhat recordit.  

![image](https://github.com/user-attachments/assets/36aa9f98-a317-49d5-b8d0-17081aebfd64)  

Kävin kokeilemassa onko DNS päivittynyt ja näkyykö sivulla "Hello world" -teksti.  
  
![image](https://github.com/user-attachments/assets/ec907e2f-8cbc-4aee-b968-90c6167e68ec)  
  
Kaikki toimi hyvin. DNS muutokset eivät tapahtuneet heti.  

Seuraavaksi tein käyttäjälleni kansioita ja tiedostoja, jotta voin muokata sivua ilman sudo komentoa.  
Navigoin kotikansiooni ja loin sinne kansion publicsites, johon loin vielä kansion joonalindholm.me.  
Komento: mkdir publicsites  
Komennot: cd publicsites ja mkdir joonalindholm.me  

Tämän jälkeen loin kansioon joonalindholm.me, tiedoston index.html komennolla:  
micro index.html  

Tämä avasi tekstieditorin, jolla lisäsin html rakennetta tiedostoon.    

![image](https://github.com/user-attachments/assets/ffa63d17-485c-4e6a-bcd3-6dbbb9ab6cf6)  
  
Tämän jälkeen kävin muokkaamassa konfiguraatio-tiedostoa komennolla:  
sudo nano /etc/apache2/sites-available/joonalindholm.me.conf  
  
Lisäsin sinne rivit:  

![image](https://github.com/user-attachments/assets/94f1b8c6-35e8-4ca5-9622-17cd09410fb1)  
  
Tallensin tekstini ctrl-s näppäinyhdistelmällä ja poistuin editorista.  
Seuraavaksi otin sivun käyttöön komennoilla:  
  
sudo a2ensite joonalindholm.me.conf  
sudo systemctl restart apache2  

Nämä komennot kopioivat konfiguraatio-tiedostoni sites-enabled kansioon ja käynnistivät apachen uudelleen.  

![image](https://github.com/user-attachments/assets/d585080d-2475-4a9f-8049-7e36784aa1f4)  
  
Olin nyt siis tehnyt kansiot ja konfiguroinut asetukset tiedostojen nimien ja polkujen mukaan.  
Sivu ei kuitenkaan näkynyt selaimessa. Olin ilmeisesti unohtanut jotakin.  
Menin error.logiin katsomaan, mitä erroreita sinne ilmestyy, kun yritän päästä sivulle.  
  
Komento:  
**sudo tail -f /var/log/apache2/error.log**  
  
Allaoleva lokimerkintä näkyi error lokissa, kun yritin päästä sivuilleni.  

[Sun Feb 09 10:34:39.056147 2025] [core:error] [pid 19236:tid 19246] (13)Permission denied: [client 88.114.9.199:50772] AH00035: access to / denied (filesystem path '/home/joona/publicsites') because search permissions are missing on a component of the path  

Tämä virhe muistutti minua siitä, että en ollut antanut pääsyoikeuksia apachelle ja siksi se ei päässyt käsiksi luomaani index.html tiedostoon.  
  
Tutkin asiaa googlailemalla ja lopuksi kysyin chatgpt:eeltä, että mitä oikeuksia apache2 tarkalleen tarvitsee.  
Sain vastaukseksi, että luku ja suoritus -oikeuksia kansiohin polulla, jossa index.html sijaitsee.  
Apache tarvitsee myös lukuoikeuden itse index.html tiedostoon.  

Komennot:  
sudo chmod -R 644 /home/joona/publicsites/*  
sudo chmod -R 755 /home/joona/publicsites  

Tarkennus numeroista komennoissa:  

644 = antoi oikeudet lukea tiedostoja (esim. apachelle oikeus lukea index.html tiedoston sisältö).  
755 = antoi oikeudet lukea ja suorittaa kansioita (esim. apachelle oikeus availla kansioita ja navigoida niissä).  
 
Näiden komentojen jälkeen sivuni näkyi selaimessa.  

![image](https://github.com/user-attachments/assets/b356ad1d-72bc-47be-88bf-244915f7e0a8)  
  
En halunnut muokata sivuja enempää, kun en ollut varma, mitä kurssilla tehdään seuraavaksi.  
Sivuista voisi tehdä tulevaisuudessa vaikka kotisivut.  

***




