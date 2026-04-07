1. Karvinen 2026: Passwordless sudo
- Opastaa, miten käyttäjälle annetaan oikeus ajaa komentoja pääkäyttäjänä (sudo) ilman salasanan kysymistä.
- Toteutetaan lisäämällä tiedosto hakemistoon /etc/sudoers.d/.
- Syntaksi on muotoa: käyttäjänimi ALL=(ALL) NOPASSWD:ALL.
- Tärkeää on myös huolehtia tiedoston oikeuksista (esim. chmod 440).
Oma huomio: Onko turvallisempaa sallia vain tietyt komennot ilman salasanaa koko ALL-oikeuden sijasta?

2. Munroe 2006: xkcd 149 (Sandwich)
- Hyvin kuvaava sarjakuva sudon voimasta.
- Käyttäjä käskee konetta tekemään voileivän, kone kieltäytyy.
- Kun komento toistetaan "sudo"-etuliitteellä, kone suostuu ("Okei").
- Oma huomio: Tämä tiivistää sen, että Linux-järjestelmässä pääkäyttäjän oikeudet ohittavat tavalliset rajoitukset.

3. Karvinen 2026: Passwordless sudo with Ansible
- Automatisoi salasanattoman sudon konfiguroinnin usealle koneelle kerralla.
- Käyttää Ansiblen copy-moduulia luomaan oikean tiedoston /etc/sudoers.d/-hakemistoon.
- Hyödyntää validate-parametria, jotta virheellinen sudo-tiedosto ei riko järjestelmää.
- Oma huomio: Automaatio on kriittistä, sillä käsin tehty virhe sudoers-tiedostossa voi lukita ylläpitäjän ulos järjestelmästä.

4. Ansiblen sisäänrakennetut dokumentaatiot
Komento: 'ansible-doc copy'
Johdanto: Kopioi tiedostoja paikalliselta tai etäkoneelta etäkoneen sijaintiin.
optiot:
content: Tiedoston sisältö suoraan tekstinä.
dest: Kohdepolku etäkoneella, jonne tiedosto kopioidaan.
src: Lähdetiedoston polku.
owner: Tiedoston omistaja.
group: Tiedoston ryhmä.
mode: Tiedoston oikeudet.
Esimerkki:
micro
- copy:
    content: "Hei maailma"
    dest: /tmp/tervehdys.txt
Oma huomio: copy on varsin päivittäinen komento.

Komento: 'ansible-doc apt'
Johdanto: Hallitsee paketteja Debian/Ubuntu-pohjaisissa järjestelmissä apt-pakethallinnalla.
optiot:
name: Paketin tai pakettien nimet.
state: Paketin tila (present = asennettu, absent = poistettu, latest = uusin versio).
update_cache: Päivittää pakettivarastot ennen asennusta.
Esimerkki:
micro
- apt:
    name: apache2
    state: present
    update_cache: yes

Komento:'ansible-doc file'
Johdanto: Hallitsee tiedostojen ja hakemistojen.
optiot:
path: Polku käsiteltävään kohteeseen.
state: Kohteen tyyppi.
src: Lähdepolku .
recurse: Asettaa oikeudet rekursiivisesti.
owner, group, mode: Omistajuus ja oikeudet.
Esimerkki:
micro
- file:
    path: /etc/conf.d
    state: directory
    mode: '0755'

Komento: 'ansible-doc user'
Johdanto: Hallitsee käyttäjätilejä ja niiden ryhmäjäsenyyksiä.
Optiot:
name: Käyttäjätunnus.
state: Onko käyttäjä olemassa vai poistettu (present, absent).
groups: Ryhmät, joihin käyttäjä kuuluu.
shell: Käyttäjän kirjautumisshell (esim. /bin/bash).
create_home: Luodaanko kotihakemisto.
comment: Käyttäjän kuvaus (GECOS-kenttä).
system: Luodaanko järjestelmäkäyttäjä.
Esimerkki:
micro
- user:
    name: tapio
    groups: sudo,admin
    shell: /bin/bash

Komento: 'ansible-doc authorized_key'
Johdanto: Lisää tai poistaa SSH-julkisia avaimia tietyn käyttäjän authorized_keys-tiedostosta.
Optiot:
user: Käyttäjä, jonka avaimia muokataan.
key: Itse julkinen avain.
Esimerkki:
micro
- authorized_key:
    user: tapiom
    key: "{{ lookup('file', '/home/tapiom/.ssh/id_rsa.pub') }}"
Oma huomio: Tämä on turvallisin ja helpoin tapa hallita SSH-pääsyä suuriin palvelinmääriin ilman salasanoja.

Debianissa tehtävä tehtävä:
Ensiksi menin aikaisemmin luomaani hakemistoon "kotitehtävät" jossa loin micro tekstieditorin:
<img width="865" height="77" alt="image" src="https://github.com/user-attachments/assets/a4ed6244-c6d6-4b07-a66d-4e79669233b3" />

Tekstieditoriin kirjoitin seuraavasti: 
<img width="1021" height="476" alt="image" src="https://github.com/user-attachments/assets/dd6d7235-be3c-4a98-8ce5-b59df448e409" />
Eli skripti luo uuden käyttäjän "antero" ja lisää sen ryhmään "sudo" ja pitää sen jo olemassa olevilla ryhmissä.
Tämän jälkeen skripti lisää anterolle SSH-avaimen annetusta hakemistosta.

Seuraavaksi skripti asentaa salasanattoman sudon anterolle sekä asentaa tekstieditori micron sekä linuxin oman "tehtävänhallinta" ohjelman nimeltä "htop" seuraavilla komennoilla:
<img width="730" height="427" alt="image" src="https://github.com/user-attachments/assets/d7a7dc99-a8c4-4671-9229-77deb710f3f4" />

Tämän jälkeen skripti luo tiedoston orjakoneelle nimellä "tehtävä_d" sekä asentaa järjestelmään aikavyöhykkeen seuraavilla komennoilla: 
<img width="723" height="429" alt="image" src="https://github.com/user-attachments/assets/cedbb1e8-b874-4e95-8f0e-86b99f80a7ce" /> 

Tulos playbookista ensimmäisen kerran ajettuna:
<img width="1867" height="874" alt="image" src="https://github.com/user-attachments/assets/8bc1c9f2-85cb-4a2f-a912-e0a01e2d1d87" />

Lähteet:
Karvinen 2026, luettu 7.4.2026: https://terokarvinen.com/passwordless-sudo/
Karvinen 2026, luettu 7.4.2026: https://terokarvinen.com/passwordless-sudo-with-ansible/ 
Munroe 2006, luettu 7.4.2026: https://xkcd.com/149/
Panovski 2026, luettu 7.4.2026: https://linuxize.com/post/how-to-set-or-change-timezone-on-debian-13/ 

