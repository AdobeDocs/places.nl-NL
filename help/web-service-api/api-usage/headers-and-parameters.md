---
title: Kopteksten en parameters
description: Kopballen en parameters die in de REST APIs van de Dienst van Plaatsen beschikbaar zijn.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 3%

---


# Headers and parameters {#headers-and-parameters}

Hier zijn de details over de kopballen en de parameters die in de REST API van de Dienst van Plaatsen beschikbaar zijn:

## Ondersteunde koppen

| Koptekst | Beschrijving | Methode | Voorbeeld |
| :--- | :--- | :--- | :--- |
| `Authorization` | Uw token voor toonder | Alle |  |
| `x-api-key` | Uw API-sleutel | Alle | `19776964b4cde49e08d8f62e5824f777b` |
| `x-gw-ims-org-id` | Uw org-id | Alle | `18FB61145BAC2FFB0A494777@AdobeOrg` |
| `Content-Type` | Indeling van verzonden of ontvangen inhoud | PUT, POST | `application/json` |
| `Accept-Language` | Taal voor foutberichten | Optioneel | `en-US` |

## Bibliotheekparameters

| Parameter | Beschrijving | Type | Limiet | Verzoek of antwoord | Voorbeeld |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `id` | ID van bibliotheek | toegewezen | n.v.t. | Antwoord | `"id": "b2488788-2d2a-462b-b1a2-305272777dda"` |
| `name` | Naam van de bibliotheek | string | 256 tekens | beide, op verzoek vereist | `"name": "Amazing Places"` |
| `orgID` | Ervaar cloud orgID van de organisatie | toegewezen | n.v.t. | Antwoord | `"orgID": "777F20F55BACA09E0A495D8F@AdobeOrg"` |
| `poiCount` | Aantal POI&#39;s in bibliotheek | integer | max. 150.000 | Antwoord | `"poiCount": 25149` |
| `metadataDescriptors` | Aantal voor elk uniek sleutelwaardepaar voor POI-metagegevens | gemengd | n.v.t. | Antwoord |  |
| `poiCountInCities` | Tellen voor elke unieke waarde voor de plaats van de POI | gemengd | n.v.t. | Antwoord |  |

## POI-parameters

| Parameter | Beschrijving | Type | Limiet | Verzoek of antwoord | Voorbeeld |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `data` | Poi-gegevens | Array met POI-details | n.v.t. | beide |  |
| `id` | ID van POI | toegewezen | n.v.t. | reactie | `"id": "1455462b-7f9c-4220-9f42-5bbce777a0d1"` |
| `name` | Naam van de POI | string | 512 tekens | beide, optioneel\* | `"name": "My Favorite Place"` |
| `description` | Beschrijving van de POI | string | 512 tekens | beide, optioneel\* | `"description": "This is a very good place."` |
| `location` | Array van type en coördinaten van POI | array (gemengd) | n.v.t. | beide | `"location": {"type": "Point", "coordinates": [-122.201007, 37.604713]` |
| `type` | Type POI | string | alleen Punt wordt momenteel ondersteund | beide, op verzoek vereist | `"type": "Point"` |
| `coordinates` | Array van lengte- en breedtegraad van POI | array (zwevend) | lengtegraad: -180 tot 180, latitude -85 tot 85 | beide, op verzoek vereist | `"coordinates": [-122.201007, 37.604713]` |
| `radius` | Grootte van de cirkelvormige geofentie rond de POI | zweven | 10-2000 meter | beide, op verzoek vereist | `"radius": 100` |
| `country` | Land van de PO | string | 32 tekens | beide, optioneel* | `"country": "United States"` |
| `state` | Staat voor de POI | string | 32 tekens | beide, optioneel* | `"state": "California"` |
| `city` | Plaats voor de POI | string | 32 tekens | beide, optioneel* | `"city": "San Jose"` |
| `street` | Straatadres voor de POI | string | 256 tekens | beide, optioneel* | `"street": "122 Woz Way"` |
| `category` | Categorie voor de POI | string | 100 tekens | beide, optioneel* | `"category": "cafe"` |
| `icon` | Pictogram voor de POI | string | 50 tekens | beide, optioneel* | `"icon": "star"` |
| `color` | Kleur voor de POI | string | 8 tekens | beide, optioneel* | `"color": "blue"` |
| `metadata` | Array van sleutel-/waardeparen voor de POI | array(tekenreeks) | toets: 256 tekens, waarde: 256 tekens, maximaal 10 paren | beide, optioneel* | `"metadata": {"region": "Equator"}` |
| `lib_id` | ID van de bibliotheek waarin de POI zich bevindt | n.v.t. | n.v.t. | beide, vereist | `"lib_id": "ac7a0b25-c6c2-43ba-bbc6-2b1777b80fe9"` |

* Als de parameterwaarde niet is opgenomen, wordt de waarde ingesteld op `empty` in de database. Als het bestaande sleutel/waardepaar niet inbegrepen is, wordt het sleutel/waardepaar verwijderd voor die POI in het gegevensbestand.

