---
title: Locatiecontext toevoegen aan verzoeken van Analytics
description: Deze sectie verstrekt informatie over hoe te om plaatscontext aan verzoeken van Analytics toe te voegen.
exl-id: bee7b6e3-a75b-4a07-b6e2-f93ce33aa042
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 7%

---

# Locatiecontext toevoegen aan verzoeken van Analytics {#run-reports-aa-locserv-data}

>[!IMPORTANT]
>
>In dit document wordt ervan uitgegaan dat de Plaatsen-service in uw toepassing is geïmplementeerd. Voor meer informatie over het uitvoeren van de Dienst van Plaatsen, zie [&#x200B; uitbreidingen van Plaatsen &#x200B;](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Nadat de Dienst van Plaatsen de ingang en uitgangsgebeurtenissen verzendt, kunt u regels in Experience Platform Launch tot stand brengen en uw gegevens van de Dienst van Plaatsen aan alle gebeurtenissen van Adobe Analytics vastmaken. Als u dit type regel wilt maken, selecteert u de eigenschap in Launch en voert u de volgende stappen uit:

## 1. Maak een regel

1. Klik op het tabblad **[!UICONTROL Rules]** op **[!UICONTROL Create New Rule]** .

   De volgende informatie onthouden:
   * Als u geen bestaande regels voor deze eigenschap hebt, bevindt de knop **[!UICONTROL Create New Rule]** zich in het midden van het scherm.
   * Als uw eigenschap regels heeft, bevindt de knop **[!UICONTROL Create New Rule]** zich rechtsboven in het scherm.

## 2. Selecteer een gebeurtenis

1. Geef uw regel een betekenisvolle naam zodat deze gemakkelijk herkenbaar is in uw lijst met regels.

   In dit voorbeeld krijgt de regel de naam **[!UICONTROL Attach Places Service Data to Analytics Track Action Events]** .

1. Klik onder de sectie **[!UICONTROL Events]** op **[!UICONTROL Add]** .

1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Extension]** de optie **[!UICONTROL Mobile Core]**.

1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Event Type]** de optie **[!UICONTROL Track Action]**.

Nu kunt u de trekkers bepalen die u voor deze Regel wilt omvatten. In dit voorbeeld is de trigger gebaseerd op alle `TrackAction` -aanroepen. Klik op **[!UICONTROL Keep Changes]** nadat u de gebeurtenis hebt geconfigureerd.

![&#x200B; &quot;creeer een gebeurtenis&quot;](/help/assets/ad-setEvent_use-analytics-data.png)


## 3. Voorwaarden toevoegen

>[!IMPORTANT]
>
>Voltooi deze procedure om Voorwaarden aan uw regel toe te voegen. Anders, overslaan aan *bepaalt hieronder de sectie van de Actie*.

In dit voorbeeld, wordt een Voorwaarde gecreeerd die de Regel veroorzaakt om slechts voor klanten te teweegbrengen AT&amp;T.

1. Klik onder de sectie **[!UICONTROL Conditions]** op **[!UICONTROL Add]** .

1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Extension]** de optie **[!UICONTROL Mobile Core]**.

1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Condition Type]** de optie **[!UICONTROL Carrier Name]**.

1. Selecteer in het venster aan de rechterkant het selectievakje **[!UICONTROL AT&T]** .

1. Klik op **[!UICONTROL Keep Changes]**.

![&#x200B; &quot;creeer een voorwaarde&quot;](/help/assets/ad-setCondition_use-analytics-data.png)

## 4. De actie definiëren

1. Klik onder de sectie **[!UICONTROL Actions]** op **[!UICONTROL Add]** .

1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Extension]** de optie **[!UICONTROL Mobile Core]**.

1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Action Type]** de optie **[!UICONTROL Attach Data]**.

1. Typ in het rechterdeelvenster in het veld **[!UICONTROL JSON Payload]** de gegevens die aan deze gebeurtenis worden toegevoegd.

1. Klik op **[!UICONTROL Keep Changes]**.

In het rechterdeelvenster kunt u een vrije JSON-payload toevoegen die gegevens toevoegt aan een SDK-gebeurtenis voordat een extensie die luistert naar deze gebeurtenis de gebeurtenis kan horen. In dit voorbeeld worden enkele contextgegevens toegevoegd aan deze gebeurtenis voordat de extensie Analytics deze verwerkt. De toegevoegde contextgegevens bevinden zich nu op de hit uitgaande Analytics.

In het volgende voorbeeld worden `poi.city` - en `poi.name` -waarden toegevoegd aan de contextgegevens van de gebeurtenis Analytics. De waarden voor de nieuwe toetsen worden dynamisch bepaald door de SDK wanneer deze gebeurtenis wordt verwerkt.

![&#x200B; &quot;creeer een actie&quot;](/help/assets/ad-setAction_use-analytics-data.png)

## 5. Sla de regel op en herstel de eigenschap

Nadat u uw configuratie voltooit, verifieer dat uw Regel als het volgende beeld kijkt:

![&#x200B; &quot;de regel is volledig.&quot;](/help/assets/ad-ruleComplete_use-analytics-data.png)

1. Klikken **[!UICONTROL Save]**

1. Bouw uw bezit van de Lancering opnieuw en stel het aan het correcte Milieu op.
