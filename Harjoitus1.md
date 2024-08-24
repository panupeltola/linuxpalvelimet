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













