# AAIEduHr MQTT IdP GUI
MQTT klijent napisan u programskom jeziku Python, pripremljen za AAI@EduHr zajednicu za prikaz statističkih podatka koje isporučuje MQTT sustav vezanih uz izdavatelje elektroničkih identiteta (IdP).

## Statistički podaci
Statistički podaci se isporučuju u vremenskom razmaku od jedne minute kao zbirni prikaz svih autentikacija nastalih u tom periodu. Ako ne postoji niti jedna autentikacija u periodu od jedne minute za pojedini način autentikacije, tada podaci neće biti poslani.
### RADIUS
Statistički podaci o svim RADIUS autentikacijama (eduroam, mobile data, ...) u vremenu povezanim s izdavateljem elektroničkih identiteta.
### SSO
Statistički podaci o svim autentikacijama s SSO uslugom (SAML, OIDC, CAS)  u vremenu povezanim s izdavateljem elektroničkih identiteta.

## Potrebna programska podrška
Programska podrška potrebna za rad ovog klijenta se sastoji od Python 3.x programskog jezika s pomoćnim programom `pip`, te je potrebno dodati i slijedece Python biblioteke :
```
python -m pip install git+https://github.com/eclipse/paho.mqtt.python
python -m pip install git+https://github.com/israel-dryer/ttkbootstrap
python -m pip install -U matplotlib
```
## Dohvačanje klijenta
Programska podrška klijenta se dohvača narebom `git clone git@gitlab.srce.hr:aai-eduhr/aaieduhr-mqtt-idp-gui.git` koja će napraviti odgovarajući direktorij i u njega prenjeti sve datoteke.
## Konfiguriranje
Svi potrebni podaci koje je potrebno prilagoditi unose se u datoteku config.ini (koju je potrebno kreirati kopiranjem datoteke config.ini.example).
Reci u kojima se unose konfiguracijski podaci (grupa MQTT) su slijedeci :
```
[MQTT]
BROKER = <broker_address>
PORT = 1883
CLIENT_ID = <client_ID>
UID = <user_name>
PWD = <password>
TOPIC = <topic>
```
* tekst `<broker_addres>` zamjeniti s odogovarajućim imenom MQTT brokera (npr.: `app.aaiedu.hr` )
* tekst `<client_ID>` zamjeniti s odgovarajućim nazivom MQTT klijenta (npr.: `asfdjGat123_45` )
* tekst `<user_name>` zamjeniti s odgovarajućim korisnićkim imenom dobivenim za autentikaciju na MQTT broker
* tekst `password>` zamjeniti s odgovarajućim korisnićkom lozinkom dobivenom za autentikaciju na MQTT broker
* tekst `<topic>` zamjeniti s odgovarajucim topicom dobivenim za koristenje MQTT klijenta (npr.: `aaiedu/minstat/IdP/srce.hr/#` )

Konfiguraciju je također moguce unjeti koristeci se sistemskim varijablama (environment) tako da se vrijednosti unesu postavljanjem slijedećih sistemskih varijabli : 
```
MQTT_BROKER=<broker_address>
MQTT_PORT=1883
MQTT_CLIENT_ID=<client_ID>
MQTT_UID=<user_name>
MQTT_PWD=<password>
MQTT_TOPIC=<topic>
```
## Pokretanje
Pokretanje klijenta se izvodi na način da se pozicija aktivnog direktorija postavi na direktorij u koji je programska podrška klijenta dohvačena (uobičajno naziv direktorija će biti `aaieduhr-mqtt-idp-gui`), te se u njemu izvede naredba 
```
python aaieduhr-mqtt-idp-gui
```
na Linux OS-u moguće je izvršiti slijedeći slčijed naredbi :
```
chmod 755 aaieduhr-mqtt-idp-gui
./aaieduhr-mqtt-idp-gui
```
## Kontakt
Sve informacije o programskoj podrsci moguće je dobiti na aai@srce.hr .
## Licensa
Programska podrška u ovom git projektu distribuira se po pravilima EUPL v1.2 ili vise license, a dodatni paketi nose s sobom svoje license koje su kompatibilne s EUPL v1.2 ili više, nositelj komercijalnih prava je Srce, Sveučilište u Zagrebu, Sveučilišni računski centar, autor je Dubravko Penezić, 2023, 2024.   

