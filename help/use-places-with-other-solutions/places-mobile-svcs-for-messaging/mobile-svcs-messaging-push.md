---
title: Pushmeldingen
description: In deze sectie ziet u hoe u de service Plaatsen gebruikt voor pushberichten.
exl-id: c094fe9c-6148-45ba-850a-f4c520d3362c
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 1%

---

# Pushmeldingen

Met Mobile Services kunt u pushberichten naar Adobe Analytics-segmenten verzenden. In de Dienst van Plaatsen, kunt u het publiek voor uw pushbericht segmenteren door hun historische interactie met uw POIs te gebruiken. U kunt bijvoorbeeld een bericht verzenden naar gebruikers die zich de afgelopen 30 dagen in een van uw winkels hebben bevinden.

Controleer voordat u begint of u de volgende taken hebt uitgevoerd:

* Plaatsingsservicegegevens zijn door Adobe Analytics verwerkt.

   Dit betekent dat uw mobiele app met succes de gegevens van de Dienst van Plaatsen naar een Reeks van het Rapport heeft verzonden en dat de gegevens voor segmentatie beschikbaar zijn.

* Het pushmeldingskanaal in Mobile Services is ingesteld.

   Zie voor meer informatie [Een pushbericht maken](https://docs.adobe.com/content/help/en/mobile-services/using/manage-app-settings-ug/configuring-app/prerequisites-push-messaging.html).

* Begrijp hoe te om een dupmelding naar een segment van Analytics in de Mobiele Diensten te verzenden.

   Zie voor meer informatie [Een pushbericht maken](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/push-messages/t-create-push-message.html).

## Een melding verzenden

Op de **[!UICONTROL Audience]** tabblad van het dialoogvenster *Pushmelding maken* kunt u het publiek voor dit bericht op een van de volgende manieren maken:

* In de **[!UICONTROL Analytics Segments]** Selecteer een eerder gemaakt Adobe Analytics-segment in de vervolgkeuzelijst.

* In de **[!UICONTROL Custom Segment]** een publiek bouwen door de beschikbare parameters van het douanesegment te gebruiken.

![instellen van een pushbericht](/help/assets/push-set-up.png)
