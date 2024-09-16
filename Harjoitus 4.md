# z) Lue ja tiivistä

## Teoriasta käytäntöön pilvipalvelimen avulla (https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/)

- Susanna hankkii virtuaalikoneen DigitalOceanin kautta
- Virtuaalikone luodaan Debian 11 käyttöjärjestelmälle ja halvimpaan virtuaalikoneeseen
- SSH-yhteys salataan salasanalla
- Nimipalvelin hankitaan Namecheap-palvelun kautta
- Nimipalvelin asetettiin ennen palomuuria
- Lopuksi kone suojataan
- Koneelle yritetään lähes välittömästi murtautua

## First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS (https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/)

- Teron ohjeessa käydään läpi uuden virtuaalikoneen käyttökuntoon laittaminen
- Ensin kirjaudutaan root käyttäjänä sisään komennolla root@ipnumero/osoite
- Ensimmäisenä asennetaan palomuuri ja sallitaan siihen SSH-portti 22 liikenne komennolla 'sudo ufw allow 22/tcp'
- Toisena lisätään uusi käyttäjä ja tämä käyttäjä liitetään ryhmiin "sudo", "adm" ja "admin"
- Hyvän tavan mukaan aina tulee käyttää mahdollisimman pieniä oikeuksia asian tekemiseen, tämän takia heti kunhan varmistetaan, että SSH yhteys toimii uudella käyttäjällä estetään root käyttäjä.
- Tämä tehdään komennoilla :
- $ sudoedit /etc/ssh/sshd_config
    # ...
    PermitRootLogin no
    # ...
  $ sudo service ssh restart  
