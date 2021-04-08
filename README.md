
# Anforderungen

## Must have:
* Bietet Tradingmöglichkeiten
* Bietet eine Kundenplattform
  * Kontostand
  * Depotstand
* Stellt Rechnungen an Kunden
## Nice to have:
* Auswertungen in Statistiken für Kunden
* Möglichkeit für Sparpläne

# Welche Schnittstellen konsumieren wir?

## Vom Wertpapiermarkt
* Abruf des Status (ist die "Unterbrechungsmöglichkeit" aktiviert?)
* Abrufen der verfügbaren Wertpapiere inkl. Informationen (Referenzpreis, usw.)
* Schnittstelle für Absetzen von (Verkaufs-/Kaufs-)order
* Abruf der Liste aller Order
* Abruf des Status eines Orders

# Frontend

## Technologien
Heutzutage entwickelt sich der Trend, dass Nutzer ungern Apps installieren und stattdessen eine Webseite nutzen, die ihre Wünsche erfüllt. Zusätzlich kann eine Web-App, im Vergleich zu einer nativen oder Cross-Plattform-App, ohne Probleme sowohl auf Desktop- und mobilen Endgeräten genutzt werden. Dementsprechend wurde für die Entwicklung des Frontends auf folgende Technologien gesetzt:

### Vue.js
Vue.js ist eine der bekanntesten State-of-the-Art Lösungen für Web-Applikationen, die sich mit nachfolgenden Pro's für das FYB-Projekt durchsetzen konnte:

* Einfachheit
* Große Entwickler-Community
* Ausgereifte Dokumentationen
* Zukunftsorientiert
* Integrationsmöglichkeiten


### Quasar
Aufbauend zu Vue.js wurde auf Quasar gesetzt. Quasar stellt ein Vue.js unterstützendes Frontend-Framework dar. Es bietet die Möglichkeit, Single-Page-Anwendungen (SPA's), Progressiv-Web-Apps (PWA'S), etc. auf einer Codebasis zu erstellen. Für den Einsatz von Quasar sprechen vor allem nachfolgende Gründe:

* Erweiterbarkeit
* Effizient gestalteter Entwicklungs-Progress
* Sehr gute Dokumentationen
* Cross-Plattform
* Vielzahl an Custom-Controls -> Out-of-the-Box im Vergleich zu Vue.js

# Backend

Es wird die Module-Komponente von NestJs zum Strukturieren der Anwendung verwendet. Diese bindet die Controller und Services ein. Die API-Anfragen werden von dem Controller entgegengenommen, der die Anfrage durch ein Aufteilen auf die Services abarbeitet. Die Funktionen der Services werden weiter untergliedert in Funktionen die von außen aufgerufen und Funktionen, die nur innerhalb des Services verwendet werden. Beim Bearbeiten der Anfragen wird sehr stark darauf geachtet, gängige Sicherheitskonzepte umzusetzen, um das Risiko für nicht autorisierte Zugriffe auf ein Minimum zu redizieren, da mit persönlichen und somit sensiblen Daten gearbeitet wird.

Bei der Entwicklung der Service-Funktionen wird besonders darauf Wert gelegt, dass diese unabhängig von anderen Funktionen wiederverwendet werden können, indem Prinzipien wie Seperation of Concers, das Single Responsibility Principle und Don't Repeat Yourself verfolgt wurden. Dadurch können Duplikationen des Codes verhindert und die Wartbarkeit, sowie Lesbarkeit der Anwendung verbessert werden. Die Lesbarkeit wird weitergehend dadurch verbessert, dass weitere Clean Code Praktiken und Best Practices angewendet werden. So werden beispielsweise für die Bearbeitung von asynchronen Aufrufen Promises anstelle von Callbacks eingesetzt.

Weiterhin werden eigene Interfaces für den Austausch von Informationen verwendet, wodurch eine Neu-Instanziierung eines Objektes bei jeder Benutzung verhindert und so die Performance auf ein erstklassiges Niveau gehoben wird.

## Technologien

Bei der Wahl des Frameworks im Backend wurde entschieden, dass eine Lösung gewählt werden soll, die neuesten Standards entspricht und die Entwicklung von REST-APIs bestmöglich unterstützt. Die Entscheidung viel auf NestJS.

### NestJS
NestJS ist ein weit verbreitetes Node.js-Framework, das verwendet werden kann, um REST-Services zu entwickeln. Besonders positiv stechen dabei die folgenden Eigenschaften von NestJS hervor, die zu der Entscheidung, NestJS einzusetzen, geführt haben:

* Effizienz
* Skalierbarkeit
* Open Source
* Damit einhergehend auch eine große Community, die Antworten zu möglichen Fragen bietet
* Typisierung durch die Unterstützung von Typescript
* NestJS unterstützt eine Dokumentation der Endpoints mit Swagger

### MariaDB
MariaDB ist ein bekanntes Datenbankmanagementsystem für relationale Datenbanken, das als Fork der Datenbanksoftware "MySQL" entstand. Besonders die folgenden Aspekte führten zum Einsatz von MariaDB im Rahmen dieses Projekts:

* Relationale Datenbank mit gängigem Syntax
* Geschäftserprobt & große Userbase (MariaDB wird bereits im großen Umfang durch verschiedenste Firmen und Projekte verwendet)
* Open Source
* Bereits vorhandene Erfahrungen/Knowledge mit MariaDB durch Teammitglieder


## Aufbau der Datenbank
Die entworfene Struktur der Datenbank untergliedert sich in 13 Enmtitäten mit Eigenschaften und Abhängigkeiten untereinander. Der vollständige Entwurf des Aufbaus der Datenbank ist auf dem folgenden Diagramm abgebildet:

![ERM Diagramm](https://github.com/Stonks2Moon/Privatkundenbroker/blob/main/ERM-Diagramm.png)

## API Endpoints
Unser Backend wird über eine REST-API angesteuert. So wird gewährleistet, dass die Anwendung durch beliebige User-Interfaces angesteuert werden kann. So wird ein Einsatz unserer Anwendung in einem professionellen Umfeld ermöglicht. Die Bezeichnungen der Endpoints wurde so gewählt, dass die Aufgaben dieser selbsterklärend sind. Ein ausführlichere Dokumentation der API wird über die im Folgenden beschriebene Swagger-Dokumentation bereitgestellt.

### Auflistung aller Endpoints
Es werden die aufgelisteten API-Endpoints implementiert. Weitere Informationen zu diesen und den verwendeten Parametern können der Swagger-Dokumenation entnommen werden.
* /loginWithPassword (GET)
* /loginWithPasswordHash (GET)
* /registerUser (POST)
* /updateAdressDataOfUser (PUT)
* /updatePasswordOfUser (PUT)
* /getBalanceAndLastTransactionsOfVerrechnungskonto (GET)
* /initiateAuszahlung (POST)
* /createTransactionAsAdmin (POST)
* /getAllShares (GET)
* /getShare (GET)
* /getPriceOfShare (GET)
* /getPriceDevelopmentOfShare (GET)
* /getDepotValues (GET)
* /buyOrder (POST)
* /sellOrder (POST)
* /deleteOrder (DELETE)
* /getOrders (GET)
* /checkIfMarketIsOpen (GET)
* /getInvoices (GET)
* /webhook/onPlace (POST)
* /webhook/onMatch (POST)
* /webhook/onComplete (POST)
* /webhook/onDelete (POST)

### Swagger-Dokumentation
Um eine exzellente Dokumentation der API-Endpoints zu gewährleisten, wird eine Swagger-Dokumentation gepflegt. Diese enthält eine Auflistung aller Endpoints und hinterlegte Parameter mit Beispielwerten, die ein effizientes Testen der einzelnen Funktion erlauben. Die Swagger Dokumentation ist unter [diesem Link](https://privat.moonstonks.space/api/) erreichbar.

## Verschlüsselung und Sicherheit
Für eine sichere, skalierbare Infrastruktur mit einer geschäftserprobten Ressourcenkontrolle und ein professionelles Netzwerkmanagement, werden Linuxcontainer (LXD), sowie eine interne Netzwerkkommunikation verwendet. Des Weiteren ist jegliche Kommunikation SSL-verschlüsselt.
Ein weiteres Sicherheitsfeature ist, dass wichtige Informationen, wie z.B. Passwörter, ausschließlich gehashed gespeichert werden. Dies gilt sowohl für die Client- als auch für die Serverseite.
Eine moderne und sichere Laufzeitumgebung wird sichergestellt, indem die Kombination aus NestJS und Typescript für das Schreiben des Codes eingesetzt werden.

## Kopplung und Kohäsion
Bei der Entwicklung der Anwendung wird darauf geachtet, dass eine klare Abgrenzung zwischen Funktionen und Aufgabenbereichen der Anwendung entsteht. So wird die Anwendung nicht nur in ein vollständig abgekapseltes Front- und Backend unterteilt, sondern auch bei der Entwicklung darauf geachtet, Funktionen sehr universell zu entwickeln.
Dies ermöglicht eine dynamische Skalierbarkeit und Erweiterbarkeit und ermöglicht einen professionellen und weiträumigen Einsatz der Anwendung. Des Weiteren wird auf eine geringe Kopplung und hohe Kohäsion geachtet, indem ähnliche Elemente möglicht nah zusammengelegt werden und verschiedene Module voneinander so unabhängig wie möglich sind.

## Skalierbarkeit
Die Anwendung wird so konzipiert, dass sie auch bei schwankenden Rahmenbedingungen uneingeschränkt einsetzbar ist.
Bei Bedarf können zum Beispiel neue Instanzen des Front- und Backends hochgefahren und bereitgestellt werden.
So kann die Anwendung auch in der Zukunft flexibel gehostet werden. Einer großen Expansion stehts nichts im Wege.

## Konfiguration
Die Anwendung kann flexibel und einfach über eine durchdachte Konfigurationdatei konfiguriert werden. Diese bietet die Möglichkeit, Server-Einstellungen zu definieren oder auch beispielsweise die Transaktionsgebühren für Orderdurchführungen festzulegen. Durch diese Konfigurationsdatei können wichtige Parameter, bei denen davon auszugehen ist, dass sich diese in der Zukunft ändern könnten, effizient modifiziert werden. Der Aufbau der Konfiguration ist im Folgenden dargestellt:

```javascript
{
  "database": {
    "host": "",
    "port": 13306,
    "user": "",
    "password": "",
    "database": ""
  },
  "maxOrderAmount": 100,
  "MoonAuthenticationToken": "",
  "webhookAuthenticationToken": "",
  "transactionFee": 10
}
```
