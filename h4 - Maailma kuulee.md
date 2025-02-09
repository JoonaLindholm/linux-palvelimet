# H4 kotitehtävät (Maailma kuulee)  

## Tehtävänannot ja raportin sisältö  

**(https://terokarvinen.com/linux-palvelimet/#h4-maailma-kuulee)**  

**x) Lue ja tiivistä  
 Susanna Lehto 2022: Teoriasta käytäntöön pilvipalvelimen avulla (h4) (opiskelijan esimerkkiraportti), kohdat  
a) Pilvipalvelimen vuokraus ja asennus  
d) Palvelin suojaan palomuurilla  
e) Kotisivut palvelimelle  
f) Palvelimen ohjelmien päivitys  
Karvinen 2012: First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS**  

**a) Vuokraa oma virtuaalipalvelin haluamaltasi palveluntarjoajalta.**  

**b) Tee alkutoimet omalla virtuaalipalvelimellasi: tulimuuri päälle, root-tunnus kiinni, ohjelmien päivitys.**  

**c) Asenna weppipalvelin omalle virtuaalipalvelimellesi.  
Korvaa testisivu. Kokeile, että se näkyy julkisesti. Kokeile myös eri koneelta, esim kännykältä.  
(Jos haluat tehdä oikeat weppisivut, tarvitset Name Based Virtual Hostin)**  

**e) Vapaaehtoinen: Laita omalle julkiselle palvelimellesi uusi Name Based Virtual Host.  
Kun sammutat muut weppisivut, niin se ainut näkyy nimestä riippumatta etusivulla.  
Name Based Virtual Host avulla pääset muokkaamaan kotisivuja normaalilla käyttäjällä, ilman sudoa.**  

# Raportti kotitehtävistä  

Aloitin tehtävien suorittamisen TÄHÄN AIKA!

Tietokoneen resurssit:  
- Windows 11 pro x64 -käyttöjärjestelmä  
- B550M-ITX/ac -emolevy  
- Amd Ryzen 7 5800X3D -prosessori  
- 32 gb -ram muistia  
- Noin 2 tb ssd -levytilaa  
- 3060ti 8GB GDDR6 -näytönohjain  

VM Linuxin resurssit ja asetukset:  
<img width="393" alt="image" src="https://github.com/user-attachments/assets/2338aa07-4497-4842-a83d-3402128cca0f" />  

## x) Tiivistelmät  

Susanna Lehto 2022: Teoriasta käytäntöön pilvipalvelimen avulla  
https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/  

**a) Pilvipalvelimen vuokraus ja asennus**  
- Valitse itsellesi sopiva pilvipalveluntarjoaja.  
- Luo käyttäjätili.  
- Määritä palvelimen asetukset omien tarpeidesi mukaan.
  Esimerkiksi sijainti ja resurssit.
  
**d) Palvelin suojaan palomuurilla**  
- Otetaan yhteys palvelimeen: ssh root@ip-osoite.  
- Annetaan palvelussa määritetty salasana.  
- Päivitetään järjestelmä: sudo apt-get update.  
- Sitten asennetaan palomuuri: sudo apt-get install ufw.  
- Tehdään reikä palomuuriin (portti 22): sudo ufw allow 22/tcp.  
- Palomuurin aktivointi: sudo ufw enable.  
  
**e) Kotisivut palvelimelle**
- Asenna Apache2-webpalvelin
- 
**f) Palvelimen ohjelmien päivitys**  
  

TÄHÄN TIIVISTELMÄ!

Karvinen 2012: First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS
https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/

## a) Virtuaalipalvelimen vuokraus  

Valitsin palveluntarjoajaksi github educationin.  
Pienen surffailun jälkeen löysin oikean paikan.  

<img width="814" alt="image" src="https://github.com/user-attachments/assets/8cf6b414-5029-4622-b903-d3e27f0a0e74" />  

<img width="324" alt="image" src="https://github.com/user-attachments/assets/d6465e63-1ca4-4b6f-846f-93da7219988c" />  

Digital Ocean ei kuitenkaan toiminut minulla ollenkaan jostain syystä. 
Koko sivu vain bugitti, kun yritin tehdä käyttäjätiliä.  
Lopulta tuli vain erroreita enkä päässyt eteenpäin joten kirjauduin ulos.  
Pankkitililtä lähti vähäksi aikaa noin 15 euroa, joka kuitenkin palautui ja kun yritin kirjautua sisään sain vaan uuden virheilmoituksen.  
Ilmeisesti onnistuin luomaan jonkinlaisen puolikkaan käyttäjätilin.  

<img width="524" alt="image" src="https://github.com/user-attachments/assets/1b351c08-8837-41a0-9a10-f86f6f5729f6" />  

Tuntui jotenkin hölmöltä alkaa tekemään tikettejä ensimmäisenä asianani tällä alustalla, joten äänestin jaloillani.  
Tunnilla käytettiin UpCloudia, joten siirryin sinne.  

**https://upcloud.com/**    

<img width="605" alt="image" src="https://github.com/user-attachments/assets/6aca59f5-7eac-4b6c-bcf6-d5a7f50dd585" />  

<img width="872" alt="image" src="https://github.com/user-attachments/assets/4141dfea-607b-453e-aaad-ef7fd6fbbc6d" />  

<img width="487" alt="image" src="https://github.com/user-attachments/assets/7212655b-2aed-45c8-b4cf-24524d13ecaf" />  

Sain tilin luotua vaivattomasti ja lisäsin tililleni 10 euroa rahaa, että sain trial-version pois päältä.  
Laitoin myös 2fa autentikoinnin päälle klikkaamalla oikeasta yläkulmasta.  

Aika tehdä palvelin.  

Klikkasin deploy now ja server.  

<img width="905" alt="image" src="https://github.com/user-attachments/assets/c789ee97-e9eb-4291-b34a-0f963d2b70ec" />  

Valitsin samat asetukset, kuin oppitunnilla eli:  

**Location = FI-HEL1**   
**Plan = Developer**    
<img width="590" alt="image" src="https://github.com/user-attachments/assets/099ba33a-6011-4fb9-8a27-435298dfdf19" />  

**Operating system**  
<img width="595" alt="image" src="https://github.com/user-attachments/assets/47e9c01a-48c7-401a-9582-20d28533f63a" />  

**Openssh asennus ja ssh-avaimen luonti**   

Komento:  
**sudo apt-get install openssh-client**  
tämän jälkeen loin ssh-avaimen komennolla:  
**ssh-keygen**  
Sitten painoin oppitunnin ohjeiden mukaan 4 kertaa entteriä.  
Tämän jälkeen navigoin kotikansiooni etsimään kansion .ssh ja tiedoston id_rsa.pub,  
jonka avasin mcro-tekstieditorilla ja kopioin sen sisältämän julkisen avaimen palvelimen määritykseen.  

<img width="183" alt="image" src="https://github.com/user-attachments/assets/36912637-43ae-4d1e-98d3-035a24130125" />  

<img width="596" alt="image" src="https://github.com/user-attachments/assets/fcfef53e-7a8f-4c47-9195-c9fbaf0de0b6" />  

<img width="580" alt="image" src="https://github.com/user-attachments/assets/21fe3550-c5b6-4068-b0b9-3ba39fa4a191" />  

Avaimeni hyväksyttiin ja pääsin eteenpäin.  
Muutin huvikseeni hostin ja palvelimen nimen ja klikkasin "Deploy".  

<img width="603" alt="image" src="https://github.com/user-attachments/assets/eee5e37f-c018-4ec8-adeb-edb56386e727" />  

<img width="797" alt="image" src="https://github.com/user-attachments/assets/3fa6e98f-52aa-4c3d-b365-083db4ad4180" />  

<img width="806" alt="image" src="https://github.com/user-attachments/assets/6fc684ec-9e16-4330-ac86-56657ed93e8c" />  

Palvelin käynnistyi ilman ongelmia.  

## b) Alkutoimet omalla virtuaalipalvelimella
Seuraavaksi yhdistin palvelimeen virtuaalikoneeltani.  

Komento:  
**ssh root@80.69.172.181 // ip-osoite luki UpCloudissa palvelimet sivulla.**   

Tämän jälkeen minulta kysyttiin haluanko yhdistää palvelimelle, johon vastasin "yes".  

<img width="463" alt="image" src="https://github.com/user-attachments/assets/c1f8cd74-d7c6-4f2b-a5d1-8e6d2f4396c9" />  

Tämän jälkeen ajoin päivitykset ja asensin palomuurin.  

Komennot:  
**sudo apt-get update  
sudo apt-get install ufw**  

<img width="689" alt="image" src="https://github.com/user-attachments/assets/dac7c57f-b4cb-4ef9-bee1-d71d1b498a0a" />  

Ohjeiden mukaan piti tehdä reikä palomuuriin porttiin 22 ja aktivoida palomuuri.  

Komennot:  
**sudo ufw allow 22/tcp**  
**sudo ufw enable**  

<img width="397" alt="image" src="https://github.com/user-attachments/assets/d97ed029-2e98-4919-9f38-3f349caab85e" />  

Seuraavaksi ohjeissa tehtiin käyttäjiä **sudo user**  

**Komento: sudo adduser joona**  

<img width="344" alt="image" src="https://github.com/user-attachments/assets/75f0c841-837e-44fd-a3d5-7eb271c98c74" />  

Tämän jälkeen luotiin salasana ja täytettiin tietoja, joita kysyttiin.  
Laitoin vain vahvan salasanan, oman nimeni ja muut kohdat jätin tyhjiksi painamalla entteriä.  

Seuraavaksi käyttäjäni lisättiin eri ryhmiin komennoilla:  

**sudo adduser joona sudo = ok  
sudo adduser joona adm = ok  
sudo adduser joona admin = admin ryhmää ei löytynyt**  

sitten otin root kirjautumisen pois päältä  
Komennot:  
**sudo usermod --lock root  
sudoedit /etc/ssh/sshd_config**  

<img width="337" alt="image" src="https://github.com/user-attachments/assets/b3c4524b-9b38-4412-9963-958bb7343f65" />  
configista muokattiin seuraava rivi:  **PermitRootLogin yes -> no**  

Sitten vielä kopioitiin root:n ssh-asetukset -> omalle käyttäjälle.  
Asetukset eli esimerkiksi julkinen avain, jonka avulla voidaan sitten kirjautua palvelimeen komennolla ssh joona@ip-osoite eikä ssh root@ip-osoite.  
Komennot palvelimella:  
**sudo cp -rvn /root/.ssh/ /home/joona/  
sudo chown -R joona:joona /home/joona/**  

## C) Weppipalvelimen asennus virtuaalipalvelimelle  

Ensin asensin apache2-web-palvelimen  
Komento:  
**sudo apt install apache2**  

Sitten katsoin onko se päällä komennolla:
**sudo systemctl status apache2**  

<img width="650" alt="image" src="https://github.com/user-attachments/assets/6c00071c-e420-4847-a145-8ddcbbc25ca7" />  

Apache2 näkyi aktiivisena.  
Seuraavaksi tein toisen reiän palomuuriin apache2:selle.  
Komento: **sudo ufw allow 80/tcp**  
Portti 80 oli siis apache2:sen käyttämä portti ja aiemmin avattu portti 22 oli ssh-etäyhteyksille avattava portti.  

Kävin kokeilemassa löytyykö palvelimen ip-osoitteella sivua selaimella.  
<img width="619" alt="image" src="https://github.com/user-attachments/assets/6cc411ea-bc5e-42d8-834f-a4898c798311" />  

Sivu löytyi ja toimi.  

Muutin vielä apachen defult sivun sivun komennolla:  

**echo Hello world! |sudo tee /var/www/html/index.html**  

<img width="119" alt="image" src="https://github.com/user-attachments/assets/4be53809-97b0-4e7d-8d8e-70e6c7d684b0" />  

Hello world näkyi ja sivu toimi.  

## e) Vapaaehtoinen: Laita omalle julkiselle palvelimellesi uusi Name Based Virtual Host.  
Kun sammutat muut weppisivut, niin se ainut näkyy nimestä riippumatta etusivulla.  
Name Based Virtual Host avulla pääset muokkaamaan kotisivuja normaalilla käyttäjällä, ilman sudoa. 

Tämän jälkeen lähdin tutkimaan Name Based Virtual Hostia github educationista.  
Sieltä löysin Namecheap kupongin, jolla saisin domain nimen vuodeksi veloituksetta.  
<img width="274" alt="image" src="https://github.com/user-attachments/assets/048f838a-a7bd-4701-9cb7-0dd6d8c3e821" />  

<img width="430" alt="image" src="https://github.com/user-attachments/assets/44bf312c-304b-439e-a9fd-46f39da26bf3" />  

<img width="440" alt="image" src="https://github.com/user-attachments/assets/55dd714c-0944-47c5-8073-7bd35eeb4b65" />  

Etsin omalla nimelläni sopivan domainin ja painoin "ADD" -> "Confirm Order"  

Tämän jälkeen liitin viel github käyttäjäni namecheapin käyttäjään.  

<img width="552" alt="image" src="https://github.com/user-attachments/assets/cf575547-67c5-4e89-8879-79f024d50628" /> 

<img width="452" alt="image" src="https://github.com/user-attachments/assets/0c0b9fe0-364a-4f85-b718-85140203c491" />  

Kirjauduin sisään tililleni ja aktivoin tilini sähköpostin kautta.  

<img width="484" alt="image" src="https://github.com/user-attachments/assets/0619884c-0fb9-47c0-b050-4525d684ac90" />  

<img width="673" alt="image" src="https://github.com/user-attachments/assets/8a676c57-ad03-4362-bc93-fc73385b5edc" />  

Jatkoin nimipalvelimen muokkausta Susanna Lehdon raportin mukaan ja lisäsin advanced DNS asetuksiin virtuaalipalvelimen ip-osoitteen.  
Postin myös vanhat recordit.  

<img width="668" alt="image" src="https://github.com/user-attachments/assets/bcf62c7e-c4a7-463e-a88a-5eb1de2525f0" />  

Kävin kokeilemassa onko DNS päivittynyt ja näkyykö sivulla "Hello world" -teksti.  

<img width="475" alt="image" src="https://github.com/user-attachments/assets/806f3034-1d4a-4df4-a60d-dd97c5c52fdf" />  

Kaikki toimi nyt hyvin. DNS muutokset eivät tapahtuneet heti.  

Seuraavaksi tein käyttäjälleni kansioita ja tiedostoja, jotta voin muokata sivua ilman sudo komentoa.  
Navigoin kotikansiooni ja loin sinne kansion publicsites, johon loin vielä kansion joonalindholm.me.  
Komento: **mkdir publicsites**  
Komennot: **cd publicsites ja mkdir joonalindholm.me**  

Tämän jälkeen loin kansioon joonalindholm.me, tiedoston index.html komennolla:  
**micro index.html**  

Tämä avasi tekstieditorin, jolla lisäsin html rakennetta tiedostoon.  

<img width="449" alt="image" src="https://github.com/user-attachments/assets/b417e4ef-0cc8-4cfc-a9e7-f0d36884b856" />  

Tämän jälkeen kävin muokkaamassa konfiguraatio-tiedostoa komennolla:  
**sudo nano /etc/apache2/sites-available/joonalindholm.me.conf**  

Lisäsin sinne rivit:  

<img width="295" alt="image" src="https://github.com/user-attachments/assets/8e4335ad-d554-4e65-9bd2-c279ec22c48e" />  

Tallensin tekstini ctrl-s näppäinyhdistelmällä ja poistuin editorista.  
Seuraavaksi otin sivun käyttöön komennoilla:  

**sudo a2ensite joonalindholm.me.conf  
sudo systemctl restart apache2**  

Nämä komennot kopioivat konfiguraatio-tiedostoni sites-enabled kansioon ja käynnistivät apachen uudelleen.  

<img width="185" alt="image" src="https://github.com/user-attachments/assets/d66715ba-18ad-4049-bd00-0a4c1aa6bfcb" />  

Olin nyt siis tehnyt kansiot ja konfiguroinut asetukset tiedostojen nimien ja polkujen mukaan.  
Sivu ei kuitenkaan näkynyt selaimessa. Olin ilmeisesti unohtanut jotakin.  
Menin error.logiin katsomaan, mitä erroreita sinne ilmestyy, kun yritän päästä sivulle.  

Komento:  
**sudo tail -f /var/log/apache2/error.log**  

[Sun Feb 09 10:34:39.056147 2025] [core:error] [pid 19236:tid 19246] (13)Permission denied: [client 88.114.9.199:50772] AH00035: access to / denied (filesystem path '/home/joona/publicsites') because search permissions are missing on a component of the path

Tämä virhe muistutti minua siitä, että en ollut antanut pääsyoikeuksia apachelle ja siksi se ei päässyt käsiksi luomaani index.html tiedostoon.  

Tutkin asiaa googlailemalla ja lopuksi kysyin chatgpt:eeltä, että mitä oikeuksia apache2 tarkalleen tarvitsee.  
Sain vastaukseksi, että luku ja suoritus -oikeudeuksia kansiohin polulla, jossa index.html sijaitsee.  
Apache tarvitsee myös lukuoikeuden itse index.html tiedostoon.  

Komennot:  
sudo chmod -R 644 /home/joona/publicsites/*  
sudo chmod -R 755 /home/joona/publicsites  

Tarkennus numeroista komennoista:    

**644 = antoi oikeudet lukea tiedostoja (esim. apachelle oikeus lukea index.html tiedoston sisältö).    
755 = antoi oikeudet lukea ja suorittaa kansioita (esim. apachelle oikeus availla kansioita ja navigoida niissä).**  

Näiden komentojen jälkeen sivuni näkyi selaimessa.    

<img width="551" alt="image" src="https://github.com/user-attachments/assets/bc6927ec-b255-4ac2-8328-bac99557280e" />  









