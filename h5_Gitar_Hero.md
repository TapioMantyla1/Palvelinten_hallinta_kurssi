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
a) 
