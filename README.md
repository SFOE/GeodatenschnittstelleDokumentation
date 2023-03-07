# Dokumentation Geodatenschnittstelle BFE
[![Dokumentation](https://badgen.net/badge/Dokumentation/Deutsch/red?icon=github)](https://github.com/SFOE/GeodatenschnittstelleDokumentation/blob/main/README.md)
[![Documentation Française](https://badgen.net/badge/Documentation/Française/blue?icon=github)](https://github.com/SFOE/GeodatenschnittstelleDokumentation/blob/main/README_FR.md)
[![Documentazione Italiana](https://badgen.net/badge/Documentazione/Italiana/green?icon=github)](https://github.com/SFOE/GeodatenschnittstelleDokumentation/blob/main/README_IT.md)

Das Bundesamt für Energie (BFE) betreibt die [Geodatenschnittstelle](https://uvek-gis.admin.ch/BFE/GeodataIngestAPI/). Über die Geodatenschnittstelle können dem BFE Interlis Daten über eine Benutzeroberfläche oder über eine Programmierschnittstelle übermittelt werden. Die Daten werden im BFE gespeichert und als aggregierte Geodaten publiziert. Diese Dokumentation beschreibt die verschiedenen Übermittlungsmöglichkeiten.

Die Geodatenschnittstelle bietet folgende Möglichkeiten:

* [Manueller Upload](https://github.com/SFOE/GeodatenschnittstelleDokumentation#manueller-upload)
* [Upload mit CURL](https://github.com/SFOE/GeodatenschnittstelleDokumentation#upload-mit-curl)
* [Upload mit FME](https://github.com/SFOE/GeodatenschnittstelleDokumentation#upload-mit-fme)


## Hinweise
* Die Geodatenschnittstelle ist unter folgender Adresse erreichbar: [https://uvek-gis.admin.ch/BFE/GeodataIngestAPI](https://uvek-gis.admin.ch/BFE/GeodataIngestAPI/)
* Die Geodatenschnittstelle akzeptiert nur Dateien mit der Endung «.xtf»
* Benutzername und Passwort sowie der Basic Token für die Autorisierung werden durch das BFE zur Verfügung gestellt
* Die hochgeladenen Daten werden täglich eingelesen und automatisch auf Modellkonformität geprüft
* Die Interlis Daten sollten vor dem Upload valididert werden. Die Daten können beispielsweise auf [ilicop.ch](https://ilicop.ch/) validiert werden
 

Bei Fragen oder Unklarheiten erstellen Sie einen [Issue](https://github.com/SFOE/GeodatenschnittstelleDokumentation/issues) oder schreiben Sie eine [E-Mail](mailto:geoinformation@bfe.admin.ch)

## Manueller Upload

1. Mit Benutzername und Passwort auf der Geodatenschnittstelle anmelden.
2. Datei per Drag&Drop hochladen oder durch Klick in das Fenster auswählen.
3. In der Benutzeroberfläche sind alle bereits hochgeladenen Dateien sichtbar und können bei Bedarf auch gelöscht werden.


## Upload mit CURL

Die Geodaten können mit CURL über einen Befehl in der Kommandzeile hochgeladen werden. Weitere Informationen zu CURL finden Sie [hier](https://curl.se/).
Eine Datei kann mit folgendem CURL-Befehl hochgeladen werden:
 ```
curl 
--location 
--request POST  https://uvek-gis.admin.ch/BFE/GeodataIngestAPI/api.php/file/upload 
--header "Authorization: Basic Token" 
--form file=@D:\xyz\xyz.xtf 
-x xyz.ch:8080 
-v 
-k
```

Folgende Zeilen müssen angepasst werden:
* --header: Den persönlichen Basic Token einsetzen. Zum Beispiel: *"Authorization: Basic asajdhfkshjdjkfasdfaeghwf"*
* --form: Pfad auf die hochzuladende Datei. Zum Beispiel *file=@D:\users\daten\geodaten_bfe.xtf*
* -x: Proxyeinstellungen ergänzen

Der Basic Token für die Authorisierung wird durch das BFE zur Verfügung gestellt.

## Upload mit FME
Eine Datei kann in FME mit einem «HTTPCaller» hochgeladen werden. Dazu können folgende Einstellungen verwendet werden:

![FME](https://github.com/SFOE/GeodatenschnittstelleDokumentation/blob/main/images/Geodatenschnittstelle_FME.png "Upload mit FME")

Beim Pfad auf die hochzuladende Datei muss der «MIME-Type» «application/octet-stream» augewählt werden.
Der Basic Token für die Authorisierung wird durch das BFE zur Verfügung gestellt.
Der Basic Token muss wie folgt definiert werden:

![Basic Token](https://github.com/SFOE/GeodatenschnittstelleDokumentation/blob/main/images/FME_BasicToken.png "Basic Token")

