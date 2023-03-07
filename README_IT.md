# Documentazione Interfaccia geodati UFE
[![Documentation française](https://badgen.net/badge/Documentation/française/blue?icon=github)](https://github.com/SFOE/GeodatenschnittstelleDokumentation/blob/main/README_FR.md)
[![Dokumentation Deutsch](https://badgen.net/badge/Dokumentation/Deutsch/red?icon=github)](https://github.com/SFOE/GeodatenschnittstelleDokumentation/blob/main/README.md)

L'Ufficio federale dell'energia (UFE) gestisce l'[interfaccia geodati](https://uvek-gis.admin.ch/BFE/GeodataIngestAPI/?lang=it). Attraverso l'interfaccia geodati, i dati in formato Interlis possono essere trasmessi all'UFE tramite un'interfaccia utente o un'interfaccia di programmazione. I dati vengono memorizzati presso l'UFE e pubblicati come geodati aggregati. La presente documentazione descrive le varie opzioni di trasmissione.

L'interfaccia geodati offre le seguenti possibilità:

* [Caricamento manuale](https://github.com/SFOE/GeodatenschnittstelleDokumentation/blob/main/README_IT.md#caricamento-manuale)
* [Caricamento con CURL](https://github.com/SFOE/GeodatenschnittstelleDokumentation/blob/main/README_IT.md#caricare-con-curl)
* [Caricamento con FME](https://github.com/SFOE/GeodatenschnittstelleDokumentation/blob/main/README_IT.md#caricare-con-fme)


## Note
* L'interfaccia geodati è raggiungibile al seguente indirizzo: [https://uvek-gis.admin.ch/BFE/GeodataIngestAPI](https://uvek-gis.admin.ch/BFE/GeodataIngestAPI/?lang=it)
* L'interfaccia geodati accetta solo file con estensione ".xtf"
* Il nome utente e la password, nonché il token di base per l'autorizzazione, sono forniti dall'UFE.
* I dati Interlis dovrebbero venir validati prima della trasmissione all'UFE, ad esempio grazie a [ilicop.ch](https://ilicop.ch/).
* I dati caricati vengono letti quotidianamente e controllati automaticamente per verificarne la conformità al modello.
 

Per domande o incertezze, creare un [issue](https://github.com/SFOE/GeodatenschnittstelleDokumentation/issues) o scrivere un [email](mailto:geoinformation@bfe.admin.ch)

## Caricamento manuale

1. Accedere all'interfaccia geodati con il proprio nome utente e la propria password.
2. caricare il file con il drag&drop o selezionarlo facendo clic nella finestra. 
3. Tutti i file già caricati sono visibili nell'interfaccia utente e, se necessario, possono essere eliminati.


## Caricare con CURL
I geodati possono essere caricati con CURL tramite riga di comando. Ulteriori informazioni su CURL sono disponibili [qui](https://curl.se/).
Un file può essere caricato con il seguente comando CURL:
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

Le seguenti linee devono essere adattate:
* --header: Inserire il Basic Token personale. Ad esempio: *"Autorizzazione: di base asajdhfkshjdjkfasdfaeghwf "*.
* --form: Percorso del file da caricare. Ad esempio *file=@D:\users\data\geodata_bfe.xtf*
* -x: Aggiungi impostazioni proxy

Il Basic Token per l'autorizzazione è fornito dall'UFE.

## Caricare con FME
Un file può essere caricato in FME con un "HTTPCaller". A tale scopo si possono utilizzare le seguenti impostazioni:

![FME](https://github.com/SFOE/GeodatenschnittstelleDokumentation/blob/main/images/Geodatenschnittstelle_FME.png "Upload mit FME")

Per il percorso del file da caricare occorre selezionare il "MIME-Type" "application/octet-stream".
Il Basic Token per l'autorizzazione è fornito dall'UFE.
Il Basic Token deve essere definito come segue:

![Basic Token](https://github.com/SFOE/GeodatenschnittstelleDokumentation/blob/main/images/FME_BasicToken.png "Basic Token")


