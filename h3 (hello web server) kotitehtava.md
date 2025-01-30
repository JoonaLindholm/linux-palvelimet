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

Kokeilin vielä lopuksi komentoa  
**sudo systemctl status apache2**  

<img width="419" alt="image" src="https://github.com/user-attachments/assets/09ea7b2e-7b90-4a4e-ae75-297f4985fc3f" />

Palvelin toimi hyvin ja oli statuksen mukaan aktiivinen.  

## b) Apache2 lokien tutkiminen ja analysointi  

Aloitin tehtävän terminaalissa komennolla  
sudo tail /var/log/apache2/error.log  
Tämä tulosti kymmenen viimeisintä lokimerkintää access.log tiedostosta.  

## c) 
Tein tehtävää opettajani Tero Karvisen ohjeiden mukaan.  
**https://terokarvinen.com/2018/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/**

Aloitin luomalla hattu.example.com.conf-asetustiedoston käytettävissä oleviin sivuihin.  
Komento:  
**sudoedit /etc/apache2/sites-available/hattu.example.com.conf**   

<img width="576" alt="image" src="https://github.com/user-attachments/assets/bcedff98-a006-47ee-9129-29df8e97dcae" />

Tallensin ja suljin nano-editorin komennoilla:   
**ctrl-s -> ctrl-x**  

sudo a2ensite hattu.example.com
sudo systemctl restart apache2
cd /etc/apache2/sites-enabled/ -> ls
sudo a2dissite Joonansivut.example.com.conf
<img width="427" alt="image" src="https://github.com/user-attachments/assets/a767608d-b919-43ee-a120-c69995b34e85" />

<img width="430" alt="image" src="https://github.com/user-attachments/assets/ece34dc4-3a16-4b44-838b-fe6e5c098aa7" />

mkdir -p /home/joona/publicsites/hattu.example.com/
echo hattu > /home/joona/publicsites//hattu.example.com/

Curl localhost

<img width="299" alt="image" src="https://github.com/user-attachments/assets/405988bf-0e2f-410d-9c0f-a577a1f12ecc" />

Seuraavaksi muokkasin index.html tiedostoa, että sain muutettua sivun tietoja.  

<img width="459" alt="image" src="https://github.com/user-attachments/assets/acba5887-d045-41a2-8955-5f873fb10b15" />

Avasin tiedoston komennolla **nano index.html**  
Lisäsin perus html-koodia:  
                                                            
<!DOCTYPE html>
<html lang="fi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hattu</title>
</head>
<body>
    <h1>Tervetuloa Hattu-sivulle!</h1>
    <p>Hatut on jees!</p>
</body>
</html> 

<img width="454" alt="image" src="https://github.com/user-attachments/assets/a342f6b7-bac2-4247-951a-aca16b51248b" />

crtl-s (tallennus) -> ctrl-x (exit)  

Menin kokeilemaan pääsenkö selaimella katsomaan hattu-sivua.  

<img width="394" alt="image" src="https://github.com/user-attachments/assets/ab4b4ec9-766b-4b6f-9031-4f99dfd9fada" />  

Hattu-sivu toimi hyvin ja oli päivittynyt.


