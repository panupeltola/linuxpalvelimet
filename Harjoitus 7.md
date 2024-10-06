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

# b) 


















