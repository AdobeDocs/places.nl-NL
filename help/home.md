---
title: Plaatsingsservice
description: 'Plaatsingsservice is een belangrijke context voor het begrijpen van de betrokkenheid van mobiele gebruikers. Met deze context kunnen ontwikkelaars van mobiele apps het toepassingsontwerp verbeteren en deze een meer persoonlijke en boeiende ervaring maken. '
translation-type: tm+mt
source-git-commit: 05b4d29aa7925f7a43e70c644e3cb88045cbe446

---


# Plaatsingsservice {#home}

![&quot;Plaatsingsservice&quot;](/help/assets/places-service-header.png)

Locatie is een belangrijke context voor het begrijpen van mobiele gebruikers en voor de communicatie met deze gebruikers. Met deze context kunnen ontwikkelaars van mobiele apps het toepassingsontwerp verbeteren en deze een meer persoonlijke en boeiende ervaring maken.

De Dienst van Plaatsen, vroeger genoemd de Dienst van de Locatie van het Platform van de Ervaring van Adobe, is een geo-locatieservice die mobiele apps met plaatsbewustzijn toelaat om de plaatscontext te begrijpen door rijke en makkelijk te gebruiken interfaces SDK te gebruiken vergezeld van een flexibele gegevensbestand van interessepunten (POIs).

Met Plaatsingsservice kunt u het volgende bereiken:

* Maak en beheer een database met POI&#39;s die kunnen worden gebruikt met andere Adobe Experience Cloud-oplossingen.
* Koppel aangepaste metagegevens aan de POI&#39;s om deze rijker en betekenisvoller te maken door extra kenmerken op te geven.
* Visualiseer de POIs op een kaart om de ruimtecontext gemakkelijk te begrijpen en meta-gegevensattributen toe te voegen/uit te geven.
* Configureer de SDK in Adobe Experience Platform Launch om de op locatie geactiveerde regels en op metagegevens gebaseerde voorwaarden te definiëren.
* Verminder de code die u moet schrijven om de plaats van een apparaat te controleren en gebruik de uitbreiding van Plaatsen om de plaats-specifieke regels automatisch teweeg te brengen.

Op deze manier kunt u acties uitvoeren vanuit locatiesignalen in real-time, wanneer en waar dat van belang is. De juiste context biedt een verrijkende mobiele ervaring in betrokkenheid.

Hier volgen enkele voorbeelden van manieren waarop u Plaatsen kunt gebruiken:

* Verzend een bericht in real time wanneer iemand een POI ingaat, *&quot;Hé..welkom in het stadion.&quot;*
* Analyseer het voetverkeer van je eigen winkels tegenover je concurrenten.
* Segmenteer een publiek dat op off-line gedrag door publieksprofielen met locatiecontext te gebruiken wordt gebaseerd.
* Richt een gebruiker met een in-store ervaring wanneer relevant.

## Plaatst servicecomponenten

De Dienst van Plaatsen omvat de volgende componenten:

* **Webservice**

   U kunt POI&#39;s maken en beheren met de REST-API&#39;s van Plaatsen. Zie Bibliotheken [beheren en](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) Inkooporderbedrijven [beheren voor meer informatie over de REST API&#39;s](/help/web-service-api/api-usage/manage-pois/manage-pois.md).

* **POI-beheerinterface**

   U kunt POI&#39;s visualiseren op een kaart om de ruimtelijke context te begrijpen en om POI&#39;s en hun aangepaste metagegevens toe te voegen/te bewerken.

* **Uitbreiding Places**

   De mobiele API-interface voor meerdere platforms om de locatiecontext in uw mobiele apps te integreren. Zie De extensie [Plaatsen voor meer informatie over de SDK&#39;s](/help/places-ext-aep-sdks/places-extension/places-extension.md).

* **Opstartregels**

   De geo-intelligente regels van de Lancering die u toelaten om acties met ingang en uitgangsgebeurtenissen teweeg te brengen. De regels staan u ook toe om geo-attributen in voorwaarden te gebruiken om de ervaring te personaliseren.

* **Hiermee wordt de extensie Monitor geplaatst**

   De mobiele SDK voor meerdere platforms die in uw mobiele app kan worden ingesloten om automatisch de wijzigingen in de locatie van uw gebruiker te controleren en de regels voor Plaatsen te activeren. Voor meer informatie, zie de uitbreiding [van de Monitor van](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)Plaatsen.

## Terminologie

Hier volgen enkele algemene termen die in deze documentatie worden gebruikt:

* Een **aandachtspunt (POI)** is een geolocatie die van belang is voor uw organisatie.

   U kunt POI&#39;s definiëren met kenmerken zoals een naam, straal, adres, categorie en metagegevenstags.

* Een **geofence** is een soort POI.

   Dit type POI is een virtuele geografische grens die door breedte- en lengtecoördinaten wordt bepaald.

* Een **baken** is een soort POI.

   Dit POI-type is een fysiek apparaat dat een locatie vertegenwoordigt door een grafisch Bluetooth-signaal met laag vermogen uit te zenden. De steun van Beacons komt in een toekomstige versie.

* Een **bibliotheek** is een verzameling van POI&#39;s, die worden gegroepeerd om eenvoudig regels aan een reeks POI&#39;s in plaats van aan één POI toe te voegen.

* Een **extensie** is de Experience Platform Launch-extensie die vereist is om de Places SDK in uw mobiele apps te integreren.

   De extensie die wordt gebruikt met de andere mobiele SDK&#39;s om locatiecontext aan uw ervaringen toe te voegen.

* Een **organisatie** is de Adobe-entiteit die uw bedrijf identificeert in de Adobe Experience Cloud.

   Een organisatie is doorgaans uw bedrijfsnaam. Een bedrijf kan echter meerdere organisaties hebben. De organisatiebeheerder kan groepen en gebruikers vormen en enige sign-on functionaliteit vormen.

* De **orgID** is de id die uw organisatie vertegenwoordigt op het Adobe Experience Platform.

   Zie [Uw orgID](https://forums.adobe.com/thread/2339895)zoeken voor meer informatie.

* De **Experience Cloud ID** -service biedt een universele, permanente id die uw bezoekers identificeert voor alle oplossingen in de Experience Cloud.

   Voor meer informatie, zie [Overzicht](https://docs.adobe.com/content/help/en/id-service/using/intro/overview.html).
