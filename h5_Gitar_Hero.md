1. Chacon and Straub 2014 (1.3 Getting Started - What is Git?):
- Git varastoi dataa ns. kuvakaappauksina ja täten ei varsinaisesti tallenna itse tiedostoja, vaan kuvia niistä. Git muuttaa kuvakaappauksia vain jos muutoksia on tehty, muuten se ei muuta niitä mitenkään.
- Gitin operaatiot toimivat pääsääntöisesti paikallisesti eikä täten tarvitse dataa muista koneista/palvelimista.
- Git käyttää mekanismia nimeltä "SHA-1", joka ennen varastoimista tarkistaa datan, mikä tekee datan korruptoitumisen ja katoamisen mahdotonta huomaamatta.

2. 'git add --all && git commit; git pull && git push'
- git add --all on komento jossa 'git add' git ottaa kuvakaappauksen tehdystä työstä ja lisää sen "staging arealle" josta se on valmiina siirtymään tallennettavaksi. ' --all' lisää kaikki työhakemistossa tehdyt muutokset mukaan.
- merkit '&&' tarkoittavat että ohjelma lukee myös sen jälkeen tulevan komennon
- 'git commit' komento tallentaa kaikki muutetut tiedostot jotka on staging areassa
- 'git pull' komento vetää muiden tekemät muutokset gitin arkistosta
- 'git push' työntää itse tekemät muutokset ulkoiselle arkistolle kuten esimekiksi githubiin ja ne ovat sen jälkeen muiden saatavilla

3. Tehtävän teko:
a) Tein Tepion-sunshine varaston GitHubiin:

<img width="1801" height="995" alt="image" src="https://github.com/user-attachments/assets/1bd735ba-fc24-4d2d-bb34-7be4742bcf14" />

b)
Loin tehtävää varten hakemiston "sunshine", tein siitä gitin ja jonka yhdistin ssh-osoitteella githubiin (tein ne jo aikaisemmin mutta en muistanut ottaa kuvakaappausta):

<img width="1592" height="466" alt="image" src="https://github.com/user-attachments/assets/cb72938c-ad45-408f-971a-95cf40b00c96" />

Seuraavaksi tein testi tiedoston ja katsoin että se tulee näkyviin githubissa:

<img width="1528" height="673" alt="image" src="https://github.com/user-attachments/assets/7871b481-69f4-41c4-adce-5d2d38bfc56e" />

tässä kuva muutetusta githubista:

<img width="1823" height="606" alt="image" src="https://github.com/user-attachments/assets/116f749b-ac7e-4038-839f-0d1d4227f5fc" />

c)
Muutin README.md tiedosta ja kirjoitin sinne tekstiä:

<img width="933" height="167" alt="image" src="https://github.com/user-attachments/assets/b6b51ca4-4bbc-4744-918b-6c7082406aa6" />

Sitten katsoin komennolla 'git status', että tein muutokset mutta ne ei ole mennyt vielä gittiin:

<img width="1422" height="553" alt="image" src="https://github.com/user-attachments/assets/68f34946-6a07-46d2-bbb7-d1bcbcb02dbc" />

Sitten ajoin komennon 'git reset --hard' ja git status:

<img width="1524" height="422" alt="image" src="https://github.com/user-attachments/assets/1b6a9bff-8026-4245-a8e4-ccdec2936bc8" />

README.md näytti sen jälkeen tältä:

<img width="951" height="119" alt="image" src="https://github.com/user-attachments/assets/b7d569e9-088f-4a70-9917-c4e339ffb703" />

d) 
Kuva lokistani:

<img width="1482" height="707" alt="image" src="https://github.com/user-attachments/assets/e0681849-9372-489f-bbee-22851c3a157a" />

Lokissa näkyy, kun yhdistin master ja main branchin yhteen (GitHub oli luonut itsestään master btanchin). Lokissa myös näkyy luomani testi tiedoston ja sen kuvauksen.

e)
Ensiksi menin ansible hakemistoon ja katsoin mitä siellä on, jonka jälkeen loin gitin:

<img width="1617" height="677" alt="image" src="https://github.com/user-attachments/assets/00cffce5-b700-43b7-a8ef-7fd4f76d6eaf" />

Sitten linkkasin hakemiston githubiin:

<img width="2116" height="84" alt="image" src="https://github.com/user-attachments/assets/3688b9a1-a536-4c70-8194-2296b04f2c6f" />

jonka jälkeen työnsin halutut tiedostot:

<img width="1247" height="420" alt="image" src="https://github.com/user-attachments/assets/5ea70831-0c41-4263-87b9-302ccb92bdbe" />

Seuraavaksi muokkasin ansible kansiosta hosts.ini tiedostoa:

<img width="941" height="281" alt="image" src="https://github.com/user-attachments/assets/cac4ece2-b3c7-43de-b6a4-ddba09eb7d07" />

jonka jälkeen ajoin sen onnistuneesti: 

<img width="1430" height="192" alt="image" src="https://github.com/user-attachments/assets/69f3250d-5fd0-4201-a7df-8f131dda8ca3" />

Tämän jälkeen committasin ja työnsin muutoksen githubiin:

<img width="1377" height="522" alt="image" src="https://github.com/user-attachments/assets/8e189d25-f172-4de8-b773-57134f73d582" />

hosts.ini näkymä githubissa:

<img width="888" height="472" alt="image" src="https://github.com/user-attachments/assets/a341652c-7fc4-4c12-93f5-7e81b30b4b89" />


- Lähteet:

Chacon and Straub 2014: https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F 
(Harisudhan.s 5.6.2025) medium: git add || git commit || git push || git clone || git branch || .git || git communication || Best Practices (luettu 27.4.2026) https://medium.com/@speaktoharisudhan/git-add-git-commit-git-push-git-clone-git-branch-git-git-communications-8fcfac467748
