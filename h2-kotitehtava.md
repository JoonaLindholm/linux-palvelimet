# Kotitehtävä h2 raportti  

## Sisällys ja tehtävät  

x) Lue ja tiivistä Karvinen 2020: Command line basics revisited.  
https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited  

a) Micro-editorin asennus.  

b) Komentoriviohjelmien asennus apt-get komennolla.  

c) FHS. Kansioiden esittely.  

d) Grep-komennon esittely.  

e) Pipe-komennon esittely.  

f) Koneen raudan listaus komentorivillä.  

g) Analysoi lokeja.  

h) Micro-editorin plugin.  


## x) Tiisitelmä tulee tähän  

## a) Micro editorin asennus  
Aloitin asennuksen 23.1. klo 13:30.  

Tietokoneen resurssit:  
- B550M-ITX/ac -emolevy  
- Amd Ryzen 7 5800X3D -prosessori  
- 32 gb ram muistia  
- Noin 2 tb ssd levytilaa  
- 3060ti 8GB GDDR6 -näytönohjain  

VM Linuxin resurssit ja asetukset:  
<img width="393" alt="image" src="https://github.com/user-attachments/assets/2338aa07-4497-4842-a83d-3402128cca0f" />


Virtual linuxin käynnistys -> salasana -> työpöydältä Applications -> Terminal Emulator  

<img width="628" alt="image" src="https://github.com/user-attachments/assets/b1ca6d91-a252-49d6-b6f0-50629a4f2c7b" />  

Tässä vaiheessa muistin, että olen asentanut jo tuon Micro-ohjelman.  
Voisin siis harjoituksen vuoksi ensin poistaa sen. Lähdin googlailemaan kuinka ohjelmia voi poistaa.  
Googlesta löytyi joku keskustelu aiheesta:  
https://support.google.com/chromebook/thread/211306991/uninstall-linux-apps-using-terminal?hl=en  
Kokeillaan "sudo apt-get remove $package-name" komentoa. Package namen tilalle tulisi micro.  

<img width="239" alt="image" src="https://github.com/user-attachments/assets/31a23680-6867-4e69-8790-04924cf5720c" />  

Komentorivin mukaan homma meni maaliin.  

<img width="413" alt="image" src="https://github.com/user-attachments/assets/db9ab217-e326-42dc-b45f-b5a307e1dcf6" />

Hienoa! Nyt voimme asentaa tuon micron uudestaan. Samassa keskustelussa on myös ohjeet asentamiseen.  
Komento onkin melkein sama, mutta removen tilalle tuleekin install. Loogista.  
Sudo apt-get install micro -komento käyttöön.  

<img width="410" alt="image" src="https://github.com/user-attachments/assets/d890bc48-acd0-43d9-8abf-50622b0e3488" />

Tämäkin onnistui helposti. Nyt on mikro poistettu ja asennettu!  

## Komentoriviohjelmien asennus apt-get komennolla.  

Pitäisi asentaa kolme komentoriviohjelmaa apt-get komentoa käyttäen.  
Löysin youtubesta videon, jossa oli mielenkiintoisia ohjelmia.  
https://www.youtube.com/watch?v=FXu428tLhdE  

Valitsin videon ohjelmista seuraavat.  

btop  
ranger  
neofetch  

Tehtävänannossa kysytään komentoa, jolla asennetaan kaikki nuo kerralla.  
Kokeillaan yksinkertaisesti laittaa nuo nimet peräkkäin eli komento olisi:  
Sudo apt-get install btop ranger neofetch  

<img width="431" alt="image" src="https://github.com/user-attachments/assets/d30dceea-d2c8-4790-91cb-3d95ecc90320" />  

<img width="413" alt="image" src="https://github.com/user-attachments/assets/add8a8fe-cf6e-415c-ab75-d5a9e8024d8c" />  

Asennukset menivät varmaankin hyvin. Kokeillaan ohjelmia.  

### btop  
Tämän ohjelman tarkoituksena on, että käyttäjä voi seurata resurssien käyttöä reaaliajassa.  
Käyttäjä voi myös sulkea ohjelmia btopin kautta.

Kirjoitin terminaaliin btop.  

<img width="98" alt="image" src="https://github.com/user-attachments/assets/dfa3c92f-51dd-43ed-95ee-f81f4eb60598" />  

Aukesi allaoleva ikkuna:  

<img width="791" alt="image" src="https://github.com/user-attachments/assets/d47ba70f-20c0-472c-a470-6d7bdf345cee" />  

Kokeilin sulkea ohjelman käyttäen btopia. Kokeillaan voiko btop "tappaa" itsensä.  

<img width="788" alt="image" src="https://github.com/user-attachments/assets/fb428a5f-4802-4eab-826a-ec94efbe027d" />  

Valitsin hiirellä btopin luettelosta ja painoin alhaalta "kill".  

<img width="248" alt="image" src="https://github.com/user-attachments/assets/2b9cfd25-18a1-4dbc-9fd2-dccc39d03089" />  

Yes Yes haluamme päästä itsestämme eroon.  

<img width="791" alt="image" src="https://github.com/user-attachments/assets/88d0c7a7-a796-4df9-99de-d5c8b9478327" />  

btop taisi mennä tästä solmuun tai ainakin se jumittui ja komentorivi vain sekoilee.  

<img width="793" alt="image" src="https://github.com/user-attachments/assets/1490ceb4-ce0e-4fa2-9e3e-9129d26db9d1" />  

Jouduin lopulta sulkemaan koko terminaalin yläkulman x-painikkeesta.  
Haluan kokeilla vielä, mitä terminate tekee btopille.  

<img width="241" alt="image" src="https://github.com/user-attachments/assets/9bbff5c4-5d2a-4ad3-8516-46ea0d72e81c" />  

<img width="247" alt="image" src="https://github.com/user-attachments/assets/2ce2168f-af5d-48a6-a179-34f64375cfe5" />  

Painetaan taas "yes".  

<img width="899" alt="image" src="https://github.com/user-attachments/assets/3f68bc29-6bec-47aa-9cec-792927ba5b6f" />  

Tämä sulki koko terminaalin ja palasimme takaisin työpöydälle.  
Ehkä btopille löytyy vielä oikeaa käyttöä tulevaisuudessa eikä tämmöistä leikkimielistä testailua.  

## ranger  

Tämän ohjelman tarkoituksena on tarjota tehokas, intuitiivinen ja helppokäyttöinen käyttöliittymä tiedostonhallintaan.  

Kokeilin kirjoittaa ranger komentoriville ja se tuotti heti tulosta.  

<img width="452" alt="image" src="https://github.com/user-attachments/assets/328818cd-ab15-4f14-86aa-8efabe420445" />  

Menin tietenkin sotkemaan niitä. Ranger-ohjelmassa pystyy liikkumaan nuolinäppäimiä ja hiirtä käyttäen kansioista toiseen.  

<img width="2506" alt="image" src="https://github.com/user-attachments/assets/874ab44e-28d6-4675-8afb-7abe11c2a3c5" />  

Viikonpaivat kansiossa näytti olevan tiedostoja, jotka loimme tunnilla.  

<img width="2506" alt="image" src="https://github.com/user-attachments/assets/ec180da9-bdf5-4623-a976-0c88918a4e6f" />  

Valitsin yhdestä kansiosta tektitiedoston ja painoin entteriä.  
Avautui editor ohjelman valinta kohta. Valitsin micron.  

<img width="323" alt="image" src="https://github.com/user-attachments/assets/b2d6b752-f877-4a25-9206-30d4a57648ba" />  

Kirjoittelin tiedostoon jotain testiksi ja tämän jälkeen en tiennyt miten pääsen takaisin kansionäkymään.  
Ruudun alaosassa oli kuitenkin ctrl-g : help, joten painoin sitä.

<img width="524" alt="image" src="https://github.com/user-attachments/assets/b3d301b7-cb43-45f6-905d-2b1e2f3d86fc" />  

<img width="789" alt="image" src="https://github.com/user-attachments/assets/13d6a14d-1203-4377-b572-775e32c5d873" />  

Tallennetaan tärkeä kirjoitus ctrl-s ja sitten suljetaan editori ctrl-q.  
Tämä palautti minut takaisin kansionäkymään, johon oli ilmestynyt mahtava kirjoitukseni.  
Nähtävästi ranger ei ymmärrä skandeja.  

<img width="629" alt="image" src="https://github.com/user-attachments/assets/66e69379-672d-4569-9221-24d6311f84ca" />  




























 





## Lähdeluettelo  
- Tero Karvinen 2020
https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited  

- Google support -keskustelu
  https://support.google.com/chromebook/thread/211306991/uninstall-linux-apps-using-terminal?hl=en

- 
