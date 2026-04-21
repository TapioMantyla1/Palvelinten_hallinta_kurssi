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



b) Seuraavaksi loin automatisoivan skriptin joka näyttää tältä:



c) 
Lähteet: 
Karvinen 2023, kohdat 4.12.1, 4.12.2 ja 4.12.3.1 luettu 20.4.2026: https://westminsterresearch.westminster.ac.uk/item/w7vvz/configuration-management-of-distributed-systems-over-unreliable-and-hostile-networks
The PostgreSQL Global Development Group, PostgreSQL Downloads: https://www.postgresql.org/download/linux/debian/
