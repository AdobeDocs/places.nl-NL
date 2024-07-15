---
title: Pushmeldingen
description: In deze sectie ziet u hoe u de service Plaatsen gebruikt voor pushberichten.
exl-id: c094fe9c-6148-45ba-850a-f4c520d3362c
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 2%

---

# Pushmeldingen

Met Mobile Services kunt u pushberichten naar Adobe Analytics-segmenten verzenden. In de Dienst van Plaatsen, kunt u het publiek voor uw pushbericht segmenteren door hun historische interactie met uw POIs te gebruiken. U kunt bijvoorbeeld een bericht verzenden naar gebruikers die zich de afgelopen 30 dagen in een van uw winkels hebben bevinden.

Controleer voordat u begint of u de volgende taken hebt uitgevoerd:

* Plaatsingsservicegegevens zijn door Adobe Analytics verwerkt.

  Dit betekent dat uw mobiele app met succes de gegevens van de Dienst van Plaatsen naar een Reeks van het Rapport heeft verzonden en dat de gegevens voor segmentatie beschikbaar zijn.

* Het pushmeldingskanaal in Mobile Services is ingesteld.

  Voor meer informatie, zie [ een duwbericht ](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.htmlhtml?lang=bl) creëren.

* Begrijp hoe te om een dupmelding naar een segment van Analytics in de Mobiele Diensten te verzenden.

  Voor meer informatie, zie [ een duwbericht ](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.htmlhtml?lang=bl) creëren.

## Een melding verzenden

Op het **[!UICONTROL Audience]** lusje van *creeer duw bericht* werkschema, kunt u het publiek voor dit bericht op één van de volgende manieren tot stand brengen:

* Selecteer in de vervolgkeuzelijst **[!UICONTROL Analytics Segments]** een eerder gemaakt Adobe Analytics-segment.

* In de **[!UICONTROL Custom Segment]** sectie, bouw een publiek door de beschikbare parameters van het douanesegment te gebruiken.

![ vestiging een duw bericht ](/help/assets/push-set-up.png)
