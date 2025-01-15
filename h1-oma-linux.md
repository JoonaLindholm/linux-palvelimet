#Oman Linuxin asentaminen virtuaalikoneelle.

Aloitin h1 kotitehtävän teon 15.1. töiden jälkeen klo 12:40.
Päätin asentaa virtuaalikoneen itse rakentamaani tietokoneeseen.

Komponentteina minulla on:

-Amd Ryzen 7 5800X3D

<img width="526" alt="image" src="https://github.com/user-attachments/assets/c5d5de30-85ed-477f-9c09-0f77abd7cc18" />

-Vajaa 2 tb ssd levytilaa

-3060ti näytönohjain

-32 gb ram muistia

Aloitin asentelun Tero Karvisen ohjeiden mukaan: https://terokarvinen.com/2021/install-debian-on-virtualbox/#create-a-new-virtual-machine
Latasin Virtualboxin virallisilta sivuilta https://www.virtualbox.org/wiki/Downloads

<img width="317" alt="image" src="https://github.com/user-attachments/assets/bee8265d-57a8-4f8e-a373-4139ba8854b4" />

Tietokoneessani on Win 11 pro, joten päädyin lataamaan "Windows hosts" version.

Tämän jälkeen siirryin lataamaan Teron ohjeiden mukaan "Debian ISO image" tiedostoa. Versio oli tuolloin 12.9.0.

https://cdimage.debian.org/debian-cd/current-live/amd64/iso-hybrid/

<img width="716" alt="image" src="https://github.com/user-attachments/assets/a3778afe-2912-47f8-9c9f-a60ca2e27101" />

#Asennus

Aloitin asentamalla VirtualBoxin.

En muuttanut allaolevan kuvan valintoja. Painoin vain "Next".

<img width="377" alt="image" src="https://github.com/user-attachments/assets/b84d5924-bf8a-4435-af5f-30eab9563104" />

Sain varoituksen internet yhteyden katkeamisesta. Hyväksyin painamalla "Yes" ja seuraavassa kohdassa en muuttanut mitään oletuksia, painoin "Next". Tämän jälkeen sain vihdoin painaa "Install".

<img width="380" alt="image" src="https://github.com/user-attachments/assets/82dcb61d-34c2-4d94-b2c5-789b2954b24d" />

<img width="374" alt="image" src="https://github.com/user-attachments/assets/f6887ec7-7230-49fa-9d65-4709de62abfe" />

Asennus kesti noin 5 sekuntia.
Käynnistin VirtualBoxin suoraan asennuksesta.

<img width="385" alt="image" src="https://github.com/user-attachments/assets/f05dad7c-fec8-40bc-b42c-e4b53e2f58f1" />



VirtualBox avautui seuraavaan päävalikkoon.

<img width="836" alt="image" src="https://github.com/user-attachments/assets/fd588c05-b7db-45df-9c88-95ac72e3570a" />

Klikkasin "New".

<img width="835" alt="image" src="https://github.com/user-attachments/assets/90a91714-28da-4405-a376-fd5944027fe5" />

Laitoin nimeksi Linux_VM, en muuttanut "Folder" kohtaa, laitoin ISO Imageen aiemmin lataamani Debian ISO Imagen.
Muutin version 64-bittiseksi, koska tietokoneeni on 64 bittinen. Klikkasin Teron ohjeiden mukaan "Skip unattended installation" boksin.

<img width="559" alt="image" src="https://github.com/user-attachments/assets/d5a28ffa-76e3-4ba6-9f5e-3dd8e4bbc89c" />

Seuraavaksi siirryin "Hardware" kohtaan. En ollut varma miten paljon kannattaisi laittaa muistia ja CPU:ita, joten päädyin kysymään asiasta tekoälyltä.

<img width="524" alt="image" src="https://github.com/user-attachments/assets/eb80334d-9e05-4329-889d-c21f1e66894c" />

En ollut varma mihin kaikkeen tulen tulevaisuudessa tätä virtuaalikonetta käyttämään, joten päädyin varautumaan myös raskaaseen käyttöön. Tutkin myös internetin keskutelupalstoilta asiaa ja siellä oli hyvin paljon eri mielipiteitä asiasta. Lopulta päädyin kuitenkin tekoälyn ehdotukseen. Ainahan voi lisätä tai vähentää resursseja tarpeen mukaan.

Allaolevilla asetuksilla eteenpäin "Hard Disk" kohtaan.
<img width="558" alt="image" src="https://github.com/user-attachments/assets/07788b1a-bdb2-4143-b7d2-66fb3a53bc28" />

Valitsin 80 GB tilaa virtuaalikoneen kovalevylle ja vaihdoin oletus kovalevyä sekä kansiota, joka oli oletuksena.

En muuttanut muita asetuksia. Jatkoin eteenpäin painamalla "Finish".

<img width="566" alt="image" src="https://github.com/user-attachments/assets/e33ef4ba-903e-4be8-ba29-692ec65d93ee" />

Päädyin seuraavaan kohtaan, jossa painoin ylhäältä nuolta "Start".

<img width="836" alt="image" src="https://github.com/user-attachments/assets/4cec02be-4a91-4450-9ea5-c97711e0d977" />

Ohjeiden mukaisesti valitsin valikosta ylimmän vaihtoehdon "Live system (amd64)".

<img width="317" alt="image" src="https://github.com/user-attachments/assets/f04acde5-3cc7-4773-a55f-ab53b6437dc2" />

Tämän jälkeen tuli vähäksi aikaa Debian logo, jonka jälkeen musta ruutu. Jatkoin odottelua tekemättä mitään.

Lopulta käyttöjärjestelmä avautui.

<img width="635" alt="image" src="https://github.com/user-attachments/assets/1bb3f5e8-8d05-40f3-8ec8-012dedd05922" />

Ohjeissa käsketään seuraavaksi testaamaan, että kaikki toimii.

Hiiri ainakin toimii mainiosti. Menin "Applications" kohtaan ja klikkasin "Web browser".

<img width="206" alt="image" src="https://github.com/user-attachments/assets/7d892068-a253-4120-83bf-31bbde0c4e8b" />

Skippailin kaikki Firefoxin stepit ja painoin "Start browsing".

<img width="638" alt="image" src="https://github.com/user-attachments/assets/a34163ee-28f1-4996-b0c6-c1d8e071ffd5" />

Kaikki näyttäisi toimivan. Pystyin kirjoittamaan youtuben hakuun "sql".

<img width="629" alt="image" src="https://github.com/user-attachments/assets/8714f939-e272-461e-8beb-b2e92777836b" />

Sitten muistin, että tunnilla laitettiin suomenkielinen näppäimistö. Tämmöistä kohtaa en ollut nähnyt asennuksessa.
Kokeilin hakukenttään skandeja, mutta ne eivät toimineet.

Aloin tutkimaan VirtualBoxin ylävalikkoa. Sieltä löysin "Input" kohdasta "keyboard" asetukset.

<img width="218" alt="image" src="https://github.com/user-attachments/assets/b31f37e3-59ff-4081-8e3c-c1258465a184" />

Pääsin seuraavaan valikkoon, josta menin "Language" kohtaan. Sieltä ei kuitenkaan löytynyt Suomea :(

<img width="638" alt="image" src="https://github.com/user-attachments/assets/216c2877-9108-4638-bb05-8af6768acdd3" />

Lueskelin ohjeita eteenpäin ja huomasin, että kieli valitaankin vasta myöhemmin Debianin asennuksen yhteydessä. Onneksi tähän ei kulunut paljoa aikaa :)

Seuraavaksi asennetaan siis Debian. Kello oli tällöin 13:47. Tunti oli siis kulunut asennuksiin.

<img width="654" alt="image" src="https://github.com/user-attachments/assets/d5e43190-cd03-4e26-867a-01d1df5189dd" />

Klikkasin kuvaketta ja pääsin seuraavaan ruutuun. Valitsin ohjeiden mukaisesti "American English" ja next.

<img width="637" alt="image" src="https://github.com/user-attachments/assets/94e196b4-5b28-4bb3-bf24-40d4c61a7771" />

Alueeksi laitoin Helsingin.

<img width="517" alt="image" src="https://github.com/user-attachments/assets/f4531b78-6689-46f5-afc6-4fb0e7414070" />

Vihdoin pääsin valitsemaan näppäimistön kielen. Finnish ja default, sitten next.

<img width="837" alt="image" src="https://github.com/user-attachments/assets/b1ce2ab3-4b6b-42d1-9d78-4826da2e4fb5" />

Partitions kohdassa valitsin ohjeiden mukaiset valinnat eli "Erase disk" ja boot loaderiin "Master Boot Record" sitten next.

<img width="515" alt="image" src="https://github.com/user-attachments/assets/476d9b19-6592-42e1-a611-2d8f691ef904" />

Users kohdassa noudatin edelleen ohjeita ja täytin kentät kuvanmukaisesti.

<img width="632" alt="image" src="https://github.com/user-attachments/assets/1afa4d0f-c043-43dd-8ccf-216817702419" />

Tämän jälkeen tuli yhteenveto kohta, jossa painoin install.

<img width="633" alt="image" src="https://github.com/user-attachments/assets/834b33b5-3a33-47d7-9fa8-3a29023050c1" />

<img width="632" alt="image" src="https://github.com/user-attachments/assets/23855778-9115-4536-a1f8-9c5d5746171a" />

Lopulta asennus valmistui. Asennukseen meni noin 5 minuuttia. Aika käynnistää kone uudelleen.

<img width="515" alt="image" src="https://github.com/user-attachments/assets/47b7c884-8926-4470-a9b9-a871a811d92c" />

Lopulta pääsin kirjautumiskohtaan, johon laitoin asennuksen yhteydessä kysytyt tiedot.
<img width="641" alt="image" src="https://github.com/user-attachments/assets/ed2b4cb9-601a-417f-a3fe-42e394039458" />

Kirjautumisen jälkeen pääsin työpöydälle.

<img width="638" alt="image" src="https://github.com/user-attachments/assets/19302cc2-9f55-4714-98e0-859cc39f043a" />

Menin taas web browseriin ja youtubeen. Skandit ja äänet toimivat.

<img width="641" alt="image" src="https://github.com/user-attachments/assets/7a72c17b-2fd4-433f-92ad-ef3368723f07" />

#Päivitys

Jatkoin ohjeiden mukaisesti ja avasin työpöydältä terminalin (punainen ympyrä).

<img width="640" alt="image" src="https://github.com/user-attachments/assets/03086e4c-cae7-4b1c-9f48-4810b412f9f8" />

kirjoitin terminalin kenttään "sudo apt-get update", jonka jälkeen se pyysi salasanaani.

<img width="637" alt="image" src="https://github.com/user-attachments/assets/3d47d5ea-c881-45b8-b1cd-4de1f2d51640" />

<img width="452" alt="image" src="https://github.com/user-attachments/assets/8b267d94-741e-49fe-a97e-026351e8b83d" />

Tämän jälkeen terminaaliin päivittyi kaikki mahdolliset päivitykset, jotka voin asentaa.

<img width="598" alt="image" src="https://github.com/user-attachments/assets/42019f61-58a4-4662-afae-fc0327be0fb3" />

Tämän jälkeen asennetaan kaikki päivityksen kuvassa olevalla komennolla.

<img width="257" alt="image" src="https://github.com/user-attachments/assets/368f9930-c396-49a7-94d1-c3edadee7a06" />

Päivitykset näyttivät onnistuvan.

<img width="580" alt="image" src="https://github.com/user-attachments/assets/884cc58c-21a9-465f-a655-19f30783df02" />

Seuraavaksi ohjeissa asennetaan palomuuri.

<img width="242" alt="image" src="https://github.com/user-attachments/assets/026dbb61-4c10-42b1-b016-c714062957cb" />
<img width="421" alt="image" src="https://github.com/user-attachments/assets/ea911e1e-9965-4225-864b-9f55f793e955" />

Ja laitetaan se päälle.

<img width="412" alt="image" src="https://github.com/user-attachments/assets/1c2b50d4-3ea1-4e5e-a92c-ad38e87baa12" />
<img width="464" alt="image" src="https://github.com/user-attachments/assets/301872b6-fcbd-4e21-9ff4-6f90f0841577" />

Tämän jälkeen on rebootin aika.

<img width="604" alt="image" src="https://github.com/user-attachments/assets/f73fddfb-ac2d-47bd-b947-7bcea66b561f" />
<img width="580" alt="image" src="https://github.com/user-attachments/assets/c3bd91f4-096c-4201-a195-a7746a2a7200" />

Tämän jälkeen pääsin taas login valikkoon ja kirjauduin sisään.

Lopuksi ohjeissa mainitaan VirtualBoxin pieni resoluutio. 
Haluan, että voin kasvattaa ruudun kokoa yms., joten päätän tehdä vielä tämän viimeisen asennuksen.

Ohjeissa avataan yläriviltä "Devices" valikko ja sieltä valitaan "Insert Guest Additions CD image..."

<img width="166" alt="image" src="https://github.com/user-attachments/assets/0fc031b1-81bf-4e44-baaf-6cfebe52b90a" />

Tämän jälkeen klikkasin Applications valikosta File manager ja pääsin seuraavaan ruutuun.

<img width="581" alt="image" src="https://github.com/user-attachments/assets/e8830c1a-9116-4331-a997-869807d55882" />

Tämän jälkeen ohjeissa pyydetää klikkamaan levyn kuvaa ja avaamaan Applications valikosta "Terminal Emulator".

<img width="617" alt="image" src="https://github.com/user-attachments/assets/548f72cd-5345-457a-a017-be33213e0ec6" />

Ohjeissa käsketään avaaman levyn kansio ja listata sen sisältö. Käyttämällä seuraavaa komentoa.

<img width="169" alt="image" src="https://github.com/user-attachments/assets/220a9332-62ab-4642-a926-dec0e63e1f25" />

Komennon jälkeen terminaaliin ilmestyi seuraavat tiedot.

<img width="610" alt="image" src="https://github.com/user-attachments/assets/dfc31fb7-e91c-4c95-b3eb-876e7c0dbaca" />

Sitten asennetaan.

<img width="623" alt="image" src="https://github.com/user-attachments/assets/abbe98ef-6045-484e-9699-e2cd6cad078e" />
<img width="596" alt="image" src="https://github.com/user-attachments/assets/ad6521a4-a67f-48e2-a13d-85404752c6b8" />

Asennuksen jälkeen ohjeissa sanotaan, että on aika taas rebootille :)

Kone käynnistyi normaalisti ja kuva skaalautuu hienosti ruudun koon mukaan.

<img width="939" alt="image" src="https://github.com/user-attachments/assets/e2646c8e-788d-4f46-bfdc-8f8eb5d9fb2f" /> 

Laitetaan vielä shared clipboard päälle ja kokeillaan sitä :)

Ylävalikosta Devices ja shared clipboard (Bidirectional).

Löysin Applications -> Accessories -> Mousepad, johon voi kirjoittaa tai kopsata tekstiä pääkoneesta.

<img width="197" alt="image" src="https://github.com/user-attachments/assets/87b96141-05d5-47c4-ba98-245b4d293649" />

<img width="1770" alt="image" src="https://github.com/user-attachments/assets/ede84ce9-3d62-4aa3-a886-e14dc1f09df5" />

Näyttäisi kaikki toimivan :)


