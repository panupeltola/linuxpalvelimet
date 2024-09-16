# z) Lue ja tiivistä

## Teoriasta käytäntöön pilvipalvelimen avulla (https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/)

- Susanna hankkii virtuaalikoneen DigitalOceanin kautta
- Virtuaalikone luodaan Debian 11 käyttöjärjestelmälle ja halvimpaan virtuaalikoneeseen
- SSH-yhteys salataan salasanalla
- Nimipalvelin hankitaan Namecheap-palvelun kautta
- Nimipalvelin asetettiin ennen palomuuria
- Lopuksi kone suojataan
- Koneelle yritetään lähes välittömästi murtautua

## First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS (https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/)

- Teron ohjeessa käydään läpi uuden virtuaalikoneen käyttökuntoon laittaminen
- Ensin kirjaudutaan root käyttäjänä sisään komennolla root@ipnumero/osoite
- Ensimmäisenä asennetaan palomuuri ja sallitaan siihen SSH-portti 22 liikenne komennolla 'sudo ufw allow 22/tcp'
- Toisena lisätään uusi käyttäjä ja tämä käyttäjä liitetään ryhmiin "sudo", "adm" ja "admin"
- Hyvän tavan mukaan aina tulee käyttää mahdollisimman pieniä oikeuksia asian tekemiseen, tämän takia heti kunhan varmistetaan, että SSH yhteys toimii uudella käyttäjällä estetään root käyttäjä.
- Tämä tehdään komennoilla :
- $ sudoedit /etc/ssh/sshd_config
    ...
    PermitRootLogin no
    ...
  $ sudo service ssh restart
- Kun kriittisimmät asiat, eli palomuuri ja root käyttäjän poistaminen on tehty, pitää vielä päivittää paketit
- Susannan ohjeessa oli vielä Teron ohjeen komentojen 'sudo apt-get update' ja 'sudo apt-get upgrade' lisäksi komento 'sudo apt-get dist-upgrade' jolla päivitetään myös käyttöjärjestelmä.


# a) Vuokraa oma virtuaalipalvelin haluamaltasi palveluntarjoajalta

16.9.2024 klo 16:00

Olin jo luonut aiemmin tilin DigitalOceaniin ja lisänny sinne varoja. Aloitin luomalla sinne virrtuaalikoneen, eli Dropletin.
Loin sen Amsterdamiin

![kuva](https://github.com/user-attachments/assets/595e2592-f7bb-48fb-9619-9387bbf36d90)

Valitsin käyttöjärjestelmäksi uusimman Debianin

![kuva](https://github.com/user-attachments/assets/b4e8d42a-ad63-4153-bbee-935dfbaa240b)

Lopuksi valitsin vielä levytyypiksi SSD:n ja kaikista pienimmät speksit koneeseen. Toivoin niiden riittävän.
Kaikki muut lisäpalvelut hylkäsin

Päätin käyttää todentamismenetelmänä salasanaa

![kuva](https://github.com/user-attachments/assets/daec0eb4-a464-47f9-9d1a-716421991000)

Lopuksi loin vielä virtuaalikoneelle nimen, josta ei selviä esimerkiksi koneen käyttöjärjestelmää.

Tämän jälkeen loin koneen ja katsoin sen osoitteen.

![kuva](https://github.com/user-attachments/assets/c63b8231-5558-48c8-8a4c-6efd89fcd404)

Kokeilin vielä saanko virtuaalikoneelta vastausta jos yritän tavoittaa sitä 'ping' komennolla.

![kuva](https://github.com/user-attachments/assets/9ef7dee2-7be2-474c-b6ed-b89858e4c76d)

Osoite vastasi, joten totesin virtuaalikoneen olevan verkossa.

# b) Alkutoimet

16.9.2024 klo 16:27

Käytin apunani Teron ohjetta ja Susannan raporttia tehdystä tehtävästä.

Aloitin ottamalla yhteyden virtuaalikoneeseeni komennolla 'ssh root@188.166.31.99'

Tämän jälkeen terminaali kysyi luotanko koneeseen, sillä sitä ei tunnettu. Päätin luottaa sokeasti.

![kuva](https://github.com/user-attachments/assets/eaf60a8c-6b55-4ef9-a101-55cd662f0dff)

Olin nyt virtuaalikoneen sisällä.

Aloitin päivittämällä pakettilistan ja asentamalla ufw paketin.
Tein nämä komennoilla 'sudo apt-get update' ja 'sudo apt-get install ufw'

![kuva](https://github.com/user-attachments/assets/4f6ce47b-5e0e-4dbd-9260-f482c6ff0be6)

Huomasin, että juurikäyttäjänä ei tarvinnut erikseen hyväksyä asennusta, vaikka komennossa ei ollut '-y' optiota.

Loin seuraavaksi käyttäjän ja lisäsin sen ryhmiin "sudo", "adm" ja "admin" Teron ohjeen mukaisesti

Selvitin ensin mihin ryhmiin olin käyttäjää lisäämässä Debianin dokumentaation kautta (https://wiki.debian.org/SystemGroups):

- adm: Systeemien monitorointiin käytetty ryhmä. Pääsy lokeihin tärkeimpänä tekijänä.
- sudo: Ryhmän jäsenet voivat suorittaa sudo-tason komentoja

Ryhmästä admin en löytänyt mitään tietoa, joten päätin olla lisäämättä käyttäjää siihen. Teen lisäyksen tarvittaessa, sillä käyttäjä saa sudo-oikeudet.

Lisäsin käyttäjän komennolla 'sudo adduser passeli'
Loin käyttäjälle vahvan salasanan.

Tämän jälkeen lisäsin käyttäjän ryhmiin komennoilla
'sudo adduser passeli sudo' ja 'sudo adduser passeli adm'

![kuva](https://github.com/user-attachments/assets/a8f2803e-2696-495b-a5d3-aaa172f783b2)

Kun sain tämän tehtyä avasin vielä palomuuriin portin SSH yhteydelle komennolla 'sudo ufw allow 22/tcp'.

Tämän jälkeen yritin toisella terminaalin ikkunalla kirjautua sisään verkkokoneelle komennolla 'ssh passeli@188.166.31.99'

![kuva](https://github.com/user-attachments/assets/e605029e-440f-473f-8a24-8f6d1c5063fb)

Pääsin sisään, joten kirjauduin root käyttäjänä ulos komennolla 'logout'.

Siirryin toiselle käyttäjälle ja ensimmäisenä muutin ufw asetuksen, jotta se käynnistyy aina kun kone käynnistyy komennolla 'sudo ufw enable'

Seuraavaksi aloin sulkemaan root käyttäjää.

Tein sen Teron ohjeen mukaisesti komennolla 'sudo usermod --lock root'

Tämän jälkeen muokkasin vielä sshd_config tiedostosta PermitRootLogin muuttujaa.

Pääsin tiedostoon käsiksi komennolla 'sudoedit /etc/ssh/sshd_config'

![kuva](https://github.com/user-attachments/assets/328b527c-a4e2-4a2e-ad97-434ff5d072e3)

Yritin nyt kirjautua root käyttäjänä sisään. 

![kuva](https://github.com/user-attachments/assets/1e21935d-be8c-4324-9d2c-8810bd8f314a)

Pääsy oli estetty, potkaisin kuitenkin vielä ostetun koneen SSH demonia asetusten loppuun viemiseksi. Tein sen komennolla 'sudo systemctl restart ssh'

Yllätyin, kun tämä ei kirjannut aktiivista käyttäjää ulos.

Lopuksi päivitin vielä kaikki paketit sekä käyttöjärjestelmän komennoilla
'sudo apt-get update'
'sudo apt-get upgrade'
'sudo apt-get dist-upgrade'

Tämän jälkeen avasin vielä palomuuriin portin http-yhteyksille komennolla 'sudo ufw allow 80/tcp' 

![kuva](https://github.com/user-attachments/assets/9ba8a736-505c-41e3-9281-c93c02acef52)

Komennolla 'sudo ufw status' näin, että sekä portti 22 ja 80 olivat nyt avoinna

![kuva](https://github.com/user-attachments/assets/ad975555-e7f1-4c41-a365-57f7d8091875)


Asensin seuraavaksi Apache2 palvelimen virtuaalikoneelle komennolla 'sudo apt-get install apache2'

Katsoin seuraavaksi virtuaalikoneeni IP-osoitetta Firefox selaimella ja päädyin Apachen tuttuun aloitusikkunaan. Totesin siis ensiaskeleiden olevan valmiit.

![kuva](https://github.com/user-attachments/assets/98787ed1-3313-48fb-8d56-c289f20c74f5)
















  











  
