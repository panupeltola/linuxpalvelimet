# x) Lue ja tiivistä

## Name-based Virtual Host Support (https://httpd.apache.org/docs/2.4/vhosts/name-based.html)

- Nimipohjainen virtuaali isännöinti perustuu HTTP-paketin tunnisteen osana olevan "hostnamen" hyödyntämistä osana kohde isännän tunnistamista.
- Prosessissa DNS-palvelin määritellään ohjaamaan pyynnöt nimen perusteella oikeaan IP-osoitteeseen.
- Tällä säästää tarjolla olevia IPv4 osoitteita.
- Isäntää haetaan ensisijaisesti IP-osoitteen avulla, joten sen haku on abstraktoitava ennen kuin nimi nousee suuremmaksi prioriteetiksi.

## Name Based Virtual Hosts on Apache – Multiple Websites to Single IP Address (https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/)

- Ohjeessa näytetään miten luodaan uusi sivu saman Apache palvelimen sisälle
- Ohjeessa Teron käyttämä komento 'echo "Default"|sudo tee /var/www/html/index.html' luo ensin teksitn "Default" komennolla 'echo' ja putkittaa sen komnennolle 'tee' joka kirjoittaa tiedon haluttuun tiedostoon (ja oletettavasti korvaa olemassa olevan tekstin)
- Ohjeessa luodaan uusi tiedosto kansioon "sites-aviable" ja se configuroidaan vastaamaan nimeen.
- Konfiguraatiotiedoston osa 'VirtualHost *:80' ohjaa käsitykseni mukaan edellisessä tekstissä opitun IP-osoitteen prioriteetin muutoksen, jolloin kaikki isännälle tulevat HTTP paketit ovat IP-osoitteeltaan tavallaan turhia ja nimipohjainen prosessi tulee prioriteetiksi.
- Kun isäntä on luotu luodaan vielä sivu määritettyyn kansioon.
- Lopuksi testataan.


# Ympäristö:
- Windows 10 Education 22H2
- Intel Core i7-10770K (AMD 64)
- Nvidia GeForce 3080
- 32 GB RAM
- VirtualBox 7.0.20


#  a) Testaa

7.9.2024 klo 18:20

Aloitin testaamalla, että aikaisemmin asennettu ja muutetulla kotisivulla oleva palvelin toimii yhä komennolla 'curl localhost'

![kuva](https://github.com/user-attachments/assets/1f28425b-cf6c-4923-b2a3-37c1679190ba)

Tekstiä oli enemmän, kuin muistin enkä ollut enää varma ovatko asetukseni oikein ja toimiiko Apache. Päätin tarkastaa asian menemällä selaimella osoitteeseen "localhost". 

![kuva](https://github.com/user-attachments/assets/e42a3853-1f77-49b3-8c81-463844a179f1)

Totesin, että sivu toimii ja Apache pyörii.

# b) Etsi

7.9.2024 klo 18:25

Seuraavaksi tutkin näkyykö äsken lataamani sivu lokeissa. Hain tietoa T. Karvisen luennolla näyttämällä komennolla 'tail -f /var/log/apache2/access.log'

![kuva](https://github.com/user-attachments/assets/3ab6cc36-cd2e-4411-8ae2-bcf36982cb7d)

Vastaukseksi sain tänään tekemäni kaksi hakua, joista toinen tapahtui 'curl' komennolla ja toinen Firefoxin avulla.
Tutkin lähdettä lokitiedoston tulkitsemista varten ja löysin Apachen dokumentaation. Lokimerkinnän tiedot on erotettu yllä olevassa kuvassa välilyönneillä.
Viiva tarkoittaa, että tietoa ei ole saatavilla.

(https://httpd.apache.org/docs/current/logs.html)

- "127.0.0.1" Hakupyynnön tehneen laitteen IP-osoite
- "-" Tässä olisi RFC 1413 identiteetti, ei käytetä usein tiedon epätarkkuuden takia
- "-" Toisen viivan kohdalla olisi HTTP autentikaation määrittämä käyttäjäid
- "[07/Sep/2024:18:29:12 +0300]" Määrittää haun ajan, sekä aikavyöhykkeen.
- "GET / HTTP/1.1" Kertoo pyynnön tehneen laitteen käyttäneen 'GET' komentoa kohteesta "/" (juuri) protokollalla HTTP1.1
- "200" Kertoo palvelimen vastauksen, 200 ilmoittaa onnistuneesta pyynnöstä
- "3380" ilmoittaa lähetetyn tiedon koon, ilman paketin otsikon viemää tilaa.
- "-"  En löytänyt varmaa tietoa tälle tiedolle, mutta oletan sen olevan HTTP pyynnön otsikko
- "Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0" HTTP otsikon selaimen itsestään ilmoittama tieto.

# Etusivu uusiksi

Käytin tässä tehtävässä ohjeena ja pohjana T. Karvisen ohjetta "Name Based Virtual Hosts on Apache – Multiple Websites to Single IP Address" (https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/)

Ohjeessa on kuitenkin määritetty vakiosivu 'sudo' komentoa käyttäen ja päätin yrittää miten käy, jos luon uuden nimipohjaisen isännän osoitteelle  localhost.
Oletan tämän olevan erittäin huono käytäntö, sillä mikäli tämä toimii annan oikeuden muokata mahdollisesti koko palvelimen etusivua ilman pääkäyttäjän oikeuksia.
Teen tämän kokeilun vuoksi ja jos se toimii poistan osoitteen, ja teen sen käyttäjän oman avaussivun kautta.

Aloitin luomalla nimipohjaisen isännän komennolla 'sudoedit /etc/apache2/sites-aviable/localhost.conf' ja kirjaamalla sen sisällön

![kuva](https://github.com/user-attachments/assets/1b12d04d-314e-4c21-aef3-b6cf7f1d2192)

Tämä idea alkoi tuntua niin huonolta, että poistin vielä virtuaalikoneeni verkosta kaiken varalta. 

Aktivoin sivun komennolla 'sudo a2ensite localhost' ja potkaisin demonia komennolla 'systemctl restart apache2'

Tämän jälkeen loin kansion ja tiedoston määrittämääni sijaintiin ja yritin hakea localhostia 'curl' komennolla.

![kuva](https://github.com/user-attachments/assets/ed0e36e4-6b4e-4db7-a665-ea3e03b07020)


Aikaisemmin tämä oli näyttänyt minulle Apachen pääsivun lähdekoodia.

![kuva](https://github.com/user-attachments/assets/5164421f-9d18-4dc3-aca8-4952f38d35f2)

Ainakaan suoraan Apache ei antanut muuttaa koodia. Yritän vielä aktivoida käyttäjien kansiot komennolla ' sudo a2enmod userdir'

![kuva](https://github.com/user-attachments/assets/c8301e22-4db1-44e5-a273-b3d2d0bfc1a8)

Tämä oli jo sallittu. Päätin vielä koettaa katsoa apachen error logia ennen kuin nollaan muutoksen ja aloitan alusta.

![kuva](https://github.com/user-attachments/assets/d1e02e06-d470-4a48-a14d-97bd55da0fc0) 

Tajusin virheen johtuneen luodessani index.html tiedoston väärään kansioon. Loin sen samalla komennolla kuin aiemmin, korjaten kansioinnin.








  





