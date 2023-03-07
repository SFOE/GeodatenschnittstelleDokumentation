# Documentation interface de géodonnées OFEN
[![Documentazione](https://badgen.net/badge/Documentazione/italiana/green?icon=github)](https://github.com/SFOE/GeodatenschnittstelleDokumentation/blob/main/README_IT.md)
[![Dokumentation](https://badgen.net/badge/Dokumentation/Deutsch/red?icon=github)](https://github.com/SFOE/GeodatenschnittstelleDokumentation/blob/main/README.md)

L'Office fédéral de l'énergie (OFEN) exploite l'[interface de données géographiques](https://uvek-gis.admin.ch/BFE/GeodataIngestAPI/?lang=fr). L'interface de géodonnées permet de transmettre des données Interlis à l'OFEN par le moyen d'une interface utilisateur ou d'une interface de programmation. Les données sont enregistrées à l'OFEN et publiées sous forme de géodonnées agrégées. Cette documentation décrit les différentes possibilités de transmission.

L'interface de géodonnées offre les possibilités suivantes :

* [Upload manuel](https://github.com/SFOE/GeodatenschnittstelleDokumentation/blob/main/README_FR.md#upload-manuel)
* [Upload avec CURL](https://github.com/SFOE/GeodatenschnittstelleDokumentation/blob/main/README_FR.md#upload-avec-curl)
* [Upload avec FME](https://github.com/SFOE/GeodatenschnittstelleDokumentation/blob/main/README_FR.md#upload-avec-fme)


## Remarques
* L'interface de géodonnées est accessible à l'adresse suivante : [https://uvek-gis.admin.ch/BFE/GeodataIngestAPI](https://uvek-gis.admin.ch/BFE/GeodataIngestAPI/?lang=fr)
* L'interface de géodonnées n'accepte que les fichiers avec l'extension ".xtf"
* Le nom d'utilisateur et le mot de passe ainsi que le Basic Token pour l'autorisation sont mis à disposition par l'OFEN.
* Les données Interlis devraient être validées sur [ilicop.ch](https://ilicop.ch/) avant le téléchargement.
* Les données téléchargées sont lues quotidiennement et leur conformité au modèle est automatiquement vérifiée.
 
Si vous avez des questions ou des problèmes, créez un [Issue](https://github.com/SFOE/GeodatenschnittstelleDokumentation/issues) ou envoyez un [E-mail](mailto:geoinformation@bfe.admin.ch)

## Upload manuel

1. se connecter à l'interface de géodonnées avec le nom d'utilisateur et le mot de passe.
2. charger le fichier par glisser-déposer ou le sélectionner en cliquant dans la fenêtre.
3. dans l'interface utilisateur, tous les fichiers déjà téléchargés sont visibles et peuvent être supprimés si nécessaire.


## Upload avec CURL

Les géodonnées peuvent être chargées avec CURL via une commande dans la ligne de commande. Vous trouverez plus d'informations sur CURL [ici](https://curl.se/).
Un fichier peut être téléchargé à l'aide de la commande CURL suivante :
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

Les lignes suivantes doivent être adaptées :
* --header : Insérer le Basic Token personnel. Par exemple: : *"Authorization : Basic asajdhfkshjdjkfasdfaeghwf "*.
* --form : Chemin vers le fichier à télécharger. Par exemple *file=@D:\users\daten\geodaten_bfe.xtf*
* -x : compléter les paramètres du proxy

Le Basic Token pour l'autorisation est mis à disposition par l'OFEN.

## Upload avec FME
Un fichier peut être chargé dans FME avec un "HTTPCaller". Les paramètres suivants peuvent être utilisés à cet effet :

![FME](https://github.com/SFOE/GeodatenschnittstelleDokumentation/blob/main/images/Geodatenschnittstelle_FME.png "Upload avec FME")

Pour le chemin d'accès au fichier à charger, il faut sélectionner le "MIME-Type" "application/octet-stream".
Le Basic Token pour l'autorisation est mis à disposition par l'OFEN.
Le Basic Token doit être défini comme suit :

![Basic Token](https://github.com/SFOE/GeodatenschnittstelleDokumentation/blob/main/images/FME_BasicToken.png "Basic Token")


