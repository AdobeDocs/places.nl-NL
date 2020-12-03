---
title: Bestaande POI's beheren
description: In de UI van de Dienst van Plaatsen, kunt u bestaande POIs uitgeven, schrappen of filtreren.
translation-type: tm+mt
source-git-commit: 5a21e734c0ef56c815389a9f08b445bedaae557a
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 6%

---


# Bestaande POI&#39;s beheren {#managing-existing-pois}

Met behulp van de interface Plaatsen worden POI&#39;s en bibliotheken gemaakt en beheerd in de database Plaatsen.

## Een POI bewerken

1. Meld u met uw Adobe ID aan bij Plaatsen.
1. Meld u met uw Adobe ID aan bij de service Plaatsen.
1. Klik in de rechterbovenhoek op het pictogram dat eruitziet als een lijst met opsommingstekens.
1. Zoek de POI die u wilt bewerken.
1. Klik op **[!UICONTROL ...]** en selecteer **[!UICONTROL View Details]**.
1. Werk de gegevens bij en klik op **[!UICONTROL Save]**.

## Een POI verwijderen

1. Meld u met uw Adobe ID aan bij Plaatsen.
1. Meld u met uw Adobe ID aan bij de service Plaatsen.
1. Klik in de rechterbovenhoek op het pictogram dat eruitziet als een lijst met opsommingstekens.
1. Zoek de POI die u wilt verwijderen.
1. Klik op **[!UICONTROL ...]** en selecteer **[!UICONTROL Delete]**.

## POI&#39;s filteren op plaats, staat, land of metagegevens

![een POI filteren](/help/assets/filter_poi.png)

1. Meld u met uw Adobe ID aan bij de gebruikersinterface van de Plaatsingsservice.
1. Klik in de rechterbovenhoek op het filterpictogram.
1. U kunt POI&#39;s op een van de volgende manieren filteren:

   * Op bibliotheek:

      a. Selecteer een bibliotheek.

   * Op eigenschap:

      a. Selecteer **[!UICONTROL Country]**, **[!UICONTROL State]** of **[!UICONTROL City]** in de vervolgkeuzelijst Eigenschap.

      b. Voer in de volgende regel een waarde in.

      U kunt bijvoorbeeld selecteren **[!UICONTROL State]** en typen **[!UICONTROL California]**.

   * Met metagegevens:

      a. Voer een sleutel en waarde in.

## Een geofence POI definiëren

Geofences zijn een type POI en worden in de database gedefinieerd op basis van de volgende toetsen:

| Toetsen | Beschrijving | Vereist? |
| :--- | :--- | :--- |
| Id | Unieke id toegewezen aan elke POI | Ja |
| Naam | Vriendelijke naam gegeven aan de POI. | Ja |
| Bibliotheek | Elke POI moet een bibliotheek voor organisatie worden toegewezen. | Ja |
| Straal | De straal voor uw POI in meters. | Ja |
| Pictogram | Hulp bij visualisaties van de POI&#39;s. | Ja (standaard toegewezen) |
| Kleur | Hulp bij visualisaties van de POI&#39;s. | Ja (standaard toegewezen) |
| Categorie | Wijs een gemeenschappelijk kader van categorieën toe die over alle POIs in alle bibliotheken gemeenschappelijk zijn. | Nee |
| Adres | Straatadres. | Nee |
| Plaats | Stad van de POI. | Nee |
| Staat/regio | Staat of regio van de POI. | Nee |
| Land | Land van de PO. | Nee |
| Breedtegraad | Latitude-coördinaat voor het midden van de POI. | Ja |
| Lengtegraad | Longitudecoördinaat voor het midden van de POI. | Ja |
| Metagegevens | Aangepaste sleutel- en waardeparen die aan POI&#39;s kunnen worden toegewezen. Deze meta-gegevens stroomlijnt toekomstige werkschema&#39;s door u toe te staan om POIs over bibliotheken voor elk te groeperen om regels en filters in stroomafwaartse werkschema&#39;s te gebruiken zoals verzendt een dupbericht wanneer iemand POI met Type = Concurrent ingaat. | Nee |
