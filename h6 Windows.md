
x) Lue ja tiivistä

# Halonen, Rajala ja Ollikainen 2023: Installing Windows 10 on a virtual machine


- perus asennus
- Yhteydet / testuakset
- Yhteys hyökääjään ja sen testaus

# LSB Workgroup, The Linux Foundation 2015: Filesystem Hierarchy Standard

- root
- /bin sisältää erilaisia perus komentoja
- /dev sisältää eri laitetiedostoja
- /home sisältää käyttäjien kotihakemistot


# a) Asenna Windows virtuaalikoneeseen.

Asensimme tunnilla w10 virtualboxille käyttäen https://github.com/therealhalonen/PhishSticks/blob/master/notes/ollikainen/windows.md ohjeita

Kuva win10 

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/cb2d7677-0e15-42f4-b8a8-c8e4d1d28005)

# b) Asenna Salt Windowsille. Osoita 'salt-call --local' komentoa ajamalla, että asennus on onnistunut.

Asensin saltin käyttäen https://docs.saltproject.io/salt/install-guide/en/latest/topics/install-by-operating-system/windows.html ohjeita

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/507d4e81-4496-41fa-95cf-0870cab45f58)

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/af5608ff-c280-43b9-9483-ab897d6299ba)

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/2c59c1ee-d971-43a6-b448-1a41a8ab4484)

Asennuksen jälkeen käynnistin sen ja katsoin mikä versio siellä on . Versio oli 3006.4 (sulfur)

    salt-call --local --version

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/a30b91b3-9790-4d38-9b3b-a0b499359457)



# c) Kerää Windows-koneesta tietoa grains.items -toiminnolla. Poimi 'grains.item' perään muutamia keskeisiä tietoja ja analysoi ne, eli selitä perusteellisesti mitä ne ovat. Kuvaile ja vertaile numeroita.

aloitin katsomalla mitä grains.items antaa

    salt-call --local grains.items


![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/94fec7dc-3afe-4d0b-a22c-59a871d800fd)



Kuvasta näkee mikä bios versio käytössä : default system bios, prossu : 12th gen intel i5

- cwd eli tämänhetkinen hakemisto

- disks tallennuslaite eli ssd/hdd tai muut mitä käyttää tallennusasemana

- host on isäntä


# d) Kokeile Saltin file -toimintoa Windowsilla.

Loin tekstitiedoston käyttämällä komentoa :

    salt-call --local state.single file.managed C:\testi123.txt


![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/44d30c2b-be71-4d4f-8cc3-532a2908de9e)


tämän jälkeen menin C: juureen ja käytin komentoa

     dir ## Näyttää tiedostot ja kansiot nykyisessä hakemistossa

Kuvassa näkee että tekstitiedosto on tullut perille C: juureen.

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/861b4d89-baf8-4688-bf6b-868e6ab12f51)


# e) Kokeile jotain itsellesi uutta toimintoa Saltista Windowsilla. (Voit käyttää apuna edellisten vuosien kotitehtäväraporttia tai Karvinen 2018: Control Windows with Salt. Huomaa, että noissa muistiinpanoissani voi jo hieman ikä painaa, ja niissä on myös epärelevantteja kokeiluja.)

https://www.youtube.com/watch?v=gGsmeI1KKmA

Yritin saada kyseisen videon kautta saltin toimimaan linuxilla ja windowsilla samaan aikaan mutta jostain syystä en saanut sitä toimimaan mitenkään 


uusi komento jota koitin oli 

salt-call --local pkg.list_pkgs

joka näyttää asennetut paketit

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/870a19f6-68bd-4e92-a478-42f91bbf2ac9)

tutkin vielä komentoa ja löysin tämän koska ihmettelin että miksi kaikki asennetut paketit eivät näy siellä

https://github.com/saltstack/salt/issues/17948


## references

https://terokarvinen.com/2023/configuration-management-2023-autumn/
https://docs.saltproject.io/salt/install-guide/en/latest/topics/install-by-operating-system/windows.html
https://refspecs.linuxfoundation.org/FHS_3.0/fhs/index.html
https://github.com/therealhalonen/PhishSticks/blob/master/notes/ollikainen/windows.md
https://github.com/saltstack/salt/issues/17948
