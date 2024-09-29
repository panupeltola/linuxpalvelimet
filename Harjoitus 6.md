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











   
