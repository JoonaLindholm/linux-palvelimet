# h5-nimekäs  

## Raportti kotitehtävistä.  

**Tehtävänannot:  
https://terokarvinen.com/linux-palvelimet/#h5-nimekas**  

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

Olin tehnyt kotitehtävien kohdat **a** ja **b** vahingossa jo edellisissä kotitehtävissä.  
Seuraava osio, jonka olen rajannut viivalla, on siis muistelu edellisistä kotitehtävistäni.  

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

**Komento: mkdir publicsites  
Komennot: cd publicsites ja mkdir joonalindholm.me**  

Tämän jälkeen loin kansioon joonalindholm.me, tiedoston index.html komennolla:  

**micro index.html**  
  
Tämä avasi tekstieditorin, jolla lisäsin html rakennetta tiedostoon.    

![image](https://github.com/user-attachments/assets/ffa63d17-485c-4e6a-bcd3-6dbbb9ab6cf6)  
  
Tämän jälkeen kävin muokkaamassa konfiguraatio-tiedostoa komennolla:  

**sudo nano /etc/apache2/sites-available/joonalindholm.me.conf**  
  
Lisäsin sinne rivit:  
  
![image](https://github.com/user-attachments/assets/94f1b8c6-35e8-4ca5-9622-17cd09410fb1)  
  
Tallensin tekstini ctrl-s näppäinyhdistelmällä ja poistuin editorista.  
Seuraavaksi otin sivun käyttöön komennoilla:  
  
**sudo a2ensite joonalindholm.me.conf  
sudo systemctl restart apache2**  

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

**644 = antoi oikeudet lukea tiedostoja (esim. apachelle oikeus lukea index.html tiedoston sisältö).  
755 = antoi oikeudet lukea ja suorittaa kansioita (esim. apachelle oikeus availla kansioita ja navigoida niissä).**    
 
Näiden komentojen jälkeen sivuni näkyi selaimessa.  

![image](https://github.com/user-attachments/assets/b356ad1d-72bc-47be-88bf-244915f7e0a8)  
  
En halunnut muokata sivuja enempää, kun en ollut varma, mitä kurssilla tehdään seuraavaksi.  
Sivuista voisi tehdä tulevaisuudessa vaikka kotisivut.  

***

Olin siis vuokrannut nimipalvelusta domain-nimen itselleni ja tehnyt name based virtual host -konfiguraatiot sekä saanut sivuston toimimaan.  

***

## c) Kotisivu, alasivuineen  

Tehtävässä piti luoda kotisivuilleni alasivuja.  
Aloitin tehtävän 20.2.25. klo 20 aikoihin.  

Avasin virtuaalikoneeni -> avasin terminaalin -> yhdistin palvelimeeni komennolla **ssh 80.69.172.181**  

Navigoin sivustoni kansioon.   
joona@vm-linux1:~/publicsites/joonalindholm.me$  

Loin kansioon kaksi html-tiedostoa lisää nimillä.   
schoolworks.html ja workworks.html  
Kansiossa oli siis jo valmiiksi index.html.  

Alla perus html-rakennetta, jonka rakennetta kopioin vanhasta työstäni, jossa tehtiin omat kotisivut.  
Kurssi taisi olla johdanto digitaalisiin palveluihin.  

<img width="427" alt="image" src="https://github.com/user-attachments/assets/86e372b9-c51e-4c49-895c-bc3ac540b7d8" />  

<img width="436" alt="image" src="https://github.com/user-attachments/assets/5cc84953-1f2e-4687-b00d-f072babb9b53" />  

Olin siis luonut nyt kansiot ja htm tiedostot alisivuille. Ajattelin, että seuraavaksi kokeilen, mitä sivustolla näkyy.  

<img width="403" alt="image" src="https://github.com/user-attachments/assets/bad65ff0-2c4e-415e-8bae-0bbb2a50f88a" />  

Etusivulla näkyi tekemäni linkit alisivuille, mutta alisivut eivät toimineet.  
Ajattelin ongelman johtuvan siitä etten ollut muuttanut mitään oikeuksia tiedostojen luomisen jälkeen.  
Palasin siis takaisin opiskelemaan, miten oikeudet toimivatkaan.  

Löysin hyvät ohjeet seuraavilta sivuilta:  

**https://www.howtogeek.com/437958/how-to-use-the-chmod-command-on-linux/**  

chmod [kuka] [muutos] [oikeudet] tiedosto  

[kuka]  
u = omistaja  
g = ryhmä  
o = muut  
a = kaikki  
[muutos]  
+ = lisää oikeus  
- = poista oikeus  
= = määritä oikeudet ja poista kaikki muut  
[oikeudet]  
r = luku  
w = kirjoitus  
x = suoritus  

**sudo chmod g+rx /polku/joonalindholm.me/*.html = eli ryhmälle (g) lisätään oikeudet (+) lukea ja suorittaa tiedostoja (rx)   
sudo chmod u+rx /polku/joonalindholm.me/*.html = eli omistajalle (u) lisätään oikeudet (+) lukea ja suorittaa tiedostoja (rx)**  

<img width="386" alt="image" src="https://github.com/user-attachments/assets/db5399ef-529b-4baa-b2ee-2a044e718148" />  

Tämä ei korjannut ongelmaani, koska olin vahingossa laittanut html-rakenteen linkkien polut väärin.  
Tajusin tarkistaa tämän onneksi heti, kun oikeuksien antaminen ei onnistunut.   

<img width="397" alt="image" src="https://github.com/user-attachments/assets/badce58d-bbde-458e-8105-cc71b68ac5e9" />  

Korjasin jokaiseen html-tiedostoon linkin toiselle sivulle.  

<img width="388" alt="image" src="https://github.com/user-attachments/assets/4d96b3b7-c871-4f3a-b07a-791e260c9ad8" />  

<img width="472" alt="image" src="https://github.com/user-attachments/assets/be4eb343-0b72-4376-8f68-21c1f18288f5" />  

<img width="563" alt="image" src="https://github.com/user-attachments/assets/bd37be4e-f47c-45cc-b8ba-559675156648" />  

Linkit olivat muodossa **http://schoolworks.joonalindholm.me/**  
Oikea muoto tehtävässä C oli **http://joonalindholm.me/schoolworks.html**  
Tehtävään d muodot olisivat olleet oikein, mutta c tehtävässä ei käytetty vielä alidomaineja.  

Sivuni toimivat, niitä pystyi muokkaaman ilman sudoa ja ne linkittivät toisiinsa.  

## d) Alisivut oikeina alidomainena
Aloin googlailemaan ohjeita alidomainien luomiseen ja löysin hyvät ohjeet.  

**https://dev.to/tikam02/configuring-domains-and-sub-domains-in-apache-webserver-1bl1**  

Avasin virtuaalikoneeni -> avasin terminaalin -> yhdistin palvelimeeni **ssh 80.69.172.181**  
-> navigoin konfiguraatio-tiedostoon ja muokkasin sitä sivuilta löytämieni ohjeiden mukaan.  

<img width="588" alt="image" src="https://github.com/user-attachments/assets/e4a6c9de-2daf-4bf9-b1fd-c4aab0418e31" />  
  
<img width="283" alt="image" src="https://github.com/user-attachments/assets/2744336d-f347-4b13-995a-d9effb2ef4b8" />  

Tämän jälkeen aktivoin uuden konfiguraation komennolla:  
**sudo a2ensite joonalindholm.me.conf**  
Sitten käynnistin vielä apachen uudelleen komennolla:  
**sudo systemctl restart apache2**  

Seuraavaksi loin konfiguraationi sopivat kansiot ja niihin html-tiedostot.  

Navigoin kansioon /home/joona/publicsites/ ja loin sinne uuden kansion komennolla:  
**mkdir schoolworks**  

Tein saman myös workworks kansiolle:  
**polku: /home/joona/publicsites/  
Komento: mkdir workworks**   

Kansioiden luomisen jälkeen siirsin tehtävän c html tiedostot uusiin kansioihin.  

Komennot:  
**mv ~/publicsites/joonalindholm.me/schoolworks.html ~/publicsites/schoolworks/  
mv ~/publicsites/joonalindholm.me/workworks.html ~/publicsites/workworks/**  

Html-tiedostojen siirron jälkeen minun piti käydä muokkaamassa niiden rakenne takaisin alidomain muotoon.  
Tarkemmin muutin siis seuraavan kohdan esimerkiksi schoolworks.html tiedostosta:

**<li><a href="http://joonalindholm.me/workworks.html">Workworks</a></li>**  

Tämä piti muuttaa muotoon:  

**<li><a href="http://¨workworks.joonalindholm.me/workworks.html">Workworks</a></li>**  

Tein nämä korjaukset kaikkiin html-tiedostoihin eli index.html, schoolworks.html ja workworks.html.  

<img width="473" alt="image" src="https://github.com/user-attachments/assets/76dea76b-f2d8-467d-86a8-29d5b49e62ea" />  

Kävin vielä tutkimassa tekemäni muutokset konfiguraatioon ja muutin alisivuni osoittamaan etusivulleni.  
Tämän jälkeen käynnistin apache2:sen uudelleen.  

**sudo a2ensite joonalindholm.me.conf**  
**sudo systemctl restart apache2**  

<img width="329" alt="image" src="https://github.com/user-attachments/assets/cabc503a-0c53-4bd4-8831-e3a813676c92" />  

Seuraavaksi lähdin muokkaamaan dns asetuksiani NameCheap-sivuilta, että alidomainit saadaan toimintaan.  

<img width="659" alt="image" src="https://github.com/user-attachments/assets/29a1a4c4-1886-4c41-b56e-3c621f215ddd" />  

Tämän jälkeen kokeilin sivuja, mutta ne eivät heti toimineet. Noin 30 minuutin kuluttua sivut alkoivat toimimaan.  

joonalindholm.me = toi käyttäjän etusivulle, koska CNAME record oli wwww.  
Käyttäjän ei siis tarvitse syöttää osoitekenttään erikseen www.joonalindholm.me, koska CNAME on määritetty.  

Osoitekenttään syötettynä osoite toi aina etusivulle, koska apache2 konfiguraatio ja dns asetukset olivat säädetty niin.  

<img width="415" alt="image" src="https://github.com/user-attachments/assets/382ecb4f-e00e-4403-b523-a53d3a984ec3" />  

<img width="412" alt="image" src="https://github.com/user-attachments/assets/1a41e592-19cb-4569-ba5c-b12b0da98ad0" />  

Muokkaukset, joita tein konfiguraatio-tiedostoon rikkoi sivustoni sisäiset linkit.  
Kävin vielä korjaamassa kansiot oikeiksi konfiguraatiossa, niin sain sivustoni linkit takaisin toimintaan.  

<img width="314" alt="image" src="https://github.com/user-attachments/assets/c68fba44-8b4e-4a84-b5fd-40f09b30e502" />  

Loppujen lopuksi en ollut aivan varma olinko täyttänyt tehtävänantoa tämän d-tehtävän osalta.  

## e) Tutki jonkin nimen DNS-tietoja 'host' ja 'dig' -komennoilla.

Aloitin tehtävän 23.2. sunnuntaina noin klo 17 aikaan.  
kirjoitin terminaaliin host joonalindholm.me ja sain seuraavan virheen.  

<img width="348" alt="image" src="https://github.com/user-attachments/assets/0f7b07e7-dd25-4591-8edc-7a319f10e756" />  

Googlasin virheen "host command not found" ja löysin ohjeet, joissa kerrotiin kuinka asennetaan host työkalu.  

https://ioflood.com/blog/install-host-command-linux/  

Ohjeissa käytettiin debianille komentoa:  
**sudo apt-get install bind9-host**  
Asennuksen jälkeen kokeilin uudestaan host-komentoa ja komento toimi.  

joonalindholm.me has address 80.69.172.181  
joonalindholm.me mail is handled by 20 eforward5.registrar-servers.com.  
joonalindholm.me mail is handled by 10 eforward2.registrar-servers.com.  
joonalindholm.me mail is handled by 10 eforward1.registrar-servers.com.  
joonalindholm.me mail is handled by 15 eforward4.registrar-servers.com.  
joonalindholm.me mail is handled by 10 eforward3.registrar-servers.com.  

Ensimmäisellä rivillä oli sivujeni ip-osoite ja loput rivit olivat ilmeisesti DNS MX recordeja. 

Cloudflaren artikkelissa kerrotaan MX-recordien sähköpostiohjauksista ja prioriteettiarvoista, joiden mukaan palvelin käsittelee saapuvat viestit.  

Mitä pienempi "handled by" -numero, niin sitä korkeammalla prioriteetilla viesti käsitellään.  
Kyseessä siis sähköpostiviestit.  

https://www.cloudflare.com/learning/dns/dns-records/dns-mx-record/  

Host komennon käyttö name.cheap.com-sivustolle antoi vähemmän rivejä.  
namecheap käyttää ilmeisesti vain kahta sähköpostipalvelinta ja ensimmäiselle riville tuli namecheap sivun palvelimen ip-osoite.  

Komento: **host namecheap.com**  

namecheap.com has address 198.54.117.250  
namecheap.com mail is handled by 5 mx1.jellyfish.systems.  
namecheap.com mail is handled by 10 mx2.jellyfish.systems.  

Seuraavaksi halusin kokeilla, mitä host-tietoja youtube-sivusto näyttää.  

Komento: **host youtube.com**  
youtube.com has address 142.250.74.78  
youtube.com has IPv6 address 2a00:1450:400f:802::200e  
youtube.com mail is handled by 0 smtp.google.com.  

Youtubella oli ipv6 tuki ja sen sähköpostipalvelin oli googlen hallinnoima.  
Youtube on osa googlea, joten tämä on ymmärrettävää.  

Seuraavaksi kokeilin dig komentoa.  
Tämäkin työkalu puuttui. Tein nopean googlauksen ja asennuksen.  

https://askubuntu.com/questions/25098/how-do-i-install-dig  

<img width="380" alt="image" src="https://github.com/user-attachments/assets/914e0b3e-6fba-4c86-87eb-bc2c1f8c0ce8" />  

---

Komento: **dig joonalindholm.me**  

; <<>> DiG 9.18.33-1~deb12u2-Debian <<>> joonalindholm.me  
;; global options: +cmd  
;; Got answer:  
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 46148  
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1  

;; OPT PSEUDOSECTION:  
; EDNS: version: 0, flags:; udp: 512  
;; QUESTION SECTION:  
;joonalindholm.me.		IN	A  

;; ANSWER SECTION:  
joonalindholm.me.	1799	IN	A	80.69.172.181  

;; Query time: 48 msec  
;; SERVER: 94.237.127.9#53(94.237.127.9) (UDP)  
;; WHEN: Sun Feb 23 15:52:03 UTC 2025  
;; MSG SIZE  rcvd: 61  

komento: **dig namecheap.com**  

; <<>> DiG 9.18.33-1~deb12u2-Debian <<>> namecheap.com  
;; global options: +cmd  
;; Got answer:  
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 61260  
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1  

;; OPT PSEUDOSECTION:  
; EDNS: version: 0, flags:; udp: 512  
;; QUESTION SECTION:  
;namecheap.com.			IN	A  

;; ANSWER SECTION:  
namecheap.com.		60	IN	A	198.54.117.250  

;; Query time: 8 msec  
;; SERVER: 94.237.127.9#53(94.237.127.9) (UDP)  
;; WHEN: Sun Feb 23 17:47:18 UTC 2025  
;; MSG SIZE  rcvd: 58  

---

komento: **dig youtube.com**  

; <<>> DiG 9.18.33-1~deb12u2-Debian <<>> youtube.com  
;; global options: +cmd  
;; Got answer:  
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 63774  
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1  

;; OPT PSEUDOSECTION:  
; EDNS: version: 0, flags:; udp: 512  
;; QUESTION SECTION:  
;youtube.com.			IN	A  

;; ANSWER SECTION:  
youtube.com.		232	IN	A	142.250.74.78  

;; Query time: 4 msec  
;; SERVER: 94.237.127.9#53(94.237.127.9) (UDP)  
;; WHEN: Sun Feb 23 17:42:35 UTC 2025  
;; MSG SIZE  rcvd: 56  

---










