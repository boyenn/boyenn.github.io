# Bol.com Acties

## Stap 1 : juiste map
De eerste stap is altijd kijken dat je in de Terminal in "node-bolcom-offers" staat.
Als je terminal lijn begint met iets vergelijkbaar als "MacBook-Pro-van-Carina:node-bolcom-offers carina$" dan kan je deze stap skippen, anders moet je cd'en tot je in de map staat.
Op de grote mac : 
```sh
cd Documents
cd node-bolcom-offers
```
Op de kleine mac :
```sh
cd Dropbox
cd node-bolcom-offers
```

## Om het PostNL bestand te genereren
* Open bolbestelnummers.csv met Excel
* Voeg rij per rij de bestelnummers in, zorg ervoor dat het zeker in de eerste kolom staat.
* Sla het bestand op met normale Command+S
* Open de terminal en voer het commando uit
```sh
node index.js --makepostnlfile --input "bolbestelnummers.csv" --output "adressen.csv"
```
* Open het nieuwe gemaakte bestand (in dit geval adressen.csv) met excel
* Kijk kort na of er niets raar is, en sla het bestand dan op met normale Command+S
* **Sluit het bestand!**
* Ga naar de website van PostNL
* Onder nieuwe zending kan je nu klikken op Zendingen importeren
* Laad het bestand adressen.csv op
* Kijk bij "Importstatus nakijken" goed na of de import gelukt is.

## Om de prijzen op bol.com aantepassen
* Open de terminal 
* Maak het bestand met het commando ( voer jaarmaanddag-nummer-bolprijsaanpassing in met de juiste datum en nummer, bijvoorbeeld 20170630-1-bolprijsaanpassing.csv) , nummer is de hoeveelste keer dat je het die dag hebt uitgevoerd.
```
node index.js --generatecsv --input "aanbod.csv" --output "jaarmaanddag-nummer-bolprijsaanpassing.csv" --minfile "minimum.csv"
```
* Wacht zeker een kwartier
* Na in kwartier ga je in Terminal en duw je op CONTROL+C, dit stopt het commando
* Open Excel **zonder een bestand te dubbelklikken**
* Open in Excel een NIEUWE werkmap (Command+N)
* Klik op het menu Gegevens vanboven (Volledig bovenaan, niet in het programma zelf!)
* Externe gegevens ophalen -> Tekstbestand importeren
* Kies het bestand dat je net genoemd hebt door jaarmaanddag-nummer-bolprijsaanpassing in te vullen.
* Eerste tab mag je skippen (Volgende)
* Selecteer Komma in de plaats van Tab en klik op volgende
* Selecteer Tekst, klik op het tweede veld (Name) en selecteer daar ook tekst
* Klik op voltooien
* Eerste veld moet =$A$1 zijn.
* Klik op OK
* **Kijk het bestand en alle prijzen even na !**
* Sla het bestand op met ** Opslaan Als ! **
* Kies "Door komma's gescheiden tekst (csv)
* Als bestandnaam kies nu jaarmaanddag-nummer-bolprijsaanpassing-AFGEWERKT ( Bijvoorbeeld : 20170630-1-bolprijsaanpassing-AFGEWERKT.csv ) 
* Open de terminal , voer dit commando uit maar vul de jaarmaanddag-nummer weer in.
```sh
node index.js --consumecsv --input "jaarmaanddag-nummer-bolprijsaanpassing-AFGEWERKT.csv"
```
* Wacht zeker een kwartier, en stop het commando dan met CTRL+C
