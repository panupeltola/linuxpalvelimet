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




#  a) Testaa
