# Git

## Inhoud's Opgave
- [Inleiding](#inleiding)
- [Installeren](#installeren)
- [Gebruik](#gebruik)
-- [Init en Add Remote](#initenaddremote)
-- [Clone](#clone)
-- [Add, Commit & Push](#addcommitpush)
-- [Checkout](#checkout)
-- [Branch](#branch)
-- [Merge](#merge)

<a name="inleiding"></a>
###Inleiding

Bij Crosspring maken we gebruik van Git. Git is een versiebeheersysteem. Omdat we vaak met meerdere personen aan een project werken kan het gebeuren dat we aan de zelfde code werken tegelijkertijd. Dat kan voor problemen zorgen. Om dit probleem op te lossen gebruiken we Git.

Git zorgt ervoor dat iedereen zijn eigen versie van het project heeft. Zo kan iedereen lokaal aan die versie werken van het project. Verschillende versies van het project heten branches. Iedereen heeft een eigen branch van het project op de lokale development omgeving.

Er is ook een 'main' branch of ook wel 'master' branch genoemd. Wij maken gebruik van [Beanstalkapp](http://beanstalkapp.com/) om deze branch bij te houden en te hosten. Elke developer haalt zijn/haar branch dan ook van de master branch af. Als een developer een stuk heeft gemaakt van het project en online wil zetten moet hij zijn branch 'mergen' met de master branch. Als dat gedaan is kunnen andere developers zijn/haar code weer gebruiken in hun eigen branch.

Een repository is een plek waar alle branches samen komen. Heel je project met alle branches die zijn aangemaakt staan in de repository.

<a name="installeren"></a>
###Installeren

Git installeren is vrij simpel, je gaat naar de [Git](http://git-scm.com/) homepagina en download daar de nieuwste versie van Git door op Download for Windows/Linux/Mac te klikken. Daarna kom je op een pagina met instructies voor het installeren van Git.

Na het installeren moeten we een paar regels eerst instellen. Open je terminal(Git Bash in Windows) en type deze paar regels.

```
git config --global user.name "Jouw naam hier"
git config --global user.email "jouwemail@hier.nl"
git config --global push.default simple
```

De eerste twee regels zijn nodig om je te identificeren bij het commiten. De laatste regel is een beveiliging bij het pushen naar een repository.

<a name="gebruik"></a>
###Gebruik

Om een lijst te zien voor alle commands die je met Git kan gebruiken kan je in je terminal ```git``` invoeren. Daar staan korte uitleg van wat alle functies doen binnen Git.

De makkelijkste manier om git te gebruiken is via de terminal(Git Bash op Windows). Ik leg daarom ook alleen maar uit hoe je het via de terminal moet gebruiken.

<a name="initenaddremote"></a>
####Init en Add Remote

Als je een nieuwe repository aan wilt maken moet je dat eerst doen op de service die je wilt gebruiken. Na het aanmaken van de repository maak je via de terminal een nieuwe map aan met de zelfde naam als de repository

```
mkdir <repository naam>
cd <repository naam>
git init
```

Door deze drie commands uit te voeren maak je een nieuwe map aan, ga je er naar toe via de terminal en initialiseer je de map met Git. Voordat je git kan gebruiken moet je een map eerst initalizeren voordat je het kan gebruiken.

Daarna kan je een file toevoegen en het pushen naar de repository die je hebt aangemaakt.

```
touch README.md
echo "# test" >> README.md
git add README.md
git commit -m "First commit"
git remote add origin <url van repository>
git push -u origin master
```

Nu heb je een nieuwe repository aangemaakt om te gebruiken. Nu kan je nieuwe files maken en toevoegen aan de repository en die committen en pushen naar de repository die je hebt gemaakt.

<a name="clone"></a>
####Clone

Om een repository te clonen die al bestaat moet je de volgende command in de terminal uitvoeren.

```
git clone <url>
```

Met deze command kan je een repository clonen van een service zoals Beanstalkapp. Het url kan je verkijgen op de website van de repository die je wilt clonen. Na het clonen is er een map aangemaakt met de zelfde naam als die van de repository. Daarna kan je in de map gaan en dingen veranderen en weer omhoog gooien als je klaar bent.

<a name="addcommitpush"></a>
####Add, Commit & Push

Als je een stuk code hebt dat je in de master branch wil zetten kan je dit doen door een paar commands in te voeren. Als eerste moet je all files toevoegen aan git die je omhoog wil gooien. Dat kan gedaan worden op verschillende manieren.

```
git add --all   # Voegt alle bestanden toe die gewijzigd zijn sinds laatste push
git add <file>  # Zo kan je 1 voor 1 een bestand toevoegen.
```

Voordat je iets omhoog kan zetten naar de repository moet je eerst een bericht meegeven. In dit bericht komen alle veranderingen te staan die je hebt gemaakt. Het bericht hoeft niet heel lang te zijn, als je maar goed kan zien wat er is verandert.

Een commit kan je maken op twee manieren.

```
git commit -m "Klein bericht"
git commit
```

Met de eerste manier kan je een klein bericht meegeven, dit is optimaal als je een kleine verandering hebt gemaakt. Met de tweede manier kan je een groter bericht maken. Als je de tweede manier gebruikt wordt er een text editor geopent en daar kan je een groot bericht in schrijven. Dit is handig als je veel hebt verandert.

Uiteindelijk kunnen we het omhoog gooien. Dit kan gedaan worden door de volgende command.

```
git push
```

Na ```git push``` te hebben ingevoerd moet je je gebruikersnaam en daarna wachtwoord invoeren. Als dit gedaan is worden je veranderingen naar de 'Origin' gestuurd.

<a name="checkout"></a>
####Checkout

Met checkout kan je van branch veranderen. Het kan zijn dat je met meerdere branches werkt. Zo kan het zijn dat je een Master branch hebt, maar ook een branch voor staging en development. Om te switchen tussen de verschillende branches kan je de volgende command gebruiken.

```
git checkout <branch naam>
```

Als je dus meerdere branches hebt kan je zo ertussen switchen. Als je op een de branch staging zit en je wilt code pushen wordt het ook gepushed naar staging en niet naar een andere branch. Een branch moet wel eerst gemaakt worden voordat je er heen kan.

<a name="branch"></a>
####Branch

Met deze command kan je een nieuwe branch aan maken.

```
git branch <branch naam>
```

Daarna kan je de ```git checkout``` command gebruiken om naar die branch te gaan. Als je een branch lokaal aanmaakt word deze niet gelijk gepushed naar de main repository. Als je een branch op je Beanstalkapp wilt hebben moet je dus na het aanmaken van je nieuwe branch eerst pushen.

Om een branch te deleten kan je de volgende command gebruiken.

```
git branch -d <branch naam>
```

<a name="merge"></a>
####Merge

Het kan zijn dat je meerdere branches met elkaar wil mergen. Om dit te doen kan je de ```git merge``` command gebruiken.
Dit doe je als volgt. Bijv ik wil de branch staging mergen met de branch master, master branch loopt achter op staging. Om dit te doen voer ik de volgende paar commands uit.

```
git checkout master
git merge staging
```

En zo simpel is het. Het kan zijn dat je merge fouten krijgt omdat je files overschrijft. Git laat zien in welke bestanden er een conflict is ontstaan. In de bestanden kan je duidelijk zien waar het probleem zit, zo kan je de conflicten oplossen door de juiste code achter te laten en de code die je niet meer nodig hebt te deleten. Als je daar mee klaar bent kan je opnieuw ```git merge staging``` doen en zouden er geen conflicten meer moeten zijn.

#EINDE!!!
