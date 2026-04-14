1. Karvinen 2026, Apache installed with Ansible - quick notes
- Antaa hyvän esimerkin millaiselta voisi näyttää localhost nettisivun skriptit, niin että jokainen käyttäjä pystyy niitä muokkaamaan
- Hyödyllinen ns. "käsikirja" aloittelijalle
- Tärkeä huomio: Apache2 täytyy aina uudelleenkäynnistää kun muutetaan konfiguraatioita

2. Ansible Community Documentation, Handlers: running operations on change
- Handlersit ovat tehtäviä jotka suoritetaan vain, jos on tarve.
- Handlers tehtävät suoritetaan kun ollaan tehty muutoksia konfiguraatioihin (esimerkiksi apache2 käynnistetään uudelleen)
- Esimerkissä käytettiin avainsanaa "notify", kun avainsana löytyy, niin annettu komento ajetaan

3. 'ansible-doc service':
- johtando: Moduulia käytetään palveluiden hallintaan hallittavilla etäkoneilla. Moduuli toimii välittäjänä järjestelmän taustalla olevalle varsinaiselle palvelunhallintamoduulille. Se tekee playbookeista siirrettävimpiä eri Linux jakeluiden välillä
- enabled: Enabled kertoo sen että käynnisttykö kyseinen moduuli autoommaattisesti käynnistyksen yhteydessä vaiko ei.
- name: Kertoo hallittavan palvelun nimen
- state: määrittää palvelun tavoitetilan. 'started'/'stopped' komentoja ei ajeta ellei ole tarvetta. 'restarted' suorittaa käynnistyksen joka kertan, kun ajo annetaan. 'reloaded' suoritetaan aina kun se annetaan.
- examples:
Käynnistäminen: Yksinkertaisimmillaan vain palvelun nimi ja state: started.
Sammuttaminen: Palvelun nimi ja state: stopped.
Automaattinen käynnistys: Yhdistetään enabled: yes ja state: started, jolloin palvelu varmistetaan päälle nyt ja jatkossa.
Konfiguraation päivitys: Käytetään usein restarted-tilaa, jotta uudet asetukset tulevat voimaan.

Tehtävän teko:
a) 
<img width="1242" height="596" alt="image" src="https://github.com/user-attachments/assets/0d12de48-e857-4751-a32a-ba704e403aa3" />

Ensiksi katsoin komennolla "systemctl status apache2" että apache on käynnissä, jonka jälkeen muutin html hakemiston oikeuksia niin, että käyttäjänä minulla on täydet oikeudet (7), jonka jälkeen menin hemistoon.

<img width="773" height="222" alt="image" src="https://github.com/user-attachments/assets/0990d2af-2d1b-4da6-b663-a322ea7000e3" />

Seuraavaksi poistin jo olemassa olevan 'index.html' tiedoston ja loin uuden microlla.

<img width="583" height="127" alt="image" src="https://github.com/user-attachments/assets/850a0e9d-726e-4fe5-a56a-f6554d1525f0" />

Microon kirjoitin nuo asiat ^

<img width="671" height="247" alt="image" src="https://github.com/user-attachments/assets/63943e24-47ae-45b9-9838-30a8ca1e3025" />

Sitten katsoin että nettisivulle tulee kirjoittamani tekstit

ngnixin asennus b)

<img width="839" height="505" alt="image" src="https://github.com/user-attachments/assets/e8655d5b-6f67-4975-a694-f3fd3848d4a8" />

ensiksi latasin nginxin jonka jälkeen katsoin että onko ohjemlisto päällä mutta ei ollut

<img width="1573" height="293" alt="image" src="https://github.com/user-attachments/assets/ac78599f-3175-42cd-81de-9d0048ffb898" />

Tämä ilmeisesti johtui siitä, kun aikaisemmin käytössä ollut apache2 oli taustalla myös päällä joten sammutin sen ja käynnistin nginxin uudelleen

<img width="1156" height="199" alt="image" src="https://github.com/user-attachments/assets/efe75255-76bf-4ec7-a151-6450ecc1365d" />

<img width="540" height="158" alt="image" src="https://github.com/user-attachments/assets/25e33c25-56ad-4473-8101-aa616b28dfe6" />
<img width="677" height="313" alt="image" src="https://github.com/user-attachments/assets/b2e39f40-4443-4422-9fc3-922027d49a3e" />

Muokkasin tiedostoa "index.html" ja katsoin että näkyykö se paikallisesti

c) Automatisoidaan nginxin asennys ansiblella
Loin uuden tiedoston microlla 'micro install_nginx.yml' johon kirjoitin seuraavan skriptin:

<img width="984" height="777" alt="image" src="https://github.com/user-attachments/assets/17384395-2531-4407-92ab-6e01ef92358a" />

sitten kun yritin ajaa playbookkia niin tuli virheilmoitus: 

<img width="1564" height="988" alt="image" src="https://github.com/user-attachments/assets/84574ae0-ac3d-40d5-9af5-2332aa061df9" />

Tämän ilmeisesti johtui siitä kun skripti olettaa että apache2 on asennettuna ja kun sitä ei ollut asennettuna niin se jää erroriin, joten muutin skriptin seuraavaksi: 

<img width="963" height="746" alt="image" src="https://github.com/user-attachments/assets/b888d744-f95f-41f5-ab4e-fff4e882df9d" />

ja tässä on lopputulos:

<img width="1564" height="1129" alt="image" src="https://github.com/user-attachments/assets/33d53282-f9f6-49a6-87e2-37e5f8aa5f2b" />

Lähteet: 

Ansible Community Documentation: https://docs.ansible.com/projects/ansible/latest/playbook_guide/playbooks_handlers.html

How to Set Up an Nginx Web Server on Debian – Step-by-Step Tutorial https://www.youtube.com/watch?v=Ny99tBsuTfg

Karvinen 2026: [Apache installed with Ansible - quick notes](https://terokarvinen.com/apache-ansible/)
