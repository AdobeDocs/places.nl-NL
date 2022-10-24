---
title: De Dienst van Plaatsen gebruiken met de Mobiele Diensten voor overseinen
description: Deze sectie toont u hoe te om de Dienst van Plaatsen met de Mobiele Diensten voor overseinen te gebruiken.
exl-id: dfa6b8bb-6bf2-44eb-8bfc-87294807ec3b
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 1%

---

# Adobe Mobile Services {#places-mobile-services}

Alvorens u de Mobiele uitbreiding van de Diensten voor overseinen kunt gebruiken, herzie de volgende eerste vereisten:

* In de Places Service zijn interessante punten gecreëerd. Zie voor meer informatie [Een POI maken](/help/poi-mgmt-ui/create-a-poi-ui.md).

   >[!IMPORTANT]
   >
   >De dienst van Plaatsen omvat een nieuw en verbeterd POI gegevensbestand voor uw organisatie die buiten de erfenis Mobiele UI van de Diensten bestaat. POI&#39;s die zich op de mobiele service bevinden *Plaatsen beheren* paginanavigatie werkt alleen voor versie 4 van de SDK.

* Hier is het *Plaatsen beheren* De pagina van het beheer van POI in erfenis Mobiele Diensten UI voor oudere versies van SDK:

   ![Verouderde gebruikersinterface](/help/assets/legacy-location-v4-ui.png)

* Hier volgt de gebruikersinterface van de Plaatsingsservice:

   ![Gebruikerinterface voor servicebeheer plaatsen](/help/assets/places-ui.png)

* De ACS SDK is correct geconfigureerd met de extensie Plaatsen.

   Dit betekent dat gegevens beschikbaar zijn als gebeurtenissen en/of omstandigheden in de engine voor regels voor Experience Platforms Launch voor uw mobiele app. Zie voor meer informatie [Extensie Plaatsen](/help/places-ext-aep-sdks/places-extension/places-extension.md).

* Word vertrouwd met het maken en publiceren van regels voor Experience Platforms Launch voor de ACS-SDK in uw mobiele app.

   Zie voor meer informatie [Regelengine](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine).

* De gegevenselementen van het Experience Platform Launch worden gecreeerd van de uitbreidingsgegevens van Plaatsen die in de motor van Regels zullen worden gebruikt.

   Zie voor meer informatie [Gegevenselementen](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements).

## Rapportage

Voordat u rapportage kunt gebruiken, moet u aan de volgende voorwaarden voldoen:

* Plaatsen van servicegegevens naar Adobe Analytics Report Suite verzenden.

   Zie voor meer informatie [Plaatsingsservice gebruiken voor Adobe Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md).

* Word vertrouwd met het melden van de Mobiele Diensten.

   Zie voor meer informatie [Rapporten](https://docs.adobe.com/content/help/en/mobile-services/using/reports-ug/usage.html).

## Visualisatie melden

U kunt rapporten van de Mobiele Dienst in werking stellen gebruikend de gegevens van de Dienst van Plaatsen die naar Adobe Analytics worden verzonden. In het volgende voorbeeld worden gebeurtenissen verzonden wanneer gebruikers items in een van de POI&#39;s hebben. In dit rapport is een filter van de POI-invoergebeurtenis toegevoegd over het uit-van-de-box gebruikersrapport:

![Visualisatie rapporteren](/help/assets/report-visualize.png)

De extra flexibiliteit in het visualiseren van de gegevens van de Dienst van Plaatsen is beschikbaar in de interfaces van Adobe Analytics.
