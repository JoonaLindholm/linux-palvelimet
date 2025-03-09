# h7 - Maalisuora  

### Sisällysluettelo / Tehtävänannot  

**https://terokarvinen.com/linux-palvelimet/#h7-maalisuora**  

**a)** Hei maailma! -kolmella eri kielellä  

**c)** Oma komentoni kaikille käyttäjille  

**d)** Vanha laboratorioharjoitus  

---

**Tietokoneen resurssit:**  

- Windows 11 pro x64 -käyttöjärjestelmä  
- B550M-ITX/ac -emolevy  
- Amd Ryzen 7 5800X3D -prosessori  
- 32 gb -ram muistia  
- Noin 2 tb ssd -levytilaa  
- 3060ti 8GB GDDR6 -näytönohjain  

**VM Linuxin resurssit ja asetukset:**  

![image](https://github.com/user-attachments/assets/7990b8ca-0601-4e51-8877-15d8fc3b5325)  

### Tehtävät  

**a) Hello world** 

Aloitin tehtävän 7.3.2025 lukemalla Tero Karvisen -ohjeita eri kielille.  

https://terokarvinen.com/2018/hello-python3-bash-c-c-go-lua-ruby-java-programming-languages-on-ubuntu-18-04/  

Tämän jälkeen avasin virtuaalikoneeni ja menin terminaaliin.  

Ensimmäiseksi asensin eri koodauskieliä.  
Tero Karvisen sivuilla oli tehtävänannossa valmiiksi komento:  

**sudo apt-get install python3 gcc g++ openjdk-17-jdk golang-go ruby lua5.4**  

Syötin tämän komennon ja odottelin kielien asentumista.  
Kun asennukset olivat ohi, loin kotikansioosi uuden kansion nimeltä "hello_world"  

**Komento: mkdir hello_world**  

<img width="355" alt="image" src="https://github.com/user-attachments/assets/c0ce673e-33ae-43f5-8b3b-74483a6a4a36" />  

Menin cd-komennolla kansioon ja loin sinne ensimmäisen "hello world" -harjoituksen.  

### Python

**Komento: micro hello.py**  

Tämän jälkeen kirjoitin Teron ohjeiden mukaan:  

**print("Hello world")**  
Tallensin tiedoston ctrl-s ja suljin micron ctrl-q.  
Seuraavaksi kokeilin ajaa tämän yksinkertainen koodin.  

**Komento: python3 hello.py**  

<img width="216" alt="image" src="https://github.com/user-attachments/assets/a4d47632-54ff-490d-b2e8-56ab78d0670e" />  

Komento toimi moitteetta ja "Hello world" -teksti tulostui terminaalin komentoriville.  

Onnistuneen kokeilun jälkeen siirryin seuraavaan kieleen.  

### Ruby  

Tein uuden tiedoston nimellä "hello.rb"  
**Komento: micro hello.rb**  

Seurasin taas ohjeita ja kirjoitin tiedostoon:  
**print ("Hello Joona\n")**  
Tallensin ja poistuin ctrl-s ja ctrl-q.  

**Komento: ruby hello.rb**  

<img width="196" alt="image" src="https://github.com/user-attachments/assets/c7773cc4-8a7d-4a34-ab23-6194a2b7e630" />  

Rubyn komento oli melkein sama, mutta kuitenkin vähän eri kuin pythonilla.  

### C++  

Valitsin kolmanneksi kieleksi C++, koska se vaikutti monimutkaiselta.  

**Komento: micro hello.cc**  

Kirjoitin tiedostoon ohjeiden mukaisesti seuraavat rivit.  

**#include <iostream>  
int main()  
{  
 std::cout << "Hello Joona!\n";  
}**  

Ctrl-s ja Ctrl-q.  

Koodissa oli samanlainen rivi rubyn kanssa kohdassa:  
**"Hello Joona!\n"**  

Koodin ajaminen terminaalissa vaati vähän enemmän säätöä, kuin aiemmissa kielissä.  

Komennot:  

**joona@Kone:~/hello_world$ g++ hello.cc -o hello**  
**joona@Kone:~/hello_world$ ./hello**  

En ymmärtänyt miksi nämä komennot tehtiin, joten kävin googlailemassa komentoja.  

**https://www.ohjelmointiputka.net/oppaat/opas.php?tunnus=cpp_ohj_01**  

Löysin sivun, jolla kerrottiin, että C++ kielellä luotu ohjelma pitää kääntää käyttöjärjestelmän ymmärtämäksi ohjelmaksi.  
Eli tuo **g++** oli kääntäjä, joka käänsi **hello.cc** tiedoston ja nimesi sen **-o** komennolla, **hello** nimiseksi ohjelmaksi.  
Tämä ohjelma ajettiin tämän jälkeen komennolla **./hello**  

<img width="170" alt="image" src="https://github.com/user-attachments/assets/64129db1-1f65-4b86-908b-e35d4a576d1d" />  

Tämä oli mielestäni hauska tehtävä!  

## c) Oma komentoni  

Tero Karvisen sivuilla oli ohjeet myös tähän tehtävään.  

**https://terokarvinen.com/2007/12/04/shell-scripting-4/**  

Yritin miettiä hauskaa tai kätevää ohjelmaa tähän tehtävään.  
Lopulta päädyin taas googlailemaan ja löysin hyvän sivun:  

**https://medium.com/aimonks/50-cool-bash-scripts-and-what-they-do-b38b4e841ba2**  

Sivuilta löysin kätevän komennon:  

**#!/bin/bash
length=12
characters="ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789!@#$%^&*()"
password=$(head /dev/urandom | tr -dc "$characters" | head -c "$length")
echo "Generated Password: $password"**  

Ohjelman selitys:  

**https://dev.to/karandaid/how-to-generate-random-passwords-in-bash-using-devurandom-4cp8**  

length=12   
Määritti kuinka pitkä salasana luodaan.  

characters="ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789!@#$%^&*()"  
Määritti mitä kaikkia kirjaimia, numeroita ja symboleita käytetään salasanassa.  

password=$(head /dev/urandom | tr -dc "$characters" | head -c "$length")  
/dev/urandom oli Linuxiin sisäänrakennettu satunnaisgeneraattori,  
tr -dc characters poisti satunnaisesta tulosteesta kaikki merkit, jotka eivät kuuluneet characters osioon ja   
head -c length lyhensi salasanan pituuden aiemmin määriteltyyn 12 merkkiin.  
Nämä komennot ajettiin putkena | vuorotellen.  

echo tulosti generoidun salasanan komentoriville.  

Ohjelman tarkoituksena oli luoda uusi satunnainen salasana ja tulostaa se komentoriville.  
Ohjelman nimeksi tuli tietenkin "Lazy_Online_Locker" eli lyhennettynä L.O.L.  

Loin uuden ohjelman kotikansiooni komennolla:  

**micro Lazy_Online_locker.sh**  

Kopioin koodin microon ja muutin seuraavan rivin ohjelmaan sopivammaksi:  

**echo "Generated L.O.L: $password"**  

Tallensin työn ja poistuin microsta (ctrl-s ja ctrl-q)  

Tämän jälkeen annoin kaikille käyttäjille oikeuden suorittaa tiedoston.  
Komento:  
**chmod a+x Lazy_Online_locker.sh**  

Sitten suoritin ohjelman.  

<img width="194" alt="image" src="https://github.com/user-attachments/assets/895d3ea7-aa83-4b40-a9dc-0a3c073ea30f" />  

Ohjelma toimi, mutta halusin kehittää sitä vielä eteenpäin.  
Etsiessäni shell script ideoita törmäsin ohjelmiin "figlet" ja "lolcat", joka muuttavat tekstit ASCII-taiteeksi.  

**https://www.tomshardware.com/how-to/customize-linux-terminal**  

Komennot:  

**sudo apt-get install figlet  
sudo apt-get install lolcat**  

Tämän jälkeen minun piti lisätä näiden ohjelmien suoritus ohjelmaani.  
Seurasin sivun ohjeita ja käytin pipe | symbolia putkittamiseen.  

Muutin echo riviäni:  
**echo "Generated L.O.L: $password" | figlet | lolcat**  

<img width="387" alt="image" src="https://github.com/user-attachments/assets/a3710187-0854-4e41-9035-445b85342724" />  
Ajattelin ensin, että tässä ohjelmassa ei ole järkeä, kun on vaikea saada selvää salasanasta.  
Pohdittuani asiaa hieman vaihdoin mielipidettäni, koska ohjelmahan on loistava vaikka julkisella paikalla tai vaikka työpaikalla.  
Kukaan ei voi nopeasti nähdä generoitua salasanaa!  

## Päivitys tehtävään
***08.03.2025 klo 15:20***

Myöhemmin vanhaa laboratorioharjoitusta tehdessäni huomasin,  
että olin unohtanut kopioida komennon /usr/local/bin/ hakemistoon.  

Tein tämän komennolla:  

**sudo cp /home/joona/Lazy_Online_locker.sh /usr/local/bin/L.O.L**  

<img width="394" alt="image" src="https://github.com/user-attachments/assets/7d85daf2-009f-4a3e-98c7-736bdbf898b8" />  

Vaihdoin samalla ajettavaksi nimeksi L.O.L.  

Kokeilin vielä voiko uusi käyttäjä ajaa ohjelman.  
Tein uuden käyttäjän ja ajoin ohjelman.  

<img width="377" alt="image" src="https://github.com/user-attachments/assets/dc72dce1-36d0-4801-aeee-f2791fe04d45" />  
  
Ohjelma näytti toimivan normaalisti.  

## d) Vanha laboratorioharjoitus  

Aloitin tehtävän 8.3.2025. Klo 14 aikoihin.  
Kävin läpi vanhoja laboratorioharjoituksia Tero Karvisen sivuilla ja päädyin lopulta seuraavaan.  

https://terokarvinen.com/2024/arvioitava-laboratorioharjoitus-2024-syksy-linux-palvelimet/?fromSearch=laboratorio

Katselin tehtävänannon läpi ja valitsin tehtävistä ne, jotka vaikuttivat tutuilta.  
Ohitin djangoon ja tietokantoihin liittyvät tehtävät.  

---

### Valitut tehtävät  

d) 'howdy'
Tee kaikkien käyttäjien käyttöön komento 'howdy'  
Tulosta haluamaasi ajankohtaista tietoa, esim päivämäärä, koneen osoite tms  
Pelkkä "hei maailma" ei riitä  
Komennon tulee toimia kaikilla käyttäjillä työhakemistosta riippumatta  

e) Python. Osoita "Hei maailma" -ohjelmalla, että Python-kehitysympäristö toimii.  

f) Etusivu uusiksi  
Asenna Apache-weppipalvelin  
Tee kerhollemme "Free Speech Europe" kotisivu  
Kotisivu tulee näkyä koneesi IP-osoitteella suoraan etusivulla  
Sivua pitää päästä muokkaamaan normaalin käyttäjän oikeuksin (ilman sudoa). Liitä raporttiisi listaus tarvittavien   tiedostojen ja kansioiden oikeuksista.  

h) Käyttäjät. Käyttäjämme tarvitsevat käyttäjät Linuxiin. Tee uudet käyttäjät seuraaville: John Doe, Erik Vähäkäähkä, 
Akhmad Amun, Päivä Ångström, Maija-Liisa Vähäaho-Virtaoja. Listaa käyttäien salasanat raporttiin report/index.md.  

i) Etänä. Kaikki käyttäjämme haluavat käyttää modernisti etänä SSH:lla. Asenna tarvittavat palvelut. Automatisoi oman käyttäjäsi kirjautuminen julkisella avaimella.  

j) Tee käyttäjille mahdollisuus tehdä kotisivuja. Tee käyttäjille esimerkkikotisivut. (Voit kirjautua kyseisten 
 käyttäjien tunnuksilla, koska he eivät ole vielä voineet tallentaa henkilökohtaisia tietojaan kotihakemistoonsa).  

---

### Raportti vanhasta laboratotiotehtävästä  

Aloitin tekemällä uuden virtuaalikoneen samalla tavalla kuin kurssin alussa.  
Samalla tavalla asensin myös debian käyttöjärjestelmän koneelle.  

**https://github.com/JoonaLindholm/linux-palvelimet/blob/main/h1%20-%20Linuxin%20asentaminen%20VirtualBoxiin.md#asennuksia**

Asennuksen jälkeen meniin suoraan terminaaliin.  
Asensin päivitykset ja tulimuurin.  
Komento: **Sudo apt-get update ja sudo apt-get install ufw**    
Aktivoin tulimuurin.  
Komento: **Sudo ufw enable**  
En avannut vielä portteja.  

## d) Howdy  

Loin howdy.sh tiedoston kotikansiooni.  

Komento: **nano howdy.sh**  

Laitoin tiedostoon seuraavat tekstit:  

#!/bin/bash  

echo "Hei $(whoami)"
echo "Tänään on: $(date)"  
echo "Tietokoneen ip-osoite on: $(hostname -I)"  
echo "Järjestelmän käyttö: $(uptime)"  

Annoin suoritusoikeudet kaikille ja kopioin komennon /usr/local/bin/ hakemistoon.  

<img width="293" alt="image" src="https://github.com/user-attachments/assets/93237e8b-e9e4-499e-a656-8eeb845f0620" />  
  
<img width="403" alt="image" src="https://github.com/user-attachments/assets/c223635c-3fa9-4ab7-8a8d-ecb619d7e489" />  

Komennon suoritus onnistui.  

Loin nopeasti uuden käyttäjän "vieras" ja ajoin ohjelman.  

<img width="349" alt="image" src="https://github.com/user-attachments/assets/232549fc-656e-4ad9-9043-3b24166a3c75" />  

<img width="401" alt="image" src="https://github.com/user-attachments/assets/757827b7-6914-469c-8195-903b1005b339" />  

## e) Python  

Asensin ensin pythonin.  

Sudo apt-get install python3  

Tämän jälkeen loin tiedoston hei_vaan.py, hakemistoon /home/joona/  
Komento: nano hei_vaan.py  
Tiedostoon teksti: print("Hei vaan") ja tallennus.  
Tämän jälkeen terminaaliin komentoriville:  
python3 hei_vaan.py  

<img width="199" alt="image" src="https://github.com/user-attachments/assets/b10c2320-27e2-47d1-b185-2ac82de525b0" />  

Python toimi normaalisti.  

## Etusivu uusiksi  

Aloitin asentamalla apache2.  
Komento:  
**Sudo apt-get install apache2**  
Apache2 "potkaisu" eli käynnistin web-palvelimen uudelleen.  
Komento:  
**sudo systemctl restart apache2**  
Apache2 status eli katsoin onko se toiminnassa.  
**sudo systemctl status apache2**  

Sitten kävin luomassa kotikansiooni kansion publicsites ja sinne kansion freespeecheurope.com.  
Eli polku on sama kuin, mitä tulee konfiguraatioon. Näin apache2 löytää sivuni.  

<img width="289" alt="image" src="https://github.com/user-attachments/assets/48aa53a9-efea-454f-901d-9ad13b72079c" />

Loin freespeecheurope.com kansioon index.html tiedoston.  
Kirjoitin tiedostoon Free Speech Europe.  

<img width="179" alt="image" src="https://github.com/user-attachments/assets/542b9212-67c2-4d07-bc8e-0405ebd4f059" />

Tämän jälkeen loin ja menin muokkaamaan sivujen conf tiedostoa, jotta apache2 löytää sivuni ja sen asetukset.  

Komento:  
**sudo nano /etc/apache2/sites-available/freespeecheurope.com.conf**

<img width="401" alt="image" src="https://github.com/user-attachments/assets/8e31ea64-8c13-4fcd-8bed-33fa0f5a23b9" />  

Uuden konfiguraation aktivoiminen.  
Komento:  
**sudo a2ensite freespeecheurope.com.conf**  
Vanhan default-konfiguraation poistaminen käytöstä.  
Komento:  
**sudo a2dissite 000-default.conf**  
Taas "potkaisu", että uudet konfiguraatiot tuilevat aktiiviseksi web-palvelimelle. 
Komento:  
**sudo systemctl restart apache2**  
Avasin tulimuuriin portin 80, jota apache2 käyttää toiminnassaan.  
**sudo ufw allow 80**

Kävin katsomassa, mitä selain sanoo sivustani.  

<img width="179" alt="image" src="https://github.com/user-attachments/assets/1b86805f-584d-4a42-aa8f-f6b4475842f2" />  

<img width="179" alt="image" src="https://github.com/user-attachments/assets/43ce9acb-ace7-426d-a29b-01464897bc6e" />

Sivuni näkyi hyvin localhostina ja pelkällä ip-osoitteellani.  
Sivua piti pystyä muokkaamaan ilman sudo oikeuksia.  
Eli index.html -tiedoston oikeudet pitivät olla kunnossa.  

Index.html -tiedostoa pystyi muokkaamaan normaalina käyttäjänä eli siis ilman suoa, koska se oli tehty pääkäyttäjän kotikansioon. 

Tämä käyttäjä kuului sudo ryhmään ja tiedostolla oli oikeudet:  
-rw-r--r-- eli rw, kohta koski käyttäjää. Rw tarkoitti luku ja kirjoitusoikeutta.  

## h) Käyttäjät  

Seuraavaksi piti luoda käyttäjät Linuxiin.  

Loin kaikki uudet käyttäjät yksitellen komennolla:  
sudo adduser "nimi" ja laitoin salasanat sekä oikeat nimet.  

<img width="377" alt="image" src="https://github.com/user-attachments/assets/8c10d179-8a52-44ba-9f7d-b0070853ae51" />  
  
<img width="418" alt="image" src="https://github.com/user-attachments/assets/2e534ff9-1c61-47b9-ad78-619a05242e34" />  
  
<img width="392" alt="image" src="https://github.com/user-attachments/assets/c80fbb22-9c0c-45b7-9db3-78484e3bafa3" />
  
<img width="415" alt="image" src="https://github.com/user-attachments/assets/1e3847a0-4d01-4edb-8ade-a71c6bec74d7" />  
  
<img width="536" alt="image" src="https://github.com/user-attachments/assets/ccb98a44-1d7e-4653-a7f5-0d2c56ea3fdc" />  

Lopuksi listasin /home/ -hakemiston käyttäjät ja tarkistin, että kaikki löytyivät sieltä.  

<img width="500" alt="image" src="https://github.com/user-attachments/assets/80def84d-4926-415a-ad86-7937b11dbbff" />  

Huomioita tehtävästä.  
Nimi piti laittaa ilman skandeja ja välit korvata _ symbolilla.  
Nimessä oleva väliviiva sai olla väliviivana -.  

Lopuksi oikea nimi kuitenkin laitettiin oikeassa muodossa käyttäjätietoihin.  

## i) Etänä  

Aloitin tehtävän klo 18 aikoihin.  
Oli 8.3.2025.  

Käytin lähteenä vanhaa tehtävääni, joka perustui Susanna Lehdon raporttiin:  

**https://github.com/JoonaLindholm/linux-palvelimet/blob/main/h4%20-%20Maailma%20kuulee.md#susanna-lehto-2022-teoriasta-k%C3%A4yt%C3%A4nt%C3%B6%C3%B6n-pilvipalvelimen-avulla**  

Tehtävässä piti luoda SSH yhteyteen tarvittavat palvelut ja tehdä julkinen avain.  

Aloitin asentamalla ssh-palvelun.  
Komento:  
**Sudo apt-get install openssh-server**  

Tämän jälkeen katsoin oliko ssh aktiivinen.  
Komento:  
**sudo systemctl status ssh**  

<img width="482" alt="image" src="https://github.com/user-attachments/assets/3c8a1239-11ce-48d3-925a-86b294fe3a74" />  

SSH oli aktiivinen ja toimi.  

Seuraavaksi avasin portin palomuurista SSH-yhteydelle.  

Komennot:  
**sudo ufw allow 22/tcp = näin tehtiin reikä  ssh-etäyhteydelle
sudo ufw enable = näin aktivoitiin palomuuri**  

Tämän jälkeen loin itselleni julkisen avaimen komennolla:  
**ssh-keygen**  

Sitten painoin 3 kertaa entteriä ja avain oli luotu.  

Tämän jälkeen kävin tarkistamassa, että oikeat ssh -hakemistot ja tiedostot syntyivät kotikansiooni.  

<img width="553" alt="image" src="https://github.com/user-attachments/assets/32642a96-2c7b-4bd9-82ba-12c35e45c6cb" />

Kaikki oli mennyt oikein.  

Avasin tiedoston **id_rsa.pub**, micro-tekstieditorilla ja kopioin sen sisältämän julkisen avaimen authorized_keys tiedostoon, jonka loin nano komennolla samaan kansioon muiden avain-tiedostojen kanssa.  

Kävin sitten muokkaamassa config tiedostoa.  
Komento:  
**sudoedit /etc/ssh/sshd_config**  

Otin root kirjautumisen pois päältä:   
**PermitRootLogin yes -> no**
ja lisäsin tiedoston alimmalle riville kohdan:  
**AllowUsers joona**    

Käytin tähän apuna keskustelua, jonka löysin googlailemalla.   
**https://superuser.com/questions/1018760/connect-with-ssh-to-your-localhost**    

Käynnistin SSH:n uudelleen komennolla:  
**Sudo systemctl restart ssh**  
Seuraavaksi yhdistin localhostiin käyttäen ssh-etäyhteyttä.  
Komento: **ssh joona@localhost**  

Jäi epäselväksi pääsinkö ssh-yhteydellä localhostiin, niin katsoin komennolla:  
**sudo systemctl status ssh**  
Mitä statuksessa lukee.  Tämän perusteella ssh-yhteyteni näytti toimivan.  

<img width="634" alt="image" src="https://github.com/user-attachments/assets/aaa9f9fa-4b24-4540-a809-fa3bb2dea91d" />  

Kokeilin vielä komentoa: **exit**, ajattelin, että jos olen ssh-yhteydessä, niin saan jonkun logout ilmoituksen komennon jälkeen.  

<img width="163" alt="image" src="https://github.com/user-attachments/assets/6193a6ba-6679-4d6c-8f5a-17f2c1cde5d4" />

Sain sopivan ilmoituksen.  
SSH yhteys oli nyt valmisteltu omalle käyttäjälleni.  

## j) Käyttäjien kotisivut  

Tehtävässä piti varmistaa, että jokainen käyttäjä voi luoda itselleen kotisivut.  

Aloitin tehtävän John Doe käyttäjän kotisivuista.  
kirjauduin hänen käyttäjälleen komennolla:
**su john_doe** laitoin salasanan.  

Tämän jälkeen navigoin hänen kotikansioonsa ja loin sinne uuden kansion publicsites.  
Publicsites kansioon loin uuden kansion nimeltään **john_doe.com**  
Loin tähän uuteen kansioon nanolla html-tiedoston.  
komennto: **nano index.html**  
Kirjoitin tiedostoon "Tervetuloa Johnin kotisivuille"  
Tallensin ja poistuin tiedostosta.  















Huom. lähde komennoille whoami jne

---

### Sisällysluettelo  

Tehtävänanto  
**https://terokarvinen.com/linux-palvelimet/#h7-maalisuora**  

Hello World -ohjeet  
**https://terokarvinen.com/2018/hello-python3-bash-c-c-go-lua-ruby-java-programming-languages-on-ubuntu-18-04/**    

C++ kielen kääntäminen  
**https://www.ohjelmointiputka.net/oppaat/opas.php?tunnus=cpp_ohj_01**   

Shell scripting  
**https://terokarvinen.com/2007/12/04/shell-scripting-4/**  

Shell scriping ideoita  
**https://medium.com/aimonks/50-cool-bash-scripts-and-what-they-do-b38b4e841ba2**  

dev/urandom/  
**https://dev.to/karandaid/how-to-generate-random-passwords-in-bash-using-devurandom-4cp8**    

Figlet ja lolcat  
**https://www.tomshardware.com/how-to/customize-linux-terminal**  

Vanha laboratorioharjoitus  
**https://terokarvinen.com/2024/arvioitava-laboratorioharjoitus-2024-syksy-linux-palvelimet/?fromSearch=laboratorio**  

SSH Localhost  
**https://superuser.com/questions/1018760/connect-with-ssh-to-your-localhost**
