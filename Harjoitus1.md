# Harjoitus 1

# x) Lue ja tiivistä

## Raportin kirjoittaminen (Karvinen, 2006)

- Raportin kirjoittamisessa tärkeintä on tarkkuus ja olosuhteiden esittäminen
- Raportin testien on oltava toisetettavissa vastaavissa olosuhteissa, joten turhaa tietoa ei ole
- Myös epäonnistumiset on hyvä listata, sillä ne ovat seuraavalla kerralla ohjeena miten ongelma vältetään tai ratkaistaan
- Kirjoitan oman tasoni mukaan ja lähteistä oppimistani asioista, mutta pidän lähteet selvästi esillä


## What is Free Software? (Free Software Foundation, 2024)

- Ohjelmisto on ilmaista kun:
1. Sitä saa ajaa haluamaansa tarkoitukseen
2. Käyttäjällä on vapaus tutkia, miten ohjelma toimii ja muuttaa sitä tahtonsa mukaisesti
3. Käyttäjällä on oikeus jakaa ohjelmistoa vapaasti muita auttaakseen
4. Käyttäjällä on oikeus jakaa muokattua ohjelmistoa vapaasti
  
- Vain ohjelmisto joka täyttää nämä ehdot on ilmaisohjelma
- Ohjelmisto, josta vain osa ominaisuuksia on ilmaisia, ei vielä ole ilmaisohjelma
- Ilmaisen ohjelmiston muokkaamisen ja muokatun ohjelman jakamisen oikeus olettaa, että lähdekoodi on saatavilla
- Muokatuista ohjelmistoista saa pyytää rahaa


# a) **Asenna Linux virtuaalikoneeseen**

## Ympäristö:

- Windows 10
- Intel Core i7-10770K
- Nvidia GeForce 3080
- 32 GB RAM
- VirtualBox 7.0.20

## Asennus

**24.8.2024 klo 12:50**

Aloitan lataamalla Debian 12.6.0 Debianin sivuilta. Lataan ensimmäisenä ehdotetun version

![Verkkosivu](https://github.com/user-attachments/assets/5aea95e5-408a-4d0c-923c-65b95154df4c)

Seuraavaksi luon uuden virtuaalikoneen VirtualBoxin "New" painikkeesta

![Luo uusi kone](https://github.com/user-attachments/assets/e03ff5e8-ebee-4964-a11b-3fa48a9c4bdd)

Valitsen oikean ISO-kuvan ja klikkaan laatikon "Skip Unattended Installation" valitsen seuraavaksi Next

![Asetukset](https://github.com/user-attachments/assets/1d59c796-e92b-4f85-a17e-113e206c30b6)

Annan virtuaalikoneelle reilusti resurria käytettäväksi, koska se nopeuttaa arkea, vaikka vähemmällä selviäisi varmasti.
Annan 8 GB muistia ja neljä prosessoria

![Resurssit](https://github.com/user-attachments/assets/50e3f752-121a-45ba-968a-fa20572993e4)

Lopuksi luon vielä virtuaalikovalevyn, jonka koko tilan allokoin kerralla. Käsittääkseni ilman tätä täppää kovalevyn koko kasvaa annettun maksimiin asti dynaamisesti, mutta vaihtoehdolla "Pre-allocate Full Size" tila varataan fyysiseltä kovalevyltä kerralla.

![Kovalevy](https://github.com/user-attachments/assets/4ecc0a18-e954-4de7-8005-2543ca24950f)

Tämän jälkeen odotan, kun virtuaalikonetta luodaan

![kuva](https://github.com/user-attachments/assets/8d390273-0722-45c4-b585-57b05e4b25d5)

**24.8.2024 klo 13:09**

Kone on saatu luotua, joten käynnistän sen ja aloitan asennuksen

![kuva](https://github.com/user-attachments/assets/ed44d55b-b051-4de0-b368-fca620aedebf)

Muistin tässä vaiheessa, että halusin kokeilla Tero Karvisen luennolla näyttämää tapaa asentaa Debian live version kautta. Yritän saanko vain muutettua VirtualBoxissa asennuslevyn vai pitääkö minun luoda kone alusta

Lataan ensin uuden levykuvan, valitsen käyttöliittymäski Gnomen:

![kuva](https://github.com/user-attachments/assets/5f61be62-3751-4264-8cc5-41a4712bf7a1)


**24.8.2024 klo 13:25**

Tiedosto on ladannut ja yritän nyt vaihtaa asennus levyä
Poistin asennuslevyn painikkeesta "Remove disk from virtual drvie" ja tein sen ajattelematta ennen kuvan ottamista

![kuva](https://github.com/user-attachments/assets/c25a2e04-dd91-491f-942d-52edee04cfdb)

Seuraavaksi lisään asemaan ladatun levykkeen live versiosta ja käynnistän koneen uudelleen

![kuva](https://github.com/user-attachments/assets/f799fdaf-3769-451f-8416-8debffeeb5d7)

Levyn vaihto näyttää onnistuneen ja käynnistän nyt koneen Live systemin.

![kuva](https://github.com/user-attachments/assets/f4a77be8-2c1b-4f0c-b9f9-41f8b4ea844b)

Kone boottasi alkuasetuksiin.

Valitsen näppäimistön kieleksi suomen

![kuva](https://github.com/user-attachments/assets/2cf76a25-dc6f-4792-a08e-5bd44223826a)

Kokeilen, että hiiri toimii, näppäimistö toimii, joskin asetukset ovat Yhdysvaltojen asetuksilla, vaikka sen vaihdoinkin ja verkko toimii
![kuva](https://github.com/user-attachments/assets/f20ab7cd-22d7-4382-8f33-b00a76222660)

Asennan nyt koko version.

Valitsen kieleksi "American English"

![kuva](https://github.com/user-attachments/assets/d5839924-decf-462f-bc3b-fc8faacee1b1)

Sijainniksi Helsingin

![kuva](https://github.com/user-attachments/assets/fd712ecb-8061-4345-bbcb-f0f7e09026de)

Näppäimistön kieleksi Suomen

![kuva](https://github.com/user-attachments/assets/1e9379b5-b0d2-4929-b742-80a88e2bda53)

Kovalevyn tyhjennnän, enkä tässä tapauksessa salaa, en osioi levyä itse varmistan myös, että Boot loaderilla on oikea sijainti

![kuva](https://github.com/user-attachments/assets/d5f0924a-9618-48d6-bd4f-e36f26439c6e)

Seuraavassa vaiheessa luon käyttäjäni alter egoni nimiin, valitsen myös automaattisen kirjautumisen

![kuva](https://github.com/user-attachments/assets/92de2b14-7f78-4795-ab52-3a439d60f81b)

Tämän jälkeen odotan asentamista

![kuva](https://github.com/user-attachments/assets/1abd6f2b-5981-4a1b-b7ca-0de125a6a5bf)


**24.8.2024 klo 13:47**

Käyttöjärjestelmä on asentunut ja katson lähteekö laite toimimaan uudelleen käynnistyksellä

![kuva](https://github.com/user-attachments/assets/532ce393-1ab6-4c03-bf40-5589b2067dd0)

Koetin perusominaisuudet ja totesin, että hiiri, näppäimistö ääkkösineen ja verkko toimivat.
Totesin siis, että asennus on onnistunut.

![kuva](https://github.com/user-attachments/assets/21b18f68-ae27-4dcf-adc8-ebd1e82b76c6)



# k) Vapaaehtoinen bonus: suosikkiohjelmani Linuxilla

Vielä viimeisenä temppunani asennan ja kytken päälle ufw palomuurin.

Asennan sen terminaalista komennolla 'sudo apt-get install ufw'

![kuva](https://github.com/user-attachments/assets/308d9112-6efe-4fd1-9aa7-962f0c6fa429)

Asennuksen jälkeen kytken sen päälle komennolla 'sudo systemctl enable ufw'

![kuva](https://github.com/user-attachments/assets/a947493e-8330-4e0c-9299-500d781f6e9c)

Lopuksi vielä varmistan palomuurin toiminnan komennolla 'sudo sysyemctl status ufw'

![kuva](https://github.com/user-attachments/assets/788313bb-41c6-4833-bcd3-bb125ed82b34)

ufw ei näyttäisi olevan päällä, joten yritän käynnistää sen komennolla 'sudo systemctl start ufw'

![kuva](https://github.com/user-attachments/assets/2a9b5f1e-89e7-4233-a698-9101512eab9c)

Tällä komennolla palomuuri lähti liikkeelle ja Linux on toimintakunnossa

![kuva](https://github.com/user-attachments/assets/eaa22616-8d57-48fd-8478-9787a9dc7f4a)

# Lähteet:
- T. Karvinen, 2006, Raportin kirjoittaminen, https://terokarvinen.com/2006/raportin-kirjoittaminen-4/, luettu 24.8.2024
- Free Software Foundation, 2024, What is Free Software?, https://www.gnu.org/philosophy/free-sw.html, luettu 24.8.2024  













































