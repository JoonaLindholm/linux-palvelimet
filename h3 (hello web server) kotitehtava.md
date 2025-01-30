# H3 kotitehtävät (Hello Web Server)  

## Tehtävänannot ja raportin sisältö  

**https://terokarvinen.com/linux-palvelimet/#h3-hello-web-server**  

**x)** Lue ja tiivistä  
**The Apache Software Foundation 2023: Apache HTTP Server Version 2.4 Documentation: Name-based Virtual Host Support**    
**Karvinen 2018: Name Based Virtual Hosts on Apache – Multiple Websites to Single IP Address**  

**a)** Weppipalvelimen toimivuuden testaus    

**b)** Apache2 lokien tutkiminen ja analysointi  

**c)** Etusivu uusiksi. Tee uusi name based virtual host. Sivun tulee näkyä suoraan palvelimen etusivulla http://localhost/. Sivua pitää pystyä muokkaamaan normaalina käyttäjänä, ilman sudoa. Tee uusi, laita vanhat pois päältä. Uusi sivu on hattu.example.com, ja tämän pitää näkyä: asetustiedoston nimessä, asetustiedoston ServerName-muuttujassa sekä etusivun sisällössä (esim title, h1 tai p).  

**e)** Tee validi HTML5 sivu.  

**f)** Anna esimerkit 'curl -I' ja 'curl' -komennoista. Selitä 'curl -I' muutamasta näyttämästä otsakkeesta (response header), mitä ne tarkoittavat.  

**m)** Vapaaehtoinen, suosittelen tekemään: Hanki GitHub Education -paketti.  

**o)** Vapaaehtoinen, vaikea: Laita sama tietokone vastaamaan kahdellla eri sivulla kahdesta eri nimestä. Eli kaksi weppisiteä samalla koneelle, esim. foo.example.com ja bar.example.com. Voit simuloida nimipalvelun toimintaa hosts-tiedoston avulla.  

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

## x)  
Tähän tulee tiivistelmät  

## a)  Weppipalvelimen toimivuuden testaus  

Apache2 -weppipalvelin asennettiin jo tunnilla, joten aloitin tehtävän kokeilemalla toimiiko se.  

Avasin terminaalin ja annoin syötteen **curl localhost**  

<img width="187" alt="image" src="https://github.com/user-attachments/assets/5706137a-eada-4c11-abd1-f9a9844af14a" />  

Tämä tulosti sivun sisällön HTML-koodina.  
Menin myös guin kautta kokeilemaan aukeaako localhost -sivu.  
Annoin osoitekenttään osoitteen:  
**http://localhost/**  

<img width="394" alt="image" src="https://github.com/user-attachments/assets/656e5703-08b2-49a3-a069-268c98cdf40f" />  

Palvelin toimi hyvin.  

## b) Apache2 lokien tutkiminen ja analysointi  

Aloitin tehtävän navigoimalla oikeaan kansioon terminaalissa komennolla  











