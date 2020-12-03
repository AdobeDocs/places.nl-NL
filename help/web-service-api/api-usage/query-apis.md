---
title: Overzicht
description: Inzicht in en gebruik van Query API's.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---



# Query-API&#39;s

Een methode van de GET die u toestaat om POIs te vragen die aan de bezoeker het dichtst zijn.

## Verzoek

```text
GET https://query.places.adobe.com/placesedgequery
```

Met de volgende input, keert de dienst een lijst van POIs terug die aan de bezoeker het dichtst zijn:

* De positie van de aanroeper (breedte, lengte).
* De id&#39;s van de POI-bibliotheken die in de zoekopdracht moeten worden opgenomen.
* Het maximumaantal te retourneren POI&#39;s.  De standaardwaarde is 100.

   De afstand tussen de bezoeker en POI wordt gedefinieerd als de afstand van de bezoeker tot de rand van de geofence van POI. In de reactie, zal POIs die de bezoeker bevatten duidelijk zijn zoals hebbend de bezoeker.

Argumenten worden opgegeven als de volgende queryparameters:

* (**Vereist**) `latitude`

   De breedtegraad van de aanroeper, die tussen -85 en 85 moet liggen.
* (**Vereist**) `longitude`

   De lengtegraad van de aanroeper, die tussen -180 en 180 moet zijn.

* (**Optional**) `limit`

   Het maximumaantal te retourneren POI&#39;s.

* (**Vereist**) `library`

   De id van de bibliotheek waarnaar moet worden gezocht. Om veelvoudige bibliotheken te vragen, zorg ervoor dat u veelvoudige exemplaren van de bibliotheekparameter in de vraag omvat.

Hier volgt een voorbeeld van de JSON-indeling die met succes is geretourneerd:

```markup
{
    "places": {
        "userWithin": [
            {
                "p": [
                    "poi id",
                    "poi name",
                    "poi center's latitude",
                    "poi center's longitude",
                    poiRadius,
                    rank
                ],
                "x": {
                    "country": "US",
                    "city": "Fremont",
                    "street": "Vineyard Heights",
                    "Color": "Blue",
                    "state": "CA",
                    <other POI metadata>
                }
            }
        ],
        "pois": [
            {
                "p": [
                    "poi id",
                    "poi name",
                    "poi center's latitude",
                    "poi center's longitude",
                    poiRadius,
                    rank
                ],
                "x": {
                    "country": "US",
                    "city": "Milpitas",
                    "street": null,
                    "state": "CA"
                }
            },
            {
                "p": [
                    "poi id",
                    "poi name",
                    "poi center's latitude",
                    "poi center's longitude",
                    poiRadius,
                    rank
                ],
                "x": {
                    "country": "US",
                    "city": "Fremont",
                    "street": null,
                    "state": "CA"
                }
            }
        ]
    }
}
```

De POIs onder `places.pois` worden gesorteerd door afstand van bezoeker aan de rand van POIs. POIs onder `places.userWithin` bevat de bezoeker, en deze POIs worden bevolen door rang en dan door straal te verhogen.

## Voorbeeld

Hier is een voorbeeld van de vraag:

```text
GET https://query.places.adobe.com/placesedgequery?latitude=<userLatitude>&longitude=<userLongitude>&library=<libID1>&library=<libID2>&limit=20
```
