---
title: De rang van een bibliotheek ophalen
description: U krijgt de rang van een bibliotheek met de REST-API van Plaatsen.
translation-type: tm+mt
source-git-commit: 8a84fe2dc5a0efe94ce3121e589524e3c7a80c5e

---


# De rang van een bibliotheek ophalen {#get-library-rank}

Een GET methode waarmee u bibliotheken kunt rangschikken.

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
>Vervang variabelen zoals `<API KEY>`, `<TOKEN>`en `<ORGID>` met werkelijke waarden.

