---
title: Berichten in de app met Plaatsen Service
description: Deze sectie verstrekt informatie over hoe te om het Overseinen van de Duw in de Norm van de Campagne met in-app berichten in de Norm van de Campagne te gebruiken.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b

---


# Berichten in de app met Plaatsen Service {#in-app-messages-loc-service}

Deze informatie helpt u begrijpen hoe u de informatie van de Dienst van Plaatsen kunt gebruiken om Berichten in-app of Lokale Meldingen te verzenden.

## Vereisten

Voer de volgende taken uit voordat u begint:

* Een mobiele toepassing hebben geconfigureerd met de Adobe Experience Platform Mobile SDK, inclusief de [Adobe Campagne Standard-extensie](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard).

* Integreer de [Adobe Experience Platform Mobile SDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) in uw app.
* Voeg de standaardextensie [voor](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) Adobe Campagne toe aan uw mobiele toepassingsconfiguratie.

* [Creeer POI](/help/poi-mgmt-ui/create-a-poi-ui.md) in de het beheersinterface van POI van de Dienst van Plaatsen.

* Installeer en configureer de extensie [](/help/places-ext-aep-sdks/places-extension/places-extension.md) Plaatsen en [Plaatst Monitor-extensies](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md) in uw mobiele toepassing.

## In-app-berichten verzenden op basis van een geo-fence-item of -uitgang

1. Klik in uw Adobe Campagne Standard-exemplaar op **[!UICONTROL Create In-App message]**.
1. Selecteer voor het berichttype **[!UICONTROL Target all users of a Mobile application]**.
1. Klik op de algemene details **[!UICONTROL Next]** en typ deze.
1. Controleer in het linkerdeelvenster of u verschillende triggers kunt gebruiken die verwant zijn aan Places Services.

   * U kunt ervoor kiezen om de berichtweergave in de app te laten weergeven als de gebruiker een POI-geo-fence heeft ingevoerd.
   * U kunt meta-gegevens ook gebruiken die in de UI van de Diensten van Plaatsen worden bepaald om publiek te filtreren.
   In het onderstaande voorbeeld kunt u een bericht in de app activeren dat alleen wordt weergegeven voor gebruikers die een van de vakantieruimten invoeren die deelnemen aan een programma voor gratis dranken. U wilt deze gebruikers een coupon sturen wanneer ze aankomen.

   ![&quot;Metagegevens voor berichtlocaties in de app&quot;](/help/assets/last-entered-vacation.png)

1. Click the **[!UICONTROL Next]** to finish creating the In-app message for delivery.

   ![&quot;Een gebeurtenis maken&quot;](/help/assets/prepare-ACS.png)

   Als u de berichtlevering in de app wilt testen, start u de toepassing in de Xcode- of Android-studio en gebruikt u de locatiesimulator om een POI te selecteren die voldoet aan de berichtcriteria.

   ![&quot;coupon drank&quot;](/help/assets/drink-coupon-on-app.png)

Als u de Diensten van Plaatsen met de Norm van de Campagne van Adobe gebruikt, hebt u een krachtig hulpmiddel om uw overseinen aan gebruikers te segmenteren en te richten die op geo-fence ingangen en uitgang wordt gebaseerd. Dankzij deze integratie kunt u meer persoonlijke en contextafhankelijke gebruiksgevallen maken.

>[!VIDEO](https://www.youtube.com/watch?v=ikiTTQw9c-o)