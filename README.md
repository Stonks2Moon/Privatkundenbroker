# Privatkundenbroker

## Anforderungen

### Must have:
* Bietet Tradingmöglichkeiten
* Bietet eine Kundenplattform
  * Kontostand
  * Depotstand
* Stellt Rechnungen an Kunden
### Nice to have:
* Auswertungen in Statistiken für Kunden
* Möglichkeit für Sparpläne

## Welche Schnittstellen konsumieren wir?

### Vom Wertpapiermarkt
* Abruf des Status (ist die "Unterbrechungsmöglichkeit" aktiviert?)
* Abrufen der verfügbaren Wertpapiere inkl. Informationen (Referenzpreis, usw.)
* Schnittstelle für Absetzen von (Verkaufs-/Kaufs-)order
* Abruf der Liste aller Order
* Abruf des Status eines Orders

## Technologien

### Frontend
Vue.js

### Backend
Nest.JS

MariaDB als die Datenbank

#### ERM Diagramm
![ERM Diagramm](https://github.com/Stonks2Moon/Privatkundenbroker/blob/main/ERM-Diagramm.png)
