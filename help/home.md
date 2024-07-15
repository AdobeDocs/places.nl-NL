---
title: Places Service
description: Plaatsingsservice is een belangrijke context voor het begrijpen van de betrokkenheid van mobiele gebruikers. Met deze context kunnen ontwikkelaars van mobiele apps het toepassingsontwerp verbeteren en deze een meer persoonlijke en boeiende ervaring maken.
exl-id: 7369176f-c072-437a-9ee3-b463c5ff1d12
source-git-commit: e78e3c5ee6623d6cdf2a33c0582667a70283fdc6
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 7%

---

# Places Service {#home}

Locatie is een belangrijke context voor het begrijpen van mobiele gebruikers en voor de communicatie met deze gebruikers. Met deze context kunnen ontwikkelaars van mobiele apps het toepassingsontwerp verbeteren en deze een meer persoonlijke en boeiende ervaring maken.

De Dienst van Plaatsen, die vroeger als de Dienst van de Plaats van Adobe Experience Platform wordt bekend, is een geo-plaatsdienst die mobiele apps met plaatsbewustzijn toelaat om de plaatscontext te begrijpen door rijke en gemakkelijk-aan-gebruiksSDK interfaces te gebruiken die door een flexibele gegevensbestand van belangenpunten (POIs) worden vergezeld.

Met Plaatsingsservice kunt u het volgende bereiken:

* Maak en beheer een database van POI&#39;s die kunnen worden gebruikt met andere Adobe Experience Cloud-oplossingen.
* Koppel aangepaste metagegevens aan de POI&#39;s om deze rijker en betekenisvoller te maken door extra kenmerken op te geven.
* Visualiseer de POI&#39;s op een kaart om de ruimtelijke context gemakkelijk te begrijpen en metagegevenskenmerken toe te voegen/te bewerken.
* Configureer de SDK in Adobe Experience Platform Launch om de regels en op metagegevens gebaseerde voorwaarden te definiëren die door de locatie worden geactiveerd.
* Verminder de code die u moet schrijven om de plaats van een apparaat te controleren en gebruik de uitbreiding van Plaatsen om de plaats-specifieke regels automatisch teweeg te brengen.

Op deze manier kunt u acties uitvoeren vanuit locatiesignalen in real-time, wanneer en waar dat van belang is. De juiste context biedt een verrijkende mobiele ervaring in betrokkenheid.

Hier volgen enkele voorbeelden van manieren waarop u Plaatsen kunt gebruiken:

* Verzend een bericht in real time wanneer iemand een POI ingaat, *&quot;Hee..welkom aan het stadion.&quot;*
* Analyseer het voetverkeer van je eigen winkels tegenover je concurrenten.
* Segmenteer een publiek dat op off-line gedrag door publieksprofielen met locatiecontext te gebruiken wordt gebaseerd.
* Richt een gebruiker met een in-store ervaring wanneer relevant.

## Plaatst servicecomponenten

De Dienst van Plaatsen omvat de volgende componenten:

* **de dienst van het Web**

  U kunt POI&#39;s maken en beheren met de REST-API&#39;s van Plaatsen. Voor meer informatie over REST APIs, zie [ bibliotheken beheren ](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) en [ leiden POIs ](/help/web-service-api/api-usage/manage-pois/manage-pois.md).

* **POI de interface van het Beheer**

  U kunt POI&#39;s visualiseren op een kaart om de ruimtelijke context te begrijpen en om POI&#39;s en hun aangepaste metagegevens toe te voegen/te bewerken.

* **de uitbreiding van Plaatsen**

  De mobiele API-interface voor meerdere platforms om de locatiecontext in uw mobiele apps te integreren. Voor meer informatie over SDKs, zie {de uitbreiding van Plaatsen 0} ](/help/places-ext-aep-sdks/places-extension/places-extension.md).[

* **de regels van de Lancering**

  De geo-intelligente regels van de Lancering die u toelaten om acties met ingang en uitgangsgebeurtenissen teweeg te brengen. De regels staan u ook toe om geo-attributen in voorwaarden te gebruiken om de ervaring te personaliseren.

## Terminologie

Hier volgen enkele algemene termen die in deze documentatie worden gebruikt:

* A **punt van belang (POI)** is een geo-plaats die van belang voor uw organisatie is.

  U kunt POI&#39;s definiëren met kenmerken zoals een naam, straal, adres, categorie en metagegevenstags.

* A **geofence** is een type van POI.

  Dit type POI is een virtuele geografische grens die door breedte- en lengtecoördinaten wordt bepaald.

* A **baken** is een type van POI.

  Dit POI-type is een fysiek apparaat dat een locatie vertegenwoordigt door een grafisch Bluetooth-signaal met laag vermogen uit te zenden. De steun van Beacons komt in een toekomstige versie.

* Een **bibliotheek** is een verzameling van POI&#39;s, die worden gegroepeerd om eenvoudig regels aan een reeks POI&#39;s in plaats van aan één POI toe te voegen.

* Een **uitbreiding** is de uitbreiding van het Experience Platform Launch die wordt vereist om Plaatsen SDK in uw mobiele apps te integreren.

  De extensie die wordt gebruikt met de andere mobiele SDK&#39;s om locatiecontext aan uw ervaringen toe te voegen.

* Een **organisatie** is de Adobe-entiteit die uw bedrijf identificeert in de Adobe Experience Cloud.

  Een organisatie is doorgaans uw bedrijfsnaam. Een bedrijf kan echter meerdere organisaties hebben. De organisatiebeheerder kan groepen en gebruikers vormen en enige sign-on functionaliteit vormen.

* De **orgID** is de id die uw organisatie vertegenwoordigt op het Adobe Experience Platform.

  Voor meer informatie, zie [ Vindend uw orgID ](https://forums.adobe.com/thread/2339895).

* De **dienst van identiteitskaart van het Experience Cloud 0} {verstrekt een universele, blijvende identiteitskaart die uw bezoekers over alle oplossingen in het Experience Cloud identificeert.**

  Voor meer informatie, zie [ Overzicht ](https://experienceleague.adobe.com/docs/id-service/using/intro/overview.html).

