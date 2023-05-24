---
title: Een bibliotheek bijwerken
description: Werk een bibliotheek bij met de REST-API van Plaatsen.
exl-id: 37ca2be2-39e1-4f8e-87c2-ef4cb366db0d
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '48'
ht-degree: 0%

---

# Een bibliotheek bijwerken {#update-a-library}

Een methode van de PUT waarmee u een bibliotheek kunt bijwerken.

## Verzoek

```text
PUT https://api-places.adobe.io/places/placesapi/v1/libraries/<lIBRARYID>
```

## Kopteksten

```text
-H' Content-Type: application/json'  -H 'Authorization: bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## Lichaam

```text
{"name": "<NEW_LIBRARY_NAME>"}
```

## Samplereactie

```text
{       "id": "449f08f3-eff5-4658-9329-2d9687af777e",       "name": "Really facinating places",      "customerID": "777F20F55BACA09E0A495D8F@AdobeOrg",       "poiCount": 0  }
```

## CURL, opdracht

Gebruik de volgende CURL-opdracht om deze API te testen:

```text
curl -X PUT 'https://api-places.adobe.io/places/placesapi/v1/libraries/<LIBRARYID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' -d '{"name":"Updated Library Name"}' -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>Variabelen zoals `<lIBRARYID>`, `<API KEY>`, `<TOKEN>`, en `<ORGID>` met werkelijke waarden.
