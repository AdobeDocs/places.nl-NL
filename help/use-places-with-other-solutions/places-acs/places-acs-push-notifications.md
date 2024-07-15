---
title: Push-berichten met Places Service
description: Deze sectie bevat informatie over het gebruik van de Places Service met pushberichten in het Campaign Standard.
exl-id: 4b50f552-deb8-49cd-9221-fbbf33aaa5f9
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '913'
ht-degree: 2%

---

# Push Notifications with Places Service {#push-notifications}

In deze sectie leert u hoe u historische geo-locatiegegevens kunt gebruiken om pushberichten te activeren die via Adobe Campaign Standard worden geleverd.

## Vereisten

Voer de volgende taken uit voordat u begint:

* Heb een mobiele toepassing die met Adobe Experience Platform Mobile SDK, met inbegrip van de [ uitbreiding van Adobe Campaign Standard ](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) wordt gevormd.

* Integreer [ Adobe Experience Platform Mobile SDK ](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) in uw app.
* Voeg de [ Uitbreiding van Adobe Campaign Standard ](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) aan uw mobiele toepassingsconfiguratie toe.

* [ creeer een POI ](/help/poi-mgmt-ui/create-a-poi-ui.md) in het POI van de Dienst van Plaatsen beheersinterface.

* Laat en installeer de [ uitbreiding van Plaatsen ](/help/places-ext-aep-sdks/places-extension/places-extension.md) toe.


## Gegevenselementen maken in Experience Platform Launch

Na het verifiëren dat de uitbreiding van Plaatsen en een gebied controlerende oplossing ([ documentatie CoreLocation ](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) voor iOS, of [ de plaatsdocumentatie van Android ](https://developer.android.com/training/location/geofencing)) correct in uw toepassing werken, moet u gegevenselementen in Experience Platform Launch tot stand brengen. Met gegevenselementen kunt u de informatie lezen die is verschaft door de extensies die via de Mobile SDK-gebeurtenishub komen en fungeren als een alias voor het ophalen van gegevens van de clienttoepassing. Om gegevens van de uitbreidingen van Plaatsen terug te winnen en de informatie van de Dienst van Plaatsen naar Campagne te verzenden, moet u een paar gegevenselementen tot stand brengen.

Een gegevenselement maken:

1. Klik op de tab **[!UICONTROL Data Elements]** van de mobiele eigenschap van het Experience Platform Launch en klik op **[!UICONTROL Add Data Element]** .
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Extension]** de optie **[!UICONTROL Places Service]**.
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Data Element Type]** de optie **[!UICONTROL Name]**.
1. In het rechterdeelvenster kunt u **[!UICONTROL Current POI]** selecteren waarmee de naam wordt opgehaald van de POI waarin de gebruiker zich momenteel bevindt.

   **[!UICONTROL Last Entered]** haalt de naam op van de POI die de gebruiker het laatst heeft ingevoerd en **[!UICONTROL Last Exited]** geeft de naam van de POI die de gebruiker het laatst heeft verlaten. In dit voorbeeld hebben we **[!UICONTROL Last Entered]** geselecteerd en een naam voor het gegevenselement getypt, zoals **[!UICONTROL Last Entered POI Name]** en geklikt **[!UICONTROL Save]** .

   ![ &quot;Push messaging in Campaign Standard&quot;](/help/assets/ACS_Push1.png)

1. Herhaal de stappen 1-4 hierboven en creeer gegevenselementen voor *Laatste binnengekomen POI Breedte*, *Laatste ingevoerde POI Lengte*, en *Laatste binnen POI Straal*.

Naast de gegevenselementen voor de Dienst van Plaatsen, zorg ervoor dat u de Mobiele gegevenselementen van de Kern voor *identiteitskaart van de Toepassing* en *identiteitskaart van het Experience Cloud* creeert.

## Een regel maken om locatiegegevens naar Adobe Campaign Standard te verzenden

De regels in Experience Platform Launch staan u toe om complexe, multi-oplossing werkschema&#39;s tot stand te brengen die op gebeurtenistrekkers worden gebaseerd. Met regels kunt u nieuwe regels maken of bestaande regels wijzigen en de updates dynamisch laten implementeren in uw mobiele toepassingen. In het volgende voorbeeld, zal de regel worden teweeggebracht wanneer een gebruiker geo-fenced POI ingaat. Nadat de regel wordt teweeggebracht, wordt een update verzonden naar Campaign Standard om een ingang aan specifieke POI voor een bepaalde gebruiker te registreren die op Experience Cloud ID wordt gebaseerd.

1. Klik op het tabblad **[!UICONTROL Rules]** op de mobiele eigenschap van uw Experience Platform Launch op **[!UICONTROL Add Rule]** .
1. Klik onder de sectie **[!UICONTROL Events]** op **[!UICONTROL +]** en selecteer **[!UICONTROL Places Service]** als de extensie.
1. Selecteer **[!UICONTROL Enter POI]** voor **[!UICONTROL Event Type]** .
1. Noem de regel, bijvoorbeeld, **Gebruiker ging POI** binnen.
1. Klik op **[!UICONTROL Keep Changes]**.
1. Laat de sectie **[!UICONTROL Conditions]** leeg.

   In deze sectie kunt u filteren op of beperkingen instellen voor het tijdstip waarop deze regel moet worden geactiveerd.

1. Klik onder de sectie **[!UICONTROL Actions]** op **[!UICONTROL +]** .
1. Selecteer **[!UICONTROL Mobile Core]** in de vervolgkeuzelijst **[!UICONTROL Action Type]** en selecteer **[!UICONTROL Send Postback]** in de vervolgkeuzelijst **[!UICONTROL Extension]** .
1. In **[!UICONTROL URL]**, moet u uw Campaign Standard plaatseindpunt construeren.

   De URL moet er ongeveer zo uitzien als `https:///rest/head/mobileAppV5//locations/` .
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
>* Het zou nuttig kunnen zijn om een Slack Web-haakopstelling als extra actie te hebben om te bevestigen dat de ingangen worden teweeggebracht en dat de juiste gegevens worden verzameld.
>* Vergeet niet de recente wijzigingen in uw app te publiceren om ervoor te zorgen dat de regel en al uw gegevenselementen worden geïmplementeerd als onderdeel van uw configuratie. Nadat u de mobiele toepassing hebt gepubliceerd, start u deze opnieuw om de meest recente configuratie-updates op te halen.

## Locatiegegevens gebruiken om campagneberichten als doel in te stellen

Nu we locatiegegevens hebben die in Campagne worden gevuld, kunnen we POI&#39;s gebruiken als een hulpmiddel voor publiekssegmenten.

1. Klik in uw Adobe Campaign Standard-instantie op **[!UICONTROL Create Push Notification]** .
1. Selecteer **[!UICONTROL Send push to Campaign profiles]** voor het type pushmelding.
1. Klik op **[!UICONTROL Next]** en typ de algemene details.
1. Klik in het scherm Publiek op **[!UICONTROL Count]** om te bepalen hoeveel gebruikers de pushmelding wordt verzonden.

   >[!TIP]
   >
   >In dit voorbeeld is het aantal 3, omdat er drie geïnstalleerde apparaten zijn waarop de toepassing wordt getest.

1. Vouw in het linkerdeelvenster de tab **[!UICONTROL Profile]** uit en sleep het filter **[!UICONTROL POI location]** naar het hoofdgebied.
1. Voer in het venster POI-filter de exacte naam in van de POI die u als doel wilt gebruiken.

   >[!TIP]
   >
   >U kunt extra selecties maken om de periode te bepalen sinds het vorige bezoek van de gebruiker aan deze POI.

   ![ &quot;Push messaging 2 in ACS&quot;](/help/assets/ACS_push2.png)

1. Klik op **[!UICONTROL Confirm]**.
1. Voer de telling opnieuw bovenaan uit om de grootte van uw publiek te wijzigen.

   Als u uw tellersupdate niet ziet, zou u een POI naam kunnen zijn ingegaan waarvoor geen apparaten een ingang hebben teweeggebracht. De Slack-webhaak is in deze situatie waardevol, omdat u een lijst met POI-items van verschillende testapparaten kunt zien.

1. U kunt extra POI-locatiefilters uitslepen om meerdere POI&#39;s in uw bericht op te nemen.
1. Klik op **[!UICONTROL Next]** om het maken van de pushmelding voor levering te voltooien.

   ![ &quot;Push messaging 3 in ACS&quot;](/help/assets/ACS_push3.png)

Het gebruiken van de Dienst van Plaatsen met Adobe Campaign Standard geeft u een krachtig hulpmiddel om uw overseinen aan gebruikers te segmenteren en te richten die op geo-fence ingangen en uitgang worden gebaseerd. Deze integratie helpt u meer gepersonaliseerde en contextuele gebruiksgevallen te bouwen.
