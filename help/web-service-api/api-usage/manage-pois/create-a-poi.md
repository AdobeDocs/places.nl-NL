---
title: Een POI maken
description: Een POI maken met de REST-API's van Plaatsen.
exl-id: 0f5b5b40-11f0-4122-b3d5-c3853a6e8ca5
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 0%

---

# Een POI maken {#create-a-poi}

Een methode van de POST die u laat tot een POI leiden.

## Verzoek

```text
POST https://api-places.adobe.io/places/placesapi/v1/pois
```

## Kopteksten

```text
-H' Content-Type: application/json'  
-H 'Authorization: Bearer <TOKEN>'  
-H 'x-api-key: <API KEY>'  
-H 'x-gw-ims-org-id: <ORGID>'  
-H 'Accept-Language: en-US'
```

## Lichaam

```text
{
  "name": "string",
  "description": "string",
  "location": {
    "type": Point",
    "coordinates": [<LONGITUDE>, <LATITUDE>]
  },
  "radius": radius,
  "country": "string",
  "state": "string",
  "city": "string",
  "street": "string",
  "category": "string",
  "icon": "string",
  "color": "string",
  "metadata": {
          "brand": "string",
          "owndership": "string",
          "Color": "string"
  },
  "lib_id": "{libraryID}"
}
```

## Samplereactie

```text
{
    "id": "66e3c0fb-12fe-4af2-863e-16e0e777d777",
    "name": "New POI",
    "description": "18827",
    "location": {
        "type": "Point",
        "coordinates": [
            -123.000507,
            37.698029
        ]
    },
    "radius": 66,
    "country": "US",
    "state": "CA",
    "city": "Small City",
    "street": "1 Island Road",
    "category": "",
    "icon": "",
    "color": "",
    "metadata": {
        "ownership": "LS",
        "brand": "Island station"
    },
    "lib_id": "6efd87bc-c9c4-4ff3-9503-051bfbc81777"
}
```

## CURL, opdracht

Gebruik de volgende CURL-opdracht om deze API te testen:

```text
curl -X POST 'https://api-places.adobe.io/places/placesapi/v1/pois' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' -d '<SINGLEPOIDATA>' -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>Herinneren om te vervangen `<API KEY>`, `<TOKEN>`, &#39;,&#39; en `<SINGLEPOIDATA>` met werkelijke waarden.
