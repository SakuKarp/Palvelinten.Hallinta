h4 Demonit
# x) Lue ja tiivistä.

Karvinen 2023: Salt Vagrant - automatically provision one master and two slaves
- Hakemiston luonti
- Tiedoston muokkaaminen
- catti komento tarkastamiseen

Salt contributors: Salt overview

- YAMLin perussäännöt jotka liittyvät salttiin
- Kolme perus elementtiä : scalars, lists, dictionaries
- Järjestely ja sisennys

Salt contributors: Salt states

- Tilojen luomiseen käytettävät moduulit sekä toiminnot
- status check
- saltin esimerkki rakenteet
- saltin tree
- top.sls tiedoston rakenteen ja sen määrittäminen kohdejoukoille


# a) Hello SLS! Tee Hei maailma -tila kirjoittamalla se tekstitiedostoon, esim /srv/salt/hello/init.sls.

Alotin tekemällä https://terokarvinen.com/2023/salt-vagrant/ ohjeiden mukaan yhden masterin ja 2 slavea. Tämän jälkeen tein 

    sudo mkdir -p /srv/salt/hello
    sudoedit /srv/salt/hello/init.sls
    sudo salt '*' state.apply hello

Lisäsin init.sls tiedostoon
/tmp/hello-world:
  file.managed

state applyllä näkyy että se loi orjille hello-world tiedoston.
    
![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/234417e1-eb8b-414c-bbd3-ef63d7f4c08d)



# b) Top. Tee top.sls niin, että tilat ajetaan automaattisesti, esim komennolla "sudo salt '*' state.apply".

Aloitin tekemällä top.sls tiedoston

    sudoedit /srv/salt/top.sls

lisäsin sinne tekstin mikä näkyy kuvassa

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/3cb4745b-3298-4672-b7e0-d9fe9ae18116)
 
    cat /srv/salt/top.sls

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/e2b84f49-64b4-4ab8-a8d0-2a5085047e8d)


    sudo salt '*' state.apply
    

# c) Apache. Asenna Apache, korvaa sen testisivu ja varmista, että demoni käynnistyy.

Aloitin lataamalla apache2 orjalle:

    sudo salt 't001' state.single pkg.installed apache2
    sudo salt 't001' state.single pkg.removed apache2

Tämän jälkeen poistin sen onnistuneesti 

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/75b22444-a100-43a4-a479-6f94c3d643ff)


Tämän jälkeen testasin käyttäen teron ohjeita tekemällä sls tiedoston ja sen vaihtamaan kotisivut.

https://terokarvinen.com/2018/apache-user-homepages-automatically-salt-package-file-service-example/

Aluksi loin sls tiedoston ja index tiedoston. Tämän jälkeen ajoin masterilta

    sudo salt '*' state.apply apache
    

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/ca77aed6-db1d-4ed3-a942-de7093d8d728)

t002

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/cf222f47-eb85-4c36-b01a-ea515b90db96)


![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/a715f7be-d661-436b-9526-2c3bba42d954)

t001

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/0016a4b4-da05-4683-ace2-81df6519b1bb)


![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/81edec92-4164-4f2d-a25f-28511fe9fbb4)

kuva sls tiedostosta

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/ef147b29-d5d4-458e-b77b-908564a8f52a)

kuva index

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/e471fd30-c3a4-4ed5-a458-cc2f474c6456)





# d) SSHouto. Lisää uusi portti, jossa SSHd kuuntelee.

aloitin luomalla 2 eri tiedostoa (sls ja config) joihin lisäsin teron sivuilta conffaukset 

https://terokarvinen.com/2018/04/03/pkg-file-service-control-daemons-with-salt-change-ssh-server-port/?fromSearch=karvinen%20salt%20ssh


    sudo nano /srv/salt/sshd.sls
    sudo nano /srv/salt/sshd_config

Tämän jälkeen käytin

    sudo salt '*' state.apply sshd

jonka jälkeen paketti oli asennettu oikein

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/5bc14e07-6fbc-4540-9448-c6f5b09c073e)

katsoin että portti on oikea 

    nc -vz 192.168.12.100 8888


ja yhteys on succeeded

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/e7cf6587-df87-4b62-b055-5d1d2135c7c6)


## References
https://terokarvinen.com/2018/04/03/pkg-file-service-control-daemons-with-salt-change-ssh-server-port/?fromSearch=karvinen%20salt%20ssh

https://terokarvinen.com/2023/salt-vagrant/#infra-as-code---your-wishes-as-a-text-file

https://terokarvinen.com/2023/salt-vagrant/

https://terokarvinen.com/2023/configuration-management-2023-autumn/

https://terokarvinen.com/2018/apache-user-homepages-automatically-salt-package-file-service-example/

https://docs.saltproject.io/salt/user-guide/en/latest/topics/states.html#state-modules
