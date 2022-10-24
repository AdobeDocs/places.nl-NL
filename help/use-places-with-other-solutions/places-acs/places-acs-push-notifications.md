---
title: Pushmeldingen met Places Service
description: In deze sectie vindt u informatie over het gebruik van de Places Service met pushberichten in Campaign Standard.
exl-id: 4b50f552-deb8-49cd-9221-fbbf33aaa5f9
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '937'
ht-degree: 4%

---

# Push Notifications with Places Service {#push-notifications}

In deze sectie leert u hoe u historische geo-locatiegegevens kunt gebruiken om pushberichten te activeren die via Adobe Campaign Standard worden geleverd.

## Vereisten

Voer de volgende taken uit voordat u begint:

* Een mobiele toepassing hebben geconfigureerd met de Adobe Experience Platform Mobile SDK, inclusief de [Adobe Campaign Standard-extensie](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard).

* De [Adobe Experience Platform Mobile SDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) in uw app.
* Voeg de [Adobe Campaign Standard-extensie](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) naar uw mobiele toepassingsconfiguratie.

* [Een POI maken](/help/poi-mgmt-ui/create-a-poi-ui.md) in de POI van de Dienst van Plaatsen beheersinterface.

* Schakel de [Extensie Plaatsen](/help/places-ext-aep-sdks/places-extension/places-extension.md).


## Gegevenselementen maken in Experience Platform Launch

Na te hebben gecontroleerd of de extensie Plaatsen en een oplossing voor regiobewaking ([CoreLocation-documentatie](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) voor iOS, of [Documentatie over Android-locatie](https://developer.android.com/training/location/geofencing)) correct werkt in uw toepassing, moet u gegevenselementen in Experience Platform Launch creëren. Met gegevenselementen kunt u de informatie lezen die is verschaft door de extensies die via de Mobile SDK-gebeurtenishub komen en fungeren als een alias voor het ophalen van gegevens van de clienttoepassing. Om gegevens van de uitbreidingen van Plaatsen terug te winnen en de informatie van de Dienst van Plaatsen naar Campagne te verzenden, moet u een paar gegevenselementen tot stand brengen.

Een gegevenselement maken:

1. Klik in de mobiele eigenschap van uw Experience Platform Launch op de knop **[!UICONTROL Data Elements]** en klik op **[!UICONTROL Add Data Element]**.
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Extension]** de optie **[!UICONTROL Places Service]**.
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Data Element Type]** de optie **[!UICONTROL Name]**.
1. In het rechterdeelvenster kunt u **[!UICONTROL Current POI]** die de naam ophaalt van de POI waarin de gebruiker zich momenteel bevindt.

   **[!UICONTROL Last Entered]** wint de naam van POI terug die de gebruiker het laatst inging, en **[!UICONTROL Last Exited]** geeft de naam van de POI weer die de gebruiker het laatst heeft verlaten. In dit voorbeeld hebben we **[!UICONTROL Last Entered]** en typt u een naam voor het gegevenselement, zoals **[!UICONTROL Last Entered POI Name]** en geklikt **[!UICONTROL Save]**.

   ![&quot;Push messaging in Campaign Standard&quot;](/help/assets/ACS_Push1.png)

1. Herhaal bovenstaande stappen 1-4 en maak gegevenselementen voor *Laatste ingevoerde Latitude POI*, *Laatste ingevoerde lengtegraad van POI*, en *Laatste ingevoerde I-straal*.

Naast de gegevenselementen voor de Dienst van Plaatsen, zorg ervoor dat u Mobiele de gegevenselementen van de Kern creeert voor *Toepassings-id* en *Experience Cloud-id*.

## Een regel maken om locatiegegevens naar Adobe Campaign Standard te verzenden

De regels in Experience Platform Launch staan u toe om complexe, multi-oplossing werkschema&#39;s tot stand te brengen die op gebeurtenistrekkers worden gebaseerd. Met regels kunt u nieuwe regels maken of bestaande regels wijzigen en de updates dynamisch laten implementeren in uw mobiele toepassingen. In het volgende voorbeeld, zal de regel worden teweeggebracht wanneer een gebruiker geo-fenced POI ingaat. Nadat de regel wordt teweeggebracht, wordt een update verzonden naar Campaign Standard om een ingang aan specifieke POI voor een bepaalde gebruiker te registreren die op Experience Cloud identiteitskaart wordt gebaseerd.

1. In uw Experience Platform Launch mobiele eigenschap, op de **[!UICONTROL Rules]** tabblad, klikt u op **[!UICONTROL Add Rule]**.
1. Onder de **[!UICONTROL Events]** sectie, klikt u op **[!UICONTROL +]** en selecteert u **[!UICONTROL Places Service]** als de extensie.
1. Selecteer **[!UICONTROL Enter POI]** voor het **[!UICONTROL Event Type]**.
1. Geef de regel bijvoorbeeld een naam, **Door gebruiker ingevoerde POI**.
1. Klik op **[!UICONTROL Keep Changes]**.
1. Laat de **[!UICONTROL Conditions]** sectie leeg.

   In deze sectie kunt u filteren op of beperkingen instellen voor het tijdstip waarop deze regel moet worden geactiveerd.

1. Onder de **[!UICONTROL Actions]** sectie, klikt u op **[!UICONTROL +]**.
1. In de **[!UICONTROL Extension]** vervolgkeuzelijst, selecteert u **[!UICONTROL Mobile Core]** en in de **[!UICONTROL Action Type]** vervolgkeuzelijst, selecteert u **[!UICONTROL Send Postback]**.
1. In **[!UICONTROL URL]**, moet u uw de plaatsingsparameter van Campaign Standard construeren.

   De URL moet er ongeveer als volgt uitzien `https:///rest/head/mobileAppV5//locations/`.
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

Nu we locatiegegevens hebben die in Campagne worden gevuld, kunnen we POI&#39;s gebruiken als een hulpmiddel voor publiekssegmenten.

1. Klik in uw Adobe Campaign Standard-exemplaar op **[!UICONTROL Create Push Notification]**.
1. Selecteer bij het type pushmelding de optie **[!UICONTROL Send push to Campaign profiles]**.
1. Klikken **[!UICONTROL Next]** en typ de algemene details.
1. Klik in het scherm Publiek op **[!UICONTROL Count]** om te bepalen hoeveel gebruikers naar schatting worden verstuurd, wordt de pushmelding verzonden.

   >[!TIP]
   >
   >In dit voorbeeld is het aantal 3, omdat er drie geïnstalleerde apparaten zijn waarop de toepassing wordt getest.

1. Vouw in het linkervenster de **[!UICONTROL Profile]** en sleep de **[!UICONTROL POI location]** naar het hoofdgebied.
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
