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
Tämä on siis muistelu edellisistä kotitehtävistäni.  

***

Tehtävä e
https://github.com/JoonaLindholm/linux-palvelimet/blob/main/h4%20-%20Maailma%20kuulee.md  

Aloitin tämän tehtävän 9.2.2025. Alkaen noin klo 10 aamulla.  

Tämän jälkeen lähdin tutkimaan Name Based Virtual Hostia github educationista.
Sieltä löysin Namecheap kupongin, jolla saisin domain nimen vuodeksi veloituksetta.
image

image image
Etsin omalla nimelläni sopivan domainin ja painoin "ADD" -> "Confirm Order"

Tämän jälkeen liitin viel github käyttäjäni namecheapin käyttäjään.

image image
Kirjauduin sisään tililleni ja aktivoin tilini sähköpostin kautta.

image image
Jatkoin nimipalvelimen muokkausta Susanna Lehdon raportin mukaan ja lisäsin advanced DNS asetuksiin virtuaalipalvelimen ip-osoitteen.

Postin myös vanhat recordit.

image
Kävin kokeilemassa onko DNS päivittynyt ja näkyykö sivulla "Hello world" -teksti.

image
Kaikki toimi hyvin. DNS muutokset eivät tapahtuneet heti.

Seuraavaksi tein käyttäjälleni kansioita ja tiedostoja, jotta voin muokata sivua ilman sudo komentoa.
Navigoin kotikansiooni ja loin sinne kansion publicsites, johon loin vielä kansion joonalindholm.me.
Komento: mkdir publicsites
Komennot: cd publicsites ja mkdir joonalindholm.me

Tämän jälkeen loin kansioon joonalindholm.me, tiedoston index.html komennolla:
micro index.html

Tämä avasi tekstieditorin, jolla lisäsin html rakennetta tiedostoon.

image
Tämän jälkeen kävin muokkaamassa konfiguraatio-tiedostoa komennolla:
sudo nano /etc/apache2/sites-available/joonalindholm.me.conf

Lisäsin sinne rivit:

image
Tallensin tekstini ctrl-s näppäinyhdistelmällä ja poistuin editorista.
Seuraavaksi otin sivun käyttöön komennoilla:

sudo a2ensite joonalindholm.me.conf
sudo systemctl restart apache2

Nämä komennot kopioivat konfiguraatio-tiedostoni sites-enabled kansioon ja käynnistivät apachen uudelleen.

image
Olin nyt siis tehnyt kansiot ja konfiguroinut asetukset tiedostojen nimien ja polkujen mukaan.
Sivu ei kuitenkaan näkynyt selaimessa. Olin ilmeisesti unohtanut jotakin.
Menin error.logiin katsomaan, mitä erroreita sinne ilmestyy, kun yritän päästä sivulle.

Komento:
sudo tail -f /var/log/apache2/error.log

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

image
En halunnut muokata sivuja enempää, kun en ollut varma, mitä kurssilla tehdään seuraavaksi.
Sivuista voisi tehdä tulevaisuudessa vaikka kotisivut.




