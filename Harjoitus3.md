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

# c) Etusivu uusiksi

Käytin tässä tehtävässä ohjeena ja pohjana T. Karvisen ohjetta "Name Based Virtual Hosts on Apache – Multiple Websites to Single IP Address" (https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/)

Ohjeessa on kuitenkin määritetty vakiosivu 'sudo' komentoa käyttäen ja päätin yrittää miten käy, jos luon uuden nimipohjaisen isännän osoitteelle  localhost.
Oletan tämän olevan erittäin huono käytäntö, sillä mikäli tämä toimii annan oikeuden muokata mahdollisesti koko palvelimen etusivua ilman pääkäyttäjän oikeuksia.
Teen tämän kokeilun vuoksi ja jos se toimii poistan osoitteen, ja teen sen käyttäjän oman avaussivun kautta.

## Riskin tavan testaaminen

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
Tällä kertaa curl löysi tiedon ja totesin, että tällä tapaa saa luotua ilman pääkäyttäjän oikeuksia muokattavan sivun localhost osoitteelle ilmeisesti koko palvelimelle.

Suljin ensin isännän komennolla 'sudo a2dissite localhost' ja potkaisin demonia, testasin vielä onko localhost palannut normaaliksi.

![kuva](https://github.com/user-attachments/assets/abce491f-3afe-4771-988d-07277bbcf283)

'curl localhost' näytti taas lähdekoodia, eli totesin sivun suljetuksi. Tämän jälkeen poistin vielä luomani tiedostot, etten vahingossa kytke niitä päälle.

![kuva](https://github.com/user-attachments/assets/f68c8ea3-d78d-435c-bd3d-c4499d99b014)

En saanut poistettua localhost.conf tiedostoa, joten päätin asentaa koko apachen uudelleen.

Käytin komentoja 'sudo apt-get purge apache2' ja sudo apt-get install apache2'

Tiedosto ei poistunut, vaikka koko ohjelman poisti.

![kuva](https://github.com/user-attachments/assets/90db5e06-81d2-4a09-83f6-66ee2be723ae)


Lopulta sain tiedoston poistettua komennolla 'sudo rm -f  /etc/apache2/sites-available/localhost.conf'

Tämän jälkeen asensin Apachen uudelleen, sillä olin poistanut kaiken turhan ja haitallisen.
Palautin virtuaalikoneen yhteyden verkkoon.

## Parempi tapa

7.9.2024 klo 20:20

Käytin tähän tapaan T. Karvisen toista ohjetta (https://terokarvinen.com/2016/new-default-website-with-apache2-show-your-homepage-at-top-of-example-com-no-tilde/)

Loin ensin uuden konfigurointitiedoston komennolla 'sudo micro /etc/apache2/sites-aviable/passeli.conf'

Lisäsin sinne alla olevan konfiguraation erona hetki sitten huonosti tehtyyn tapaan, tällä kertaa sivu localhost ei ohjaa suoraan sivulle.

![kuva](https://github.com/user-attachments/assets/c0f9a0f2-c7b0-4035-97fc-08252517b126)

Seuraavaksi aktivoin tämän sivun ja deaktivoin vakiosivun komennoilla 'sudo a2ensite passeli.conf' ja 'sudo a2dissite 000-default.conf'
Tämän jälkeen potkaisin demonia.

Yritin mitä komento 'curl localhost' kertoo.

![kuva](https://github.com/user-attachments/assets/b0a9424f-1c5c-425f-957d-cff3bd8b0f66)

Sivua ei ole olemassa, sillä sitä ei ole luotu. Luon sen komennoilla 'mkdir /home/passeli/public_html' ja 'micro /home/passeli/public_html/index.html'

Kirjasin yksinkertaisen tekstin index.html tiedostoon ja koetan sivun toimivuuden 'curl localhost' komennolla.

![kuva](https://github.com/user-attachments/assets/7e1ae8b3-7bb2-415f-8acb-6c0c4884f296)

Totesin localhostin sivun toimivan.

Seuraavaksi loin uuden isännän osoitteelle hattu.example.com. Aloitin luomalla sille konfiguraatiotiedoston.
Tein sen komennolla 'sudo micro /etc/apache2/sites-aviable/hattu.conf' Laadin ohjeen mukaisen konfiguraation.

![kuva](https://github.com/user-attachments/assets/4eedf910-e9b0-4d59-b5cd-3546ae4083ec)

Seuraavaksi aktivoin sivun ja loin sille sisällön määritettyyn sijaintiin.

![kuva](https://github.com/user-attachments/assets/0b5af74b-5be4-4b9a-b116-52e5fb9fa670)


Käytin HTML sivun tekemiseen myös T.Karvisen ohjetta. (https://terokarvinen.com/2016/new-default-website-with-apache2-show-your-homepage-at-top-of-example-com-no-tilde/?fromSearch=homepage)

![kuva](https://github.com/user-attachments/assets/af46b2fd-b5fd-459a-9824-ea58367a1dda)

Seuraavaksi potkaisin demonia ja katsoin miten käy kun menen sivulle hattu.example.com.


![kuva](https://github.com/user-attachments/assets/c26677cf-1d69-4a98-9dcc-c2186c79f616)

Sivu ei toiminut. Aloin selvittämään ongelmaa.

Yritin seuraavaksi tehdä samat asiat uudelleen, mutta nimesin sivun, konfiguraation ja tiedoston nimellä hattu.example.com.

![kuva](https://github.com/user-attachments/assets/a3c3b289-997c-4e86-b671-b6e2e7c78689)

Tällä kertaa sivu toimi. Käytin testiin Karvisen sivulta löytynyttä komentoa 'curl -H 'Host: hattu.example.com' localhost.

![kuva](https://github.com/user-attachments/assets/9835fde1-50dc-4da5-aaf5-12e90b2fadca)


Totesin tehtävän onnistuneeksi.

# e) HTML5

Päätin liimata äsken tekemäni sivun sisällön aikaisemmin tekemäni public_html sivun koodiksi ja katsoa toimiiko se.


![kuva](https://github.com/user-attachments/assets/d6b5d796-8e38-4074-82c0-e327af733c42)

Sivu näytti rumalta, mutta se toimi.

Alla vielä kuva lähdekoodista.

![kuva](https://github.com/user-attachments/assets/1eae5827-5b6c-4bbb-aac1-6f168fdaab4a)


# f) curl

Curlilla sai haettua sivun koodin. Esimierkkinä localhost, sillä koodi on lyhyt.

![kuva](https://github.com/user-attachments/assets/a002184f-03f6-425d-8751-83538658f74c)


Komennolla 'curl -I  https://bandcamp.com' näin sivun koodia otsikkotasolla. Tämä johtuu siitä, että komento 'curl -I' ei lähetä GET pyyntöä vaan HEAD pyynnön. Eli vastaukset ovat sivun otsikkoja ja niiden arvoja. (https://stackoverflow.com/questions/24563889/curl-i-and-curl-i-returning-different-results)

![kuva](https://github.com/user-attachments/assets/e1f6867c-2bc9-4e24-b1c0-54dff29530ec)

Tästä näen esimerkiksi käytetyn protokollan, aineiston tyypin, palvelimen ajan, sivun sisällön ja evästetietoja.

# Lähteet

Apache Software Foundation, 2024, Name-based Virtual Host Support, https://httpd.apache.org/docs/2.4/vhosts/name-based.html, luettu 7.9.2024
Apache Software Foundation, 2024, Log Files, https://httpd.apache.org/docs/current/logs.html, Luettu 7.9.2024
T. Karvinen, 2018, Name Based Virtual Hosts on Apache – Multiple Websites to Single IP Address, https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/, luettu 7.9.2024
T. Karvinen, 2016, New Default Website with Apache2 – Show your homepage at top of example.com, no tilde, https://terokarvinen.com/2016/new-default-website-with-apache2-show-your-homepage-at-top-of-example-com-no-tilde/, luettu 7.9.2024





































  





