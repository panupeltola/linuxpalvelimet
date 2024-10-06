# a) Hei Maailma

6.10.2024 klo 10:40

Päätin tehdä "Hei maailma!" ohjelmat Pythonilla, Javalla ja Rustilla

## Python

Aloitin luomalla oman kansion pythonille ja loin sille koodin.

![kuva](https://github.com/user-attachments/assets/65a9c634-cd75-440a-b4f7-45aa6757b5b8)

Ajoin ohjelman komennolla 'python3 heimaailma.py'


![kuva](https://github.com/user-attachments/assets/b6b03026-ea87-4238-ae27-f63db86419bd)


## Java

Käytin ohjeena löytämääni artikkelia (https://linuxconfig.org/how-to-install-java-on-ubuntu-18-04-bionic-beaver-linux)
Ohjeessa ollut komento 'sudo apt install openjdk-11-jdk' antoi kuitenkin virheen, että pakettia ei löydy.
Tutkin paketteja komennolla 'sudo apt install openjdk-11-jdk' ja näin, että tarjolla oli vain paketteja "openjdk-17-jdk"
Asensin tämän komennolla 'sudo apt install openjdk-11-jdk'
Tällä kertaa asennus onnistui.

![kuva](https://github.com/user-attachments/assets/b98583a6-f802-4de0-99be-25f8309cc93c)

Varmistin vielä asennuksen onnistumisen komennolla 'java --version'

Oikea versio näkyi.

![kuva](https://github.com/user-attachments/assets/ff1d483b-4db4-4e8e-9bf7-e12594aa6ef0)

Seuraavaksi seurasin ohjetta ohjelman tekemistä varten ja kirjoitin ohjeen mukaisen koodin.

![kuva](https://github.com/user-attachments/assets/f046f400-a35a-4840-b769-039a51e9984a)

Tästä koodista ensimmäiset kaksi riviä luovat luokan ja pääfunktion ja oikea tavara on kolmannella rivillä, jossa funktio println tulostaa konsoliin halutun tiedon.

Seuraavaksi kokosin ohjelman komennolla 'javac HelloWorld.java' ja katsoin, että kansioon oli ilmestynyt .class päätteinen tiedosto.

![kuva](https://github.com/user-attachments/assets/6584c925-a617-44d9-8faa-b8e4ceb65b60)

Lopuksi ajoin ohjelman komennolla 'java HelloWorld'

![kuva](https://github.com/user-attachments/assets/eb849ec9-f889-4e8e-aac1-2987ace4758f)

Tuloste oli oikein.

## Rust

Käytin tässä ohjeena Rustin virallista dokumentaatiota (https://doc.rust-lang.org/beta/book/ch01-02-hello-world.html).

Loin ohjeen mukaisen main.rs tiedoston ja loin sille sisällön.

![kuva](https://github.com/user-attachments/assets/7016b472-a249-47c1-9881-16d0fb970186)

Yrittäessäni koota ohjelmaa komennolla 'rustc main.rs' sain virheen komennon puutteesta. Totesin, että minulla ei ole rustin ympäristöä asennettuna ja päätin korjata asian.

![kuva](https://github.com/user-attachments/assets/16bd1156-f5f9-4a42-9c85-be61e4a04545)

Rustin dokumentaatiossa annetaan ohjeeksi ajaa komento 'curl --proto '=https' --tlsv1.2 https://sh.rustup.rs -sSf | sh'
Chat GPT:n mukaan tämä tekee seuraavia asioita:
- 'curl' kutsuu komennon
- '--proto 'https' pakottaa curlin käyttämään https protokollaa
- 'tlsv1.2' määrittää käytetyn TLS version
- 'https://sh.rustup.rs' määrittää kohdesivun
- '-sSf' mykistää tila ja virheilmoitukset pois lukien latauksen epäonnistumisen
- '| sh' ajaa kaiken shell komennoksi

Tämä ei ole turvallisin tapa ladata tiedostoja, sillä koodi ei ole paketinhallinnan kuratoima, koodi oli kuitenkin avoin ja luotan tässä tapauksessa lähteeseen ja ajan komennon.

![kuva](https://github.com/user-attachments/assets/e63ab044-fc18-442c-acfd-74299cc21d69)

Tämä asensi Rustin. Kehotteen mukaisesti käynnistin komentorivin uudelleen.
Yritin nyt ajaa komennon 'rustc main.rs' uudelleen

Kansioon oli ilmestynyt uusi tiedosto.

![kuva](https://github.com/user-attachments/assets/cecde3c2-0f69-406c-89a9-c626ee03c3ac)


Ajoin sen ohjeen mukaan komennolla './main'

![kuva](https://github.com/user-attachments/assets/8770121b-98d8-4691-8c6d-c7863a44cdbf)

Tuloste oli oikea ja totesin tehtävän tehdyksi.

# b) Uusi komento

## Funktio

Halusin luoda komennon, joka heittää noppaa antaen satunnaisen numeron väliltä 1-6.

Löysin foorumilta keskustelua satunnaisen numeron luonnista ja se luotiin komennolla 'shuf -i 1-100 -n 1' katsoin komennon 'shuf' manuaalia osien selvittämiseksi:
- 'shuf' kutsuu prosessin
- '-i 1-100' määrittää numeroarvojen välin (tässä tapauksessa 1-100)
- '-n 1' määrittää luotavien tulosteiden määrän (arpoo useamman nopan)

(https://unix.stackexchange.com/questions/140750/generate-random-numbers-in-specific-range)

Muokkasin komennon muotoon 'shuf -i 1-6 -n 1' ja kokeilin miten käy, halusin myös tarkastaa mitä -n arvon muuttaminen tekee koska en täysin ymmärtänyt sitä dokumentaatiosta, joten testasin sitäkin

![kuva](https://github.com/user-attachments/assets/eced423e-b9da-4684-980d-1f9dabbc51c6)

Halusin lisätä komentoon myös tekstiä, joten päätin luoda komentoon muuttujan.
Ensin piti kuitenkin tehdä komento ja testata sen toimivuus.
Olen aikaisemmassa kurssissa myös luonut komentoja, joten minulla on jo jotain osaamista niistä.

Loin uuden shell komennon 'micro noppa.sh'

Aluksi laitoin #!/bin/sh ohjaamaan oikeaan ympäristöön ja loin hei maailma tekstin tulemaan 'echo' komennon kautta.

Yritin ajaa komentoa komennolla './noppa.sh'

![kuva](https://github.com/user-attachments/assets/a1579005-031d-4fd8-b29f-a756551bb364)

Sain virheen "Permission denied" kun katsoin tiedoston oikeuksia, niin totesin ettei kenelläkään ole oikeutta ajaa sitä. Korjasin tämän komennolla 'chmod ugo+x noppa.sh'.

![kuva](https://github.com/user-attachments/assets/2c785dd5-2642-4b9f-ade2-ab69e3006a26)

Nyt ohjelman pystyi ajamaan. Seuraavaksi halusin koittaa luoda nopasta muuttujan ja tulostaa sen komentoon.

![kuva](https://github.com/user-attachments/assets/0aea1585-27eb-4650-89a8-8da4f142663a)

Löysin muuttujaan ohjeen (https://www.shellscript.sh/variables1.html)

Lisäsin myös shuf komennon yksinään, jotta näen mikäli jokin tuloste puuttuu, että onko ongelma oletettavasti muuttujassa vai funktiossa.

![kuva](https://github.com/user-attachments/assets/e64b70ec-a1fd-4819-b5f1-60e80f637652)

Ensimmäinen yritys epäonnistui, huomasin, että olin jättänyt 'echo' komennon 'shuf' funktion eteen, mikä johti siihen, että vain teksti tulostui.

Myös muuttuja epäonnistui, mutta palaan siihen seuraavassa revisiossa. Nyt haluan nopan heiton toimimaan.

![kuva](https://github.com/user-attachments/assets/832e018f-1477-4b59-8d7f-c5b094b139c9)

Tällä versiolla nopan heitto toimi. Nyt vain pitäisi saada muuttuja toimimaan.

![kuva](https://github.com/user-attachments/assets/5d142422-42db-418d-a667-c468a962194d)

Hetken googlailtuani ja ihmeteltyäni en ollut askeltakaan lähempänä oikeaa, päätin kysyä ChatGPT:ltä promptilla "how do i set a variable value from a 'shuf' function in shell script with linux"

Sain vastaukseksi alla olevan ohjeen.

![kuva](https://github.com/user-attachments/assets/e55dbcc9-a55c-44d2-8438-e453dffc4818)

Pienen taistelun välilyöntien kanssa sain vihdoin ohjelman logiikan toimimaan. 
Ongelmana oli, että muuttujassa käytin välilyöntejä, mikä ei toiminut ja olin unohtanut välilyönnin viimeisen 'echo' komennon jälkeen.

![kuva](https://github.com/user-attachments/assets/c8f20e13-92ba-4691-a451-f1b85167dad1)

Poistin nyt testaamiseen tarvitut rivit ja jätin vain noppafunktion.

## Siirto

Muistin aikaisemmasta kurssista, että tiedosto pitää viedä kansioon /usr/local/bin
Kopioin tiedoston komennolla 'sudo cp noppa.sh /usr/local/bin/noppa.sh'

Nyt kun kirjoitin 'noppa.sh' heitin noppaa.

![kuva](https://github.com/user-attachments/assets/5b2d3152-9352-456f-a5fe-216a33eb4ca7)

Halusin vielä koettaa miten käy jos poistan komennosta ".sh liitteen"

Tein sen komennolla kopioimalla tiedoston uudelleen 'sudo cp noppa.sh /usr/local/bin/noppa'

![kuva](https://github.com/user-attachments/assets/c568b162-fd9c-4def-80ad-ac6a581a379b)

Tämä toimi ja nyt pystyin heittämään noppaa tehokkaammin.

