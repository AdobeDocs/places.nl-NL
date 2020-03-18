---
title: De Dienst van Plaatsen gebruiken met de Mobiele Diensten voor overseinen
description: Deze sectie toont u hoe te om de Dienst van Plaatsen met de Mobiele Diensten voor overseinen te gebruiken.
translation-type: tm+mt
source-git-commit: 5a21e734c0ef56c815389a9f08b445bedaae557a

---


# Adobe Mobile Services {#places-mobile-services}

Alvorens u de Mobiele uitbreiding van de Diensten voor overseinen kunt gebruiken, herzie de volgende eerste vereisten:

* In de Places Service zijn interessante punten gecreëerd. Zie Een [POI](/help/poi-mgmt-ui/create-a-poi-ui.md)maken voor meer informatie.

   >[!IMPORTANT]
   >
   >De dienst van Plaatsen omvat een nieuw en verbeterd POI gegevensbestand voor uw organisatie die buiten de erfenis Mobiele UI van de Diensten bestaat. POI&#39;s die zich bevinden op de navigatie op de pagina Mobiele service *Plaatsen* beheren, werken alleen voor versie 4 van de SDK.

* Hier volgt de pagina POI-beheer van locaties *beheren* in de oudere gebruikersinterface voor mobiele services voor oudere versies van de SDK:

   ![Verouderde gebruikersinterface](/help/assets/legacy-location-v4-ui.png)

* Hier volgt de gebruikersinterface van de Plaatsingsservice:

   ![Gebruikerinterface voor servicebeheer plaatsen](/help/assets/places-ui.png)

* De ACS SDK is correct geconfigureerd met de extensies Places Service en/of Places Monitor.

   Dit betekent dat gegevens beschikbaar zijn als gebeurtenissen en/of voorwaarden in de GPU-engine voor startregels voor uw mobiele app. Voor meer informatie, zie de uitbreiding [van](/help/places-ext-aep-sdks/places-extension/places-extension.md) Plaatsen of de uitbreiding [van de Monitor van](/help/places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.md)Plaatsen.

* Word vertrouwd met het maken en publiceren van de regels voor het starten van het Experience Platform voor de ACP SDK in uw mobiele app.

   Zie [Regels voor meer informatie](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine).

* De gegevenselementen van de Lancering van het Platform van de ervaring worden gecreeerd van de uitbreidingsgegevens van Plaatsen die in de motor van Regels zullen worden gebruikt.

   Zie [Gegevenselementen](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements)voor meer informatie.

## Rapportage

Voordat u rapportage kunt gebruiken, moet u aan de volgende voorwaarden voldoen:

* Verzend de servicegegevens van Plaatsen naar de rapportsuite van Adobe Analytics.

   Zie Plaatsingsservice [gebruiken met Adobe Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md)voor meer informatie.

* Word vertrouwd met het melden van de Mobiele Diensten.

   Zie [Rapporten](https://docs.adobe.com/content/help/en/mobile-services/using/reports-ug/usage.html)voor meer informatie.

## Visualisatie melden

U kunt rapporten van de Mobiele Dienst in werking stellen gebruikend de gegevens van de Dienst van Plaatsen die naar de Analytics van Adobe worden verzonden. In het volgende voorbeeld worden gebeurtenissen verzonden wanneer gebruikers items in een van de POI&#39;s hebben. In dit rapport is een filter van de POI-invoergebeurtenis toegevoegd over het uit-van-de-box gebruikersrapport:

![Visualisatie rapporteren](/help/assets/report-visualize.png)

De extra flexibiliteit in het visualiseren van de gegevens van de Dienst van Plaatsen is beschikbaar in de interfaces van de Analytics van Adobe.

