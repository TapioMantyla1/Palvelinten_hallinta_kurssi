1. Karvinen 2023: Configuration Management of Distributed Systems over Unreliable and Hostile Networks (pdf, ̣mirrors: local, archive.org):
4.12.1
- Tekstissä verrataan kahta eri konfiguraatiotyökalua Salt sekä Puppet
- Salt on huomattavasti suurempi (sisältää 510 funktioita ja niiden pelkkä ohjeistus sisätlää yli 75 000 sanaa) ja antaa täten enemmän vaihtoehtoja konfiguraatiohallintaan. Luo koodia Jinja2 pohjautuen.
- Puppet on suppeampi (sisältää 113 funktiota) ja hyvin erilainen kuin perinteinen koodi kuten esimerkiksi Python, mutta käyttää virtuaalisia resursseja hyödyksi ja täten voi olla hyödyllisempi

4.12.2
- Kirjoituksessa verrataan kahta erilaista työkalua kuin aikaisemmin mainitut salt ja puppet
- Ensimmäisen työkalun (Mozilla Release Engineering Puppet) tarkastelussa todetaan että kaikista olevista komennoista vain 87% on aktiivisessa käytössä (komento 'case' sekä 'file' ovat yleisimpiä)
- Toisen työkalun (United States Government Configuration Baseline) tarkastelussa käytetyin komento on augeas minkä avulla pystyy muokkaamaan tiedostoja sen sijaan että ne korvattaisiin.

4.12.3.1
- Konfiguraatio keskittyy pää kategorioiden ympärille: Deamonin asennus, Sovellusten asennus, käyttäjienhallinta sekä tiedostojen hallinta
- Idempotenssi = ohjelma tekee muutoksia vain jos on tarve, esimerkiksi ohjelma luo uuden tiedoston jos sellaista ei löytynyt (if-komento)

2. h4 Pizza Fantasia
a) Valitsin Postgresql daemon ladattavaksi komennolla: sudo apt install postgresql, jonka jälkeen testasin että se toimii:  

<img width="1150" height="277" alt="Screenshot_16" src="https://github.com/user-attachments/assets/116916f5-a374-4eed-8c1f-c4bfb2b3231f" />

b) Seuraavaksi loin automatisoivan skriptin joka näyttää tältä:

<img width="1571" height="716" alt="uusi_skripti" src="https://github.com/user-attachments/assets/6c9c175b-a076-40e3-a85c-da60736ac005" />

ja sen ajaminen onnistui:

<img width="2212" height="988" alt="Eka_ajo" src="https://github.com/user-attachments/assets/de50e24b-29cc-4f5f-bc39-8721c64e7196" />

c) Sitten muokkasin skriptiä niin että lisäsin sinne kohteen josta muokattu tiedosto kopioidaan master-koneelta, mihin se halutaan menevän ja mitkä oikeudet sille annetaan:

<img width="1571" height="716" alt="uusi_skripti" src="https://github.com/user-attachments/assets/88eeff55-fe6a-4acf-826a-ccd77b25644e" />

d) Tässä kohdassa poistin postgresql:n konffin orja koneesta, jonka jälkeen ajoin ansiblella skriptin uudelleen ja testasin että se toimii:

<img width="2304" height="1209" alt="tehtävä4_kohtaD" src="https://github.com/user-attachments/assets/5e3b682b-6159-4f87-8fa5-c3afc0ce1d59" />

Seuraavaksi muutin postgresql.conf skriptiä niin että muutin timezonen eurooppa/finlandista UTC ja ajoin ansiblella:

<img width="2211" height="1092" alt="vika_ajo" src="https://github.com/user-attachments/assets/67d3987a-157c-4d6e-9e8f-adb133262649" />


e) Tässä näkyy että tila on idempotentti, eli ei tee mitään muutoksia ellei niitä tarvita:

<img width="2312" height="1048" alt="tehtävä4_kohtaE" src="https://github.com/user-attachments/assets/43842fd2-40cd-4e43-ad42-9ef6fa547445" />


Lähteet: 
Karvinen 2023, kohdat 4.12.1, 4.12.2 ja 4.12.3.1 luettu 20.4.2026: https://westminsterresearch.westminster.ac.uk/item/w7vvz/configuration-management-of-distributed-systems-over-unreliable-and-hostile-networks
The PostgreSQL Global Development Group, PostgreSQL Downloads: https://www.postgresql.org/download/linux/debian/
