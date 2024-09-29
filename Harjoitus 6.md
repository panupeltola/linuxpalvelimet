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

Puhun jatkossa verkossa olevast virtuaalikoneestani nimellä host ja paikallisesta virtuaalikoneestani nimellä local

1. Päivitin localin paketit komennoilla sudo apt-get update ja sudo apt-get upgrade'
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





















   
