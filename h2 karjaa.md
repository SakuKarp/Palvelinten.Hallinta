# x) Lue ja tiivistä.

Slater 2017: What is the definition of "cattle not pets"?. (Vain tuo yksi vastaus DevOps Stack Exchangen kysymykseen)

 - pets ovat palvelimia joita pitää huolellisesti käyttää

-  Cattle on palvelimia joita käytetään joukoissa, ne ovat automatisoituja ja ne voidaan korvata helposti tekemällä uuden

Karvinen 2017: Vagrant Revisited – Install & Boot New Virtual Machine in 31 seconds (Suosittelen koneeksi 'vagrant init debian/bullseye64')

- uuden asennus ja käynnistys nopeasti

- Vagrant ja virtualboxi

- ssh kirjautuminen

- hallinta

- tuhoaminen

Karvinen 2023: Salt Vagrant - automatically provision one master and two slaves

- vagrantin asennus

- tehdään vagrantfile tietokoneille

- Käytetään komentoja etäkoneille

- 1 master 2 slave

- tietokoneen tuhoaminen

a) Asenna Vagrant. (Toiminee parhaiten isäntäkäyttöjärjestelmässä, siis siinä, joka pyörii raudalla)

Asensin vagrantin https://developer.hashicorp.com/vagrant/downloads

- Käytin versiota: 2.4.0 AMD64

b) Yksi maankiertäjä. Asenna yksi kone Vagrantilla, ota siihen SSH-yhteys, osoita että netti toimii.
 
      $ vagrant init debian/bullseye64
      $ vagrant up
      $ vagrant ssh

- vagrant init debian/bullseye64 luo uuden Vagrant tiedoston
- vagrant up käynnistää koneen
- vagrant ssh luo SSH-yhteyden virtaalikoneeseen
  
![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/3f7d3e32-a5db-4774-a116-f4fef3541662)

- Tässä pingasin googlea ja katsoin että se on yhteydessä nettiin

      $ ping google.com


c) Oma orjansa. Asenna Salt herra ja orja samalle koneelle.

      $ sudo apt update #päivitin paketit
      $ sudo apt install salt-master salt-minion # asensin salt masterin ja minionin
      $ sudo systemctl start salt-master # starttasin masterin
      $ sudo systemctl start salt-minion # starttasin minionin
      $ sudo systemctl status salt-master # katsoin masterin statuksen
      $ sudo systemctl status salt-minion # katsoin minion statuksen

Master status: Active
![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/528327e7-1530-42d0-b963-3225a2b2d117)
Minion status: Active
![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/2eccb2b0-fa3a-4801-9628-f90d67881061)


d) Asenna Saltin herra-orja arkkitehtuuri toimimaan verkon yli.




e) Aja useita idempotentteja (state.single) komentoja verkon yli.


f) Kerää teknistä tietoa orjista verkon yli (grains.item)


g) Aja shell-komento orjalla verkon yli.


h) Hello, IaC. Tee infraa koodina kirjoittamalla /srv/salt/hello/init.sls. Aja tila jollekin orjalle. Tila voi esimerkiksi tehdä esimerkkitiedoston johonkin hakemistoon. Testaa toisella komennolla, että pyytämäsi muutos on todella tehty.
