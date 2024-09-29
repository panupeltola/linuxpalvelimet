# Harjoitus 6 Hello Django

# Ympäristö:
- Windows 11 Education 23H2
- Intel Core i7-10770K (AMD 64)
- Nvidia GeForce 3080
- 32 GB RAM
- VirtualBox 7.0.20

## Virtuaalikone
- Debian 12

# a) Django esimerkkinä

Teen tehtävän käyttäen Tero Karvisen ohjetta (https://terokarvinen.com/2022/django-instant-crm-tutorial/) 

29.9.2024 klo 10:06

1. Päivitin virtuaalikoneeni paketit komennoilla sudo apt-get update ja sudo apt-get upgrade'
2. Asensin virtualenv paketin komennolla 'sudo apt-get -y install virtualenv'
3. Tarkistin seuraavaksi, mitä Teron ohjeessa oleva komento 'virtualenv --system-site-packages -p python3 env/' tarkoittaa ja mitä lupia kohteelle annetaan komennolla 'man virtualenv'

- virtualenv kutsuu prosessia
- '--system-site-packages' antaa virtuaaliympäristölle pääsyn site-packages kansioon, tämä on oletuksena estetty
- '-p' osoittaa mille kääntäjälle luodaan virtuaalinen yhteys (vakiona /usr/bin/python3)
- "/env" määrittää kansion, johon virtuaaliympäristö luodaan

4. Ajoin komennon 'virtualenv --system-site-packages -p python3 env/' ja tarkastin komennolla ls, että uusi kansio on tullut haluamaani kansioon

![kuva](https://github.com/user-attachments/assets/08205c0e-56d8-40a5-931a-de8945b68d20)

5. Käynnistin virtuaaliympäristön komennolla 'source env/bin/activate' Näin edenneeni virtuaalitympäristöön nimen vieressä olevasta (env) tekstistä.

![kuva](https://github.com/user-attachments/assets/e673f933-278a-4232-b3c5-f05254da927f)

6. Tarkistin pip paketin olemassa olemisen komennolla 'which pip' ja loin tiedoston "requirements.txt" jonne kirjasin sisällöksi "django"
7. Muistin Teron luennolla painottaneen, että tässä on oltava erittäin tarkka, että paketin nimi on oikein, sillä pip pakettivarasto on huonosti seurattu ja väärin kirjoitettu nimi voi ladata paketin, joka saastuttaa koneen
8. Tarkistuksen jälkeen ajoin komennon 'pip install -r requirements.txt'
9. Asentamisen jälkeen tarkistin vielä asennetun Djangon version komennolla 'django-admin --version'

![kuva](https://github.com/user-attachments/assets/2ef9c130-983c-4680-99ba-417fd3af0c0e)

10. Seuraavaksi loin uuden projektin nimeltään "passelico" komennolla 'django-admin startproject passelico'
11. Tämän jälkeen käynnistin palvelun siirtymällä luotuun projektiin komennolla 'cd passelico/' ja ajamalla komennon './manage.py runserver'

![kuva](https://github.com/user-attachments/assets/c16813f9-d744-4e4d-aac3-f8b1c2bfc496)

12. Tässä vaiheessa sain virheilmoituksen tekemättömistä migraatioista. Teron ohjeessa kuitenkin ajetaan ehdotetut komennot seuraavassa vaiheessa.
13. Seuraavaksi ajoin komennot './manage.py makemigrations' ja './manage.py migrate'

![kuva](https://github.com/user-attachments/assets/b70e59d5-f476-4a5f-a71a-1b2b7a41a4a8)

14. Seuraavaksi loin käyttäjän ja generoin sille salasanan asentamalla pwgen paketin ja ajamalla sen komennolla 'pwgen -s 20 1'

Komento määritettiin seuraavasti
- pwgen kutsuu
- -s luo salasanan täysin sattumanvaraisesti
- 20 määrittää salasanan pituuden
- 1 määrittää generoitavien salasanojen määrän

 15. Tämän jälkeen loin uuden käyttäjän komennolla './manage.py createsuperuser'
 16. Lisäsin käyttäjätiedot ja koetin seuraavaksi pääsenkö kirjautumaan admin ikkunaan sisään.

![kuva](https://github.com/user-attachments/assets/3ee18859-fd8a-4c78-81e9-579f16cebbb6)

17. Sain kuvassa näkyvän virheen, ja päätin vielä yrittää käynnistää palvelimen uudestaan komennolla './manage.py runserver' 

![kuva](https://github.com/user-attachments/assets/60c4e81b-8c4a-4a06-a0ea-6825a076c4a2)

18. Tällä kertaa sivu toimi
19. Yritin kirjautua sisään luomillani tunnuksilla

![kuva](https://github.com/user-attachments/assets/5a6084ab-4113-419f-9b2d-f112a86a8f9b)

20. Olin sisällä.
21. Loin uuden superkäyttäjän samalla tapaa kuin aiemmin ja nimesin sen "arto"
22. Pääsin tälläkin käyttäjällä kirjautumaan sisään admin oikeuksin
23. Seuraavaksi käynnistin ohjelman crm komennolla './manage.py startapp crm' ja lisäsin sen asennettujen ohjelmien luetteloon ohjeen määrittämällä tavalla

![kuva](https://github.com/user-attachments/assets/cf9a9dbe-4800-45f7-ab17-c27d4956fa41)

24. Loin models tietokantaan uuden kentän ohjeen opettamalla tavalla. Ymmärrykseni mukaan komennossa määritetään uusi luokka Customer, jolle annetaan yksi tieto, joka tässä tapauksessa on nimi maksimipituudeltaan 300 merkkiä.
    
![kuva](https://github.com/user-attachments/assets/fe66c93c-d262-4080-8fce-0ce07b67affb)

25. Ajoin seuraavaksi komennot './manage.py makemigrations' ja './manage.py migrate'
26. Ymmärtääkseni tämä lisää toiminnallisuudet django projektiin, muttei anna vielä suoraa mahdollisuutta päästä näihin ominaisuuksiin käsiksi. Tätä varten ne pitää lisätä admin.py tiedostoon.

![kuva](https://github.com/user-attachments/assets/3eeb12e0-05a5-4b76-bf66-013733c0d8ff)

27. Yrittäessäni käynnistää palvelinta komennolla './manage.py runserver' sain pitkän virhekomennon. Siinä oli kuitenkin selvästi määritetty virhe, sulku puuttui.

![kuva](https://github.com/user-attachments/assets/22789b4d-60a7-4d98-8527-cda4b186d963)

28. Korjasin virheen ja palvelin lähti iloisesti käyntiin.

![kuva](https://github.com/user-attachments/assets/41fca29a-4d59-4780-9530-120b67845841)

29. CRM ja Customers taulu olivat ilmestyneet admin näkymään
30. 
![kuva](https://github.com/user-attachments/assets/f29ef542-c25e-4f58-91b3-603f16bf0470)

31. Lisäsin uusia asiakkaita ja ne tulivat näkyviin "Customer object (n)" muotoisina merkintöinä, joiden sisältä löytyi määritetty nimi.
 
![kuva](https://github.com/user-attachments/assets/138a50e4-0e69-4e37-8907-de4bdf5e7fc4)

33. Yritin poistaa ja lisätä uuden nähdäkseni mitä numero Customer objectin perässä tarkoittaa.

![kuva](https://github.com/user-attachments/assets/d31b0b57-e60a-4629-ba10-3a7356bd85f4)

34. Luotuani uuden käyttäjän totesin, että tämä kuvaa juoksevaa numerointia, sillä uuden objektin numero oli 4 eikä 3.
35. Tein vielä Teron ohjeen mukaiset päivitykset ja lisäsin models.py tiedostoon funktion, joka vaihtaa ID:n tilalle nimen.

![kuva](https://github.com/user-attachments/assets/c2fd59c4-1cc9-4307-8127-6f2ccc59289d)

36. Totesin tämän tehtävän onnistuneen.

# b) Django tuotantoon

29.9.2024 klo 13:36

Käytin tehtävän tekemiseen Tero Karvisen ohjetta (https://terokarvinen.com/2022/deploy-django/)

1. Moni ohjeen vaiheista oli jo tehty aiemmissa tämän kurssin harjoituksissa, kuten name based hosting ja apachen asentaminen, sekä tässä harjoituksessa aiemmin tehty
2. En muistanut enää tarkkaan, mitä name based hostingeja minulla oli käytössä, joten päätin luoda uuden ja deaktivoida muut saadakseni puhtaan alkutilanteen
3. Olin jo aikaisemmassa vaiheessa siirtänyt edellisessä tehtävässä tehdyt aineistot uuteen kansioon, sillä en halunnut pitää niitä Home kansiossa
4. Tein siirron komennolla 'mv passelico publicwsgi/passelico'
5. Loin sijainnin ja väliaikaisen html tiedoston.

![kuva](https://github.com/user-attachments/assets/a1596dd5-ae75-43a3-bb6d-58817fc244dc)

6. Seuraavaksi loin yksinkertaisen Name Based Virtual Hosting konfigruraatiotiedoston Apachen asetuksiin.

![kuva](https://github.com/user-attachments/assets/6e60608f-8a6b-4ab1-82dc-dc499e1cb5f4)

7. Tutkin vielä mitä teron ohjeessa oleva 'Alias' komento tekee, sillä en muista huomanneeni sitä aiemmissa tehtävissä
8. Totesin kyseessä olevan Apachen ominaisuus mod_alias, joka toimii liikenteen ohjaamisessa sivuston sisällä (https://httpd.apache.org/docs/2.4/mod/mod_alias.html#alias)

![kuva](https://github.com/user-attachments/assets/f5401c17-7f09-4aa4-a67b-eb03aa7d627e)

9. Tehtyäni uuden sivun päätin vielä ottaa muut sites-aviable kansion conf tiedostot pois päältä komennolla 'sudo a2dissite [sivun nimi]'

![kuva](https://github.com/user-attachments/assets/0713bafe-f8b0-4756-980c-f0eb8d6587a7)

10. Tämän jälkeen vielä aktivoin uuden konfiguraation komennolla 'sudo a2ensite passelico.conf'

![kuva](https://github.com/user-attachments/assets/250caf78-7366-404f-96b4-10c9201435e0)

11. Yritin tehdä ohjeen mukaan, mutta tämä ohjasi minut Apachen muokkaamattomaan pääikkunaan.
12. Yritin tämän jälkeen muokata tiedostoa "/var/www/html/index.html"
13. Tämä muutti pääsivun ja totesin, että ongelma on jossain konfiguraatiotiedostossa.
14. Yritin edellisissä harjoituksessa käyttämääni DocumentRootia Aliaksen sijaan ja uusi sivu lähti toimimaan localhost osoitteessa
15. Loin uuden ympäristön komennolla 'virtualenv -p python3 --system-site-packages env' ja tein kaikki kohdan a) toimet uudelleen, koska en päässyt pois Debug sivulta.
16. Lopulta tajusin virheen johtuneen siitä, että käytin osoitteena 127.0.0.1:8000 ja /admin puuttui perästä, mutta tulipahan harjoiteltua toistamiseen
17. Muokkasin passelico.conf tiedostoa Teron ohjeen pohjalta.

![kuva](https://github.com/user-attachments/assets/bf87b19f-31fb-498d-a96c-dc624aed6636)



18. Tehtyäni nämä toimet asensin ohjeen mukaan libapache2-mod-wsgi-py3 paketin komennolla 'sudo apt-get -y install libapache2-mod-wsgi-py3'
19. Tämän jälkeen tarkistin ohjeen mukaan syntaxin ja käynnistin apachen uudelleen.

![kuva](https://github.com/user-attachments/assets/1afb8d5d-1936-4b7f-a57c-fc240e37bb34)

20. Sain kuitenkin vastaukseksi 404. Hetken asiaa mietittyäni totesin, että minun palvelimeni ei ole käynnissä.
21. Vaikka sen käynnistinkin, ei palvelin lähtenyt pelaamaan
22. Katsoin läpi konfiguraatiotiedostoani ja huomasin, että minulla on jäänyt kahteen määritykseen ylimääräinen kautta viiva

![kuva](https://github.com/user-attachments/assets/5db43d78-3caf-43be-b158-3f767f06499b)


23. Tämäkään ei toiminut, joten katsoin lokeja


![kuva](https://github.com/user-attachments/assets/c8aa6155-af64-487a-9435-33d88193ae0e)

24. Lokeista selvisi, että wsgi.py reitti oli väärin. Olin laittanut yhden kansion liian vähän jonoon. Tämän jälkeen käynnistin Apachen uudelleen ja toivoin parasta.


![kuva](https://github.com/user-attachments/assets/aeddf806-031f-4719-bbab-adcf37fd1f8e)

25. Djangon asennus onnistui vihdoin, tässä vaiheessa meni noin tunti kirotessa ja hermoillessa, eikä se suoranaisesti auttanut tarkkaavaisuutta.
26. Seuraavaksi poistin debug tilan päältä ohjeen mukaisesti settings.py tiedostosta.

![kuva](https://github.com/user-attachments/assets/f061b767-9d27-492d-9604-b2d25567ad0c)

27. Sivua ei enää löytynyt, kuten tarkoitus oli. Tämä on kuitenkin erilainen viesti kuin aiemmin, joten näin asian edenneen.

![kuva](https://github.com/user-attachments/assets/f70bbc0a-76bc-48c4-9a90-92cc2570cfd4)

28. Menin osoitteeseen localhost/admin ja löysin väärin ladanneen sivun. Koetin pääsenkö kirjautumaan sisään.
29. Sisäänkirjautuinen onnistui, seuraavaksi korjaan ohjeen mukaan tyyliseikkoja.
30. Muokkasin taas settings.py tiedostoa microlla.

![kuva](https://github.com/user-attachments/assets/3de9601d-89f9-4b12-8f77-3158ebba3db4)

32. Lisäsin ohjeen mukaisen polun juureen ja "import os" tiedoston alkuun.
33. Ajoin komennon '.manage.py collectstatic'
34. Tästä huolimatta sivun ulkoasu ei toiminut, vaikka ajon jälkeen tuli ilmotus 127 staattisen tiedoston kopioimisesta. Tätä tilannetta ei myöskään muuttanut Apachen uudelleen käynnistäminen.

![kuva](https://github.com/user-attachments/assets/3d372fc2-bb07-44f8-b281-5ab5abfe7dd8)
 
35. Päätin jättää asian sellaseen keskeneräiseksi ja kysyä asiasta mahdollisuuden tullessa, sillä pelkään korjaamalla rikkovani tilannetta entisestään. Ja logiikka toimii.

# Lähteet:

1. T. Karvinen, 2022, Django 4 Instant Customer Database Tutorial, https://terokarvinen.com/2022/django-instant-crm-tutorial/, luettu 29.9.2024
2. T. Karvinen, 2022, Deploy Django 4 - Production Install, https://terokarvinen.com/2022/deploy-django/, luettu 29.9.2024
3. The Apache Software Foundation, 2024, mod_alias, https://httpd.apache.org/docs/2.4/mod/mod_alias.html#alias, luettu 29.9.2024
4. 'man virtualenv', luettu 29.9.2024
5. 'man pwgen', luettu 29.9.2024
