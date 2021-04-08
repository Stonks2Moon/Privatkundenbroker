
# Anforderungen

## Must have:
* Bietet Tradingmöglichkeiten
* Bietet eine Kundenplattform
  * Kontostand
  * Depotstand
* Stellt Rechnungen an Kunden
## Nice to have:
* Auswertungen in Statistiken für Kunden
* Möglichkeit für Sparpläne

# Welche Schnittstellen konsumieren wir?

## Vom Wertpapiermarkt
* Abruf des Status (ist die "Unterbrechungsmöglichkeit" aktiviert?)
* Abrufen der verfügbaren Wertpapiere inkl. Informationen (Referenzpreis, usw.)
* Schnittstelle für Absetzen von (Verkaufs-/Kaufs-)order
* Abruf der Liste aller Order
* Abruf des Status eines Orders

# Frontend

## Technologien

Heutzutage entwickelt sich der Trend, dass Nutzer ungern Apps installieren und stattdessen eine Webseite nutzen, die ihre Wünsche erfüllt. Zusätzlich kann eine Web-App, im Vergleich zu einer nativen oder Cross-Plattform-App, ohne Probleme sowohl auf Desktop- und mobilen Endgeräten genutzt werden. Aufgrund dieser Tatsache, wird die App nach dem Mobile First Ansatz entwickelt. Der Mobile First Ansatz ist nach dem Glossar des französischen Web-Analytics Unternehmens AT Internet eine Herangehensweise, den Entwurf einer Webanwendung mit der mobilen Version zu starten und diese dann an größere Bildschirme anzupassen, um unter anderem die Benutzerfreundlichkeit von Beginn an zu verbessern. Dementsprechend wurde für die Entwicklung des Frontends auf folgende Technologien gesetzt:

### Vue.js

Vue.js ist einer der bekanntesten State-of-the-Art Lösungen für Web-Applikationen, die sichmit nachfolgenden Vorteilen für die MoonStonks-WebApp durchsetzen konnten. Zum einem ist Vue.js einfach und schnell lernbar, im Hintergrund befindet sich eine große Entwickler-Community mit ausgereiften Dokumentationen. Ein großer Vorteil sind zudem die zahlreichen Integrationsmöglichkeiten externer Komponenten.

### Quasar

Aufbauend zu Vue.js wurde auf Quasar CLI gesetzt. Quasar stellt ein Vue.js unterstützendes Frontend-Framework dar, das die Möglichkeit bietet, bspw. Single-Page-Anwendungenund Progressiv-Web-Applikationen auf einer Codebasis zu erstellen. Für den Einsatz von Quasar sprechen vor allem ein sehr effizient gestalteter Entwicklungsprozess, eine ausgereifte Dokumentation und die Vielzahl an vorgefertigten Custom-Controls, die im Vergleichzu Vue.js sofort einsetzbar sind.

Weitere Vorteile:
- Erweiterbarkeit
- Cross-Plattform

## Struktur des Codes

Grundsätzlich kann die Struktur des Codes mehrere Bereiche untergliedert werden. Im Unterordner **boot** können andere Libraries importiert werden. Dafür wird jeweile eine neue Boot-Datei angelegt, wodruch im Code auf diese dann zugefriffen werden kann. Im Unterordner **Components** werden einzelne UI-Elemente programmiert, die entweder oftmals wiederverwendet werden, oder in sich abgekapselt sein sollten. Der Unterorder **Pages** enthält alle einzelnen Webpages, die wiederum Components werden können. Der Unterorder **Layout** beihnhaltet zwei verschieden Layouts: das Login- und Mainlayout. Somit werden die jeweiligen Pages dann in das passende Layout eingebettet. Geregelt wird dies und das Routing zwischen den Pages über die **index.js** und die **routes.js** im Unterordner **Router**. Interessant sind zusätzlich die Unterordern **Store** und **I18N**. Im **Store**-Unterordner kann eine Viezahl an Datenmodellen angelegt werden, die persistent Daten innerhalb der WebApp speichern und ändern können. So bietet sich darüber an, Nutzerdaten zu speichern und bspw. die aktuellen UI-Einstellungen wie die Sprache oder der Farbmodus. Auf die Funktionsweise der Unterstützung der Mehrsprachigkeit durch den Unterordner **I18N** wird nachfolgend genauer eingegangen. 

## Aufbau der WebApp

Die Trading-App für Privatkunden ist hauptsächlich in 5 Bereiche unterteilt:
- Übersicht
- Order-Bereich
- Transaktionen
- Rechnungen
- Profil-Bereich

### Übersicht

Auf der Übersichtsseite erhält der Nutzer Einblicke über seine aktuellen Depotwerte. Dabei wird ein PieChart von eCharts angezeigt, das im Verhältnis die Verteilung der eigenen Positionen darstellt. In der Auflistung der Depotwerte wird angezeigt, wie viele Anteile im Besitz sind, was der durchschnittliche Kaufwert ist und der aktuelle Kurs. Darüber hinaus wird der aktuelle Gesamtwert und das Gewinn/Verlust-Verhältnis dargestellt.

Zusätzlich wird dem Nutzer ein Einblick in sein Verrechnungskonto gewährt. Dabei werden seine IBAN, der aktuelle Kontostand und die neusten Transaktionen angezeigt. Ebenso kann eine Auszahlung an ein angegeben Bankkonto aufgegeben werden.

Zuletzt werden im untersten Bereich die aktuell offenen Order angezeigt. Dabei wird die Information geliefert, um welche Position es sich handelt, was der Ausführungstyp ist, wie viele gekauft oder verkauft werden und wann diese Order aufgegeben wurde. Außerdem ist es möglich, eine offene Order händisch zu entfernen.

### Order-Bereich

Im Order-Bereich erhält der Nutzer eine Übersicht über die aktuell beliebtesten Aktien. Ebenso kann eine spezielle Akite gesucht werden. Angezeigt wird dabei der Name der Aktie, die ID, wie auch der aktuelle Kurs und die Kursveränderung zum Vortag. Wählt der Nutzer eine Aktie aus, so landet er auf der Orderseite, auf der angezeigt wird, ob gerade der Handel aktiv ist. Ebenso werden erneut der aktuelle Kurs wie auch die Kursveränderung zum Vortag sowol prozentual als auch absolut. Darüber hinaus wird in einem Chart der Kursverlauf dargestellt, der im Zeitraum angepasst werden kann. Des Weiteren kann eine Kaufs- oder Verkaufsorder plaziert werden. Dabei wählt der Nutzer den Order-Typ (Limit, Market, Stop Market, Stop Limit) aus und gibt die notwendigen Order-Informationen an. Im Hintergrund wird gleichzeitig jede zehn Sekunden der aktuelle Kurs abgefragt und angepasst.

### Transaktionen

Im Transaktions-Bereich wird dem Nutzer eine Übersicht aller bisherigen Transaktionen geliefert. Darunter fallen alle Aktienkäufe, Verkäufe, Einzahlungen und Auszahlungen. Dabei wird farblich hinterlegt, ob es sich um eine Minderung des Kontostandes handelt oder einer Erhöherung. Ebenso werden Abbrüche von gelöschten offenen Order angezeigt. Der Nutzer erhält immer eine Übersicht über den Wert der Transaktion, das Ausführungsdatum, beim Aktienhandel die Anzahl und bei Geldeinzahlungen und -auszahlungen das jeweilige Bankkonto.

### Rechnungen

Des Weiteren werden dem Nutzer im Rechnungs-Bereich alle Rechnungen aufgelistet. Innerhalb der Rechnung werden die Kontaktdaten dargestellt, Informationen zum Kunden und dem Depot. Es folgt eine Auflistung der Positionen inklusive der Beschreibung und dem Wert. Mit Addition der Transaktionsgebühr ergibt sich der vollständige Rechnungspreis.

### Profil-Bereich

Der Nutzer kann die Sprache der WebApp anpassen, zur Zeit Deutsch und Englisch. Ebenso kann zwischen dem Hell- und Dunkelmodus gewechselt werden. In der Profil-Übersicht werden alle Kontaktdaten und die Kundennummer aufgelistet. Dabei kann nachträglich die Adresse aktualisiert und das Passwort geändert werden.

## Features

### Mehrsprachigkeit
Da die Web-App auf die Mehrsprachigkeit ausgelegt werden soll, ist es notwendig, mehrere Sprachen zu unterstützen. Im Ordner **i18n** befindet sich eine zentrale Datei, die **index.js** die dafür zuständig ist, die jeweiligen Sprachdateien zu laden. Die dementsprechenden Sprachdateien werden in einem Unterordern innerhalb **i18n** mit einer neuen Datei **index.js** angelegt. In dieser Datei werden alle relevanten Anzeigetexte angegeben. Durch das Erstellen einer solchen Datei kann unkompliziert eine weitere Sprache hinzugefügt werden, sobald die Texte händisch übersetzt worden sind. Im Code kann somit über **$t.kuerzel** auf den Anzeigetext zugegriffen werden. Dieser passt sich der ausgewählten Sprache an.

### User Experience

Zusätzlich wurde für die beste User Experience sowohl der Hell- als auch Dunkelmodus implementiert, um den Nutzer, nach seinen Präferzen, das best mögliche User Interface zu liefern. Darüber hinaus wird ein automatisierter Login angeboten, wenn sich der Nutzer nicht vorher abgemeldet hat.

### Diagramme

Um dem Nutzer möglichst klar dazustellen, wie sein aktuelles Depotverhältnis aufgestellt ist, oder wie der Aktienkurs einer Aktie in der Vergangenheit verlaufen ist, wurden zwei Chart-Typen eingebaut. Für das Depotverhältnis viel die Wahl auf ein PieChart, einem Kreisdiagramm, da somit einfach, intuitiv und sehr übersichtlich das Verhältnis der einzelnen Positionen dargestellt wird. Zusätzlich kann bei Auswahl einer Aktie der genau Depotwert angezeigt werden.
Für den Aktienkursverlauf wird eine dargestellt.
Beide Charts stammen aus der Librarie der ECHarts. Die Wahl dafür fiel vor allem aufgrund der robusten und flexiblen Charttypen. Ein großer Punkt ist die gute Performance bei immer größer Anzahl an anzuzeigenden Daten. Des Weiteren ist positiv, dass die Charts viele Konfigurationsmöglichkeiten bieten, die auch ausgereift dokumentiert sind.

# Backend

Es wird die Module-Komponente von NestJs zum Strukturieren der Anwendung verwendet. Diese bindet die Controller und Services ein. Die API-Anfragen werden von dem Controller entgegengenommen, der die Anfrage durch ein Aufteilen auf die Services abarbeitet. Die Funktionen der Services werden weiter untergliedert in Funktionen die von außen aufgerufen und Funktionen, die nur innerhalb des Services verwendet werden. Beim Bearbeiten der Anfragen wird sehr stark darauf geachtet, gängige Sicherheitskonzepte umzusetzen, um das Risiko für nicht autorisierte Zugriffe auf ein Minimum zu reduzieren, da mit persönlichen und somit sensiblen Daten gearbeitet wird.

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
Die entworfene Struktur der Datenbank untergliedert sich in 13 Entitäten mit Eigenschaften und Abhängigkeiten untereinander. Der vollständige Entwurf des Aufbaus der Datenbank ist auf dem folgenden Diagramm abgebildet:

![ERM Diagramm](https://github.com/Stonks2Moon/Privatkundenbroker/blob/main/ERM-Diagramm.png)

## API Endpoints
Unser Backend wird über eine REST-API angesteuert. So wird gewährleistet, dass die Anwendung durch beliebige User-Interfaces angesteuert werden kann. Dadurch wird ein Einsatz unserer Anwendung in einem professionellen Umfeld ermöglicht. Die Bezeichnungen der Endpoints wurde so gewählt, dass die Aufgaben dieser selbsterklärend sind. Eine ausführlichere Dokumentation der API wird über die im Folgenden beschriebene Swagger-Dokumentation bereitgestellt.

### Auflistung aller Endpoints
Es werden die aufgelisteten API-Endpoints implementiert. Weitere Informationen zu diesen und den verwendeten Parametern können der Swagger-Dokumentation entnommen werden.
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
Um eine exzellente Dokumentation der API-Endpoints zu gewährleisten, wird eine Swagger-Dokumentation gepflegt. Diese enthält eine Auflistung aller Endpoints und hinterlegte Parameter mit Beispielwerten, die ein effizientes Testen der einzelnen Funktion erlauben. Die Swagger-Dokumentation ist unter [diesem Link](https://privat.moonstonks.space/api/) erreichbar.

## Verschlüsselung und Sicherheit
Für eine sichere, skalierbare Infrastruktur mit einer geschäftserprobten Ressourcenkontrolle und einem professionellem Netzwerkmanagement, werden Linuxcontainer (LXD), sowie eine interne Netzwerkkommunikation verwendet. Des Weiteren ist jegliche Kommunikation SSL-verschlüsselt.
Ein weiteres Sicherheitsfeature ist, dass wichtige Informationen, wie z.B. Passwörter, ausschließlich gehashed gespeichert werden. Dies gilt sowohl für die Client- als auch für die Serverseite.
Eine moderne und sichere Laufzeitumgebung wird sichergestellt, indem die Kombination aus NestJS und Typescript für das Schreiben des Codes eingesetzt werden.

## Kopplung und Kohäsion
Bei der Entwicklung der Anwendung wird darauf geachtet, dass eine klare Abgrenzung zwischen Funktionen und Aufgabenbereichen der Anwendung entsteht. So wird die Anwendung nicht nur in ein vollständig abgekapseltes Front- und Backend unterteilt, sondern auch bei der Entwicklung darauf geachtet, Funktionen sehr universell zu entwickeln.
Dies ermöglicht eine dynamische Skalierbarkeit und Erweiterbarkeit und ermöglicht einen professionellen und weiträumigen Einsatz der Anwendung. Des Weiteren wird auf eine geringe Kopplung und hohe Kohäsion geachtet, indem ähnliche Elemente möglichst nah zusammengelegt werden und verschiedene Module voneinander so unabhängig wie möglich sind.

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
