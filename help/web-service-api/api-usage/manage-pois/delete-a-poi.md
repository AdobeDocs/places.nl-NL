---
title: Een POI verwijderen
description: Verwijder een POI met de REST-API's van Plaatsen.
translation-type: tm+mt
source-git-commit: 8a84fe2dc5a0efe94ce3121e589524e3c7a80c5e
workflow-type: tm+mt
source-wordcount: '44'
ht-degree: 0%

---


# Een POI verwijderen {#delete-a-poi}

Een methode van DELETE waarmee u een POI kunt schrappen.

## Verzoek

```text
DELETE https://api-places.adobe.io/places/placesapi/v1/pois/<POIID>
```

## Kopteksten

```text
-H' Content-Type: application/json'  
-H 'Authorization: Bearer <TOKEN>'  
-H 'x-api-key: <API KEY>'  
-H 'x-gw-ims-org-id: <ORGID>'  
-H 'Accept-Language: en-US'
```

## Samplereactie

```text
If successful a Status of "204 No Content" is returned.
```

## CURL, opdracht

Gebruik de volgende CURL-opdracht om de API te testen:

```text
curl -X DELETE 'https://api-places.adobe.io/places/placesapi/v1/pois/<POIID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>Vervang `<POIID>`, `<API KEY>`, `<TOKEN>`en `<ORGID>` met werkelijke waarden.

