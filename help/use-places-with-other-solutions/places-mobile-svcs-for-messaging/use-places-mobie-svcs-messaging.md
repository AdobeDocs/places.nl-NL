---
title: De Dienst van Plaatsen gebruiken met de Mobiele Diensten voor overseinen
description: Deze sectie toont u hoe te om de Dienst van Plaatsen met de Mobiele Diensten voor overseinen te gebruiken.
exl-id: dfa6b8bb-6bf2-44eb-8bfc-87294807ec3b
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# Adobe mobiele services {#places-mobile-services}

Alvorens u de Mobiele uitbreiding van de Diensten voor overseinen kunt gebruiken, herzie de volgende eerste vereisten:

* In de Places Service zijn interessante punten gecreëerd. Voor meer informatie, zie [&#x200B; een POI &#x200B;](/help/poi-mgmt-ui/create-a-poi-ui.md) creëren.

  >[!IMPORTANT]
  >
  >De dienst van Plaatsen omvat een nieuw en verbeterd POI gegevensbestand voor uw organisatie die buiten de erfenis Mobiele UI van de Diensten bestaat. POIs die op de Mobiele Dienst *worden gevestigd leidt de paginanavigatie van Plaatsen* slechts voor versie 4 van SDK.

* Hier is *beheert Plaatsen* POI beheerspagina in de erfenis Mobiele Diensten UI voor oudere versies van SDK:

  ![&#x200B; Verouderde UI &#x200B;](/help/assets/legacy-location-v4-ui.png)

* Hier volgt de gebruikersinterface van de Plaatsingsservice:

  ![&#x200B; het beheer UI van POI van de Dienst van Plaatsen &#x200B;](/help/assets/places-ui.png)

* De ACS SDK is correct geconfigureerd met de extensie Plaatsen.

  Dit betekent dat gegevens beschikbaar zijn als gebeurtenissen en/of omstandigheden in de engine voor regels voor Experience Platforms Launch voor uw mobiele app. Voor meer informatie, zie [&#x200B; uitbreiding van Plaatsen &#x200B;](/help/places-ext-aep-sdks/places-extension/places-extension.md).

* Word vertrouwd met het maken en publiceren van regels voor Experience Platforms Launch voor de ACS-SDK in uw mobiele app.

  Voor meer informatie, zie [&#x200B; motor van Regels &#x200B;](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine).

* Experience Platform Launch gegevenselementen worden gecreeerd van de uitbreidingsgegevens van Plaatsen die in de motor van Regels zullen worden gebruikt.

  Voor meer informatie, zie [&#x200B; elementen van Gegevens &#x200B;](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements).

## Rapportage

Voordat u rapportage kunt gebruiken, moet u aan de volgende voorwaarden voldoen:

* Plaatsen van servicegegevens naar Adobe Analytics Report Suite verzenden.

  Voor meer informatie, zie [&#x200B; Dienst van Plaatsen van het Gebruik met Adobe Analytics &#x200B;](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md).

* Word vertrouwd met het melden van de Mobiele Diensten.

  Voor meer informatie, zie [&#x200B; Rapporten &#x200B;](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.htmlhtml?lang=bl).

## Visualisatie melden

U kunt rapporten van de Mobiele Dienst in werking stellen gebruikend de gegevens van de Dienst van Plaatsen die naar Adobe Analytics worden verzonden. In het volgende voorbeeld worden gebeurtenissen verzonden wanneer gebruikers items in een van de POI&#39;s hebben. In dit rapport is een filter van de POI-invoergebeurtenis toegevoegd over het uit-van-de-box gebruikersrapport:

![&#x200B; visualisatie van het Rapport &#x200B;](/help/assets/report-visualize.png)

De extra flexibiliteit in het visualiseren van de gegevens van de Dienst van Plaatsen is beschikbaar in de interfaces van Adobe Analytics.
