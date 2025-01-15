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
