---
title: POI's voor uploaden in bulk
description: Deze sectie verstrekt informatie over hoe te om uw POIs in bulk te uploaden.
exl-id: 72704bfc-5837-4439-bdb2-e77ddf935639
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '835'
ht-degree: 0%

---

# Bulkupload van POI&#39;s {#bulk-upload-pois}

De **knoop van POIs van de Invoer** in de Dienst van Plaatsen kan worden gebruikt om nieuwe POIs in bulk te uploaden gebruikend een Csv- dossier. Er is een voorbeeldspreadsheetsjabloon beschikbaar waarmee u kunt zien welke gegevenskolommen vereist zijn en hoe u optionele aangepaste metagegevens kunt toevoegen.

![ Bulk het Scherm van de Invoer ](/help/assets/Bulk-import.png)

In deze video ziet u het proces voor bulkimport en bulkbewerking:

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

[ het Bulk van de Dienst van Plaatsen Invoer en geeft POIs ](https://www.youtube.com/watch?v=75qVtirsXhg) uit

## Python API-scripts

Een reeks manuscripten Python zijn gecreeerd om de partijinvoer van POIs van een .csv dossier in een POI gegevensbestand te vereenvoudigen door de Dienst APIs van het Web te gebruiken. Deze manuscripten kunnen van deze open bron [ git repo ](https://github.com/adobe/places-scripts) worden gedownload.

Alvorens u deze manuscripten in werking stelt, om tot de Webdienst APIs toegang te hebben, zie *Vereisten voor gebruikerstoegang* in [ het overzicht van de Integratie en eerste vereisten ](/help/web-service-api/adobe-i-o-integration.md).

Hier volgt wat informatie over de scripts:

>[!TIP]
>
>Deze informatie is ook inbegrepen in een readmedossier in [ git repo ](https://github.com/adobe/places-scripts).

## CSV-bestand

Een voorbeeld-CSV-bestand `places_sample.csv` maakt deel uit van dit pakket en bevat de vereiste kopteksten en een rij voorbeeldgegevens. Deze koppen zijn allemaal kleine letters en komen overeen met de gereserveerde metagegevenstoetsen die worden gebruikt in de database Plaatsen. Kolommen die u aan het .csv- dossier toevoegt zullen aan het POI- gegevensbestand in een afzonderlijke meta-gegevenssectie voor elke POI als sleutel/waardeparen worden toegevoegd, en de kopbalwaarde wordt gebruikt als sleutel.

Hier volgt een lijst met de kolommen en de waarden die u moet gebruiken:

* `lib_id`

  Een geldige bibliotheek-id die is opgehaald uit de POI-database.

* `type`

  Point is momenteel de enige geldige waarde.

* `longitude`

  Een waarde tussen -180 en 180.

* `latitude`

  Een waarde tussen -85 en 85.

* `radius`

  Een waarde tussen 10 en 20.000.

### Kolomwaarden

De waarden van de volgende kolommen worden gebruikt in de Dienst UI van Plaatsen:

* kleur, die wordt gebruikt als de kleur van het punt dat de plaats van POI in de kaart van de Dienst van Plaatsen vertegenwoordigt.
   * De geldige waarden zijn &quot;&quot;, #3E76D0, #AA99E8, #DC2ABA, #FC685B, #FC962E, #F6C436, #BECE5D, #61B56B, en #3DC8DE, en &quot;&quot;.
   * Als de waarde leeg blijft, gebruikt de gebruikersinterface van de Dienst van Plaatsen blauw als standaardkleur.

     De waarden komen overeen met blauw (#3E76D0), paars (#AA99E8), fuschia (#DC2ABA), oranje (#FC685B), lichtoranje (#FC962E), geel (#F6C436), lichtgroen (#BECE5D), groen (#61A B56B) en lichtblauw (#3DC8DE).

* pictogram, dat als pictogram op de speld wordt gebruikt die de plaats van POI op de kaart van de Dienst van Plaatsen UI vertegenwoordigt.

   * De geldige waarden zijn &quot;&quot;, winkel, hotelbed, auto, vliegtuig, trein, schip, stadion, amusementpark, anchor, beaker, bell, bid, book, box, briefcase, browse, brush, building, calculator, camera, klok, education, flashlight, follow, game, vrouwelijk, man, gift, hammer, hart, thuis, key, launch, lichtbol, mailbox, money, pin, Promoting, ribnl. bon, shoppingCart, star, target, teapot, thumbDown, thumbUp, trap, trophy, moersleutel.

     De pictogramwaarden worden weergegeven in de volgorde waarin ze worden weergegeven in de volgende afbeelding:

     ![ pictogrammen in UI ](/help/assets/UI_icons.png)

   * Als de waarde leeg blijft, gebruikt de gebruikersinterface ster als het standaardpictogram.

* Kolommen die niet worden vermeld, kunnen leeg worden gelaten.

## Het script uitvoeren

1. De dossiers van de download van [ git repo ](https://github.com/adobe/places-scripts) aan uw lokale folder.
1. Open het `config.py` -bestand in een teksteditor en voer de volgende taken uit:

   a. Bewerk de volgende variabelewaarden als tekenreeksen:

   * `csv_file_path`

     Dit is het pad naar uw `.csv` -bestand.

   * `access_code`

     Dit is uw toegangscode die uit de vraag aan Adobe IMS werd verkregen. Voor informatie over hoe te om deze toegangscode te verkrijgen, zie *Vereisten voor gebruikerstoegang* in [ het overzicht van de Integratie en eerste vereisten ](/help/web-service-api/adobe-i-o-integration.md).

   * `org_id`

     De orgID van het Experience Cloud waarin POIs moeten worden ingevoerd. Voor informatie over hoe te om org identiteitskaart te verkrijgen, zie *Vereisten voor gebruikerstoegang* in [ het overzicht van de Integratie en eerste vereisten ](/help/web-service-api/adobe-i-o-integration.md).

   * `api_key`

     Dit is de REST API-sleutel van uw Plaatsen die is verkregen via de Adobe I/O Places Integration. Voor informatie over hoe te om de API sleutel te verkrijgen, zie *Vereisten voor gebruikerstoegang* in [ het overzicht van de Integratie en eerste vereisten ](/help/web-service-api/adobe-i-o-integration.md).

   b. Sla uw wijzigingen op.

1. Navigeer in een terminalvenster naar de map `…/places-scripts/import/` .
1. Voer `python ./places_import.py` in en druk op **[!UICONTROL enter]** (**[!UICONTROL return]**).


## CSV-controles vooraf importeren

Het script voert de volgende controles op het CSV-bestand in eerste instantie uit:

* Of een `.csv` -bestand is opgegeven.
* Of het bestandspad geldig is.
* Of de gereserveerde kopteksten van meta-gegevens inbegrepen zijn.

  De gereserveerde metagegevenskoppen zijn lib_id, name, description, type, longitude, latitude, radius, country, state, city, street, category, icon en color.

  >[!TIP]
  >
  >De kopteksten zijn allemaal kleine letters en kunnen in om het even welke orde worden vermeld.

* Controleert de waarden van de kolommen die in de CSV- dossiersectie worden gespecificeerd.

Als er fouten worden gevonden, worden de fouten afgedrukt en wordt het script afgebroken. Als geen fouten worden gevonden, probeert het manuscript om POIs in partijen van 1000 in te voeren. Als de batch is geïmporteerd, rapporteert het script de statuscode 200. Als de batch niet is geïmporteerd, worden fouten gerapporteerd.

## Eenheidstests

Eenheidstests staan in het `tests.py` -bestand, moeten vóór elke pull-aanvraag worden uitgevoerd en moeten allemaal worden doorgegeven. Aanvullende tests moeten met nieuwe code worden toegevoegd. Navigeer naar de map `…/places-scripts/import/` en voer `python ./places_import.py` in de terminal in om de tests uit te voeren.
