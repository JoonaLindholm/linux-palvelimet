# H3 kotitehtävät (Hello Web Server)  

## Tehtävänannot ja raportin sisältö  

**https://terokarvinen.com/linux-palvelimet/#h3-hello-web-server**  

**x)** Lue ja tiivistä  
**The Apache Software Foundation 2023: Apache HTTP Server Version 2.4 Documentation: Name-based Virtual Host Support**    
**Karvinen 2018: Name Based Virtual Hosts on Apache – Multiple Websites to Single IP Address**  

**a)** Weppipalvelimen toimivuuden testaus    

**b)** Apache2 lokien tutkiminen ja analysointi  

**c)** Uusi name based virtual host

**e)** Tee validi HTML5 sivu

**f)** Esimerkit 'curl -I' ja 'curl' -komennoista

**m)** GitHub Education -paketti.  

**o)** Vapaaehtoinen, vaikea: Laita sama tietokone vastaamaan kahdellla eri sivulla kahdesta eri nimestä.  

# Raportti kotitehtävistä  

Aloitin tehtävien suorittamisen 30.1.2025. klo 17:00.

Käytin samaa rautaa ja ympäristöä kuin aiemmissa kotitehtävissä.  

Tietokoneen resurssit:  
- Windows 11 pro x64 -käyttöjärjestelmä  
- B550M-ITX/ac -emolevy  
- Amd Ryzen 7 5800X3D -prosessori  
- 32 gb -ram muistia  
- Noin 2 tb ssd -levytilaa  
- 3060ti 8GB GDDR6 -näytönohjain  

VM Linuxin resurssit ja asetukset:  
<img width="393" alt="image" src="https://github.com/user-attachments/assets/2338aa07-4497-4842-a83d-3402128cca0f" />  

*Päivitys 2.2.2025. Nostin video memoryn määrää = 256 MB.  
 Virtual Box muuttui mustaksi isolla näytöllä, kun video memoryn määrä ei ollut riittävä.*

## x) Tiivistelmät  

### **The Apache Software Foundation 2023: Apache HTTP Server Version 2.4 Documentation: Name-based Virtual Host Support**

- Jokaisella sivulla on oma IP-osoitteensa, mutta yhden IP-osoitteen voi jakaa monelle sivulle HTTP-otsikon eli headerin Host-nimen avulla.
  Palvelin vertaa ServerName ja/tai ServerAlias nimiä valitakseen ensimmäisen oikean, joka vastaa pyyntöön.
  Jos täsmäävää nimeä ei löydy, käytetään ensimmäistä.

- Nimeen perustuva virtuaali-isännöinti säästää IP-osoitteita ja yksinkertaistaa DNS-konfiguraatiota.

- Jos VirtualHostiin ei määritellä ServerName kohtaa, palvelin käyttää oletuksena system hostnamea.  
  Tämä voi aiheuttaa ongelmia.  

### **Karvinen 2018: Name Based Virtual Hosts on Apache – Multiple Websites to Single IP Address**  

Artikkelissa kerrotaan selkeät ohjeet, kuinka Apache-palvelimella voi tehdä useita verkkosivustoja yhdellä IP-osoitteella käyttäen nimiin perustuvaa virtuaali-isännöintiä.  

- Apache-palvelimen asennus ja oletussivuston korvaaminen.  
  Komennot:  
  **sudo apt-get -y install apache2**  
  **echo "Default" | sudo tee /var/www/html/index.html**  

- Nimiin perustuvan virtuaali-isännän luominen konfiguraatiotiedostossa.  
Komento: **sudoedit /etc/apache2/sites-available/pyora.example.com.conf**
Tämän jälkeen konfiguroidaan sisältö.  

<img width="319" alt="image" src="https://github.com/user-attachments/assets/d5490283-9efc-4cf6-9fdc-274c5fd8ac75" />  

- Uuden virtuuali-isännän eli hostin käyttöönotto.  
  Komennot:  
  **sudo a2ensite pyora.example.com**  
  **sudo systemctl restart apache2**  

- Sivun luominen tavallisena käyttäjänä eli ilman sudoa.  
  Komennot:  
  **mkdir -p /home/xubuntu/publicsites/pyora.example.com/**  
  **echo pyora > /home/xubuntu/publicsites/pyora.example.com/index.html**  

- Sivujen testaus terminaalissa curl-komennolla.
  Komennot:  
  **curl -H 'Host: pyora.example.com' localhost  
  curl localhost**

- DNS-asetuksien asettaminen.  
  Komennot:   
  **sudoedit /etc/hosts 
  127.0.0.1 localhost  
  127.0.1.1 xubuntu  
  127.0.0.1 pyora.example.com**   
  
- Sivujen testaus selaimessa.
  kokeile URL-osoitteita  
  **http://localhost  
  http://pyora.example.com**  

## a)  Weppipalvelimen toimivuuden testaus  

Apache2 -weppipalvelin asennettiin jo tunnilla, joten aloitin tehtävän kokeilemalla toimiiko se.  

Avasin terminaalin ja annoin syötteen **curl localhost**  

<img width="187" alt="image" src="https://github.com/user-attachments/assets/5706137a-eada-4c11-abd1-f9a9844af14a" />  

Tämä tulosti sivun sisällön HTML-koodina.  
Menin myös guin kautta kokeilemaan aukeaako localhost -sivu.  
Annoin osoitekenttään osoitteen:  
**http://localhost/**  

<img width="394" alt="image" src="https://github.com/user-attachments/assets/656e5703-08b2-49a3-a069-268c98cdf40f" />  

Kokeilin vielä lopuksi komentoa  
**sudo systemctl status apache2**  

<img width="419" alt="image" src="https://github.com/user-attachments/assets/09ea7b2e-7b90-4a4e-ae75-297f4985fc3f" />

Palvelin toimi hyvin ja oli statuksen mukaan aktiivinen.  

## b) Apache2 lokien tutkiminen ja analysointi  

Tein tehtävää 2.2. noin klo 14 eteenpäin.

Aloitin tehtävän terminaalissa komennolla  
**sudo tail /var/log/apache2/access.log**  

<img width="260" alt="image" src="https://github.com/user-attachments/assets/caaaa152-422a-4422-9a56-b95ad211a319" />  

Tämä komento ei tulostanut mitään komentoriville, vaikka sen oli tarkoitus näyttää 10 viimeisintä lokijälkeä.  
Kokeilin testiksi saisinko error lokitiedoston tietoja näkyviville.  
Komento:  
**sudo tail /var/log/apache2/error.log**  

<img width="868" alt="image" src="https://github.com/user-attachments/assets/9aaa8a51-36ab-42fe-9b16-125954647409" />  

Tämä toimi ja sain näkyville erilaisia error tapahtumia.  

Minua jäi kuitenkin vaivaamaan, että miksi access.log ei näytä yhtään tapahtumaa.  
Menin tutkimaan kansiota /var/log/apache2/, jos sieltä vaikka löytyisi jotain.  
Komento: **sudo ls /var/log/apache2**  

<img width="739" alt="image" src="https://github.com/user-attachments/assets/e18a2ac5-9ff6-4d13-b48b-e44f3cb60720" />  

/var/log/apache2/ kansio oli täynnä lokitiedostoja.  
Ilmeisesti edellisistä virtual host-sivusto harjoituksista.  

Tämä herätti epäilykseni siitä, että tämän uusimman sivun lokit eivät menneet access.log lokiin vaan johonkin toiseen tiedostoon kansion lokeista.  
Aloin käymään kansion access.log tiedostoja läpi yksi kerrallaan. Tavoitteena löytää tältä päivältä joku jälki.  

**sudo tail /var/log/apache2/access.log.1 = Vanhoja lokeja**    
**sudo tail /var/log/apache2/other_vhosts_access.log.2.gz = Jotain hämärää alien kieltä**  
**sudo tail /var/log/apache2/other_vhosts_access.log = we have a winner**  

<img width="983" alt="image" src="https://github.com/user-attachments/assets/51abee87-3131-4c8e-b6ac-7b320731342d" />

Oikeaksi komennoksi selvisi:  
**sudo tail /var/log/apache2/other_vhosts_access.log**  

<img width="962" alt="image" src="https://github.com/user-attachments/assets/108237ab-9f86-4c7e-8491-bd98996eb61a" />  

Tehtävänantona oli analysoida loki, joka syntyy avatessani sivun palvelimelta.  
Käytin tähän Teron tunnilla opettamaa komentoa ja tapaa.  
**Komento: sudo tail -f /var/log/apache2/other_vhosts_access.log**  
Näin sain terminaalin "seuraamaan" tuota lokia eli näin kaikki tapahtumat heti komentorivillä reaaliajassa.  
Tämän jälkeen latasin sivun selaimella ja sain jäljen lokiin.  

**hattu.example.com:80 127.0.0.1 - - [02/Feb/2025:16:26:14 +0200] "GET / HTTP/1.1" 200 636 "-" "Mozilla/5.0 (X11; Linux x86_64; rv:128.0) Gecko/20100101 Firefox/128.0"**  

- **hattu.example.com:80: Tämä oli palvelimen nimi ja portti (80 on HTTP:n oletusportti).  
Selain lähettää pyynnön näihin osoitetietoihin. Pyyntö voi olla vaikka sivun avaaminen.**  

- **127.0.0.1: Tämä oli lähdeosoite (pyyntö tuli tästä osoitteesta) eli pyynnön oli tehnyt sama kone, jossa palvelin oli (localhost).**
 
- **[02/Feb/2025:14:54:33 +0200]: Tämä oli aikaleima ja se kertoi milloin pyyntö oli tehty.**  

- **"GET / HTTP/1.1": Tämä oli get pyyntö, jonka tarkoituksena oli saada tietoa sivun juurikansiosta käyttäen HTTP/1.1 -protokollaa.
  GET / tarkoitti sivun juurikansiota, josta haluttiin tietoa.**  
  
- **200: Tämä oli HTTP-vastaus, joka tarkoitti "OK" ja kertoi, että pyyntö onnistui ja palvelin palautti pyydetyn tiedon.**  
  
- **636: Tämä oli lähetetyn datan koko tavumäärä (bytes). Se kertoi, että palvelin lähetti selaimen pyynnön seurauksena 636 tavua tietoa selaimelle.**  
  
- **"Mozilla/5.0 (X11; Linux x86_64; rv:128.0) Gecko/20100101 Firefox/128.0"  
  Tämä oli user agent, joka kertoi, että pyyntö tuli Firefox-selaimelta, joka oli asennettu Linux-järjestelmään.  
  5.0 = Mozillan yhteensopivuus -versio, tämä kertoo selaimen yhteensopivuudesta.  
  X11 = Linux ja UNIX pohjiasten järjestelmien graafinen ympäristö (X window system)  
  Linux x86_64 = 64 bittinen Linux  
  rv:128.0 = revision 128.0 asennettu firefox versio  
  Gecko/20100101 = Selaimen moottori ja sen versionumero**   
  
## c) 
Tein tehtävää opettajani Tero Karvisen ohjeiden mukaan.  
**https://terokarvinen.com/2018/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/**

Aloitin luomalla hattu.example.com.conf-asetustiedoston käytettävissä oleviin sivuihin.  
Komento:  
**sudoedit /etc/apache2/sites-available/hattu.example.com.conf**   

<img width="576" alt="image" src="https://github.com/user-attachments/assets/bcedff98-a006-47ee-9129-29df8e97dcae" />

Lisäsin ohjeiden mukaiset tiedot tiedostoon ja muutin ne tehtävänannon mukaisiksi.  
Vaihdoin siis pyörät hattuihin ja kansioiden polut vastaamaan omaa käyttäjääni.  

**ServerName = palvelimen nimi = hattu  
DocumentRoot = kansio, jossa on sivun tiedostot  
Directory = oikeudet kaikille kansioon /home/joona/publicsites/hattu.example.com**  

Tallensin ja suljin nano-editorin komennoilla:   
**ctrl-s -> ctrl-x**  

Seuraavaksi aktivoin hattu.example.com sivun apache2:lle, luoden sen sites-enabled kansioon.  
Komento:  
**sudo a2ensite hattu.example.com**  

Tämän jälkeen käynnistin apache2 uudelleen, jotta muutokset aktivoituvat.  
Komento:  
**sudo systemctl restart apache2**  

Sitten luin tehtävänantoa ja huomasin, että vanha asetustiedosto piti käydä poistamassa.  
Navigoin aktiivisiin apache2 sivuihin ja poistin vanhan sivun.  
Komennot:
**cd /etc/apache2/sites-enabled/ -> ls  

<img width="427" alt="image" src="https://github.com/user-attachments/assets/a767608d-b919-43ee-a120-c69995b34e85" />  

**sudo a2dissite Joonansivut.example.com.conf**  

<img width="430" alt="image" src="https://github.com/user-attachments/assets/ece34dc4-3a16-4b44-838b-fe6e5c098aa7" />  

Jatkoin ohjeiden seuraamista ja loin kansiot kotikansiooni seuraavalla komennolla.  

**mkdir -p /home/joona/publicsites/hattu.example.com/**
-p loi myös kaikki puuttuvat välikansiot.  
Ohjeissa oli seuraavaksi komento luoda tekstiä hattu.example.com tiedostoon komennolla:
**echo hattu > /home/joona/publicsites//hattu.example.com/**  

Tämän jälkeen kokeilin tulostaako curl localhost tekstin "hattu" komentoriville.   
Komento oli siis **Curl localhost**  

<img width="299" alt="image" src="https://github.com/user-attachments/assets/405988bf-0e2f-410d-9c0f-a577a1f12ecc" />  

Sivu toimi ja hattu tulostui selaimeen.    

Seuraavaksi muokkasin index.html tiedostoa, että sain muutettua sivun tietoja.  
Enemmän hattu-tekstiä siis sivulle.  

<img width="459" alt="image" src="https://github.com/user-attachments/assets/acba5887-d045-41a2-8955-5f873fb10b15" />

Avasin tiedoston komennolla **nano index.html**  
Lisäsin perus html-koodia:  
                                                            
<img width="454" alt="image" src="https://github.com/user-attachments/assets/a342f6b7-bac2-4247-951a-aca16b51248b" />

crtl-s (tallennus) -> ctrl-x (exit)  

Menin kokeilemaan pääsenkö graafisella selaimella katsomaan hattu-sivua.  

<img width="394" alt="image" src="https://github.com/user-attachments/assets/ab4b4ec9-766b-4b6f-9031-4f99dfd9fada" />  

Hattu-sivu toimi hyvin ja oli päivittynyt.  
Sivua pystyi myös muokkaamaan ilman sudo oikeuksia.  

## e) Validi HTML5-sivu  
Olin periaatteessa, jo suorittanut tämän tehtävän vahingossa jo edellisessä tehtävässä.  
Halusin kuitenkin muokata lisää hattu-sivua ja lisätä jotain tekstiä siihen.  
Opettajallani Terolla oli sivuillaan myös ohjeet perus HTML5-sivun tekemiseen.  

**https://terokarvinen.com/2012/short-html5-page/**  

Navigoin kansioon, jossa oli index.html tiedosto.  
**Komennot**
**cd /home/joona/publicsites/hattu.example.com -> 
ls ->
nano index.html**  

<img width="455" alt="image" src="https://github.com/user-attachments/assets/342c21e9-0d09-4f4c-9a28-1133fde53636" />  

Googlasin mikä on maailman kallein hattu ja päädyin sivulle:  
**https://damiaglobalservices.com/article/most-expensive-hats-in-the-world/**  
Lisäsin sivulta tietoa hattu-sivulle.  

<img width="443" alt="image" src="https://github.com/user-attachments/assets/386e3daf-3592-49a0-9245-3ddfd82bf45e" />  

<img width="395" alt="image" src="https://github.com/user-attachments/assets/d531b04c-23ad-4539-8606-98f42b34852f" />  

### Validointi 
Tein sivun validoinnin w3 sivustolla  
**https://validator.w3.org/#validate_by_input**   
Laitoin HTML-koodin validate by direct input kohtaan ja painoin check.  

<img width="389" alt="image" src="https://github.com/user-attachments/assets/2cc8b6ee-ff67-451b-b3c7-5636492ce7e5" />  

<img width="388" alt="image" src="https://github.com/user-attachments/assets/bb20c9f4-b761-49ba-bd95-b811cb0b4f47" />  

<img width="386" alt="image" src="https://github.com/user-attachments/assets/c4683f07-1c61-42ca-84d7-7bded29f1141" />  

Validointi meni läpi ja sivuni oli hyväksytty.  

## 'curl -I' ja 'curl' -komennot ##  

Kokeilin molempia komentoja terminaaliin.  
Curl -I localhost ja curl localhost.  

![image](https://github.com/user-attachments/assets/924e24a4-8ece-4123-b569-662ec90999fc)  

Curl -I palautti komentoriville HTTP-vastauksen otsakkeet ja curl palautti HTML sivun sisällön.  

Curl -I palautti seuraavat tiedot:  

**HTTP/1.1 200 OK  
Date: Sat, 01 Feb 2025 12:57:41 GMT  
Server: Apache/2.4.62 (Debian)  
Last-Modified: Thu, 30 Jan 2025 17:52:08 GMT  
ETag: "19d-62cf015b77bc3"  
Accept-Ranges: bytes  
Content-Length: 413  
Vary: Accept-Encoding  
Content-Type: text/html**  

Server: kohtaan tuli palvelimen tiedot eli apache2 ja versio 2.4.62.
Server kohdassa oli myös käyttöjärjestelmä, johon palvelin oli asennettu.  

Content-Type kertoi, että palvelin lähetti HTML tietoa. Tämä tieto menee selaimelle.  

HTTP/1.1 200 OK tarkoitti, että palvelin palautti pyydetyt tiedot eli sivun. 200 tarkoitti, että OK.  
1.1 oli HTTP versio numero.  



## m) GitHub Education -paketti  

Googletin github education ja päädyin sivulle:  

https://github.com/education  

<img width="671" alt="image" src="https://github.com/user-attachments/assets/4d9cdddd-8584-453e-af0f-39eca964e047" />  

Klikkasin Join GitHub Education ja student.  

<img width="686" alt="image" src="https://github.com/user-attachments/assets/80e03403-0dfb-4347-b4ba-99f2734ba552" />

Tarkistin vaaditut tiedot github -käyttäjäsivuiltani, lisäsin koulun nimen kenttään ja painoin continue.  

<img width="532" alt="image" src="https://github.com/user-attachments/assets/3d1aa94f-f389-4429-a269-85c772a7e1eb" />  

<img width="548" alt="image" src="https://github.com/user-attachments/assets/8a5ff390-9fe1-48e0-b817-5275bad746d8" />  

Lopuksi piti todistaa oma opiskelija status. Nappasin kuvan pepistä ja kokeilin kelpaako se.  

<img width="750" alt="image" src="https://github.com/user-attachments/assets/6a8e9c2f-ebba-4862-8531-c4bf5f227f46" />  

Jäin odottelemaan vahvistusta.  

*päivitys: 2.2.2025. ei vielä vahvistusta :(*  

## o) Sama tietokone vastaamaan kahdellla eri sivulla kahdesta eri nimestä  

Aloitin tehtävän tekemisen 2.2. klo 17:37.  
Muistin, että Tero Karvisen sivuilla oli tähän sopivat ohjeet.  
https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/  

Aloin kokeilemaan saanko tehtävän ratkaistua muokkaamalla /etc/hosts -tiedostoa.   
Tein uuden rivin jonka nimesin kengäksi ja annoin sille saman osoitteen kuin hatulle.  
<img width="329" alt="image" src="https://github.com/user-attachments/assets/305c224b-36b7-4cb6-9c52-e8fd3e3a3bc2" />  
 
Seuraavaksi minun täytyi luoda uusi sivu kengälle eli mennä ohje alusta.  
Komento:  
**sudoedit /etc/apache2/sites-available/kenka.example.com.conf**  
Laitoin tiedostoon allaolevat tiedot:  

<VirtualHost *:80>  
 ServerName kenka.example.com  
 ServerAlias www.kenka.example.com  
 DocumentRoot /home/joona/publicsites/kenka.example.com  
 <Directory /home/joona/publicsites/kenka.example.com>  
   Require all granted  
 </Directory>  
</VirtualHost>  
ctrl-s eli tallennus  

Tämän jälkeen aktivoin sivun seuraavalla komennolla:  
**sudo a2ensite kenka.example.com**  
Apachen uudelleenkäynnistys komennolla:  
**sudo systemctl restart apache2**

Tämän jälkeen kävin vielä luomassa index.html tiedoston kansioon, josta asetustiedosto sen löytää.  
Komento:  
**mkdir -p /home/joona/publicsites/kenka.example.com/**  
Navigoin kansioon komennolla: **cd /home/joona/publicsites/kenka.example.com/**  
Loin sinne uuden index.html-tiedoston ja lisäsin sinne nanolla perus HTML-sivun rakenteen.  
Komento:  
**/publicsites/kenka.example.com$ nano index.html**  

<img width="405" alt="image" src="https://github.com/user-attachments/assets/8a7b5aea-8701-40fe-a3c9-9030c87f896d" />  

Tämän jälkeen kävin kokeilemassa selaimella onko minulla kaksi sivua.  

**hattu.example.com  
kenka.example.com**  

<img width="1676" alt="image" src="https://github.com/user-attachments/assets/4f18ebaf-14a3-4b0a-bdcc-43608c05af64" />  

Kaikki näytti toimivan.  

## Lähdeluettelo  

- Tehtävänanto  
  https://terokarvinen.com/linux-palvelimet/#h3-hello-web-server  

- Karvinen 2018: Name Based Virtual Hosts on Apache – Multiple Websites to Single IP Address  
  https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/  

- The Apache Software Foundation 2023: Apache HTTP Server Version 2.4 Documentation: Name-based Virtual Host Support  
  https://httpd.apache.org/docs/2.4/vhosts/name-based.html  

- Maailman kallein hattu  
  https://damiaglobalservices.com/article/most-expensive-hats-in-the-world/  

- Sivun validointi  
  https://validator.w3.org/#validate_by_input  

- Komentoja ja neuvoja (esim kansion poistaminen sisältöineen)  
  https://chatgpt.com/  







