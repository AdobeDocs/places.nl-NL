---
title: Een bibliotheek verwijderen
description: Verwijder een bibliotheek met de REST-API's van Plaatsen.
exl-id: ad45ea38-9e12-43d7-b05f-17d3e40abaf5
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 0%

---

# Een bibliotheek verwijderen {#delete-a-library}

Een methode van DELETE waarmee u een bibliotheek kunt verwijderen.

## Verzoek

```text
DELETE https://api-places.adobe.io/places/placesapi/v1/libraries/<lIBRARYID>
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

Gebruik de volgende CURL-opdracht om deze API te testen:

```text
curl -X DELETE 'https://api-places.adobe.io/places/placesapi/v1/libraries/<LIBRARYID>' -H 'x-api-key: <API KEY>' -H 'Authorization: Bearer <TOKEN>' -H 'x-gw-ims-org-id: <ORGID>'
```

>[!IMPORTANT]
>
>Variabelen zoals `<lIBRARYID>`, `<API KEY>`, `<TOKEN>`, en `<ORGID>`met werkelijke waarden.
