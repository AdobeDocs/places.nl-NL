---
title: De rang van een bibliotheek ophalen
description: U krijgt de rang van een bibliotheek met de REST-API van Plaatsen.
exl-id: c0abedd0-5ff4-4a01-9f8d-e3d17ea53a97
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '41'
ht-degree: 0%

---

# De rang van een bibliotheek ophalen {#get-library-rank}

Een methode van de GET die u toestaat om bibliotheken te rangschikken.

## Verzoek

`GET https://api-places.adobe.io/places/placesapi/v1/libraries/rank`

## Kopteksten

```
-H Content-Type: application/JSON  
-H 'Authorization: Bearer <TOKEN>'  
-H 'x-api-key: <API KEY>'  
-H 'x-gw-ims-org-id: <ORGID>'  
-H 'Accept-Language: en-US'
```

## Monsterreactie

```
{"library_rank_order":["ea45781f-26af-44b1-b4f8-43baf5f0fe28","dfcc5270-1d6d-4bc9-9cd9-85ecd5ebc12b"]}
```

## CURL, opdracht

```
curl -X GET 'https://api-places.adobe.io/places/placesapi/v1/libraries/rank ' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>Variabelen zoals `<API KEY>`, `<TOKEN>`, en `<ORGID>` met werkelijke waarden.
