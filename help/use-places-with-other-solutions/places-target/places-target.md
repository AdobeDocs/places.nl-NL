---
title: Adobe Target
description: In deze sectie vindt u informatie over het gebruik van de Places Service bij Adobe Target.
exl-id: 6ee91fca-ea48-4de2-8dcf-87981813c678
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 7%

---

# Plaatsingsservice gebruiken voor Adobe Target {#places-target}

In dit document wordt ervan uitgegaan dat de extensie Plaatsen is geïmplementeerd in de toepassing. Als u hulp nodig hebt bij het implementeren van de extensie Plaatsen, raadpleegt u [Extensies plaatsen](/help/places-ext-aep-sdks/places-extension/places-extension.md).

Nadat de extensie Plaatsen gebeurtenissen voor entry en exits verzendt, kunt u regels in Launch gebruiken om de gegevens van de Plaatsingsservice aan uw Adobe Target SDK-gebeurtenissen toe te voegen. Als de gewenste eigenschap is geselecteerd in Launch, kunt u dit type regel maken door de volgende taken uit te voeren:

## 1. Een regel maken

1. Op de **[!UICONTROL Rules]** tabblad, klikt u op **[!UICONTROL Create New Rule]**.

   De volgende informatie onthouden:

   * Als u geen bestaande regels voor deze eigenschap hebt, bevindt de knop zich in het midden van het scherm.
   * Als uw eigenschap regels heeft, bevindt de knop zich rechtsboven in het scherm.

## 2. Selecteer een gebeurtenis

1. Geef uw regel een betekenisvolle naam zodat deze gemakkelijk herkenbaar is in uw lijst met regels.

   In dit voorbeeld krijgt de regel de naam **[!UICONTROL Attach Places Service Data to Target Content Requested]**.

1. Onder de **[!UICONTROL Events]** sectie, klikt u op **[!UICONTROL Add]**.
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Extension]** de optie **[!UICONTROL Adobe Target]**.
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Event Type]** de optie **[!UICONTROL Content Requested]**.
1. Klik op **[!UICONTROL Keep Changes]**.

![een gebeurtenis toevoegen](/help/assets/ad-setEvent_target.png)

## 3. Voorwaarden toevoegen

>[!IMPORTANT]
>
>Voltooi deze stap als u Voorwaarden aan uw regel wilt toevoegen. Anders gaat u naar de *De handeling definiëren* hieronder.

In het volgende voorbeeld wordt een voorwaarde gemaakt die ervoor zorgt dat de regel alleen wordt geactiveerd voor gebruikers die de app vijf of meer keren hebben gestart.

1. Onder de **[!UICONTROL Conditions]** sectie, klikt u op **[!UICONTROL Add]**.
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Extension]** de optie **[!UICONTROL Mobile Core]**.
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Condition Type]** de optie **[!UICONTROL Launches]**.
1. Wijzig in het rechterdeelvenster de vervolgkeuzelijst en de nummerbesturingselementen, zodat de voorwaarde wordt gelezen **[!UICONTROL User has launched the app greater than or equal to 5 times]**.
1. Klik op **[!UICONTROL Keep Changes]**.

![een voorwaarde toevoegen](/help/assets/ad-setCondition_target.png)

## 4. De handeling definiëren

1. Onder de **[!UICONTROL Actions]** sectie, klikt u op **[!UICONTROL Add]**.
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Extension]** de optie **[!UICONTROL Mobile Core]**.
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Action Type]** de optie **[!UICONTROL Attach Data]**.
1. In het rechterdeelvenster, in het dialoogvenster **[!UICONTROL JSON Payload]** Typ de gegevens die aan deze gebeurtenis worden toegevoegd.
1. Klik op **[!UICONTROL Keep Changes]**.

In het rechterdeelvenster kunt u een vrije JSON-payload toevoegen die gegevens toevoegt aan een SDK-gebeurtenis voordat de extensies die naar deze gebeurtenis luisteren deze horen.

In het volgende voorbeeld: `poiCity` en `poiName` waarden worden toegevoegd aan de **[!UICONTROL mboxparameters]** voor elke aanvraag die in de gebeurtenis Target wordt verwerkt. De waarden voor de nieuwe toetsen worden dynamisch bepaald door de SDK op het moment dat deze gebeurtenis plaatsvindt.

>[!TIP]
>
>Deze JSON-lading gebruikt een speciale notatie voor de `request` object. In het oorspronkelijke geval: `request` is een array van anonieme objecten. Wanneer gegevens aan alle objecten in een array worden gekoppeld met de opdracht Gegevens koppelen, wordt `[*]` notatie op een sleutel waarvan bekend is dat deze een array bevat, zorgt ervoor dat de payload wordt toegepast op alle objecten in die array.
>
>De notatie van `request[*]` hardop kunnen worden voorgelezen _voor elk object in het dialoogvenster `request` array_.

![de handeling definiëren](/help/assets/ad-setAction-target.png)

## 5. Sparen de Regel en herbouwt uw Bezit

Nadat u uw configuratie voltooit, verifieer dat uw Regel als het volgende beeld kijkt:

![voltooide regel](/help/assets/ad-ruleComplete-target.png)

1. Klik op **[!UICONTROL Save]**
1. Bouw uw bezit van de Lancering opnieuw en stel het aan het correcte Milieu op.
