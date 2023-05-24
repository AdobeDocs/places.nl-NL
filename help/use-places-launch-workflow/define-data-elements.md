---
title: Gegevenselementen definiëren
description: Deze sectie biedt informatie over het maken, gebruiken en publiceren van gegevenselementen in Experience Platform Launch voor Plaatsen.
exl-id: 57e88a37-0b0b-4064-ab72-382a36a0d01d
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 1%

---

# Een gegevenselement definiëren {#define-data-elements}

Aan de hand van de volgende informatie krijgt u inzicht in gegevenselementen en hoe u deze kunt maken en publiceren.

## Informatie over gegevenselementen

Gegevenselementen zijn de bouwstenen voor het gegevenswoordenboek van de toepassing en worden gebruikt om gegevens te verzamelen, te organiseren en te leveren over marketing en advertentietechnologie.

Een gegevenselement is een variabele waarbij de waarde kan worden toegewezen aan een bezoeker-id, een carriernaam, een advertentie-id, een pushid enzovoort. In Experience Platform Launch, kunt u deze waarde door zijn veranderlijke naam van verwijzingen voorzien. Deze verzameling gegevenselementen wordt het woordenboek van gedefinieerde gegevens dat u kunt gebruiken om uw regels (gebeurtenissen, voorwaarden en handelingen) samen te stellen. Dit woordenboek wordt in het hele Experience Platform Launch gedeeld waar het kan worden gebruikt met elke extensie in uw eigenschap.

Met de extensie Plaatsen kunt u naar waarden verwijzen vanuit de volgende doelen:

* Huidige POI, die verwijst naar de POI waarin uw klant zich momenteel bevindt.

   Als de gebruiker in veelvoudige POIs wordt gevestigd, behoort één tot de bibliotheek met hogere rang wordt gekozen. Als meerdere POI&#39;s tot de bibliotheek met de hoogste rang behoren, wordt de POI met de kleinste straal gekozen.
* Laatst afgesloten POI, die verwijst naar de meest recente POI die de gebruiker heeft verlaten.
* Laatst ingevoerde POI, die verwijst naar de meest recente POI die de gebruiker heeft ingevoerd.

Elke POI bevat de volgende gegevensverwijzingen:

* **[!UICONTROL Category]**: categorie van de POI
* **[!UICONTROL City]**: de stad POI
* **[!UICONTROL Country]**: land van de POI
* **[!UICONTROL Latitude]**: breedtegraad van de POI
* **[!UICONTROL Longitude]**: lengtegraad van de POI
* **[!UICONTROL Metadata]**: aangepaste metagegevens van de POI
* **[!UICONTROL Name]**: naam van de POI
* **[!UICONTROL Radius]**: straal van de POI
* **[!UICONTROL Region ID]**: Id van de POI
* **[!UICONTROL Region/State]**: regio, provincie of staat van de POI

### Een data-element maken

1. Klik op de pagina Eigenschappen voor uw app op de knop **[!UICONTROL Data Elements]** tab.

1. Klik op **[!UICONTROL Create New Data Element]**.

1. Zoek in de lijst met geïnstalleerde extensies naar **[!UICONTROL Places]**.

1. In de **[!UICONTROL Data Element Type]** Selecteer een gegevensverwijzing voor dit gegevenselement in de vervolgkeuzelijst.

1. Selecteer een POI-doel.

1. Als dit gegevenselement een aangepaste metagegevensverwijzing is, selecteert u een metagegevenssleutel.

1. Typ een naam voor het gegevenselement en klik op **[!UICONTROL Save]**.

   ![Gegevenselement maken](/help/assets/create-de-7-v3.png)


## Een gegevenselement gebruiken

Nadat een gegevenselement wordt gecreeerd, als een plukker van het gegevenselement aanwezig is, kunt u het gegevenselement van om het even welke regelcomponent gebruiken.

![Het gegevenselement gebruiken](/help/assets/use-de-v2.png)

Als een plukker van gegevenselement niet in de regelcomponent aanwezig is, kunt u het gegevenselement gebruiken door de naam van het gegevenselement met te verpakken **[!UICONTROL %%]** tokens.
Als de naam van het gegevenselement bijvoorbeeld **[!UICONTROL Last POI City]** kunt u toevoegen **[!UICONTROL LAST POI City]** naar een tekstinvoer.


## Gegevenselementen publiceren

Als gegevenselementen in om het even welke regelcomponenten worden gebruikt, moeten deze gegevenselementen ook in de bibliotheek worden omvat en worden gepubliceerd.
