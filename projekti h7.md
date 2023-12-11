## Projekti

Projektissa aion tehdä salt-staten jolla se lataa tietyt filut minioneille.

Aloitin luomalla 1 masterin ja 2 slavea teron koodia käyttäen jota käytettiin h2 osioissa.

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


Tämän jälkeen tein helloworld testin onnistuneesti

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


