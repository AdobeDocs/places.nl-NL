---
title: Meerdere POI's verwijderen
description: Gebruik de batch-API's om meerdere POI's te verwijderen.
exl-id: f170b722-e6f4-42a2-b3a6-1bf56965eb17
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '56'
ht-degree: 0%

---

# Meerdere POI&#39;s verwijderen {#delete-multiple-pois}

Een methode van de POST die u veelvoudige POIs laat schrappen.

## Verzoek

```text
POST https://api-places.adobe.io/places/placesapi/v1/pois/batchDelete
```

## Kopteksten

```text
-H' Content-Type: application/json'  -H 'Authorization: Bearer <TOKEN>'  -H 'x-api-key: <API KEY>'  -H 'x-gw-ims-org-id: <ORGID>'  -H 'Accept-Language: en-US'
```

## Lichaam

```text
{  "ids": [    "<POIID>",    "<POIID>",    .    .    .    "<POIID>",    "<POIID>"  ]}
```

## Samplereactie

```text
If successful a Status of "204 No Content" is returned.
```

## CURL, opdracht

Gebruik de volgende CURL-opdracht om deze API te testen:

```text
curl -X POST 'https://api-places.adobe.io/places/placesapi/v1/pois/batchDelete' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>' --data-binary "@<PATHTOBATCHDELETEJSONFILE>" -H "Content-Type: application/json"
```

>[!IMPORTANT]
>
>Vervangen `<API KEY>`, `<TOKEN>`, `<ORGID>`, en `<PATHTOBATCHDELETEJSONFILE>` met echte waarden.

## Voorbeeld-JSON-bestand

Hier volgt het JSON-voorbeeldbestand voor het `batchDelete` API:

```text
{​"ids":["31a49d5c-c6ad-46ae-b88d-a6912a8a6b2f","6a78a729-7973-4373-9199-36da18cc5b8c","74eaa3da-2464-4298-9b6d-5376fa7ea00f"]​}
```
