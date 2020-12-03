---
title: Een bibliotheek maken
description: Maak een bibliotheek met de REST-API van Plaatsen.
translation-type: tm+mt
source-git-commit: 8a84fe2dc5a0efe94ce3121e589524e3c7a80c5e
workflow-type: tm+mt
source-wordcount: '48'
ht-degree: 0%

---


# Een bibliotheek maken {#create-a-library}

Een methode van de POST waarmee u een bibliotheek kunt creëren.

## Verzoek

```text
POST https://api-places.adobe.io/places/placesapi/v1/libraries
```

## Kopteksten

```text
-H' Content-Type: application/json'  -H 'Authorization: Bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## Lichaam

```text
{"name": "<LIBRARY_NAME>"}
```

## Samplereactie

```text
{       "id": "449f08f3-eff5-4658-9329-2d9687af777e",       "name": "Facinating places",      "customerID": "777F20F55BACA09E0A495D8F@AdobeOrg",       "poiCount": 0  }
```

## CURL, opdracht

Gebruik de volgende CURL-opdracht om deze API te testen:

```text
curl -X POST 'https://api-places.adobe.io/places/placesapi/v1/libraries' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' -d '{"name":"New Library Name"}' -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>Vervang variabelen zoals `<API KEY>`, `<TOKEN>`en `<ORGID>` met werkelijke waarden.

