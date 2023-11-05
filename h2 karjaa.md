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

- Loin kolme konetta t001, t002 ja debian tmasterin käyttäen Teron koodia. Sain tehtyä tämän luomalla ensin kansion omaan koneeseen c:\users\saku\vagrant\debian. Siirsin sinne luomani Vagrantfilen ja lisäsin fileen teron koodin "Ready made Vagrantfile for three computers".

  ![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/0a5b86f8-3710-49ef-8d1f-02886307bcc7)


d) Asenna Saltin herra-orja arkkitehtuuri toimimaan verkon yli.

Kirjauduin vagrant masterilla sisään käyttäen komentoa 


    $vagrant ssh tmaster
    $sudo salt-key -A
    $sudo salt '*' test.ping

- Hyväksyin avaimet sekä testasin yhteyden.

    ![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/5de8e05e-b26f-470a-a633-1864c01d3814)



e) Aja useita idempotentteja (state.single) komentoja verkon yli.

 - Alotin käyttämällä komentoja

        $ sudo salt '*' state.single file.managed '/tmp/see-you-at-terokarvinen-com'
        $ sudo salt --state-output=terse '*' state.single file.managed '/tmp/see-you-at-terokarvinen-com'
        $ sudo salt '*' state.single pkg.installed apache2
   

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/7a9ac581-361b-4068-b987-4027ca35dfab)

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/7ff20e3d-a2ce-4770-83f5-e0ade15fa60a)

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/de40d9b0-f7f5-4a60-8ea0-2c83eddeb01a)

f) Kerää teknistä tietoa orjista verkon yli (grains.item)

- käytin näitä komentoja katsomaan tietoa "orjista" verkon yli.

       $ sudo salt '*' grains.items
       $ sudo salt '*' grains.items osfinger ipv4
   

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/88b9718b-1dd6-4040-9f85-5886dbeb674a)

g) Aja shell-komento orjalla verkon yli.

- Katsoin tällä komennolla hallinnoimani koneiden ip-osoitteet. 

      $ sudo salt '*' cmd.run 'hostname -I'


![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/f0fc5c40-983b-472f-993e-3aef1a7d2304)



h) Hello, IaC. Tee infraa koodina kirjoittamalla /srv/salt/hello/init.sls. Aja tila jollekin orjalle. Tila voi esimerkiksi tehdä esimerkkitiedoston johonkin hakemistoon. Testaa toisella komennolla, että pyytämäsi muutos on todella tehty.

- Alotin tekemällä tiedoston, avasin sen ja tekstieditorilla muokkasin sitä käyttäen Teron sivustoa.

      $sudo mkdir -p /srv/salt/hello
      $sudoedit /srv/salt/hello/init.sls

 - Lisäsin tekstitiedostoon


       "/tmp/infra-as-code:
        file.managed"

  Top.sls tiedostoon lisäsin: 

    $ sudoedit /srv/salt/top.sls
    
      base:
         '*':
            - hello


-

     $ sudo salt '*' state apply
     

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/84e69857-b4cd-496b-aeef-4a2272fac739)



BYE BYE

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/8865b3a2-e454-42bd-a9b5-8f10a13b3b67)


## References

https://terokarvinen.com/2023/configuration-management-2023-autumn/

https://terokarvinen.com/2023/salt-vagrant/

https://devops.stackexchange.com/questions/653/what-is-the-definition-of-cattle-not-pets#654         
  

