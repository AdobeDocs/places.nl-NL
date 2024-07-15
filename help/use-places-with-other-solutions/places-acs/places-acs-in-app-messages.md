---
title: Berichten in de app met Plaatsen Service
description: Deze sectie verstrekt informatie over hoe te om het Overseinen van de Duw in Campaign Standard met In-App berichten in Campaign Standard te gebruiken.
exl-id: c80727b8-20c9-4ca0-9f2c-20ec646bb7fa
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# Berichten in de app met Plaatsen Service {#in-app-messages-loc-service}

Deze informatie helpt u begrijpen hoe u de informatie van de Dienst van Plaatsen kunt gebruiken om Berichten in-app of Lokale Meldingen te verzenden.

## Vereisten

Voer de volgende taken uit voordat u begint:

* Heb een mobiele toepassing die met Adobe Experience Platform Mobile SDK, met inbegrip van de [ uitbreiding van Adobe Campaign Standard ](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) wordt gevormd.

* Integreer [ Adobe Experience Platform Mobile SDK ](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) in uw app.
* Voeg de [ Uitbreiding van Adobe Campaign Standard ](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) aan uw mobiele toepassingsconfiguratie toe.

* [ creeer een POI ](/help/poi-mgmt-ui/create-a-poi-ui.md) in het POI van de Dienst van Plaatsen beheersinterface.

* Installeer en vorm de [ uitbreiding van Plaatsen ](/help/places-ext-aep-sdks/places-extension/places-extension.md) en een gebied controlerende oplossing ([ documentatie CoreLocation ](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) voor iOS, of [ de plaatsdocumentatie van Android ](https://developer.android.com/training/location/geofencing)) in uw mobiele toepassing.

## In-app-berichten verzenden op basis van een geo-fence-item of -uitgang

1. Klik in uw Adobe Campaign Standard-instantie op **[!UICONTROL Create In-App message]** .
1. Selecteer **[!UICONTROL Target all users of a Mobile application]** voor het berichttype.
1. Klik op **[!UICONTROL Next]** en typ de algemene details.
1. Controleer in het linkerdeelvenster of u verschillende triggers kunt gebruiken die verwant zijn aan Places Services.

   * U kunt ervoor kiezen om de berichtweergave in de app te laten weergeven als de gebruiker een POI-geo-fence heeft ingevoerd.
   * U kunt meta-gegevens ook gebruiken die in de UI van de Diensten van Plaatsen worden bepaald om publiek te filtreren.

   In het onderstaande voorbeeld kunt u een bericht in de app activeren dat alleen wordt weergegeven voor gebruikers die een van de vakantieruimten invoeren die deelnemen aan een programma voor gratis dranken. U wilt deze gebruikers een coupon sturen wanneer ze aankomen.

   ![ &quot;In-App Message Places metadata&quot;](/help/assets/last-entered-vacation.png)

1. Klik op **[!UICONTROL Next]** om het maken van het In-app-bericht voor levering te voltooien.

   ![ &quot;creeer een gebeurtenis&quot;](/help/assets/prepare-ACS.png)

   Als u de berichtlevering in de app wilt testen, start u de toepassing in de Xcode- of Android-studio en gebruikt u de locatiesimulator om een POI te selecteren die voldoet aan de berichtcriteria.

   ![ &quot;drink coupon&quot;](/help/assets/drink-coupon-on-app.png)

Het gebruiken van de Diensten van Plaatsen met Adobe Campaign Standard geeft u een krachtig hulpmiddel om uw overseinen aan gebruikers te segmenteren en te richten die op geo-fence ingangen en uitgang worden gebaseerd. Dankzij deze integratie kunt u meer persoonlijke en contextafhankelijke gebruiksscenario&#39;s maken.

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

[ de Dienst van de Plaats van Adobe Experience Platform met het Overseinen van de Campagne ](https://www.youtube.com/watch?v=ikiTTQw9c-o)
