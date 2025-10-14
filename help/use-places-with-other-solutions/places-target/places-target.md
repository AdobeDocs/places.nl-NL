---
title: Adobe Target
description: In deze sectie vindt u informatie over het gebruik van de Places Service bij Adobe Target.
exl-id: 6ee91fca-ea48-4de2-8dcf-87981813c678
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 7%

---

# Plaatsingsservice gebruiken voor Adobe Target {#places-target}

In dit document wordt ervan uitgegaan dat de extensie Plaatsen is geïmplementeerd in de toepassing. Als u hulp het uitvoeren van de uitbreiding van Plaatsen nodig hebt, zie [&#x200B; uitbreidingen van Plaatsen &#x200B;](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Nadat de extensie Plaatsen gebeurtenissen voor entry en exits verzendt, kunt u regels in Launch gebruiken om de gegevens van de Plaatsingsservice aan uw Adobe Target SDK-gebeurtenissen toe te voegen. Als de gewenste eigenschap is geselecteerd in Launch, kunt u dit type regel maken door de volgende taken uit te voeren:

## 1. Een regel maken

1. Klik op het tabblad **[!UICONTROL Rules]** op **[!UICONTROL Create New Rule]** .

   De volgende informatie onthouden:

   * Als u geen bestaande regels voor deze eigenschap hebt, bevindt de knop zich in het midden van het scherm.
   * Als uw eigenschap regels heeft, bevindt de knop zich rechtsboven in het scherm.

## 2. Selecteer een gebeurtenis

1. Geef uw regel een betekenisvolle naam zodat deze gemakkelijk herkenbaar is in uw lijst met regels.

   In dit voorbeeld krijgt de regel de naam **[!UICONTROL Attach Places Service Data to Target Content Requested]** .

1. Klik onder de sectie **[!UICONTROL Events]** op **[!UICONTROL Add]** .
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Extension]** de optie **[!UICONTROL Adobe Target]**.
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Event Type]** de optie **[!UICONTROL Content Requested]**.
1. Klik op **[!UICONTROL Keep Changes]**.

![&#x200B; voeg een gebeurtenis &#x200B;](/help/assets/ad-setEvent_target.png) toe

## 3. Voorwaarden toevoegen

>[!IMPORTANT]
>
>Voltooi deze stap als u Voorwaarden aan uw regel wilt toevoegen. Anders, overslaan aan *bepaalt hieronder de Actie*.

In het volgende voorbeeld wordt een voorwaarde gemaakt die ervoor zorgt dat de regel alleen wordt geactiveerd voor gebruikers die de app vijf of meer keren hebben gestart.

1. Klik onder de sectie **[!UICONTROL Conditions]** op **[!UICONTROL Add]** .
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Extension]** de optie **[!UICONTROL Mobile Core]**.
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Condition Type]** de optie **[!UICONTROL Launches]**.
1. Wijzig in het rechterdeelvenster de vervolgkeuzelijst en de nummerbesturingselementen, zodat de voorwaarde **[!UICONTROL User has launched the app greater than or equal to 5 times]** leest.
1. Klik op **[!UICONTROL Keep Changes]**.

![&#x200B; voeg een voorwaarde &#x200B;](/help/assets/ad-setCondition_target.png) toe

## 4. De actie definiëren

1. Klik onder de sectie **[!UICONTROL Actions]** op **[!UICONTROL Add]** .
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Extension]** de optie **[!UICONTROL Mobile Core]**.
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Action Type]** de optie **[!UICONTROL Attach Data]**.
1. Typ in het rechterdeelvenster in het veld **[!UICONTROL JSON Payload]** de gegevens die aan deze gebeurtenis worden toegevoegd.
1. Klik op **[!UICONTROL Keep Changes]**.

In het rechterdeelvenster kunt u een vrije JSON-payload toevoegen die gegevens toevoegt aan een SDK-gebeurtenis voordat de extensies die naar deze gebeurtenis luisteren deze horen.

In het volgende voorbeeld worden `poiCity` - en `poiName` -waarden toegevoegd aan **[!UICONTROL mboxparameters]** voor elke aanvraag die wordt verwerkt in de gebeurtenis Target. De waarden voor de nieuwe toetsen worden dynamisch bepaald door de SDK op het moment dat deze gebeurtenis plaatsvindt.

>[!TIP]
>
>Deze JSON-payload gebruikt een speciale notatie voor het `request` -object. In de oorspronkelijke gebeurtenis is `request` een array van anonieme objecten. Wanneer gegevens aan alle objecten in een array worden gekoppeld met behulp van Gegevens koppelen, zorgt de notatie `[*]` op een sleutel die een array bevat, ervoor dat de lading op alle objecten in die array wordt toegepast.
>
>De aantekening van `request[*]` kan luid als _voor elk voorwerp in de `request` serie_ worden gelezen.

![&#x200B; bepaal de actie &#x200B;](/help/assets/ad-setAction-target.png)

## 5. Sparen de Regel en herbouwt uw Bezit

Nadat u uw configuratie voltooit, verifieer dat uw Regel als het volgende beeld kijkt:

![&#x200B; voltooide regel &#x200B;](/help/assets/ad-ruleComplete-target.png)

1. Klikken **[!UICONTROL Save]**
1. Bouw uw bezit van de Lancering opnieuw en stel het aan het correcte Milieu op.
