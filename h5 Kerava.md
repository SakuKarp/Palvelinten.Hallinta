# x) Lue ja tiivistä. Karvinen 2018: Apache User Homepages Automatically – Salt Package-File-Service Example

- Palvelimen konffaus
- komennot "states"
- find komento
- Konffaus kotisivuille ja niiden toimiminen


# a) CSI Kerava.

Aloitin tehtävän käyttämällä teron sivuilta saatua https://terokarvinen.com/2023/configuration-management-2023-autumn/ komentoa: 

    find -printf '%T+ %p\n'

- find: Komento tiedostojen ja hakemistojen etsimiseen
- -printf '%T+ %p\n': Määrittää tulostusmuodon
- %T+: tiedoston muokkausaika
- %p: polku ja nimi
- \n: Luo uuden rivin tiedostoille jonka komento löysi.

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/491ce91b-576a-4094-87de-133c19f4cc79)


# b) Gui2fs. Muokkaa asetuksia jostain graafisen käyttöliittymän (GUI) ohjelmasta käyttäen ohjelman valikoita ja dialogeja. Etsi tämä asetus tiedostojärjestelmästä.

Aloitin miettimällä mitä ohjelmaa alan muokkaamaan. Koitin aluksi katsoa geditin asetuksia mutta en löytänyt sen conffi tiedostoa kun olin tehnyt muutokset fonttiin.

 Tämän jälkeen aloitin tutkimalla Gnotea ja löysin sieltä asetukset ja pluginit.

 ![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/3b4f62e2-5e06-41bb-9f71-ee0340df5d8e)

 Disabloin print supportin ja kävin katsomassa oliko se oikeasti mennyt pois 


aloitin etsimään .ini tiedostoa josta löydän nämä ja ne olivat 

    cd .config/gnote/addins

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/a714d950-41ff-49ee-b47e-549ea2093b05)


Siellä menin ini tiedostoon 

    nano global.ini

jossa näkyi että printNotesAddin oli = false

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/8abdc9a2-3d37-4e67-8b50-21c5e90b5131)



# c) Komennus. Tee Salt-tila, joka asentaa järjestelmään uuden komennonon


Aloitin tekemällä uuden hello-world komennon

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/088f39c2-a226-4f1d-bafc-61dfeb255d2a)


annoin sille oikeudet :

    sudo chmod +x hello-world

loin helloworld.sls tiedoston

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/f0692877-c431-4504-aaee-53fcfa7be2f6)

käytin komentoa : 

    sudo salt-call --local state.apply helloworld


![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/12deeee8-10bc-4080-90d0-02a8863ce304)















# d) Apassi. Tee Salt-tila, joka asentaa Apachen näyttämään kotihakemistoja.




# e) Ämpärillinen. Tee Salt-tila, joka asentaa järjestelmään kansiollisen komentoja.

## References

