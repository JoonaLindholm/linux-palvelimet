# h7 - Maalisuora  

### Sisällysluettelo / Tehtävänannot  

**https://terokarvinen.com/linux-palvelimet/#h7-maalisuora**  

**a)** Hei maailma! -kolmella eri kielellä  

**c)** Oma komentoni kaikille käyttäjille  

**d)** Vanha laboratorioharjoitus  

---

### Tehtävät  

**a)** 

Aloitin tehtävän lukemalla Tero Karvisen -ohjeita eri kielille.  

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

Komennon tarkoituksena oli luoda uusi satunnainen salasana ja tulostaa se komentoriville.  
Ohjelman nimeksi tuli tietenkin "Lazy_Online_Locker" eli lyhennettynä L.O.L.  






Rakensimme tunnilla oman ajettavan komennon ja 

---

### Sisällysluettelo  

Tehtävänanto  
**https://terokarvinen.com/linux-palvelimet/#h7-maalisuora**  

Hello World -ohjeet  
**https://terokarvinen.com/2018/hello-python3-bash-c-c-go-lua-ruby-java-programming-languages-on-ubuntu-18-04/**    

C++ kielen kääntäminen  
**https://www.ohjelmointiputka.net/oppaat/opas.php?tunnus=cpp_ohj_01**   

Shell scripting  
https://terokarvinen.com/2007/12/04/shell-scripting-4/  

Shell scriping ideoita  
**https://medium.com/aimonks/50-cool-bash-scripts-and-what-they-do-b38b4e841ba2**  
