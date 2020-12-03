---
title: Pushmeldingen met Places Service
description: In deze sectie vindt u informatie over het gebruik van de Places Service met pushberichten in Campaign Standard.
translation-type: tm+mt
source-git-commit: fd469358845e14c47a58b40bb18c9144828a8996
workflow-type: tm+mt
source-wordcount: '911'
ht-degree: 3%

---


# Push Notifications with Places Service {#push-notifications}

In deze sectie leert u hoe u historische geo-locatiegegevens kunt gebruiken om pushberichten te activeren die via Adobe Campaign Standard worden geleverd.

## Vereisten

Voer de volgende taken uit voordat u begint:

* Een mobiele toepassing hebben geconfigureerd met de Adobe Experience Platform Mobile SDK, inclusief de [Adobe Campaign Standard-extensie](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard).

* Integreer de [Adobe Experience Platform Mobile SDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) in uw app.
* Voeg de extensie [Adobe Campaign Standard](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) toe aan de configuratie van uw mobiele app.

* [Creeer POI](/help/poi-mgmt-ui/create-a-poi-ui.md) in de het beheersinterface van POI van de Dienst van Plaatsen.

* Schakel de extensie [Plaatsen in en installeer deze](/help/places-ext-aep-sdks/places-extension/places-extension.md).


## Gegevenselementen maken in Experience Platform Launch

Nadat u hebt gecontroleerd of de extensie Plaatsen en de extensie Plaatsen Monitor correct werken in uw toepassing, moet u gegevenselementen in Experience Platform Launch maken. Met gegevenselementen kunt u de informatie lezen die is verschaft door de extensies die via de Mobile SDK-gebeurtenishub komen en fungeren als een alias voor het ophalen van gegevens van de clienttoepassing. Om gegevens van de uitbreidingen van Plaatsen terug te winnen en de informatie van de Dienst van Plaatsen naar Campagne te verzenden, moet u een paar gegevenselementen tot stand brengen.

Een gegevenselement maken:

1. Klik op het **[!UICONTROL Data Elements]** tabblad van de mobiele eigenschap van het Experience Platform Launch **[!UICONTROL Add Data Element]**.
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Extension]** de optie **[!UICONTROL Places Service]**.
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Data Element Type]** de optie **[!UICONTROL Name]**.
1. In het rechterzijpaneel, kunt u selecteren **[!UICONTROL Current POI]** die de naam van POI terugwint waarin de gebruiker momenteel wordt gevestigd.

   **[!UICONTROL Last Entered]** wint de naam van POI terug die de gebruiker het laatst inging, en **[!UICONTROL Last Exited]** verstrekt de naam van POI die de gebruiker het laatst verliet. In dit voorbeeld hebben we een naam voor het gegevenselement geselecteerd **[!UICONTROL Last Entered]** en getypt, zoals **[!UICONTROL Last Entered POI Name]** en erop geklikt **[!UICONTROL Save]**.

   ![&quot;Push messaging in Campaign Standard&quot;](/help/assets/ACS_Push1.png)

1. Repeat the steps 1-4 above and create data elements for *Last Entered POI Latitude*, *Last Entered POI Longitude*, and *Last Entered POI Radius*.

Naast de gegevenselementen voor de Dienst van Plaatsen, zorg ervoor dat u Mobiele de gegevenselementen van de Kern voor identiteitskaart *van de* Toepassing en identiteitskaart *van de* Experience Cloud creeert.

## Een regel maken om locatiegegevens naar Adobe Campaign Standard te verzenden

De regels in Experience Platform Launch staan u toe om complexe, multi-oplossing werkschema&#39;s tot stand te brengen die op gebeurtenistrekkers worden gebaseerd. Met regels kunt u nieuwe regels maken of bestaande regels wijzigen en de updates dynamisch laten implementeren in uw mobiele toepassingen. In het volgende voorbeeld, zal de regel worden teweeggebracht wanneer een gebruiker geo-fenced POI ingaat. Nadat de regel wordt teweeggebracht, wordt een update verzonden naar Campaign Standard om een ingang aan specifieke POI voor een bepaalde gebruiker te registreren die op Experience Cloud identiteitskaart wordt gebaseerd.

1. Klik op het **[!UICONTROL Rules]** tabblad van de mobiele eigenschap van uw Experience Platform Launch **[!UICONTROL Add Rule]**.
1. Klik onder de **[!UICONTROL Events]** sectie op **[!UICONTROL +]** en selecteer **[!UICONTROL Places Service]** de extensie.
1. Selecteer voor de **[!UICONTROL Event Type]** optie **[!UICONTROL Enter POI]**.
1. Geef de regel een naam, bijvoorbeeld **Gebruiker heeft een POI** ingevoerd.
1. Klik op **[!UICONTROL Keep Changes]**.
1. Laat de **[!UICONTROL Conditions]** sectie leeg.

   In deze sectie kunt u filteren op of beperkingen instellen voor het tijdstip waarop deze regel moet worden geactiveerd.

1. Under the **[!UICONTROL Actions]** section, click **[!UICONTROL +]**.
1. Selecteer in de **[!UICONTROL Extension]** vervolgkeuzelijst de optie **[!UICONTROL Mobile Core]** en selecteer in de **[!UICONTROL Action Type]** vervolgkeuzelijst **[!UICONTROL Send Postback]**.
1. In **[!UICONTROL URL]**, moet u uw Campaign Standard plaatseindpunt construeren.

   De URL moet er ongeveer zo uitzien `https:///rest/head/mobileAppV5//locations/`.
Zorg ervoor dat u de juiste gegevenselementen gebruikt die u eerder voor uw campagneserver en pKey hebt gemaakt.

1. Klik op het vakje om een berichttekst toe te voegen en het volgende te verzenden:

   ```
   {
    "locationData": {
    "distances": "{%%Last Entered POI Radius%%}",
    "poiLabel": "{%%Last Entered POI Name%%}",
    "latitude": "{%%Last Entered POI Lat%%}",
    "longitude": "{%%Last Entered POI Long%%}",
    "appId": "{%%AppID%%}",
    "marketingCloudId": “{%%ecid%%}”
    }
   }
   ```

1. Zorg ervoor dat u gegevenselementen gebruikt die u in de vorige sectie hebt gemaakt.
1. In **[!UICONTROL Content Type]** typt u **[!UICONTROL application/json]**.
1. Klik op **[!UICONTROL Keep Changes]**.

>[!IMPORTANT]
>
>* Het kan handig zijn om een Slack-webhaak in te stellen als een aanvullende actie om te controleren of items worden geactiveerd en of de juiste gegevens worden verzameld.
>* Vergeet niet de recente wijzigingen in uw app te publiceren om ervoor te zorgen dat de regel en al uw gegevenselementen worden geïmplementeerd als onderdeel van uw configuratie. Nadat u de mobiele toepassing hebt gepubliceerd, start u deze opnieuw om de meest recente configuratie-updates op te halen.


## Locatiegegevens gebruiken om campagneberichten als doel in te stellen

Nu we locatiegegevens hebben die in Campagne worden gevuld, kunnen we POI&#39;s gebruiken als een hulpmiddel voor het publiekssegment.

1. Klik in uw Adobe Campaign Standard-exemplaar op **[!UICONTROL Create Push Notification]**.
1. Selecteer voor het type pushmelding **[!UICONTROL Send push to Campaign profiles]**.
1. Klik op de algemene details **[!UICONTROL Next]** en typ deze.
1. Klik in het scherm Publiek **[!UICONTROL Count]** om te bepalen hoeveel gebruikers het pushbericht wordt verzonden.

   >[!TIP]
   >
   >In dit voorbeeld is het aantal 3, omdat er drie geïnstalleerde apparaten zijn waarop de toepassing wordt getest.

1. In the left pane, expand the **[!UICONTROL Profile]** tab and drag the **[!UICONTROL POI location]** filter to the main area.
1. Voer in het venster POI-filter de exacte naam in van de POI die u als doel wilt gebruiken.

   >[!TIP]
   >
   >U kunt extra selecties maken om de periode te bepalen sinds het vorige bezoek van de gebruiker aan deze POI.

   ![&quot;Push messaging 2 in ACS&quot;](/help/assets/ACS_push2.png)

1. Klik op **[!UICONTROL Confirm]**.
1. Voer de telling opnieuw bovenaan uit om de grootte van uw publiek te wijzigen.

   Als u uw tellersupdate niet ziet, zou u een POI naam kunnen zijn ingegaan waarvoor geen apparaten een ingang hebben teweeggebracht. De Slack-webhaak is in deze situatie waardevol, omdat u een lijst met POI-items van verschillende testapparaten kunt zien.

1. U kunt extra POI-locatiefilters uitslepen om meerdere POI&#39;s in uw bericht op te nemen.
1. Klik op **[!UICONTROL Next]** om het maken van de pushmelding voor levering te voltooien.

   ![&quot;Push messaging 3 in ACS&quot;](/help/assets/ACS_push3.png)

Het gebruiken van de Dienst van Plaatsen met Adobe Campaign Standard geeft u een krachtig hulpmiddel om uw overseinen aan gebruikers te segmenteren en te richten die op geo-fence ingangen en uitgang worden gebaseerd. Deze integratie helpt u meer gepersonaliseerde en contextuele gebruiksgevallen te bouwen.