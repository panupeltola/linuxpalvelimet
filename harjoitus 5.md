# Nimekäs

#a) Kotisivu

1. Aloitin luomalla kolme yksinkertaista HTML sivua.
2. Käytin ohjeena Tero Karvisen ohjetta yksinkertaisen HTML5 sivun luomiseen (https://terokarvinen.com/2012/short-html5-page/)
3. HTML5 komentoihin käytin apuna w3 schoolsin artikkeleja (https://www.w3schools.com/html/html_links.asp) ja (https://www.w3schools.com/html/html_images.asp)
4. Loin ensimmäisen yksinkertaisen laskeutumissivun. Halusin sivulle kuvan nähdäkseni miten ne toimivat sivulle lisätessä oman palvelimen kautta.

![kuva](https://github.com/user-attachments/assets/381e73e6-662c-4f86-b6f8-3d558045665e)

Sivun koodi

![kuva](https://github.com/user-attachments/assets/8fa8bc3c-682a-446e-aa4e-08cdf0a04552)

Sivu Firefox selaimella avattuna.

4. Seuraavaksi halusin vielä luoda linkit kahteen tulevaan sivuuni. Tein ne yksinkertaisella linkillä 'href' komennolla.

Lopulline sivu alla:
<!doctype html>
<html>
<head>
	<title>Panun ihmeellinen maailma</title>
	<meta charset="utf-8" />
</head>
<body>
	<h1>Tässä testataan sivun toimivuutta</h1>
	<p>Näyttäisi toimivan</p>
   <p><img src="thumbs-up.jpg" alt="Eveyrthing is working" style="width:800px;height:600px;"> </p>  
    <a href="www.panupeltola.com/minusta">Minusta </a>
    <a href="www.panupeltola.com/yhteystiedot">Yhteystietoni </a>
    
</body>
</html>

5. Koitin vielä validoida sivun ennen kuin menen eteenpäin. Linkkejä en voi testata, sillä tiedostoja ei ole vielä luotu.

![kuva](https://github.com/user-attachments/assets/a30ae6c5-59e8-4600-82da-62facf2739e0)

Ensimmäinen sivu validoitui

6. Tein samalla sapluunalla kaksi muuta sivua, joista poisitin kuvan, muutin vähän tekstiä ja päivitin linkit.

![kuva](https://github.com/user-attachments/assets/bea2a43f-9dd6-42b3-b180-6bdaaec7f06f)

Toisen sivun validointi ja lähdekoodi.

![kuva](https://github.com/user-attachments/assets/a6ea6dfd-bc13-4309-867e-8c0b7a46965d)

Viimeinen sivu.

7. Kun olin tässä onnistunut koitin vielä HTML tiedostojen välillä siirtymistä. Tämä ei toiminut, sillä tiedostojen päätteeksi ei ollut .html päätettä.
8. Tulevassa ratkaisussa kuitenkin liikenne ohjataan Name Based Hostingin avulla. Päätin siis yrittää saisinko tämän toimimaan oikealla koneella.

9. Yritin ottaa yhteyttä virtuaalikoneeseeni Windows käyttöjärjestelmän kautta, mutta huomasin, ettei koneen fingerprint ole sama kuin aiemmin raportoimani.
10. Halusin varmistaa, ettei kyseessä ole minkään sortin MITM hyökkäys ja avasin Debianin, jolla koneeseen oli jo liitytty nähdäkseni tuleeko tästä huomautusta.
11. Pääsin kirjautumaan virtuaalikoneelleni ilman mitään häiriöilmoitusta. Tutkin miten saan ECDSA julkisen avaimeni näkymään ja löysin StackOverFlowsta vastaukseksi komennon 'ssh-keygen -l -f /etc/ssh/ssh_host_ecdsa_key.pub'. Fingerprint vastasi verkkokoneen antamaa vastausta. Syytä sille miksi julkinen avain on muuttunut en tiedä.
12. Syötettyäni sen virtuaalikoneeseen alkoi homma taas pelittämään. Päätin tässä vaiheessa myös tehdä hiukan taustatyötä ja tehdä HTML dokumentit Debianilleni.
13. Tämän tehtyäni loin kansion Host koneelle uusille sivuille sen /home/passeli hakemistoon komennolla 'sudo mkdir /home/passeli/public_site'

![kuva](https://github.com/user-attachments/assets/5b757b00-e4a4-462e-9c3c-b6ed5d7c01f3)

14. Seuraavaksi piti saada tiedostot host koneelle. Päätin käyttää tässä Teron ohjeessaan mainitsemaa 'scp -r kansio/ tero@example.com:public_html/' komentoa. Halusin kuitenkin ensin ymmärtää mitä komento tekee ennen ajamista.

- scp kutsuu prosessin
- '-r'kopioi kansion rekursiivisesti
- seuraavaksi määritetään haluttu kansio
- lopuksi vielä kohdelaite ja kaksoispisteiden jälkeen kohdekansio.

15. Tein tämän ja katsoin miten käy.

![kuva](https://github.com/user-attachments/assets/ccb0b368-b400-4b07-b91f-d0a33fd42ce8)

16. Näin heti, että oikeat tiedostot ovat ilmeisesti johonkin siirtyneet. Katsoin seuraavaksi host koneelta näkyvätkö ne siellä.

![kuva](https://github.com/user-attachments/assets/63e66bc4-fd17-43e0-8439-3ce41bd95700)

Sekä tiedostot olivat paikallaan. Huomasin myös, että tämän lisäksi koko kansio tuli mukaan.

17. Seuraavaksi aloin luomaan Name Based Hosting raktaisuja.











   

