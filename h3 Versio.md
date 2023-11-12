
# Online

Loin uuden varaston GitHubiin. Nimesin sen "winterkuusipalaa" ja lisäsin siihen luomisvaiheessa README.md filen sekä GNU General Public license 3:sen

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/ee43c1ce-2e86-482f-967c-151977ca7ee1)


# Dolly

- Aloitin tekemällä päivitykset ja asensin Gitin

      sudo apt-get update
      sudo apt install git
      
![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/be9ada82-cf30-4771-814c-e8cf9dd43c9a)

https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent

- Tein uuden ssh-avaimen.

      ssh-keygen -t ed25519 -C saku_karppinen@hotmail.com

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/d0502b7f-20e2-4e49-886a-4e4854b0699d)


- Tämän jälkeen katsoin catti komennolla avaimen

      cat /home/sakuk/.ssh/id_ed25519.pub

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/5fc13a28-7f62-414d-81a0-6e4113f012d2)

- lisäsin avaimen gittiin

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/95b88e45-def2-4bd1-8974-f7b6ab216a1e)


- Katsoin oman osoitteeni gitistä

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/a1803919-94cf-41fd-bc8e-695c06eb7949)

      git clone git@github.com:SakuKarp/winterkuusipalaa.git // kloonaa
      cd winterkuusipalaa // siirtyy hakemistoon
      nano winter.md // tekee uuden tekstitiedoston
      git add winter.md // merkitsee muutokset 
      git commit // tallentaa paikallisesti
      git pull // noutaa muutokset
      git push // puskee ulos commitit
      
![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/a0d05528-605b-4344-a622-bd4d5f6b3df6)

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/32eabd82-cea5-4d61-955f-30c81837a8ea)

# Doh!


1. Poistin tiedoston README.md
2. tarkistin onko tiedostoa vielä tallella
3. käytin komentoa git reset --hard
4. katsoin onko tiedosto tullut takaisin

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/3929eaaf-b737-4a3b-9897-8a5e15521c05)



# Tukki

        git log --patch

![image](https://github.com/SakuKarp/Palvelinten.Hallinta/assets/148875105/3144fa77-15ee-41c1-a5d4-3220581de791)

- SHA-1-tunniste
- Käyttäjä joka teki commitin
- päivämäärä
- commitin sisältö
- lisenssi


## References
https://terokarvinen.com/2023/configuration-management-2023-autumn/
https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent
