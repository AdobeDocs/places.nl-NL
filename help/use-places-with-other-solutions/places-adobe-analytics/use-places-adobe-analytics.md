---
title: POI-invoer- en afsluitgegevens naar Analytics verzenden
description: Deze sectie verstrekt informatie over hoe te om POI ingang en uitgangsgegevens naar Analytics te verzenden.
translation-type: tm+mt
source-git-commit: 8a84fe2dc5a0efe94ce3121e589524e3c7a80c5e
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 8%

---


# POI-invoer- en afsluitgegevens naar Analytics verzenden {#places-data-analytics}


>[!IMPORTANT]
>
>Deze sectie veronderstelt dat u de Dienst van Plaatsen in uw toepassing hebt uitgevoerd. Zie Extensies [Plaatsen voor meer informatie over het implementeren van Plaatsen Service](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Nadat de Dienst van Plaatsen de ingang en uitgangsgebeurtenissen verzendt, kunt u regels in Experience Platform Launch tot stand brengen om de gegevens van de Dienst van Plaatsen naar Adobe Analytics te verzenden. Als u dit type regel wilt maken, selecteert u de eigenschap in Launch en voert u de volgende stappen uit:

## 1. Een regel maken

1. On the **[!UICONTROL Rules]** tab, click **[!UICONTROL Create New Rule]**.

   De volgende informatie onthouden:

   * Als u geen bestaande regels voor deze eigenschap hebt, bevindt de **[!UICONTROL Create New Rule]** knop zich in het midden van het scherm.
   * Als uw eigenschap regels bevat, bevindt de **[!UICONTROL Create New Rule]** knop zich rechtsboven in het scherm.

## 2. Een gebeurtenis selecteren

1. Typ een betekenisvolle naam voor uw regel.

   Op die manier is de regel gemakkelijk herkenbaar in uw lijst met regels. In dit voorbeeld is de naam van de regel **[!UICONTROL Send Data to Analytics]**.

1. In the **[!UICONTROL Events]** section, click **[!UICONTROL Add]**.

1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Extension]** de optie **[!UICONTROL Places Service]**.

1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Event Type]** de optie **[!UICONTROL Enter POI]**.

1. Klik op **[!UICONTROL Keep Changes]**.

   ![&quot;select an event&quot;](/help/assets/pt-selectEvent.png)


## 3. Voorwaarden toevoegen

>[!IMPORTANT]
>
>Voltooi deze stap om Voorwaarden aan uw regel toe te voegen. Anders gaat u verder met *de onderstaande handeling* definiëren.

In dit voorbeeld wordt een voorwaarde gemaakt die ervoor zorgt dat de regel alleen wordt geactiveerd wanneer de naam van de huidige POI gelijk is aan **[!UICONTROL My POI]**.

1. Under the **[!UICONTROL Conditions]** section, click **[!UICONTROL Add]**.

1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Extension]** de optie **[!UICONTROL Places Service]**.

1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Condition Type]** de optie **[!UICONTROL Name]**.

1. Typ in het rechterdeelvenster in het tekstveld **[!UICONTROL My POI]**.

1. Klik op **[!UICONTROL Keep Changes]**.

   ![&quot;een voorwaarde instellen&quot;](/help/assets/pt-setCondition.png)


## 4. De handeling definiëren

1. Under the **[!UICONTROL Actions]** section, click **[!UICONTROL Add]**.

1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Extension]** de optie **[!UICONTROL Adobe Analytics]**.

1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Action Type]** de optie **[!UICONTROL Track]**.

1. Voeg in het rechterdeelvenster de handeling of status toe die u naar Analytics wilt verzenden.

   U kunt ook aanvullende contextgegevens toevoegen aan deze aanvraag. Herinner dat u gegevenselementen kunt gebruiken om deze gegevens dynamisch van SDK te krijgen.

1. Klik op **[!UICONTROL Keep Changes]**.

   In het volgende voorbeeld wordt een `TrackAction` aanroep verzonden naar Analytics met aanvullende contextgegevens die gelijk zijn `poi.name` aan de naam van de POI die deze entry-gebeurtenis heeft geactiveerd:

   ![&quot;Een handeling instellen&quot;](/help/assets/pt-setAction.png)

## 5. Sla de regel op en maak de eigenschap opnieuw op

Nadat u uw configuratie voltooit, verifieer dat uw Regel als het volgende beeld kijkt:

![&quot;rule is created&quot;](/help/assets/pt-ruleComplete.png)

1. Klik op **[!UICONTROL Save]**

1. Maak uw opstarteigenschap opnieuw en implementeer deze in de juiste omgeving.
