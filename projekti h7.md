## Projekti

Projektissa aion tehdä salt-staten jolla se lataa tietyt filut minioneille.

Lataan koneelle Micron ja Gitin käyttämällä salttia.

Aloitin luomalla 1 masterin ja 2 slavea teron koodia käyttäen jota käytettiin h2 osioissa.

https://terokarvinen.com/2023/salt-vagrant/


    $ vagrant init debian/bullseye64
    $ vagrant up
    $ vagrant ssh tmaster
    $ ping google.comn

kirjauduin masterilla, pingasin ja tarkastin onko kone verkossa.

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/3fcb6a45-82f9-42be-a5a4-91015f863212)

Tämän jälkeen hyväksyin avaimet sekä testasin yhteyden minioneihin

    $sudo salt-key -A
    $sudo salt '*' test.ping

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/5082ceb6-ff9f-48d8-9208-76e389e038ff)


Tämän jälkeen tein hello testi init.sls 

    sudo mkdir -p /srv/salt/hello
    sudoedit /srv/salt/hello/init.sls
    sudo salt '*' state.apply hello
    
![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/c2935ad2-0796-4cae-b78f-a19338c54f4e)

Tämän jälkeen aloin tekemään omaa salt-statea. Loin kansion omastate jonne loin init.sls tiedoston


    sudo mkdir omastate
    sudoedit init.sls


![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/61c5b6b5-c4ab-4b8a-b7b3-e64b3a9e0afb)

    #/srv/salt/omastate/init.sls
    mypkgs:
    pkg.installed:
    - pkgs:
      - micro
      - git

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/50d163ee-1fda-473e-a463-c2dc6530960c)


Ylempänä kuvana testi paikallisesti koneella

        salt-call --local state.apply omastate


Sitten pistin samat minioneille 

        sudo salt '*' state.apply omastate


t001

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/e30ab070-4548-40ae-ac59-89da84c49d82)

t002

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/16b4f23e-81a1-48c3-b26b-9d8e93fa82b3)


Tämän jälkeen menin testaamaan että micro ja gitti toimii minioneilla

    exit (masterilta)
    vagrant ssh t001
    vagrant ssh t002


t001

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/c92f98b5-6c4b-4335-89eb-af9f87873375)


![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/914ddd39-e70d-4aa0-ba9e-e7a49b76f837)

t002

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/d72fbbb7-dfc9-4e97-b4df-d82f3dadfe89)


![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/b44147d7-b9f0-4da0-ad99-cc5caa08cf21)


# lopetus

Sain projektissa onnistuneesti asennettua micron ja gitin paikallisesti sekä minioneille.

## References

https://terokarvinen.com/2023/salt-vagrant/
https://github.com/SakuKarp/Palvelinten.Hallinta/blob/main/h2%20karjaa.md




