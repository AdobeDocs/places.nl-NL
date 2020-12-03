---
title: Locatiecontext toevoegen aan verzoeken van Analytics
description: Deze sectie verstrekt informatie over hoe te om plaatscontext aan verzoeken van Analytics toe te voegen.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 7%

---


# Locatiecontext toevoegen aan verzoeken van Analytics {#run-reports-aa-locserv-data}

>[!IMPORTANT]
>
>In dit document wordt ervan uitgegaan dat de Plaatsen-service in uw toepassing is geïmplementeerd. Zie Extensies [Plaatsen voor meer informatie over het implementeren van Plaatsen Service](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Nadat de Dienst van Plaatsen de ingang en uitgangsgebeurtenissen verzendt, kunt u regels in Experience Platform Launch tot stand brengen en uw gegevens van de Dienst van Plaatsen aan alle gebeurtenissen van Adobe Analytics vastmaken. Als u dit type regel wilt maken, selecteert u de eigenschap in Launch en voert u de volgende stappen uit:

## 1. Een regel maken

1. On the **[!UICONTROL Rules]** tab, click **[!UICONTROL Create New Rule]**.

   De volgende informatie onthouden:
   * Als u geen bestaande regels voor deze eigenschap hebt, bevindt de **[!UICONTROL Create New Rule]** knop zich in het midden van het scherm.
   * Als uw eigenschap regels bevat, bevindt de **[!UICONTROL Create New Rule]** knop zich rechtsboven in het scherm.

## 2. Selecteer een gebeurtenis

1. Geef uw regel een betekenisvolle naam zodat deze gemakkelijk herkenbaar is in uw lijst met regels.

   In dit voorbeeld is de naam van de regel **[!UICONTROL Attach Places Service Data to Analytics Track Action Events]**.

1. Under the **[!UICONTROL Events]** section, click **[!UICONTROL Add]**.

1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Extension]** de optie **[!UICONTROL Mobile Core]**.

1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Event Type]** de optie **[!UICONTROL Track Action]**.

Nu kunt u de trekkers bepalen die u voor deze Regel wilt omvatten. In dit voorbeeld is de trigger gebaseerd op alle `TrackAction` aanroepen. Nadat u de Gebeurtenis vormt, klik **[!UICONTROL Keep Changes]**.

![&quot;Een gebeurtenis maken&quot;](/help/assets/ad-setEvent_use-analytics-data.png)


## 3. Voorwaarden toevoegen

>[!IMPORTANT]
>
>Voltooi deze procedure om Voorwaarden aan uw regel toe te voegen. Anders gaat u verder met de onderstaande sectie *Handeling* definiëren.

In dit voorbeeld, wordt een Voorwaarde gecreeerd die de Regel veroorzaakt om slechts voor klanten te teweegbrengen AT&amp;T.

1. Under the **[!UICONTROL Conditions]** section, click **[!UICONTROL Add]**.

1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Extension]** de optie **[!UICONTROL Mobile Core]**.

1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Condition Type]** de optie **[!UICONTROL Carrier Name]**.

1. Selecteer het **[!UICONTROL AT&T]** selectievakje in het rechtervenster.

1. Klik op **[!UICONTROL Keep Changes]**.

![&quot;Een voorwaarde maken&quot;](/help/assets/ad-setCondition_use-analytics-data.png)

## 4. De handeling definiëren

1. Under the **[!UICONTROL Actions]** section, click **[!UICONTROL Add]**.

1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Extension]** de optie **[!UICONTROL Mobile Core]**.

1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Action Type]** de optie **[!UICONTROL Attach Data]**.

1. Typ in het rechterdeelvenster in het **[!UICONTROL JSON Payload]** veld de gegevens die aan deze gebeurtenis worden toegevoegd.

1. Klik op **[!UICONTROL Keep Changes]**.

In het rechterdeelvenster kunt u een vrije JSON-payload toevoegen die gegevens toevoegt aan een SDK-gebeurtenis voordat een extensie die luistert naar deze gebeurtenis de gebeurtenis kan horen. In dit voorbeeld worden enkele contextgegevens toegevoegd aan deze gebeurtenis voordat de extensie Analytics deze verwerkt. De toegevoegde contextgegevens bevinden zich nu op de hit uitgaande Analytics.

In het volgende voorbeeld worden `poi.city` en `poi.name` waarden toegevoegd aan de contextgegevens van de gebeurtenis Analytics. De waarden voor de nieuwe toetsen worden dynamisch bepaald door de SDK wanneer deze gebeurtenis wordt verwerkt.

![&quot;Een handeling maken&quot;](/help/assets/ad-setAction_use-analytics-data.png)

## 5. Sla de regel op en maak de eigenschap opnieuw op

Nadat u uw configuratie voltooit, verifieer dat uw Regel als het volgende beeld kijkt:

![&quot;de regel is volledig.&quot;](/help/assets/ad-ruleComplete_use-analytics-data.png)

1. Klik op **[!UICONTROL Save]**

1. Bouw uw bezit van de Lancering opnieuw en stel het aan het correcte Milieu op.
