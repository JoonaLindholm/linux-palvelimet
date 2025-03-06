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
- less = näyttää tiedoston sisällön sivu kerrallaan.  
- | (pipe) = Yhdistää kahden komennon tuloksen, jolloin ensimmäisen komennon tuottama tulos siirretään seuraavalle komennolle.  
- nano, micro jne. = tekstieditoreja.  
- mv = käyttäjä voi siirtää tai nimetä tiedostoja tai kansioita.  
- cp = kopioi tiedoston tai kansion. "-r" lisättyäsi voit kopioida myös kansioiden sisällön.  
- rm = poistaa tiedoston. "-r" lisättyäsi voit poistaa myös kansion ja sen sisällön.  
- rmdir = poistaa tyhjän kansion.  
- ssh = avaa etäyhteyden turvallisesti palvelimelle.  
- scp = kopioi tiedoston tai kansion turvallisesti etäpalvelimelle.  
- man = näyttää komennon manuaalisivut.  
-  --help tai -h = näyttää komennon lyhyen avun.  
- history = näyttää käyttäjän aiemmin suorittamat komennot.
   
### sudo komennot = suorittaa komennon korkeammilla käyttöoikeuksilla.  

- sudo apt-get update = päivittää saatavilla olevien pakettien listauksen.  
- sudo apt-get install (ohjelmannimi) = asentaa ohjelman.  
- sudo apt-get purge (ohjelmannimi) = poistaa ohjelman ja sen asetustiedostot.  
- dpkg --listfiles (ohjelmannimi) = näyttää ohjelman asentamat tiedostot.  
- tab = täydentää komennot tai tiedostonimet automaattisesti, jos mahdollista.  

### Tärkeitä kansioita:  

- / = juurihakemisto, josta kaikki alkaa.
- /home/ = käyttäjien kotihakemistot.
- /etc/ = järjestelmän asetukset.
- /media/ = irrotettavat tallennusvälineet, kuten CD-levyt ja USB-tikut.
- /var/log/ = järjestelmälokit.  

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

Tässä vaiheessa muistin, että olin jo asentanut tuon Micro-ohjelman.  
Ajattelin, että voisin siis harjoituksen vuoksi ensin poistaa sen.  
Lähdin googlailemaan kuinka ohjelmia voi poistaa.  
 
Löysin google-haulla keskustelun aiheesta:  
https://support.google.com/chromebook/thread/211306991/uninstall-linux-apps-using-terminal?hl=en  
Kokeillaan "sudo apt-get remove $package-name" komentoa. Package namen tilalla tuli olla "micro".  

<img width="239" alt="image" src="https://github.com/user-attachments/assets/31a23680-6867-4e69-8790-04924cf5720c" />  

Komentorivin mukaan homma meni maaliin.  

<img width="413" alt="image" src="https://github.com/user-attachments/assets/db9ab217-e326-42dc-b45f-b5a307e1dcf6" />  

Hienoa! Pystyin asentamaan micron uudestaan. Samassa keskustelussa oli myös ohjeet asentamiseen.  
Komento olikin melkein sama, mutta removen tilalle tuli install. Loogista.  

Sudo apt-get install micro -komento.  

<img width="410" alt="image" src="https://github.com/user-attachments/assets/d890bc48-acd0-43d9-8abf-50622b0e3488" />  

Tämäkin onnistui helposti. Olin nyt poistanut micron ja asentanut sen uudestaan.  

## b) Komentoriviohjelmien asennus apt-get komennolla.  

Piti asentaa kolme komentoriviohjelmaa apt-get komentoa käyttäen.  
Löysin youtubesta videon, jossa oli mielenkiintoisia ohjelmia.  

https://www.youtube.com/watch?v=FXu428tLhdE  

Valitsin videon ohjelmista seuraavat.  

btop  
ranger  
neofetch/hollywood  

Tehtävänannossa kysyttiin komentoa, jolla asennetiin kaikki nuo kerrallaan.  
Kokeilin yksinkertaisesti laittaa nuo nimet peräkkäin eli komento oli:  
Sudo apt-get install btop ranger neofetch  

<img width="431" alt="image" src="https://github.com/user-attachments/assets/d30dceea-d2c8-4790-91cb-3d95ecc90320" />  

<img width="413" alt="image" src="https://github.com/user-attachments/assets/add8a8fe-cf6e-415c-ab75-d5a9e8024d8c" />  

Asennukset menivät hyvin. Kokeilin ohjelmia.  

### btop  
Tämän ohjelman tarkoituksena oli, että käyttäjä voi seurata resurssien käyttöä reaaliajassa.  
Käyttäjä voi myös sulkea ohjelmia btopin kautta.  

Kirjoitin terminaaliin btop.  

<img width="98" alt="image" src="https://github.com/user-attachments/assets/dfa3c92f-51dd-43ed-95ee-f81f4eb60598" />  

Aukesi allaoleva ikkuna:  

<img width="791" alt="image" src="https://github.com/user-attachments/assets/d47ba70f-20c0-472c-a470-6d7bdf345cee" />  

Kokeilin sulkea ohjelman käyttäen btopia. Kokeilin voiko btop "tappaa" itsensä.  

<img width="788" alt="image" src="https://github.com/user-attachments/assets/fb428a5f-4802-4eab-826a-ec94efbe027d" />  

Valitsin hiirellä btopin luettelosta ja painoin alhaalta "kill".  

<img width="248" alt="image" src="https://github.com/user-attachments/assets/2b9cfd25-18a1-4dbc-9fd2-dccc39d03089" />  

Klikkasin yes.   

<img width="791" alt="image" src="https://github.com/user-attachments/assets/88d0c7a7-a796-4df9-99de-d5c8b9478327" />  

btop taisi mennä tästä solmuun tai ainakin se jumittui ja komentorivi vain sekoili.    

<img width="793" alt="image" src="https://github.com/user-attachments/assets/1490ceb4-ce0e-4fa2-9e3e-9129d26db9d1" />  

Jouduin lopulta sulkemaan koko terminaalin yläkulman x-painikkeesta.  
Halusin vielä kokeilla, mitä terminate tekee btopille.  

<img width="241" alt="image" src="https://github.com/user-attachments/assets/9bbff5c4-5d2a-4ad3-8516-46ea0d72e81c" />  

<img width="247" alt="image" src="https://github.com/user-attachments/assets/2ce2168f-af5d-48a6-a179-34f64375cfe5" />  

Painettiin taas "yes".  

<img width="899" alt="image" src="https://github.com/user-attachments/assets/3f68bc29-6bec-47aa-9cec-792927ba5b6f" />  

Tämä sulki koko terminaalin ja palasimme takaisin työpöydälle.  
Ajattelin, että ehkä btopille löytyisi vielä oikeaa käyttöä tulevaisuudessa eikä tämmöistä leikkimielistä testailua.  

## ranger  

Tämän ohjelman tarkoituksena oli tarjota tehokas, intuitiivinen ja helppokäyttöinen käyttöliittymä tiedostonhallintaan.  

Kokeilin kirjoittaa ranger komentoriville ja se tuotti heti tulosta.  

<img width="452" alt="image" src="https://github.com/user-attachments/assets/328818cd-ab15-4f14-86aa-8efabe420445" />  

Ranger-ohjelmassa pystyi liikkumaan käyttäen nuolinäppäimiä tai hiirtä, liikkuessa kansioista toiseen.  

<img width="2506" alt="image" src="https://github.com/user-attachments/assets/874ab44e-28d6-4675-8afb-7abe11c2a3c5" />  

Viikonpaivat kansiossa näytti olevan tiedostoja, jotka luotiin tunnilla.  

<img width="2506" alt="image" src="https://github.com/user-attachments/assets/ec180da9-bdf5-4623-a976-0c88918a4e6f" />  

Valitsin yhdestä kansiosta tektitiedoston ja painoin entteriä.  
Avautui editor ohjelman valinta kohta. Valitsin micron.  

<img width="323" alt="image" src="https://github.com/user-attachments/assets/b2d6b752-f877-4a25-9206-30d4a57648ba" />  

Kirjoittelin tiedostoon jotain testiksi ja tämän jälkeen en tiennyt miten pääsen takaisin kansionäkymään.  
Ruudun alaosassa oli kuitenkin ctrl-g : help, joten painoin sitä.  

<img width="524" alt="image" src="https://github.com/user-attachments/assets/b3d301b7-cb43-45f6-905d-2b1e2f3d86fc" />  


<img width="789" alt="image" src="https://github.com/user-attachments/assets/13d6a14d-1203-4377-b572-775e32c5d873" />  

Tallensin tärkeän kirjoitukseni ctrl-s -näppäinyhdistelmällä ja sitten suljin editorin ctrl-q -näppäinyhdistelmällä.  
Tämä palautti minut takaisin kansionäkymään, johon oli ilmestynyt mahtava kirjoitukseni.  

Ranger ei ymmärtänyt skandeja tai sitten skandit eivät näkyneet jonkun muun syyn vuoksi.  

<img width="629" alt="image" src="https://github.com/user-attachments/assets/66e69379-672d-4569-9221-24d6311f84ca" />  

## neofetch    

Neofetchin tarkoituksena oli listata nätisti kaikki järjestelmätiedot.  
Aloitin kirjoittamalla neofetch komentoriville.  

<img width="379" alt="image" src="https://github.com/user-attachments/assets/493f9252-ee40-4004-88e5-b6e0e219686e" />  

Kyseessä olikin yksinkertainen ohjelma.  

Kokeilin vielä asentaa yhden ohjelman.  

Videolla oli maininta hauskannäköisestä ohjelmasta nimeltä hollywood.  

## Hollywood  

sudo apt-get install hollywood  
Tämän jälkeen tuli pitkät rivit komentorivejä.  
Kokeillaan ohjelmaa.  

<img width="790" alt="image" src="https://github.com/user-attachments/assets/f7261d53-f652-42dc-8f8b-72026d308153" />  

Ohjelma oli nimensä mukainen ja pyöritti ruudulla vilisevää dataa, joka ei ilmeisesti kuitenkaan tarkoittanut mitään.  

Kokeilin laittaa hollywood -ohjelman koko näytön levyiseksi spektaakkeliksi.  

<img width="2559" alt="image" src="https://github.com/user-attachments/assets/2ec2c80f-4aef-4e22-a81c-a9f4815a4572" />  

Kuvassa olevat "tiedot" liikkuivat ja vaihtuivat.  
Ohjelmalla pystyi varmaankin esittämään neroa puolisolle tai pomolle tms...  

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

Tästä juurikansiosta pystyi navigoimaan muihin kansioihin. Siirryin home kansioon tutkimaan, mitä sieltä löytyi.  
Menin cd home komennolla eteenpäin.  

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
Kokeilin avata README -tiedoston.

<img width="389" alt="image" src="https://github.com/user-attachments/assets/911676fd-7805-4f41-b88e-f9c39022ce70" />  

README avautui.  

<img width="695" alt="image" src="https://github.com/user-attachments/assets/dd0ad584-fc0b-43fe-ba0d-74217fef64db" />  

Sain READMEsta selville, että lokitiedostot ovatkin journalctrl journalissa, joka on ilmeisesti päivitetty versio Syslogista.  

## d) grep-komennon esittely  

Seuraavaksi tehtävänäni oli esitellä grep-komentoa.  
Kysyin googlelta, mikä on grep, koska en enää muistanut tarkalleen, mistä siinä olikaan kyse.  

https://www.google.com/search?q=what+is+linux+grep&oq=what+is+linux+grep&gs_lcrp=EgZjaHJvbWUyBggAEEUYOTIGCAEQLhhA0gEINDk4NmowajGoAgiwAgE&sourceid=chrome&ie=UTF-8  

<img width="550" alt="image" src="https://github.com/user-attachments/assets/67a49c72-6fb9-4d02-9c11-9ea6a4c30d9c" />  

Eli kyseessä oli vähän kuin hakukone terminaaliin.  

Loin kokeiluun tekstitiedoston, jossa oli hedelmiä.  
Loin ensin kansion "hedelmat"  

Komento:  
**mkdir hedelmat**  
Tein tämän omassa kansiossani. /Home/joona/  

<img width="496" alt="image" src="https://github.com/user-attachments/assets/86aab218-19cb-40ae-b9ee-6b56ab1b46a2" />  

Menin hedelmat kansioon ja loin sinne hedelmat.txt.  

Komento: **micro hedelmat.txt**  

<img width="212" alt="image" src="https://github.com/user-attachments/assets/0f285d88-caa3-4da7-88c1-dcdfabdf0ef5" />  

  
<img width="474" alt="image" src="https://github.com/user-attachments/assets/54fc99d2-c7b5-4037-ae15-877907c52160" />  

Ctrl-s tallensi hedelmät micro tekstieditorissa. Seuraavaksi kokeilin grep komentoa hedelmiini.  
Etsin googlesta grep -komentoja ja löysin seuraavan sivun:  

https://linux-tips.us/lets-learn-about-grep/  

Kokeilin miltä riviltä "Persikka" löytyy.  
Komento:  
**grep -n "Persikka"**  

<img width="275" alt="image" src="https://github.com/user-attachments/assets/c7e19f11-cf69-415e-8ea1-0ed974496798" />  

Persikka löytyi riviltä 5.  

Tässä vaiheessa ajattelin, että tekstitiedostoni sisällön täytyy olla monimutkaisempi.  
Chatgpt sai luoda listaamistani hedelmistä tarinan, josta voisin sitten etsiä asioita grepillä.  

<img width="833" alt="image" src="https://github.com/user-attachments/assets/2222618b-ae41-4368-9f9c-9baac448e123" />  

Syntyi "kaunis" tarina hedelmista.  
Kokeilin greppiä tarinaan.  

Etsin rivit, joissa ei esiintynyt sanaa "Omena".  

komento: **grep -v "Omena" hedelmat.txt.**  

<img width="820" alt="image" src="https://github.com/user-attachments/assets/4b8e10d0-8c27-441f-9edb-68dcfaabd56a" />  

Tämä toimi!  

Halusin vielä kokeilla jotain erilaista ja löysin googlaamalla seuraavan sivun:  

https://www.cyberciti.biz/tips/howto-see-grep-command-output-in-colours.html  

Sivun ohjeilla kokeilin seuraavaksi värittää ananakset ja etsiä kaikki rivit, joilla ananas esiintyy.  
Komento: **grep --color "Ananas" hedelmat.txt**   

<img width="812" alt="image" src="https://github.com/user-attachments/assets/52a0f6b9-9f0d-4305-ac9e-0d614f85e53d" />  

Mahtavaa! Ajattelin, että grep voisi olla hyvä työkalu, jos vaikka haluaisi löytää jotain virhelokeja.  

## e) Pipe  
Tehtävänannossa pyydettiin esittelemään putkien käyttöä.  
Putkilla voi ketjuttaa monta toimintoa yhteen hakuun.  

Kokeilin seuraavaksi käyttää pipe | komentoa hedelmat.txt tarinaani.  
Etsitään rivit, joissa esiintyy "Ananas" ja lasketaan monta riviä niitä oli.  
Komento: **grep "Ananas" tarina.txt | wc l**   

<img width="290" alt="image" src="https://github.com/user-attachments/assets/963c1378-bad3-4e71-9cb9-c6730093b30e" />  

Etsittiin ananakset ja laskettiin, että rivejä oli 3.  

## f) Rauta  
Tässä tehtävässä minun piti listata tietokoneeni rauta käyttäen komentoa.  
Yritin ensin suoraan tehtävänannon komentoa, mutta minun pitikin asentaa ensin tarvittava ohjelma.  

<img width="411" alt="image" src="https://github.com/user-attachments/assets/02638cd5-727d-44c3-a90f-17c296322f3e" />  

Asennuksen jälkeen kokeilin uudestaan komentoa.  
**Sudo lshw -short -sanitize**  

<img width="417" alt="image" src="https://github.com/user-attachments/assets/4f193839-28bc-419a-a918-3ae0510bf80a" />  

Listaus näyttäisi olevan virtuaalikoneen ja sille antamani resurssien rauta.    
Listauksessa oli tietokoneen resursseja, mutta virtuaaliversiona eli emuloituna.  

Esimerkiksi bioksella oli 128KiB emuloitua muistia ja 11 GiB on ram-muistia virtuaalikoneelle.  

<img width="307" alt="image" src="https://github.com/user-attachments/assets/950e66cc-ce15-4869-a328-ce7891735155" />  

Osa resursseista tuli omalta pääkoneeltani, esimerkiksi kovalevy, ram-muisti ja prosessori, mutta osa listauksessa olevista asioista oli virtuaalisia koneen komponentteja ja erilaisia emuloituja ohjaimia.  

## g) Analysoidaan lokeja  
Osa lokeista oli siirtynyt journalctl paikkaan ja niitä pääsi katsomaan komennolla journalctl.  
Tämä selvisi aiemmin, kun olin /var/log/ kansiossa ja luin sieltä README.txt tiedoston.  

Journalctl komennon jälkeen terminaali täyttyi lokeista.  
Aloin katselemaan erottuvia keltaisia komentorivejä.  

<img width="692" alt="image" src="https://github.com/user-attachments/assets/bc969032-3799-46b3-9e2b-55ac75a102e2" />  

Nähtävästi pulseaudio etsi evästeitä, mutta ei löytänyt niitä.   
Ajattelin, että evästeiden puuttuminen voisi johtua siitä etten ollut tehnyt mitään toimintoja järjestelmällä, joka olisi luonut evästeitä pulseaudiolle.  

## h) Micro-editorin plugin  

Etsin internetistä micro -plugineita ja löysin sivut, joilla oli listaus.  

https://micro-editor.github.io/plugins.html  

Asensin wc nimisen pluginin, jolla voi laskea sanojen tai merkkien määrän.  

En tiennyt miten plugin asennetaan microon, joten päädyin kysymään ohjeita tekoälyltä.    

<img width="606" alt="image" src="https://github.com/user-attachments/assets/29c8cf03-01d0-43ef-966e-d4d56e12cc69" />  

Navigoin hedelmat tarinaan kokeilemaan microa.  

<img width="491" alt="image" src="https://github.com/user-attachments/assets/68d9b415-d08d-46e4-a413-a721f3882c09" />  

<img width="748" alt="image" src="https://github.com/user-attachments/assets/b6d68897-8cb1-4e28-af74-57a6613362f8" />  

Aluksi wc ei toiminut eikä mitään tapahtunut, joten käynnistin micron uudelleen, niin se alkoi toimimaan.  

Avasin micron -> ctrl-e -> komentoriville komento wc  

<img width="788" alt="image" src="https://github.com/user-attachments/assets/90672fbb-e3fb-4de9-9e14-870918206c19" />  

Ajattelin, että tämä voisi olla kätevä koulutehtävissä.  

## Lähdeluettelo  

- Kotitehtävä h2  
  https://terokarvinen.com/linux-palvelimet/#h2-komentaja-pingviini  

- Tero Karvinen 2020  
  https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited  
  
- Google support -keskustelu  
  https://support.google.com/chromebook/thread/211306991/uninstall-linux-apps-using-terminal?hl=en  

- Youtubevideo linux ohjelmista.  
  https://www.youtube.com/watch?v=FXu428tLhdE  

- What is grep -googlehaku  
  https://www.google.com/search?q=what+is+linux+grep&oq=what+is+linux+grep&gs_lcrp=EgZjaHJvbWUyBggAEEUYOTIGCAEQLhhA0gEINDk4NmowajGoAgiwAgE&sourceid=chrome&ie=UTF-8  

- grep -ohjeita  
  https://linux-tips.us/lets-learn-about-grep/    

- Grep -komentoja  
  How to see grep output in color with highlighting feature  
  https://www.cyberciti.biz/tips/howto-see-grep-command-output-in-colours.html  

- Micro editor -pluginit  
  https://micro-editor.github.io/plugins.html  

- Chatgpt -komentoja ja hedelmatarinan luominen
  

  
