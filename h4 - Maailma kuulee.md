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

**a) Vuokraa oma virtuaalipalvelin haluamaltasi palveluntarjoajalta.  
(Vaihtoehtona voit käyttää ilmaista kokeilujaksoa, GitHub Education krediittejä; tai jos mikään muu ei onnistu, voit kokeilla ilmaiseksi vagrant:ia paikallisesti.  
Suosittelen kuitenkin harjoittelemaan oikeilla, tuotantoon kelpaavilla julkisilla palveluilla).**

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

https://upcloud.com/  

<img width="605" alt="image" src="https://github.com/user-attachments/assets/6aca59f5-7eac-4b6c-bcf6-d5a7f50dd585" />  

<img width="872" alt="image" src="https://github.com/user-attachments/assets/4141dfea-607b-453e-aaad-ef7fd6fbbc6d" />  

<img width="487" alt="image" src="https://github.com/user-attachments/assets/7212655b-2aed-45c8-b4cf-24524d13ecaf" />  

Sain tilin luotua vaivattomasti ja lisäsin tililleni 10 euroa rahaa, että sain trial-version pois päältä.  
Laitoin myös 2fa autentikoinnin päälle klikkaamalla oikeasta yläkulmasta.  

Aika tehdä palvelin.  

Klikkasin deploy now ja server.  

<img width="905" alt="image" src="https://github.com/user-attachments/assets/c789ee97-e9eb-4291-b34a-0f963d2b70ec" />  

Valitsin samast asetukset, kuin oppitunnilla eli:  

Location = FI-HEL1  
Plan = Developer  
<img width="590" alt="image" src="https://github.com/user-attachments/assets/099ba33a-6011-4fb9-8a27-435298dfdf19" />  

Operating system  
<img width="595" alt="image" src="https://github.com/user-attachments/assets/47e9c01a-48c7-401a-9582-20d28533f63a" />  





