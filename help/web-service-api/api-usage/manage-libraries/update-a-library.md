---
title: Een bibliotheek bijwerken
description: Werk een bibliotheek bij met de REST-API van Plaatsen.
translation-type: tm+mt
source-git-commit: 8a84fe2dc5a0efe94ce3121e589524e3c7a80c5e

---


# Een bibliotheek bijwerken {#update-a-library}

Een PUT-methode waarmee u een bibliotheek kunt bijwerken.

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
>Vervang variabelen zoals `<lIBRARYID>`, `<API KEY>`, `<TOKEN>`en `<ORGID>` met werkelijke waarden.

