x) Lue ja tiivistä.

# Slater 2017: What is the definition of "cattle not pets"?. (Vain tuo yksi vastaus DevOps Stack Exchangen kysymykseen)

pets ovat palvelimia joita pitää huolellisesti käyttää

Cattle on palvelimia joita käytetään joukoissa, ne ovat automatisoituja ja ne voidaan korvata helposti tekemällä uuden

# Karvinen 2017: Vagrant Revisited – Install & Boot New Virtual Machine in 31 seconds (Suosittelen koneeksi 'vagrant init debian/bullseye64')

-uuden asennus ja käynnistys nopeasti

-Vagrant ja virtualboxi

-ssh kirjautuminen

-hallinta

-tuhoaminen

#Karvinen 2023: Salt Vagrant - automatically provision one master and two slaves

-vagrantin asennus

-tehdään vagrantfile tietokoneille

-Käytetään komentoja etäkoneille

-1 master 2 slave

-tietokoneen tuhoaminen

a) Asenna Vagrant. (Toiminee parhaiten isäntäkäyttöjärjestelmässä, siis siinä, joka pyörii raudalla)
b) Yksi maankiertäjä. Asenna yksi kone Vagrantilla, ota siihen SSH-yhteys, osoita että netti toimii.
c) Oma orjansa. Asenna Salt herra ja orja samalle koneelle.
d) Asenna Saltin herra-orja arkkitehtuuri toimimaan verkon yli.
e) Aja useita idempotentteja (state.single) komentoja verkon yli.
f) Kerää teknistä tietoa orjista verkon yli (grains.item)
g) Aja shell-komento orjalla verkon yli.
h) Hello, IaC. Tee infraa koodina kirjoittamalla /srv/salt/hello/init.sls. Aja tila jollekin orjalle. Tila voi esimerkiksi tehdä esimerkkitiedoston johonkin hakemistoon. Testaa toisella komennolla, että pyytämäsi muutos on todella tehty.
