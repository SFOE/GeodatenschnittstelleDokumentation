# Dokumentation Geodatenschnittstelle BFE
Das Bundesamt für Energie (BFE) betreibt die Geodatenschnittstelle. Über die Geodatenschnittstelle können dem BFE Geodaten über eine Benutzeroberfläche oder über eine Programmierschnittstelle übermittelt werden.

Diese Dokumentation beschreibt die verschiedenen Übermittlungsmöglichkeiten.
Die Geodatenschnittstelle bietet folgende Möglichkeiten:

* [Manueller Upload](https://s)
* [Upload mit CURL](https://s)
* [Upload mit FME](https://s)

## Manueller Upload

1. Mit Benutzername und Passwort auf der Geodatenschnittstelle anmelden
2. Datei per Drag&Drop hochladen oder durch Klick in das Fenster auswählen
3. In der Benutzeroberfläche sind alle bereits hochgeladenen Dateien sichtbar und können bei Bedarf auch gelöscht werden.

## Upload mit CURL

Eine Datei kann mit folgendem CURL-Befehl hochgeladen werden:
 ```
curl 
--location 
--request POST  http://www.energiestadtfinder.ch/bfe-ingest-api/api.php/file/upload 
--header "Authorization: Basic Token" 
--form file=@D:\xyz\xyz.xtf 
-x xyz.ch:8080 
-v 
-k
```
Der Basic Token für die Authorisierung wird durch das BFE zur Verfügung gestellt.

## Upload mit FME
Eine Datei kann in FME mit einem «HTTPCaller» hochgeladen werden. Dazu können folgende Einstellungen verwendet werden:

bild 1

Beim Pfad auf die hochzuladende Datei muss der «MIME-Type» «application/octet-stream» augewählt werden.
