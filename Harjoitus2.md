# Harjoitus 2 Komentaja Pingviini

# x) 

## Command Line Basics Revisited, Karvinen 2020

- Linuxin komentokehtteilla pystyy muutamalla komennolla välttämään suuren määrän graafisen käyttöliittymän klikkailuja
- Komentokehotteella tehdyt siirrot, poistot ja kopioinnit eivät kysele varmistuksia ja väärällä komennolla voi kadota suuri määrä asioita kerralla vahingossa
- Lähes jokaisesta ohjelmasta on olemassa käyttöohje, jonka saa näkyviin komennolla 'man ohjelmannimi'
- 'sudo' (Superuser do) komento ajaa kehotteen ylläpitäjänä, olettaen, että sen ajajalla on ylläpitäjän oikeudet
- Linuxin kansiorakenne on standardoitu ja käyttöjärjestelmässä olevat ohjelmat noudattavat sitä, mikäli haluavat toimia

# Ympäristö:
- Windows 10 Education 22H2
- Intel Core i7-10770K (AMD 64)
- Nvidia GeForce 3080
- 32 GB RAM
- VirtualBox 7.0.20


# a) Micro
31.8.2024 klo 9:00

Aloitin avaamalla terminaalin ja päivitin saatavilla olevat paketit komennolla 'sudo apt-get update'

![kuva](https://github.com/user-attachments/assets/bdf4afe7-8ff2-4cef-afa7-56b64a38bf96)

Tämän jälkeen asensin micron komennolla 'sudo apt-get -y install micro'

![kuva](https://github.com/user-attachments/assets/c08ed21b-e8c5-4272-aaa9-670838f5e6e4)

Olin jo asentanut Micron, joten poistin sen ja asensin uudelleen harjoituksen vuoksi. Poistin Micron komennolla 'sudo apt-get purge micro'

![kuva](https://github.com/user-attachments/assets/666de6b9-bf4c-4a0f-a213-f78ba5d3d958)

Varmistin vielä poiston onnistumisen komennolla 'apt list micro' löytämäni foorumilinkin ohjeen mukaisesti (https://askubuntu.com/questions/879877/how-to-know-whether-a-particular-package-is-installed-on-ubuntu)

![kuva](https://github.com/user-attachments/assets/b1f703f0-91ac-4bd5-b2db-def80600203d)

Micro näkyi listassa, mutta verkkosivun mukaan sen perässä pitäisi olla [installed] mikäli paketti on asennettu.
Asensin paketin komennolla 'sudo apt-get -y install micro', jonka jälkeen varmistin oliko foorumin ohjeet oikeat ajamalla vielä kerran 'apt list micro' komennon

![kuva](https://github.com/user-attachments/assets/08e5fb06-0697-4905-913f-4163820d9131)

Micro asentui ja 'apt list micro' komennolla paketin perässä näkyy nyt [installed].

Yritin vielä avata Microlla tiedoston nähdäkseni, että se toimii.

Varmistin, että työkansioni on sellainen, johon uskallan tiedostoja luoda 'pwd' komennolla. Tämän jälkeen loin uuden tiedoston komennolla 'micro passeli.txt'

![kuva](https://github.com/user-attachments/assets/a70a6b6b-9560-4a9e-b839-5670fb5afeb2)

Kirjoitin tekstiä Microon ja tallensin sen 'CTRL+S' näppäinyhdistelmällä

![kuva](https://github.com/user-attachments/assets/1f950094-f666-42ec-82ee-f0dfebee2165)

Varmistin vielä, että tiedoston teksti on tallentunut 'cat passeli.txt' komennolla

![kuva](https://github.com/user-attachments/assets/b9e4614c-ea3c-4b11-8b42-3279edda2538)

Teksti näkyy samana, joten totesin ohjelman asennuksen onnistuneen. 


# b) Apt

31.8.2024 klo 9:15

Totesin äskeistä harjoitusta tehdessäni, että minulla ei toimi tabulatuurilla automaattitäyttö. Nopealla googlettamisella kyseessä on paketti bash-completion, joka ei ole jokaisessa jakelussa automaattisesti (https://linuxhandbook.com/enable-tab-completion/). Se on siis yksi haluamani paketti, toisena otan Windowsista tutun 'tree' komennon ja viimeisenä linkistä (https://terminaltrove.com/categories/tui/) katsomieni pakettien osalta päädyin 'wiki-tui' pakettiin, jonka pitäisi näyttää helposti Wikipedian artikkeleja terminaalissa.

Yritin asentaa kaikkia kerralla komennolla 'sudo apt-get -y install bash-completion tree wiki-tui'

Asennnuksen jälkeen tuli virheilmoitus, että wiki-tui pakettia ei löydy. Tutkin sen ehdottanutta sivua tarkemmin ja totesin sen olevan osa eri paketinhallintaohjelmaa (pacman)

31.8.2024 klo 10:40

Pidin hetken taukoa ja tutkin järkeviä saatavilla olevia ohjelmia, halusin jonkun järjestelmänhallintaohjelmiston suoraan terminaliin ja nopealla googlaamisella löysin Htopin ja päätin asentaa sen. Yritin asentaa sitä komennolla sudo apt-get -y install htop'

![kuva](https://github.com/user-attachments/assets/a6616c7d-7931-4b12-b588-a26766f6b78b)

Tämän jälkeen testasin toimintoja, ja ensimmäisenä huomasin, ettei auto complete vieläkään toiminut kunnolla.
Kokeilin sitten 'tree' komentoa, mutta tämäkään ei toiminut. Tästä päättelin, että koska aikaisemmassa yrityksessäni kaikkia löytyneitä paketteja ei löytynyt, ei näistä ensimmäistäkään asennettu.
Kokeilin asentaa paketin tree uudelleen ja tällä se asentui uutena ohjelmana.

![kuva](https://github.com/user-attachments/assets/20d6ea73-8b39-491b-8e51-d612f9e1c328)


Unohdin ottaa tästä kuvan usean paketin kerrallaan asentamisesta, joista yhtä ei ollut olemassa, joten poistin asentamani tree ja htop paketit testatakseni toimiiko asentaako paketinhallinta vain jos kaikki paketit löytyvät.

Käytin uudelleen komentoa 'sudo apt-get -y install bash-completion tree wiki-tui'

![kuva](https://github.com/user-attachments/assets/ca122946-a4fb-441c-8051-edb1a7d4bf9d)

Mitään tietoa asentamisesta ei tälläkään kertaa tullut, tarkistin vielä tree ja bash-completion pakettien asennuksen aiemmin käyttämälläni 'apt list' komennolla

![kuva](https://github.com/user-attachments/assets/596f5f54-4478-4ffe-8602-f2aaaa471a9c)

Paketteja ei ollut asennettu. Totesin siis, että mikäli 'apt-get install' komennolla haluaa asentaa useampia paketteja tulee ne kaikki olla oikeita tai mitään ei kirjoiteta. Korvaan wiki-tui paketin htopilla ja ajan asennuksen uudelleen.

![kuva](https://github.com/user-attachments/assets/a3c27684-54a1-420d-9ace-c9dbbd19c2ea)

Tällä kertaa paketit asentuivat.

Kokeilin vielä niiden toiminnan.

Bash-Completionia toimii, siitä en saa järkevää kuvaa, sillä ohjelma ei tee järkeviä listauksia.

Tree loi kansioista helppolukuisen polun, missä näkyy myös alikansiot. Komentona toimi 'tree'

![kuva](https://github.com/user-attachments/assets/abd66a42-ba20-43f3-989e-f0b1c8d09d6d)

Htop näytti järjestelmän tiedot, resurssi ja prosessit. Komentona toimi 'htop'

![kuva](https://github.com/user-attachments/assets/6048a632-6a68-4713-9c4e-5cc588852a52)


# c) FHS

Katsoin seuraavaksi läpi Karvisen kirjoituksessa "Command Line Basics Revisited" läpi käymiä tärkeitä kansioita.
En lähtenyt erikseen siirtymään kansiosta toiseen vaan käytin absoluuttisia polkuja, sekä 'ls' komentoa. Esimerkiksi jos halusin nähdä juurikansion hain sen komennolla 'ls /'

![kuva](https://github.com/user-attachments/assets/0c247a45-06f0-470a-9a51-dcf690e92565)

Katsoin ensin juurikansion. Sen sisältämät kansiot ovat (https://www.howtogeek.com/117435/htg-explains-the-linux-directory-structure-explained/):

- Bin, sisältää järjestelmän käyttöön tarkoitetut tärkeät ohjelmat
- boot sisältää käynnistämiseen vaadittavat tiedostot
- dev sisältää laitteiden hallintaan liittyvät tiedostot
- etc sisältää konfiguraatio tiedostot
- home sisältää käyttäjien tiedostot
- lib sisältää ohjelmien vaatimat kirjastot
- lost+found järjestelmän kaatuessa palautetut tiedostot
- media sisältää irroitettavat laitteet, kuten cd-levyt
- mnt sisältää väliaikaisten käyttöjärjestelmien tiedot, joita voidaan käyttää esimerkiksi tiedostojen palauttamiseen
- proc sisältää järjestelmään ja prosesseihin liittyvää tietoa
- root sisältää root käyttäjän kotihakemiston
- run sisältää sovelluksien väliaikaisille tiedostoille paikan
- sbin sisältää ylläpitäjille tarkoitetut sovellukset
- srv sisältää laitteen palveluille tuottamia tiedostoja
- tmp sisältää poistettavissa olevia väliaikaisia tiedostoja
- usr sisältää vain käyttäjälle saatavilla olevia ohjelmia ja tietoja
- var sisältää esimerkiksi lokitietoja

Seuraavaksi ajoin komennon 'ls /home/' tämä kansio sisältää kaikkien käyttäjien kotihakemistot. Virtuaalikoneellani on vain yksi käyttäjä, joka sijaitsee tässä kansiossa.

![kuva](https://github.com/user-attachments/assets/8f891c71-ef06-488b-a897-6a761623e687)

Kansion /home/passeli/ sisällä on kaikki omat tiedostoni ja niille kansiot. Sen sisältö esitetty 'tree' komennolla

![kuva](https://github.com/user-attachments/assets/4374524c-96e3-4c43-8bd8-0ef4d08886df)

Seuraavaksi katsoin /etc kansion sisällön 'ls' komennolla. /etc/ sisältää kaikki ohjelmien konfiguraatio tiedostot. Avasin näistä kokeilun vuoksi sudoers tiedoston Microlla komennolla 'micro /etc/sudoers' 

![kuva](https://github.com/user-attachments/assets/59101b4a-bf40-47b3-91ec-42ff6220e97c)


Tämä estettiin, yritän samaa lisäämällä 'sudo' komennon alkuun

![kuva](https://github.com/user-attachments/assets/2e363178-fb7c-413a-bab8-95bd6ae8a088)


![kuva](https://github.com/user-attachments/assets/c525edc8-aa05-4d05-9d9c-d5ef9f373100)

Näin sain tiedoston auki ja huomasin tämän olevan tiedosto, joka hallinnoi sudo oikeuksia hallitsevia käyttäjiä. Tiedostossa ei kuitenkaan ole eritelty muita kuin käyttäjä root ja ryhmä sudo.
Yksittäisiä käyttäjiä ei siis ole listattu.


Katsoin mitä /media/ kansiossa on ja siellä näkyi myös käyttäjäni kansio. Katsoin mitä sen sisältä löytyy ja siellä oli VirtualBoxin guest additions cd paikallaan.

![kuva](https://github.com/user-attachments/assets/755289fd-54e9-45bd-9de1-156a14e80045)

Viimeisenä katosin vielä kansion /var/log/ sisään

![kuva](https://github.com/user-attachments/assets/515e40b2-0df3-4a42-84a5-64768ae55ee0)

Katsoin vielä boot.log tiedoston sisään komennolla 'sudo micro boot.log'

![kuva](https://github.com/user-attachments/assets/eef06de2-1d89-4389-b8b2-95ce73bc2c26)

# d) The Friendly M
31.8.2024 klo 12:50

Nukuin välissä hiukan kuumetta matalammaksi ja jatkan linuxin mahtavassa maailmassa.
Seuraavassa tehtävässä opettelen Grepin käyttöä, otin avuksi Youtubesta kanavan Learn Linux TV videon "Linux Crash Course - The grep Command".
Otin tästä kuitenkin vain perusideaa kiinni, sillä video tuntui selittävän asiat huonosti ja hyppi liikaa omaan makuuni. Kokeilin kuitenkin tästä oppineena tehdä grep komentoa /etc/ssh/ssh_config tiedostoon nähdäkseni mikä portti minulla on valittuna SSH yhteydelle.

![kuva](https://github.com/user-attachments/assets/7afc07a6-9013-4bd3-86f1-24013a023e6b)

Sain vastaukseksi #  Port 22. Risuaita edessä kuitenkin ehdottaisi, että tämä on vain kommenttina, eikä sitä ole todellisuudessa määritetty.

Luin seuraavaksi vielä toisen ohjeen (https://www.cyberciti.biz/faq/howto-use-grep-command-in-linux-unix/) ja yritin saada sieltä hyödyllisiä käyttökohteita, sillä pääni löi tyhjää.

Muokkasin artikkelista löytämäni komennon 'grep passeli /etc/passwd' nähdäkseni mitä tietoja passwd tiedosto sisältää käyttäjänimestäni saaden seruaavan vastauksen:


![kuva](https://github.com/user-attachments/assets/0b99b4e6-e352-488c-8127-f6051006a1da)

Halusin vielä ymmärtää mitä tämä saamani vastaus tarkoittaa ja löysin aiheesta seuraavan artikkelin (https://www.cyberciti.biz/faq/understanding-etcpasswd-file-format/)
Tieto on pätkitty kaksoispisteillä ja näyttää seuraavat asiat:
- Käyttäjän nimi
- Salasana (Ei näy tässä tiedostossa)
- Käyttäjä ID
- Ryhmä ID
- Käyttäjä ID info
- Kotihakemisto
- Käytetty shell

 # e) Pipe

 Viimeisenä vielä tutkin putkia ja koitin kahta eri asiaa. Ensin koitin ssh.config tiedoston muuttamista less tilaan ja sitten yritin tuoda verkosta jonkin artikkelin grepille.
 En enää muista tarkkaan miten verkosta saatu tieto tuodaan, mutta oman muistini mukaan sen saisi curl komennolla.

 Yritän kuitenkin ensin ssh.configia lessillä. Luen tiedoston 'cat' komennolla ja putkitan lessille.

 ![kuva](https://github.com/user-attachments/assets/9ab64b9b-f2e8-42c8-af36-85712ba5fbd4)


 Tämä onnistui. Asensin seuraavaksi curlin. 'sudo apt-get -y install curl' komennolla

 Ohjelma oli jo asennettu, joten päätin kokeilla, mitä tietoa komento 'curl https://en.wikipedia.org/wiki/Red-tailed_hawk' minulle antaa.

 ![kuva](https://github.com/user-attachments/assets/f1a65467-eeaf-4388-a3a1-f360d5bc06b9)

 Näköjään curl lataa koko lähdekoodin, jota en tässä tarvitse. Katsoin Wikipediasta haluamani tiedon ja tarkistan voiko sen hakea grepillä. Yrtiän hakea tietoa Kingdom putkittamalla äskeisen komennon perään '| grep Kingdom'

 ![kuva](https://github.com/user-attachments/assets/982899c9-e8a1-45ce-b522-8d4d12282bb8)

 Sain aivan erilaisen ongelmatilanteen. Totesin, ettei grep ole ehkä puhtaasti html koodille paras ja vaatisi jotain puhdistustoimenpiteitä.

 Halusin vielä onnistua jossain, niin päätin yritää voinko putkittaa ssh-config tiedoston suoraan microlle 'cat' komennon avulla. Koko komento on 'cat ssh_config | micro'
 
 ![kuva](https://github.com/user-attachments/assets/b7e81720-dcf8-4246-98ba-584bf5a3ee72)

 Tämä onnistui. Tarkistin voinko tallentaa tiedostoa.

![kuva](https://github.com/user-attachments/assets/280dedfe-d9ef-4f73-9160-5a4131032970)

Micro antaa tallentaa tiedoston, mutta pyytää uutta tiedoston nimeä. Näin voi siis näköjään luoda helposti kopion tiedostosta, vailla pelkoa että vahingossa rikkoisi mitään. En tallenna tiedostoa ja suljen virttuaalikoneen tältä viikkoa.


# Lähteet:
T. Karvinen, 2020, Command Line Basics Revisited, https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited, luettu 31.8.2024
askUbuntu foormuit, 2017, https://askubuntu.com/questions/879877/how-to-know-whether-a-particular-package-is-installed-on-ubuntu, luettu 31.8.2024
A. Prakash, 2020, Enable Tab Completion https://linuxhandbook.com/enable-tab-completion/, Luettu 31.8.2024
Terminal Trove,TUI Terminal Tools, 2024, https://terminaltrove.com/categories/tui/, Luettu 31.8.2024
C. Hoffman, 2016, The Linux Directory Structure, Explained, https://www.howtogeek.com/117435/htg-explains-the-linux-directory-structure-explained/, Luettu 31.8.2024
Learn Linux TV, 2022, Linux Crash Course - The grep Command, https://www.youtube.com/watch?v=Tc_jntovCM0&, katsottu 31.8.2024
V. Gite, 2024, Understanding /etc/passwd File Format, https://www.cyberciti.biz/faq/understanding-etcpasswd-file-format/, luettu 31.8.2024






 



 
