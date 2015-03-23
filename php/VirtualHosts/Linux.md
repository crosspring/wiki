# Linux virtual host toe voegen

Korte uitleg over het instellen van virtual hosts in Linux.

## Inhoud

- [Package Manager](#packagemanager)
- [Xampp](#xampp)

Er zijn verschillende manieren om een virtual host toe te voegen op Linux. Als je zelf php hebt geinstalleerd via een linux package manager met apache2 dan is de folder structuur iets anders dan via Xampp.

### Package Manager<a name="packagemanager"></a>

Ik ga er vanuit dat je Ubuntu gebruikt of een variant daarvan. Ik weet niet zeker of je op andere Linux distributions de zelfde methode kan gebruiken, maar hoogswaarschijnlijk wel.
Om een virtual host toe te voegen aan je apache moet je de volgende command in je terminal invoeren:

```shell
sudo nano /etc/apache2/sites-available/000-default.conf
```

in dit voorbeeld gebruik ik nano maar je kan ook gedit gebruiken of andere text editors.

Als het bestand is geopent moet je de volgende paar regels toe voegen aan de onderkant van de file.

```conf
<VirtualHost *:80>
    ServerName naamvanjewebsite.dev
    ServerAlias naamvanjewebsite.dev hq.naamvanjewebsite.dev
    DocumentRoot /var/www/pad/naar/je/project
    <Directory /var/www/pad/naar/je/project>
        Options Indexes FollowSymLinks Includes ExecCGI
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>
```
Om heb bestand op te slaan moet je ```Ctrl-X``` invoeren en dan ```Enter```

Als dit is toegevoegd moet je in je hosts file de virtual host toevoegen. Met de volgende regel kan je de hosts file openen in nano

```shell
sudo nano /etc/hosts
```
In de hosts file moet je dan de volgende regel toevoegen:

```
127.0.0.1   naamvanjewebsite.dev hq.naamvanjewebsite.dev
```
Om heb bestand op te slaan moet je ```Ctrl-X``` invoeren en dan ```Enter```

Als je dit gedaan hebt moet je in de terminal de volgende command invoeren:

```
sudo service apache2 restart
```

Als je dit hebt gedaan ben je klaar en kan je de virtual host gebruiken.
In je browser kan je dan naar naamvanjewebsite.dev gaan en krijg je de site te zien.

### Xampp<a name="xampp"></a>

Om een virtual host toe te voegen aan je xampp moet je de volgende code invoeren:

```shell
sudo nano /opt/lampp/etc/extra/httpd-vhost.conf
```

in dit voorbeeld gebruik ik nano maar je kan ook gedit gebruiken of andere text editors.

Als het bestand is geopent moet je de volgende paar regels toe voegen aan de onderkant van de file.

```conf
<VirtualHost *:80>
    ServerName naamvanjewebsite.dev
    ServerAlias naamvanjewebsite.dev hq.naamvanjewebsite.dev
    DocumentRoot /opt/lampp/htdocs/pad/naar/je/project
    <Directory /opt/lampp/htdocs/pad/naar/je/project>
        Options Indexes FollowSymLinks Includes ExecCGI
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>
```
Om heb bestand op te slaan moet je ```Ctrl-X``` invoeren en dan ```Enter```

Als dit is toegevoegd moet je in je hosts file de virtual host toevoegen. Met de volgende regel kan je de hosts file openen in nano

```shell
sudo nano /etc/hosts
```
In de hosts file moet je dan de volgende regel toevoegen:

```
127.0.0.1   naamvanjewebsite.dev hq.naamvanjewebsite.dev
```
Om heb bestand op te slaan moet je ```Ctrl-X``` invoeren en dan ```Enter```

Als je dit gedaan hebt moet je in de terminal de volgende command invoeren:

```
sudo /opt/lampp/xampp restart
```

Als je dit hebt gedaan ben je klaar en kan je de virtual host gebruiken.
In je browser kan je dan naar naamvanjewebsite.dev gaan en krijg je de site te zien.
