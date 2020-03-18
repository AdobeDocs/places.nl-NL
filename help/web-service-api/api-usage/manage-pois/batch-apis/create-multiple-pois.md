---
title: Meerdere POI's maken
description: Gebruik de batch-API's om meerdere POI's te maken.
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Meerdere POI&#39;s maken {#create-multiple-pois}

Een POST-methode waarmee u meerdere POI&#39;s kunt maken.

## Verzoek

```text
POST https://api-places.adobe.io/places/placesapi/v1/pois/batchCreate
```

## Kopteksten

```text
-H' Content-Type: application/json'  -H 'Authorization: Bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## Lichaam

```text
{    "createPOIRequests": [        {            "lib_id": "<lIBRARYID>",            "name": "string",            "description": "string",            "location": {                "type": "Point",                "coordinates": [<LONGITUDE>, <LATITUDE>]            },            "radius": integer,            "country": "string",            "state": "string",            "city": "string",            "street": "string",            "category": "string",            "icon": "string",            "color": "string",            "metadata": {                "ownership": "string",                "brand": "string"            }        },        {            "lib_id": "<lIBRARYID>",            "name": "string",            "description": "string",            "location": {                "type": "Point",                "coordinates": [<LONGITUDE>, <LATITUDE>]            },            "radius": integer,            "country": "string",            "state": "string",            "city": "string",            "street": "string",            "category": "string",            "icon": "string",            "color": "string",            "metadata": {                "ownership": "string",                "brand": "string"            }        },        .        .        .        {            "lib_id": "<lIBRARYID>",            "name": "string",            "description": "string",            "location": {                "type": "Point",                "coordinates": [<LONGITUDE>, <LATITUDE>]            },            "radius": integer,            "country": "string",            "state": "string",            "city": "string",            "street": "string",            "category": "string",            "icon": "string",            "color": "string",            "metadata": {                "ownership": "string",                "brand": "string"            }        },        {            "lib_id": "<lIBRARYID>",            "name": "string",            "description": "string",            "location": {                "type": "Point",                "coordinates": [<LONGITUDE>, <LATITUDE>]            },            "radius": integer,            "country": "string",            "state": "string",            "city": "string",            "street": "string",            "category": "string",            "icon": "string",            "color": "string",            "metadata": {                "ownership": "string",                "brand": "string"            }        }    ]}
```

## Samplereactie

```text
{    "ids": [        "558360b5-5b4b-4c8a-777f-5e3f4b60e4cb",        "ac01c21c-6274-4922-86d5-7777b59dc9b0",        .        .        .        "acf0fde0-22ee-470a-bfa9-b760777cefdc",        "d3cf8338-520f-49a5-8ee7-3777df69be91"    ],    "_links": {        "pois": {            "href": "https://api-places-dev.adobe.io/places/placesapi/v1/pois/{poi_id}",            "templated": true        }    }}
```

## CURL, opdracht

Gebruik de volgende CURL-opdracht om deze API te testen:

```text
curl -X POST 'https://api-places.adobe.io/places/placesapi/v1/pois/batchCreate' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' --data-binary "@<PATHTOBATCHCREATEJSONFILE>" -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>Vervang `<API KEY>`, `<TOKEN>`, `<ORGID>`en `<PATHTOBATCHCREATEJSONFILE>` met echte waarden.

## Voorbeeld-JSON-bestand

Hier volgt het voorbeeld van het JSON-bestand voor de `batchCreate` API:

```text
{    "createPOIRequests": [{            "name": "Sample POI 1",            "description": "1",            "location": {                "type": "Point",                "coordinates": [0.0, 0.0]            },            "radius": 25,            "country": "Ghana",            "state": "Ghana",            "city": "Accra",            "street": "",            "category": "cafe",            "icon": "nice",            "color": "red",            "metadata": {                "region": "Equator"            },            "lib_id" : "42b4d03c-672c-4deb-83e0-134ef070c2af"        },        {            "name": "Sample POI 2",            "description": "2",            "location": {                "type": "Point",                "coordinates": [0.025, 0.025]            },            "radius": 50,            "country": "Ghana",            "state": "Ghana",            "city": "Accra",            "street": "",            "category": "cafe",            "icon": "nice",            "color": "blue",            "metadata": {                "region": "Equator"            },            "lib_id" : "42b4d03c-672c-4deb-83e0-134ef070c2af"        },        {            "name": "Sample POI 3",            "description": "3",            "location": {                "type": "Point",                "coordinates": [0.05, 0.05]            },            "radius": 100,            "country": "Ghana",            "state": "Ghana",            "city": "Accra",            "street": "",            "category": "cafe",            "icon": "nice",            "color": "green",            "metadata": {                "region": "Equator"            },            "lib_id" : "42b4d03c-672c-4deb-83e0-134ef070c2af"        }    ]}
```
