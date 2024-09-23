# Nimekäs

# a) Kotisivu

1. Aloitin luomalla kolme yksinkertaista HTML sivua.
2. Käytin ohjeena Tero Karvisen ohjetta yksinkertaisen HTML5 sivun luomiseen (https://terokarvinen.com/2012/short-html5-page/)
3. HTML5 komentoihin käytin apuna w3 schoolsin artikkeleja (https://www.w3schools.com/html/html_links.asp) ja (https://www.w3schools.com/html/html_images.asp)
4. Loin ensimmäisen yksinkertaisen laskeutumissivun. Halusin sivulle kuvan nähdäkseni miten ne toimivat sivulle lisätessä oman palvelimen kautta.

![kuva](https://github.com/user-attachments/assets/381e73e6-662c-4f86-b6f8-3d558045665e)

Sivun koodi

![kuva](https://github.com/user-attachments/assets/8fa8bc3c-682a-446e-aa4e-08cdf0a04552)

Sivu Firefox selaimella avattuna.

4. Seuraavaksi halusin vielä luoda linkit kahteen tulevaan sivuuni. Tein ne yksinkertaisella linkillä 'href' komennolla.

Lopullinen sivu alla:

![kuva](https://github.com/user-attachments/assets/0acf80d5-5348-457d-9ba6-855ad5637a0a)

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
11. Pääsin kirjautumaan virtuaalikoneelleni ilman mitään häiriöilmoitusta. Tutkin miten saan ECDSA julkisen avaimeni näkymään ja löysin StackOverFlowsta vastaukseksi komennon 'ssh-keygen -l -f /etc/ssh/ssh_host_ecdsa_key.pub'. Fingerprint vastasi verkkokoneen antamaa vastausta. Syytä sille miksi julkinen avain on muuttunut en tiedä. (https://stackoverflow.com/questions/10060530/what-command-do-i-use-to-see-what-the-ecdsa-key-fingerprint-of-my-server-is)
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

Päivä ehti vaihtua ja jatkoin tehtävää 23.9.2024 klo 17:10.

18. Yritin ensin saada yhden sivun toimimaan ja käytin siihen ohjeena aiemmin tekemääni tehtävää.

![kuva](https://github.com/user-attachments/assets/db9835b1-b344-44e8-a5ab-81933a74e21a)

19. Loin VirtualHost configuraation ja tämän jälkeen nimesin vielä olemassa olevan main.html tiedoston index.html muotoon omaa työtäni helpottaakseni. Tein sen komennolla 'mv main.html index.html'

20. Tämän jälkeen otin sivun käyttöön komennolla 'sudo a2ensite panupeltola.conf' ja potkaisin demonia komennolla 'sudo systemctl restart apache2'

![kuva](https://github.com/user-attachments/assets/4c960aa5-aa5d-4862-8721-35aa310ed455)

21. Mentyäni sivulle sain 403 virheen. Muisitin aiemmilta oppitunneilta, että tämä voi johtua puutteellisista käyttöoikeuksista. Ajoin Teron luentomateriaalista komennon 'chmod ugo+x $HOME $HOME/public_html/'

![kuva](https://github.com/user-attachments/assets/d6780d2a-32c8-4d4d-a620-a00a3a5d5f8e)

Mestariteos areenalla.

22. Magnum Opukseni oli nyt nähtävillä. Vielä piti ratkaista sivujen välinen linkittäminen.

![kuva](https://github.com/user-attachments/assets/cc10b081-2c36-4000-9347-a426814c8135)

23. Viedessäni hiiren linkin päälle huomasin, että linkkini on aivan liian pitkä. Koitin siis yksinkertaisesti muokata HTML tiedostoja siten, että 'href' komento viittaa vain juuressa olevaan tiedostoon esim "/minusta.html"

![kuva](https://github.com/user-attachments/assets/c2c52116-1a77-4ba7-acbb-773cc321f431)

Ensimmäinen yritys lähdekoodilla näytti tältä, potkaisin demonia tämän jälkeen ja päivitin sivuni.

![kuva](https://github.com/user-attachments/assets/d9f220f5-6cd8-41fe-94da-1826d34fbd0e)

Linkki toimi, mutta sivu ei. Päätin ensin korjata muut HTML tiedostot ennen jatkamista.

![kuva](https://github.com/user-attachments/assets/e9f817a9-d37e-428f-a57f-07c6c4982fc9)

minusta.html linkit korjattu

24. Tässä vaiheessa minuun iski tajuaminen, että olin unohtanut linkkien perästä ".html" päätteen. Päätin yrittää tätä ennen pidemmälle etenemistä.

![kuva](https://github.com/user-attachments/assets/692f0ad7-a0c0-416d-a1d5-fa5bd021247c)

25. Nyt linkki toimi. Korjasin kaikki tiedostot siten, että ne linkittyivät keskenään.

![kuva](https://github.com/user-attachments/assets/38487c9a-a1d9-4e12-b723-e8d420bbf954)

Yhteystiedot.html korjattu.

![kuva](https://github.com/user-attachments/assets/f700931a-0835-4997-8b30-d0b0a088aa71)

Minusta.html korjattu.

26. Koitin vielä kaikkien välisten sivujen toimivuuden. Ihmettelin jo miksi ei toiminut, kunnes muistin, etten ollut potkaissut demonia. Tein sen ja yritin uudelleen.

27. minusta.html ja yhteystiedot.html välillä linkki toimi ja myös index.html eteenpäin. Tajusin hetken mietittyäni, että olin nimennyt main.html uudelleen index.html nimelle ja olin unohtanut vanhan nimen kohteelle.

28. Korjasin tiedostot, sama kuin aiemmissa kuvissa, mutta mainin tilalla index.

29. Viimeinen potku demonille ja toiveet olivat korkealla.

30. Tällä kertaa kaikki toimivat. Ja totesin myös ehdon ilman pääkäyttäjän oikeuksia muokkaamisesta toimivan, sillä sen verran monta kertaa näitä komennolla 'micro tiedosto.html' muokkasin.
31. Totesin siis tehtävän onnistuneen.

# B) Alidomain

23.9.2024 18:26

## CNAME vai A tietue
- CNAME (Canonical name) ohjaa aina sivulle, muttei IP-osoitteeseen
- Käytetään helpottamaan usean tietueen hallintaa
- A-tietua antaa enemmän vapautta ja mahdollistaa mihin tahansa liikenteen ohjaamisen

1. Aloitin lukemalla mitä CNAME tietue tarkoittaa. Se ohjaa yhdestä osoitteesta toiseen, kuitenkin aina verkko-osoitteeseen eikä IP-osoitteeseen. Tällä helpotetaan kahden erillisen tietueen ylläpitämistä. (https://www.cloudflare.com/learning/dns/dns-records/dns-cname-record/)
2. Seuraavaksi lähdin metsästämään NameCheapin palvelusta alidomainin luontia.
3. Löysin aiheesta videon NameCheapin sivulta ja päätin ensin yrittää CNAME tietueen luontia minusta.html sivulle. (https://www.namecheap.com/support/knowledgebase/article.aspx/10336/2254/video-how-to-create-subdomain-for-my-domain-via-namecheap-account/)

![kuva](https://github.com/user-attachments/assets/3e771f07-bf2e-4815-a9bd-54798105f0af)

Tietue luotiinn lisäämällä "Recordin" "Host" osaan haluttu alku. Tässä tapauksessa lisäsin "etusivu".

Lisäsin myös A-tietueen joka osoittaa virtuaalikoneeseen.

![kuva](https://github.com/user-attachments/assets/2794096b-3086-43c6-acf9-19ebe199dda3)

Koitin tietueita heti tehtävän tehtyäni.

![kuva](https://github.com/user-attachments/assets/f30e0b57-d301-4830-9107-658447a943c2)

Yllätyin, kun linux-kurssi.panupeltola.com näytti sivun vanhaa päivittämätöntä versiota. Oletan tämän johtuvan NameCheapin vanhasta kopiosta.

Myös CNAME tietue avaa vanhan version. Pääasia kuitenkin, että molemmat tietueet yhdistivät oikeaan osoitteeseen. Tähän voisi varmasti tehdä helposti sivuston siirtoja Name Based Virtual Hostingilla.

# C) Pubkey

1. Seuraavassa tehtävässä loin avainparin, jolla hallitsisin jatkossa virtuaalikonetta. Käytin tähän DigitalOceanin ohjetta (https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-on-debian-11)

![kuva](https://github.com/user-attachments/assets/5a99d42d-0cf7-4dfd-9f67-bedc559cc132)

Loin avainparin komennolla 'ssh-keygen' ja laadin sille salasanan.

2. Todettuani, että 'ssh-copy-id' on helpoin komento saada avain siirrettyä host koneelle käytin sitä ja kirjotin salasanani koneelle.

![kuva](https://github.com/user-attachments/assets/7aa79903-9d6b-45e2-a06d-6481a3164afc)

3. Tämän jälkeen yritin kirjautua koneelle.

![kuva](https://github.com/user-attachments/assets/21036912-2102-4a4a-bdc3-0eec836772c8)

Debian kysyi äsken asettamaani passcodea, kirjoitin sen sisään ja pääsin koneelle ilman vanhaa salasanaa.

4. Lopuksi halusin vielä sulkea mahdollisuuden kirjautua salasanalla. Tein sen muokkaamalla ssh konfiguraatiotiedostoa komennolla 'sudo micro /etc/ssh/sshd_config'

![kuva](https://github.com/user-attachments/assets/2a689951-c031-475e-877b-1d4c762f6c6e)

Salasanatodennus oli jo pois päältä, eli sitä ei tarvinnut enää erikseen muokata. Kirjauduin tässä vaiheessa virtuaalikoneelta ulos, sillä sen työ oli tehty.

# d) DNS

23.9.2024 klo 18:48

## Komennot:

- Host suorittaa yksinkertaisen DNS haun ja noutaa verkko-osoitteen nimeen liitetyt IP-osoitteet
- Dig hakee sitä vastaavat palvelimet DNS-haun avulla, tyypillinen vastaus kertoo palvelimen, paketin TTL tiedon (time to live), tyypin (IN on internet) ja tietueentyypin (esimekriksi A tietue)

## A) panupeltola.com

![kuva](https://github.com/user-attachments/assets/70b2c7f2-19d4-45d7-91c9-81e57ff297e1)

'host panupeltola.com' palautti vastaukseksi verkkokoneen IP-osoitteen.

'dig panupeltola.com' palautti enemmän tietoa.

![kuva](https://github.com/user-attachments/assets/d8b7fa45-bc1c-4a2e-a66f-b8aee5b8509c)

Vastauksesta näkyy, että osoitteella on A-tietue  omaan verkkokoneeseeni. Palvelimen tiedot hain Who.is palvelun kautta ja vastannut DNS-palvelin on rekisteröity APNIC:ille (Regional Internet registry for the Asia Pacific region). Eli kaukaa haki palvelin. Paketin TTL oli 272.



![kuva](https://github.com/user-attachments/assets/c43ca39d-6f4e-43b1-a633-0e9856ce9eae)


## B) ottosbarbershop.fi

Seuraavaksi päätin tutkia parturini kotisivut.

![kuva](https://github.com/user-attachments/assets/6624abe0-36f1-4f86-b1bf-1d5f7027e791)

'host' antoi yhden vastauksen.

Tämän vastauksen omistaa ripe ncc, joka vaikuttaa olevan euroopan IP-numeroista vastaava elin

![kuva](https://github.com/user-attachments/assets/266fcd23-9c70-4861-a5ed-edb9c8f1dfdf)

Tällä haulla näen, että IP-osoite on sama, mutta osoitteella on lisäksi CNAME tietue, jolla saadaan myös www. alku toimimaan.
DNS palvelin on sama. Paketin TTL oli erittäin korkea (1754)

## C) jimms.fi

Viimeisenä katsoin vielä Jimm's PC storen tiedot.

'host jimms.fi' palautti kolme IPv4 osoitetta, mutta myös kolme IPv6 osoitetta.

![kuva](https://github.com/user-attachments/assets/9e9fbb94-32d8-4e66-825e-8056e378b9a4)

Kaikki nämä osoitteet omistaa CloudFlare.

'dig jimms.fi' palautti kolme A-tietuetta.

![kuva](https://github.com/user-attachments/assets/725ec75f-ed28-4df2-b373-466d69058141)

Yhtään CNAME tietuetta esim www etuliitteeseen ei ollut. Tällä haulla ei myöskään näkynyt IPv6 haut.
Syytä tälle en keksi.

Yleisesti huomiona, että kaikilla yhteen hostiin liittyvillä tietueilla oli aina sama TTL.

# Lähteet:

1. T. Karvinen, 2012 Short HTML5 Page, https://terokarvinen.com/2012/short-html5-page/, luettu 22.9.2024
2. W3Schools, HTML Links, https://www.w3schools.com/html/html_links.asp, luettu 22.9.2024
3. W3Schools, HTML Images, https://www.w3schools.com/html/html_images.asp, luettu 22.9.2024
4. StackOverflow, What command do I use to see what the ECDSA key fingerprint of my server is?, https://stackoverflow.com/questions/10060530/what-command-do-i-use-to-see-what-the-ecdsa-key-fingerprint-of-my-server-is, luettu 22.9.2024
5. T.Karvinen, 2024 Linux Palvelimet 2024 alkusyksy, https://terokarvinen.com/linux-palvelimet/, luettu 23.9.2024
6. Cloudflare, What is a DNS CNAME record?, https://www.cloudflare.com/learning/dns/dns-records/dns-cname-record/, luettu 23.9.2024
7. J. Camisso, How to Set Up SSH Keys on Debian 11, https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-on-debian-11, luettu 23.9.2024
8. Phoenixnap, 2024, dig Command in Linux with Examples, https://phoenixnap.com/kb/linux-dig-command-examples, luettu 23.9.2024
9. NameCheap, How to create subdomain for my domain via Namecheap account, https://www.namecheap.com/support/knowledgebase/article.aspx/10336/2254/video-how-to-create-subdomain-for-my-domain-via-namecheap-account/, katsottu 23.9.2024







































 












   

