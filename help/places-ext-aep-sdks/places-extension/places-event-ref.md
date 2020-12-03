---
title: Referentie van gebeurtenis Plaatsen
description: 'Een lijst met de gebeurtenissen die door de extensie Plaatsen worden afgehandeld. '
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 6%

---


# Referentie van gebeurtenis Plaatsen {#places-event-reference}

Hier volgt een lijst met de gebeurtenissen die worden afgehandeld door de extensie Plaatsen.

## GetCurrentPointsOfInterest

**Gebeurtenisdetails**

| Type | Bron | Naam | Gepauzeerd |
| :--- | :--- | :--- | :--- |
| PLAATSEN | REQUEST_CONTENT | `requestgetuserwithinplaces` | Waar |

**Gebeurtenisbeschrijving**

Deze gebeurtenis is een verzoek om POIs terug te winnen waarin het apparaat momenteel wordt gevestigd.

**Gegevenstaakdefinitie**

n.v.t.

## GetNearbyPointsOfInterest

**Gebeurtenisdetails**

| Type | Bron | Naam | Gepauzeerd |
| :--- | :--- | :--- | :--- |
| PLAATSEN | REQUEST_CONTENT | `requestgetnearbyplaces` | Waar |

**Gebeurtenisbeschrijving**

Deze gebeurtenis is een verzoek om de nabijgelegen POIs te krijgen door rekening te houden met de huidige apparatenplaats en de gevormde bibliotheken van Plaatsen.

**Gegevenstaakdefinitie**

| Sleutel | Type waarde | Vereist | Standaardwaarde | Beschrijving |
| :--- | :--- | :--- | :--- | :--- |
| breedtegraad | double | true | n.v.t. | Houdt de breedtewaarde voor het centrum van het onderzoek naar nabijgelegen POIs. |
| lengtegraad | double | true | n.v.t. | Houdt de lengtewaarde voor het centrum van het onderzoek naar nabijgelegen POIs. |
| radius | integer | false | n.v.t. | Straal, in meters, gebruikt bij het zoeken naar nabijgelegen POI&#39;s. |
| count | integer | false | 10 | Maximum aantal POI&#39;s dat moet worden geretourneerd in resulterende responsgebeurtenis. |

## ProcessRegionEvent

**Gebeurtenisdetails**

| Type | Bron | Naam | Gepauzeerd |
| :--- | :--- | :--- | :--- |
| PLAATSEN | REQUEST_CONTENT | `requestprocessregionevent` | Onwaar |

**Gebeurtenisbeschrijving**

Deze gebeurtenis zorgt ervoor dat de extensie Plaatsen een gebeurtenis voor een geofence-item of -uitgang verwerkt.

**Gegevenstaakdefinitie**

| Sleutel | Type waarde | Vereist | Beschrijving |
| :--- | :--- | :--- | :--- |
| geregisteerd | string | true | Id van het gebied dat de gebeurtenis genereert. |
| regioneventtype | int | true | Type regionale gebeurtenis die wordt gegenereerd. 1 voor binnenkomst en 2 voor vertrek. |

## Gebeurtenissen verzonden door de extensie Plaatsen

Deze informatie is momenteel in uitvoering.

