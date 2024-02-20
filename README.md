# AAIEduHr MQTT IdP GUI
MQTT klijent napisan u programskom jeziku Python, pripremljen za AAI@EduHr zajednicu za prikaz statističkih podatka koje isporučuje MQTT sustav vezanih uz izdavatelje elektroničkih identiteta (IdP).

## Statistički podaci
Statistički podaci se isporučuju u vremenskom razmaku od jedne minute kao zbirni prikaz svih autentikacija nastalih u tom periodu. Ako ne postoji niti jedna autentikacija u periodu od jedne minute za pojedini nacin autentikacije, tada podaci nece biti poslani.
### RADIUS
Statistički podaci o svim RADIUS autentikacijama (eduroam, mobile data, ...) u vremenu povezanim s izdavateljem elektroničkih identiteta.
### SSO
Statistički podaci o svim autentikacijama s SSO uslugom (SAML, OIDC, CAS)  u vremenu povezanim s izdavateljem elektroničkih identiteta.

## Potrebna programska podrška
Programska podrška potrebna za rad ovog klijenta se sastoji od Python 3.x programskog jezika s pomocnim programom pip, te je potrebno dodati i slijedece Python biblioteke :
```
python -m pip install git+https://github.com/eclipse/paho.mqtt.python
python -m pip install git+https://github.com/israel-dryer/ttkbootstrap
python -m pip install -U matplotlib
```
## Konfiguriranje
Svi potrebni podaci koje je potrebno prilagoditi unose se u datoteku config.ini (koju je potrebno kreirati kopiranjem datoteke config.ini.example).
Reci u kojima se unose konfiguracijski podaci su slijedeci : 
