#
x) Lue ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva.)
Karvinen 2023: Create a Web Page Using Github
#
-Tehtiin oma web page githubiin
#
-harjoiteltiin githubin käyttöä
Karvinen 2023: Run Salt Command Locally
#
-Salt komentojen 
#
-salt slave-daemon asentaminen debianissa komennoilla
#
-ohjelman asentaminen, tiedoston hallinta, palvelun hallinta, käyttäjät
#
-idempotentisti eli vain kun tarvitsee muutoksia
#
a) Asenna Salt (salt-minion) koneellesi.
  Asensin salt-minionin käyttämällä teron ohjeita https://terokarvinen.com/2023/configuration-management-2023-autumn/ "Saltin asennus Debian 12"
b) Viisi tärkeintä. Näytä esimerkit viidestä tärkeimmästä Saltin tilafunktiosta: pkg, file, service, user, cmd. Analysoi ja selitä tulokset.

  pkg.installed: tein tämän teron ohjeiden mukaan ja nähtävästi se latasi "tree" ja resultiksi tuli true succeed removedilla se poistetaan.
  
  file.managed tein tämän teron ohjeiden mukaan ja se teki minulle tmp kansioon "hellosaku" tiedoston tulos oli succeed ja total runtime 5.6 ms
  
  service.running yritin tässä katsoa onko minulla päällä apache 2 ja resultiksi tuli false ja se näytti että apache2 is not available. failed 1
  
  user.present result true teki uuden käyttäjän "saku22" loi uuden groupin ja homen succeeded : 1

  cmd.run Tämä komento yritti nähtävästo suorittaa komennon touch /tmp/foo, mikä luo tiedoston /tmp/foo ja cmd.run -tila suorittaa annetun komennon. Tässäkin tuli succeeded 1.

c) Idempotentti. Anna esimerkki idempotenssista. Aja 'salt-call --local' komentoja, analysoi tulokset, selitä miten idempotenssi ilmenee.
  Se varmistaa tiedoston ja sen sisällön. Se suoritetaan ja se luo tidoston. Toisella suorituksella mitään ei tapahtunut koska se oli jo olemassa ja oikeassa tilassa.
  eli se on ominaisuus jota voi suorittaa useita kertoja peräkkäin ja output on aina sama.
  
  
d) Tietoa koneesta. Kerää tietoja koneesta Saltin grains.items -tekniikalla. Poimi kolme kiinnostavaa kohtaa, näytä tulokset ('grains.item osfinger virtual') ja analysoi ne.
  sudo salt-call --local grains.items
  os : käyttöjärjestelmä eli debian 
  osarch : arkkitehtuuri eli amd64
  virtual : onko järjestemä fyysinen tai virtuaalinen ja meillä se on VirtualBox

  ## References
  https://terokarvinen.com/2023/configuration-management-2023-autumn/
  https://terokarvinen.com/2020/command-line-basics-revisited/
  https://terokarvinen.com/2021/salt-run-command-locally/





