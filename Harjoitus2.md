# Harjoitus 2 Komentaja Pingviini

# x) 

## Command Line Basics Revisited, Karvinen 2020

- Linuxin komentokehtteilla pystyy muutamalla komennolla välttämään suuren määrän graafisen käyttöliittymän klikkailuja
- Komentokehotteella tehdyt siirrot, poistot ja kopioinnit eivät kysele varmistuksia ja väärällä komennolla voi kadota suuri määrä asioita kerralla vahingossa
- Lähes jokaisesta ohjelmasta on olemassa käyttöohje, jonka saa näkyviin komennolla 'man ohjelmannimi'
- 'sudo' (Superuser do) komento ajaa kehotteen ylläpitäjänä, olettaen, että sen ajajalla on ylläpitäjän oikeudet
- Linuxin kansiorakenne on standardoitu ja käyttöjärjestelmässä olevat ohjelmat noudattavat sitä, mikäli haluavat toimia


# a) Micro

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

Totesin äskeistä harjoitusta tehdessäni, että minulla ei toimi tabulatuurilla automaattitäyttö. Nopealla googlettamisella kyseessä on paketti bash-completion, joka ei ole jokaisessa jakelussa automaattisesti (https://linuxhandbook.com/enable-tab-completion/). Se on siis yksi haluamani paketti, toisena otan Windowsista tutun 'tree' komennon ja viimeisenä linkistä (https://terminaltrove.com/categories/tui/) katsomieni pakettien osalta päädyin 'wiki-tui' pakettiin, jonka pitäisi näyttää helposti Wikipedian artikkeleja terminaalissa.

Yritin asentaa kaikkia kerralla komennolla 'sudo apt-get -y install bash-completion tree wiki-tui'

Asennnuksen jälkeen tuli virheilmoitus, että wiki-tui pakettia ei löydy. Tutkin sen ehdottanutta sivua tarkemmin ja totesin sen olevan osa eri paketinhallintaohjelmaa (pacman)
Yritin kolmanneksi (https://github.com/rothgar/awesome-tuis) linkin takaa löytynyttä spotify-player pakettia.








