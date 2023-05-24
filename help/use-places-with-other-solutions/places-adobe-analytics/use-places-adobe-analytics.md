---
title: POI-invoer- en afsluitgegevens naar Analytics verzenden
description: Deze sectie verstrekt informatie over hoe te om POI ingang en uitgangsgegevens naar Analytics te verzenden.
exl-id: 69e96261-4902-47dd-a930-a8f3d19c179c
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 8%

---

# POI-invoer- en afsluitgegevens naar Analytics verzenden {#places-data-analytics}


>[!IMPORTANT]
>
>Deze sectie veronderstelt dat u de Dienst van Plaatsen in uw toepassing hebt uitgevoerd. Voor meer informatie over het uitvoeren van de Dienst van Plaatsen, zie [Extensies plaatsen](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Nadat de Dienst van Plaatsen de ingang en uitgangsgebeurtenissen verzendt, kunt u regels in Experience Platform Launch tot stand brengen om de gegevens van de Dienst van Plaatsen naar Adobe Analytics te verzenden. Als u dit type regel wilt maken, selecteert u de eigenschap in Launch en voert u de volgende stappen uit:

## 1. Een regel maken

1. Op de **[!UICONTROL Rules]** tabblad, klikt u op **[!UICONTROL Create New Rule]**.

   De volgende informatie onthouden:

   * Als u geen bestaande regels voor deze eigenschap hebt, wordt **[!UICONTROL Create New Rule]** De knop bevindt zich in het midden van het scherm.
   * Als uw eigenschap regels heeft, wordt de **[!UICONTROL Create New Rule]** Deze knop bevindt zich in de rechterbovenhoek van het scherm.

## 2. Een gebeurtenis selecteren

1. Typ een betekenisvolle naam voor uw regel.

   Op die manier is de regel gemakkelijk herkenbaar in uw lijst met regels. In dit voorbeeld krijgt de regel de naam **[!UICONTROL Send Data to Analytics]**.

1. In de **[!UICONTROL Events]** sectie, klikt u op **[!UICONTROL Add]**.

1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Extension]** de optie **[!UICONTROL Places Service]**.

1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Event Type]** de optie **[!UICONTROL Enter POI]**.

1. Klik op **[!UICONTROL Keep Changes]**.

   ![&quot;select an event&quot;](/help/assets/pt-selectEvent.png)


## 3. Voorwaarden toevoegen

>[!IMPORTANT]
>
>Voltooi deze stap om Voorwaarden aan uw regel toe te voegen. Anders kunt u overslaan naar *De handeling definiëren* hieronder.

In dit voorbeeld wordt een voorwaarde gemaakt die ervoor zorgt dat de regel alleen wordt geactiveerd wanneer de naam van de huidige POI gelijk is **[!UICONTROL My POI]**.

1. Onder de **[!UICONTROL Conditions]** sectie, klikt u op **[!UICONTROL Add]**.

1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Extension]** de optie **[!UICONTROL Places Service]**.

1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Condition Type]** de optie **[!UICONTROL Name]**.

1. Typ in het rechterdeelvenster in het tekstveld **[!UICONTROL My POI]**.

1. Klik op **[!UICONTROL Keep Changes]**.

   ![&quot;een voorwaarde instellen&quot;](/help/assets/pt-setCondition.png)


## 4. De handeling definiëren

1. Onder de **[!UICONTROL Actions]** sectie, klikt u op **[!UICONTROL Add]**.

1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Extension]** de optie **[!UICONTROL Adobe Analytics]**.

1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Action Type]** de optie **[!UICONTROL Track]**.

1. Voeg in het rechterdeelvenster de handeling of status toe die u naar Analytics wilt verzenden.

   U kunt ook aanvullende contextgegevens toevoegen aan deze aanvraag. Herinner dat u gegevenselementen kunt gebruiken om deze gegevens dynamisch van SDK te krijgen.

1. Klik op **[!UICONTROL Keep Changes]**.

   In het volgende voorbeeld wordt een `TrackAction` de vraag wordt verzonden naar Analytics met extra contextgegevens van `poi.name` gelijk aan de naam van de POI die deze entry-gebeurtenis heeft geactiveerd:

   ![&quot;Een handeling instellen&quot;](/help/assets/pt-setAction.png)

## 5. Sla de regel op en maak de eigenschap opnieuw op

Nadat u uw configuratie voltooit, verifieer dat uw Regel als het volgende beeld kijkt:

![&quot;rule is created&quot;](/help/assets/pt-ruleComplete.png)

1. Klik op **[!UICONTROL Save]**

1. Maak uw opstarteigenschap opnieuw en implementeer deze in de juiste omgeving.
