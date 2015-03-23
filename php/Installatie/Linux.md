# Linux PHP installeren

Uitleg over het installeren van PHP op linux.

## Inhoud

- [Inleiding](#inleiding)
- [Package Manager](#packagemanager)
- [Xampp](#xampp)

### Inleiding<a name="inleiding"></a>

Je kan PHP op verschillende manieren installeren, persoonlijk vind ik xampp het makkelijkste en is ook het het snelste. Maar misschien ben jij wel één van de elite en wil jij zelf php op je systeem hebben.

Er zijn geen echte voordelen aan een php op je eigen systeem en daarom raad ik je aan om gewoon xampp te gebruiken. Xampp heeft verschillende extensions al geinstalleerd staan en hoef je dat niet meer handmatig te doen. Dit moet dus wel als je zelf je php gaat installeren.

Ik ga er vanuit dat je Ubuntu of één van de varianten van Ubuntu Linux hebt geinstalleerd. Als je dat niet hebt zullen de verschillen waarschijnlijk niet verschikkelijk groot zijn. Maar als dat wel zo is moet je zelf in je oneindige wijsheid het probleem oplossen... of aan iemand anders vragen misschien.

### Package Manager<a name="packagemanager"></a>

### Xampp<a name="xampp"></a>

Om xampp te installeren op Linux moet je naar de volgend website gaan:

[Homepage van Xampp](https://www.apachefriends.org/index.html)

Klik dan op xampp for linux en hoppa daar gaat hij downloaden. Als de download klaar is moet je je terminal openen. In je terminal ga je naar je download folder met de volgende command.

```
cd Downloads/
```

Zodra je in de download folder zit run je deze command in de terminal.

```
sudo chmod +x xampp-linux-x64-5.6.3-0-installer.run
```

De file naam klopt misschien niet precies omdat de versie van xampp misschien anders is dan die ik heb gebruikt.
Daarna run je de volgende command om de installatie van xampp te starten.

```
sudo ./xampp-linux-x64-5.6.3-0-installer.run
```

Installeer xampp door een paar keer op next te klikken. De volgende commands die ik gebruikt gaan er van uit dat je de default settings van de installatie hebt gebruikt. Dus als jij het hebt verandert kant het zijn dat de commands iets anders zijn.

Het eerste wat we moeten doen is PHP toevoegen aan je applicaties. Dit kan door de volgende command in te voeren in de terminal.

```
sudo ln -s /opt/lampp/bin/php /usr/bin/php
```

Nu heb je een symlink naar je /usr/bin folder gemaakt en kan je php gebruiken vanuit je terminal. Dit is nodig om composer te installeren als je dat ooit wil doen.
Als je nu in je terminal de volgende code invoert moet je als het goed is een response krijgen met versie nummer van php.

```
php -v

PHP 5.6.3 (cli) (built: Nov 17 2014 15:16:53)
Copyright (c) 1997-2014 The PHP Group
Zend Engine v2.6.0, Copyright (c) 1998-2014 Zend Technologies
```

Als dit werkt moet je nog één ding instellen en dat is het toelaten van de virtual hosts. Het toelaten van virtual hosts word niet gelijk door xampp ondersteund en moet je dat eerst aanzetten in de httpd.conf file. Je komt bij deze file door de volgende command in te voeren in de terminal.

```
sudo nano /opt/lampp/etc/httpd.conf
```

Als je de file hebt geopent moet je voor de volgende regel zoeken door op ```CTRL-W``` te drukken en dit in te voeren ```#Include etc/extra/httpd-vhosts.conf```. Als je het hebt gevonden kan je de # weghalven voor Include etc/extra/httpd-vhosts.conf en kan je het bestand op slaan door op ```CTRL-X``` te drukken en daarna op ```Enter```.

Nu dit klaar is moet je alleen nog je xampp te herstarten door de volgende command in de terminal in te voeren.

```
sudo /opt/lampp/xampp restart
```

Nu is de istallatie klaar van PHP. Nu kan je de installatie van composer doen en het toevoegen van virtual hosts.
