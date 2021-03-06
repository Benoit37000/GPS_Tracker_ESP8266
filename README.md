#### Préambule

Durant la mise au point des balises, voici un décodeur/afficheur de trames beacons bien pratique basé sur une carte TTGO T-Display ESP32 décrite ici http://www.lilygo.cn/prod_view.aspx?TypeId=50033&Id=1126&FId=t3:50033:3

<img width = "400" src="img/TTGOCapture1.png" />

https://github.com/dev-fred/Decode_balise_ESP32/tree/master/Decode_Balise_ESP32_TFT


# GPS_Tracker_ESP8266V1  

### [Code](GPS_Tracker_ESP8266V1)

Balise basé sur https://github.com/f5soh/balise_esp32 et adapté pour un ESP8266 D1 mini.

Fonctionne avec un buzzer actif optionnel et un GPS BN-180 ou un BN-220, pèse 11g.

### Librairie TinyGPS++

Télécharger la librairie zip https://github.com/mikalhart/TinyGPSPlus/releases

<img src="img/TinyGPSplus.PNG" width = "500"> 


### Carte 
Se compile avec le type de carte "Generic ESP8266 Module"

Que l'on obtient après avoir ajouté l'URL https://arduino.esp8266.com/stable/package_esp8266com_index.json dans Fichier->Préférences->URL de gestionnaire de cartes supplémentaires et installé "esp8266" dans Outils->Gestionnaire de carte

<img src="img/carte.PNG" width = "500"> 

### Câblage

<img src="img/connections_BUZ_ACTIF.PNG" width = "700">

### Face avant 

<img src="img/Balise.jpg" width = "300">

#### Code du buzzer optionnel

* tick = phase de recherche de satellites
* Beep = un satellite de +
* Beep Beep Beep = enregistrement des coordonnées de départ

#### Code de la led bleue esp8266

*  reste allumée durant la phase de recherche de satellites qui s'achève avec l'enregistrement de la position de départ quand hdop < 2.0 et nb sats > 5
*  change d'état à chaque envoi de trame toutes les 3 secondes

#### Code des leds du GPS

* TX LED BLEUE  : Clignote à chaque donnée transmise
* PPS LED ROUGE : Eteinte lorque le GPS ne reçoit pas de satellite, 1 Pulse Par Seconde si 3D fix => >= 4 satellites

![](img/Balise_led.gif)


# GPS_Tracker_ESP8266V1_WEB

### [Code](GPS_Tracker_ESP8266V1_WEB)

Ajoute un serveur WEB dans la balise qui permet de recevoir en même temps que la trame est émise, les données GPS sur son smartphone via un navigateur. Il faudra au préalabre se connecter sur l'adresse IP de ce serveur.

<img src="GPS_Tracker_ESP8266V1_WEB/img/smart.PNG" width = "300">

# GPS_Tracker_ESP8266V1_WEB_FRSKY

### [Code](GPS_Tracker_ESP8266V1_WEB_FRSKY)

<img src="GPS_Tracker_ESP8266V1_WEB_FRSKY/img/Balise-S6R.PNG" width = "300">

Battit au-dessus de GPS_Tracker_ESP8266V1_WEB, cette version ajoute une sortie FRSKY S.port sur le connecteur JR d'alimentation afin d'envoyer les données du GPS de la balise à un récepteur FRSKY via la télémétrie que l'on pourra afficher avec un script LUA.
Le gros avantage c’est la réception des infos GPS à travers la télémétrie qui passe par le couple émetteur/récepteur qui a une bien meilleure portée que le couple Balise/Smartphone ce qui permet à la balise de rendre un service de localisation assez fiable en cas de perte de l’appareil.

<img src="GPS_Tracker_ESP8266V1_WEB_FRSKY/img/Capture Balise0_censored.jpg" width = "600">

# GPS_Tracker_ESP8266V1_MAP

Projet retiré, il ne tient pas ses promesses, la portée de la balise est insuffisante.

