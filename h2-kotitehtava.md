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


## x) Command line basics revisited -tiivistelmä

Komentorivillä voi käyttää järjestelmää nopeasti ja kätevästi tekstipohjaisilla komennoilla.  

Peruskomentoja:  

- pwd = näyttää käyttäjälle kansion, jossa hän on komennon suorittaessa.
- ls = listaa tämän kansion tiedostot.
- cd = käyttäjä voi vaihtaa hakemistoa.
- mkdir = käyttäjä voi luoda uuden kansion.
- 


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

## b) Komentoriviohjelmien asennus apt-get komennolla.  

Pitäisi asentaa kolme komentoriviohjelmaa apt-get komentoa käyttäen.  
Löysin youtubesta videon, jossa oli mielenkiintoisia ohjelmia.  
https://www.youtube.com/watch?v=FXu428tLhdE  

Valitsin videon ohjelmista seuraavat.  

btop  
ranger  
neofetch/hollywood  

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

Ranger-ohjelmassa pystyy liikkumaan nuolinäppäimiä ja hiirtä käyttäen kansioista toiseen.  

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

## neofetch    

Neofetchin tarkoituksena on listata nätisti kaikki järjestelmäntiedot.  
Aloitetaan kirjoittamalla neofetch komentoriville.  

<img width="379" alt="image" src="https://github.com/user-attachments/assets/493f9252-ee40-4004-88e5-b6e0e219686e" />  

No tämä olikin aika yksinkertainen ohjelma ja toiminnot jäivät tähän.  

Kokeillaan vielä asentaa yksi ohjelma. Videolla oli myös maininta hauskannäköisestä ohjelmasta nimeltä hollywood.

## Hollywood

sudo apt-get install hollywood  
Tämän jälkeen tuli pitkät rivit komentorivejä.  
Kokeillaan ohjelmaa.  

<img width="790" alt="image" src="https://github.com/user-attachments/assets/f7261d53-f652-42dc-8f8b-72026d308153" />  

Mitä tästä nyt sanoisi. Ohjelma on nimensä mukainen ja pyörittää ruudulla vilisevää dataa, joka ei ilmeisesti kuitenkaan tarkoita mitään.  
Aika hauska "lelu".  

Kokeillaan laittaa tämä koko näytön levyiseksi spektaakkeliksi.  

<img width="2559" alt="image" src="https://github.com/user-attachments/assets/2ec2c80f-4aef-4e22-a81c-a9f4815a4572" />  

Kuvassa olevat "tiedot" liikkuvat ja vaihtuvat.  
Tällä voi varmaankin esittää neroa vaimolle tms...  

## c) FHS. Kansioiden esittely.  

Aloitin tehtävän 24.1. klo 16.  
Tehtävänantona oli esitellä tärkeitä linuxin kansioita opettajan materiaalin avulla.  

https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited  

Aloitin kirjoittamalla dir terminaaliin.  

<img width="410" alt="image" src="https://github.com/user-attachments/assets/4e8ca137-65d3-43bf-93b3-7fa3373e957f" />  

Käytin cd .. kehotetta ja siirryin ylöspäin kunnes olin root kansiossa.  
Kokeilin, mitä käy jos yritän vielä enemmän siirtyä kansioissa ylöspäin, mutta mitään ei tapahtunut.  
Root kansio oli ylin kansio, johon pääsin. Listasin sen sisällön ls komennolla.  

<img width="409" alt="image" src="https://github.com/user-attachments/assets/7cc1e3cf-172b-4ebf-9229-f35f9317e1c1" />  

Tästä juurikansiosta voi navigoida muihin kansioihin. Siirrytään home kansioon tutkimaan, mitä sieltä löytyy.  
cd home komennolla eteenpäin.  

<img width="419" alt="image" src="https://github.com/user-attachments/assets/09f1761a-825e-409c-b4d6-9337bde45158" />  

Home kansiossa oli käyttäjän kansiot. Sieltä löytyi vain omani tällä kertaa.  
Jatkoin matkaa joona kansioon.  

cd joona komennolla siirryin joona kansioon, jossa oli käyttäjäni tiedostot. Esimerkiksi aiemmin luotu viikonpaiva kansio.  

<img width="412" alt="image" src="https://github.com/user-attachments/assets/9f7ed86e-fdba-4735-b78f-d030a5064e4e" />  

Palasin takaisin juurikansioon käyttämällä kaksi kertaa cd .. komentoa.  

<img width="377" alt="image" src="https://github.com/user-attachments/assets/85d8d769-6d04-4d38-94b1-f428795a4145" />  

Seuraavaksi menin tutkimaan, mitä etc kansiosta löytyy. Tämä kansio oli juurikansiossa.  

Käytin cd etc komentoa ja listasin tiedostot ls komennolla.  

etc kansiossa oli hyvin paljon tiedostoja yms.  

<img width="449" alt="image" src="https://github.com/user-attachments/assets/e8984571-4461-4b1d-a247-9d81d1a07e0e" />  

Kokeilin voinko tehdä jotain gimp nimiselle tiedostolle.  
Selvisi, että kyseessä oli ilmeisesti gimp ohjelman kansio, jossa oli siihen liittyviä tiedostoja.  

<img width="374" alt="image" src="https://github.com/user-attachments/assets/28812d1e-d856-4597-8baf-5d0e6873d698" />  

Etc kansiossa oli Teron ohjeiden mukaan kaikki järjestelmän asetukset tekstitiedostoina.  
Ihmisille luettavassa muodossa.  

Seuraavaksi palasin takaisin juurikansioon cd .. komennolla ja sieltä media kansioon cd media komennolla. Tämän jälkeen piti vielä valita käyttäjäkansioni joona.  
Media kansiossa ei ollut mitään, koska minulla ei ollut irroitettavaa mediaa kiinni virtual tietokoneessani. Siellä olisi voinut olla vaikka usb-tikun sisältö.  

<img width="154" alt="image" src="https://github.com/user-attachments/assets/757e4215-c554-4869-ab04-4946f13e7bc1" />  

Palasin taas juurikansioon etsimään seuraavaa tehtävänannon kansiota.  
Siellä näkyi var kansio. Navigoin sinne cd var komennolla ja listasin kansion sisällön ls komennolla. 
   
<img width="500" alt="image" src="https://github.com/user-attachments/assets/e2db2eea-acd8-44e7-9eaa-ff1cd83f8c14" />  

var kansiosta jatkoin navigointia log kansioon. cd log komennolla.  

<img width="463" alt="image" src="https://github.com/user-attachments/assets/fc25d134-2200-4e3a-b026-7d8e7bd8049a" />  

Tässä kansiossa oli lokitiedostoja.  
Kokeillaan avata README tiedosto.  

<img width="389" alt="image" src="https://github.com/user-attachments/assets/911676fd-7805-4f41-b88e-f9c39022ce70" />  

README avautui.  

<img width="695" alt="image" src="https://github.com/user-attachments/assets/dd0ad584-fc0b-43fe-ba0d-74217fef64db" />  

Sain READMEsta selville, että lokitiedostot ovatkin journalctrl journalissa, joka on ilmeisesti päivitetty versio Syslogista.  

## d) grep-komennon esittely  

Seuraavaksi tehtävänäni oli esitellä grep-komentoa.  
Kysyin googlelta, mikä on grep, koska en enää muistanut tarkalleen, mistä siinä olikaan kyse.  

https://www.google.com/search?q=what+is+linux+grep&oq=what+is+linux+grep&gs_lcrp=EgZjaHJvbWUyBggAEEUYOTIGCAEQLhhA0gEINDk4NmowajGoAgiwAgE&sourceid=chrome&ie=UTF-8  

<img width="550" alt="image" src="https://github.com/user-attachments/assets/67a49c72-6fb9-4d02-9c11-9ea6a4c30d9c" />  

Eli kyseessä on vähän kuin hakukone terminaaliin.  
Seuraavaksi kokeilin grepin käyttöä.  
Heitin juurikansioon suoraan vain grep error ihan vain testiksi, mitä käy.  
No koko terminaali jäätyi..  hups.  

<img width="330" alt="image" src="https://github.com/user-attachments/assets/7e6bd4e5-3674-4a3d-bc7d-0c2608b3c210" />  

Terminaali ei ollutkaan jäätynyt. Pystyin kirjoittelemaan kaikenlaista komentoriville, mutta mitään ei kuitenkaan tapahtunut.  

<img width="269" alt="image" src="https://github.com/user-attachments/assets/c045749f-5414-4647-aaff-16cdc0aee599" />  

Suljin terminaalin kokonaan yläkulman x näppäimestä.  
En oikeastaan tiedä, mitä aiemmin tapahtui.  
Menin tutkimaan tarkempia ohjeita ja löysinkin niitä.  

https://linux-tips.us/lets-learn-about-grep/  

Komentoni oli väärä. Seuraavaksi kokeilin eri komentoa.  
grep "error" /var/log/syslog  

# KESKEN!! JATKA GREP!  

## e) Pipe  


## f) Rauta  
Tässä tehtävässä minun piti listata tietokoneeni rauta käyttäen komentoa.  
Yritin ensin suoraan tehtävänannon komentoa, mutta minun pitikin asentaa ensin tarvittava ohjelma.  

<img width="411" alt="image" src="https://github.com/user-attachments/assets/02638cd5-727d-44c3-a90f-17c296322f3e" />  

Asennuksen jälkeen kokeilin uudestaan komentoa.  
Sudo lshw -short -sanitize  

<img width="417" alt="image" src="https://github.com/user-attachments/assets/4f193839-28bc-419a-a918-3ae0510bf80a" />  

Listaus näyttäisi olevan virtuaalikoneen ja sille antamani resurssien rauta.  

- Listaus alkaa itse pääkomponentista eli VirtualBoxista itsestään.
  Tämä on merkitty luokkaan system.  
  
  <img width="121" alt="image" src="https://github.com/user-attachments/assets/53cf25e7-68ee-40b5-8b5a-4ad287df4412" />  
  
Seuraavaksi listauksessa tulee virtuaalisen emolevyn väylä eli luokaltaan bus.  

<img width="263" alt="image" src="https://github.com/user-attachments/assets/30b0e5f6-1513-4b8c-9515-5898b2a58bb3" />  

Biokselle on annettu 128KiB muistia käytettäväksi ja 11 GiB on ram-muistia virtuaalikoneelle.  

<img width="307" alt="image" src="https://github.com/user-attachments/assets/950e66cc-ce15-4869-a328-ce7891735155" />  

Tämän jälkeen listauksessa tulee prosessori. Tässä kohdassa ei ole kuitenkaan kerrottu virtuaalikoneen saamia prosessorin resursseja sen tarkemmin. 

<img width="394" alt="image" src="https://github.com/user-attachments/assets/c93bbf2e-41b9-4f4d-8015-a732e4a4c0cc" />  









































ls


cd log


cd var





ls

















dc .










































 





## Lähdeluettelo  

- Tero Karvinen 2020  
https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited 
  
- Google support -keskustelu  
  https://support.google.com/chromebook/thread/211306991/uninstall-linux-apps-using-terminal?hl=en  

- Youtube video linux ohjelmista.  
  https://www.youtube.com/watch?v=FXu428tLhdE  

  
