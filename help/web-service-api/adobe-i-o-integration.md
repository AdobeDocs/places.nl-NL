---
title: Overzicht van Adobe I/O-integratie
description: Informatie over het maken van een Adobe I/O-integratie.
exl-id: d7d31938-6c0e-40f8-a9d3-30af96043119
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 6%

---

# Overzicht van integratie en voorwaarden {#integration-prereqs}

Deze informatie toont u hoe te om een Adobe I/O en een integratie van de Dienst van Plaatsen tot stand te brengen.

## Vereisten voor gebruikerstoegang

Verifieer met de beheerder van het Systeem van uw organisatie dat de volgende taken zijn voltooid:

* Plaatst de Dienst van de Kern verschijnt in de admin console van uw organisatie.
* U bent toegevoegd aan de organisatie.
* U bent toegevoegd als Gebruiker aan de Dienst van de Kern van Plaatsen in uw organisatie.

   Zie voor meer informatie *Een gebruiker of ontwikkelaar toevoegen aan de service- en Experience Platform Launch-profielen Plaatsen* in [Toegang tot de Places-service](/help/places-gain-access.md).

* U bent als ontwikkelaar toegevoegd aan de Dienst van de Kern van Plaatsen in uw organisatie.

   Zie voor meer informatie over het toevoegen van ontwikkelaars *Een gebruiker of ontwikkelaar toevoegen aan de service- en Experience Platform Launch-profielen Plaatsen* in [Toegang tot de Places-service](/help/places-gain-access.md).

   Zie voor meer informatie over de rol van ontwikkelaar [Ontwikkelaars beheren](https://helpx.adobe.com/nl/enterprise/using/manage-developers.html).

### REST API-aanvragen

Voor elke aanvraag voor de REST API van de Places Service zijn de volgende items vereist:

* Een organisatie-id
* Een API-sleutel
* Een token voor toonder

Een integratie met Adobe I/O verstrekt deze punten en een manier om het dragerteken te verzoeken door een Symbolische Symbolie van het Web te gebruiken JSON (JWT).

* Voor meer informatie over JWTs, zie [Inleiding tot JSON-webtokens](https://jwt.io/introduction/).
* Als u een integratie voor Plaatsen Service wilt maken, raadpleegt u de *De integratie van de Plaatsingsservice maken* hieronder.
* Als u de API-sleutelintegratie wilt begrijpen, een JWT wilt genereren en openbare-sleutelcertificaten, raadpleegt u [Overzicht van Adobe I/O-verificatie](https://www.adobe.io/apis/cloudplatform/console/authentication/gettingstarted.html).

>[!IMPORTANT]
>
>Als u zich niet bij de console van de Adobe I/O kunt aanmelden of als de Dienst van Plaatsen geen optie op de is *Integratiepagina maken*, zie *Organisatie-eisen* in [API-overzicht webservices](/help/web-service-api/places-web-services.md).

## De integratie van de Plaatsen-service maken

Voer de volgende taken uit om een integratie met de Plaatsen-service te maken:

### Een combinatie van openbare en persoonlijke sleutels genereren

Om de integratie van de Dienst van Plaatsen tot stand te brengen, hebt u een openbare en privé zeer belangrijke paar nodig. Deze paren kunnen worden aangeschaft of u kunt uw eigen zelfondertekende toetsen genereren.

Uw eigen zelfondertekende toetsen genereren:

1. Kopieer en plak in een terminalvenster de volgende regels en druk op **[!UICONTROL Enter]** na het plakken van elke regel:

   ```text
      mkdir keys
      cd keys
      openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout places_integration_test_private.key -out    places_integration_test_public.crt
   ```

   >[!IMPORTANT]
   >
   >We raden u aan de sleutels een naam te geven die u als referentie kunt gebruiken en ze in een map op te slaan. Als u meerdere integraties maakt, kunt u gemakkelijk identificeren en beheren welke sleutels tot welke integratie behoren.

1. Typ de informatie die door OpenSSL wordt aangevraagd:

   ```text
   Country Name (2 letter code:  // Example: US
   State or Province Name (full name):  // Example: California
   Locality Name (eg, city):  // Example: San Jose
   Organization Name (eg, company):  // Example: Places
   Organizational Unit Name (eg, section):  // Example: Engineering
   Common Name (eg, fully qualified host name):  // Example: places.com
   Email Address:  // Example:  poi@places.com
   ```

   Ga voor meer informatie over OpenSSL naar [OpenSSL](https://www.openssl.org/).

   >[!IMPORTANT]
   >
   >De gegevens die u opgeeft, worden in de toetsen opgenomen.

1. Ga naar de map waarin de `.key` en `.crt` bestanden worden gevonden.

   Ga in MacOS bijvoorbeeld naar **[!UICONTROL Macintosh HD]** > **[!UICONTROL users]** > **[!UICONTROL (your user name)]** > **[!UICONTROL Keys]**.

De volgende video begeleidt u door het proces om het belangrijkste paar te produceren:

![integratievideo](/help/assets/places_integration_video.gif)

### Creeer de integratie van de Dienst van Plaatsen in de console van de Adobe I/O

Om een integratie van de Dienst van Plaatsen tot stand te brengen:

1. Ga naar [https://console.adobe.io](https://console.adobe.io) en meld u aan met uw Adobe ID.
1. In de **Snel starten** sectie, klik op **Integratie maken**.
1. Selecteer **[!UICONTROL Access an API]** en klik op **[!UICONTROL Continue]**.

   **[!UICONTROL Access an API]** is de standaardlocatie.

1. Als u toegang hebt tot meer dan één organisatie van de Experience Cloud, selecteer de organisatie van de drop-down lijst op het hoogste recht.
1. Selecteer onder **[!UICONTROL Experience Cloud]** de optie **[!UICONTROL Places Service]** als de Adobe-service die u wilt integreren en klik op **[!UICONTROL Continue]**.
1. Selecteer **[!UICONTROL New integration]** en klik op **[!UICONTROL Continue]**.
1. Voer in het scherm Een nieuwe integratie maken een naam en beschrijving in.
1. Sleep uw `xxxx_public.crt` bestand, dat u hierboven hebt gemaakt, naar het **[!UICONTROL Public keys certificates]** dropzone.
1. Selecteer een productprofiel.

   Neem contact op met de systeembeheerder als u niet zeker weet welk profiel u moet selecteren.
1. Klik onder aan de pagina op **[!UICONTROL Create integration]**.
1. Na een paar seconden, in *Integratie gemaakt* controleert u of het volgende bericht wordt weergegeven:

   `Your integration has been created.`

1. De pagina met integratiedetails wordt weergegeven met de naam van de integratie bovenaan.

   De **[!UICONTROL Overview]** wordt standaard weergegeven en geeft de API-sleutel, uw organisatie-id, de technische account-id en andere gegevens over uw integratie weer.

### De organisatie-id en de API-sleutel opnemen

1. Klik op de pagina met integratiedetails op de knop **[!UICONTROL Services]** en bevestig dat **[!UICONTROL Places Service]** wordt weergegeven onder **[!UICONTROL Configured Services]**.
1. Op de **[!UICONTROL Overview]** Zoek en neem de API-sleutel (client-id) en de organisatie-id op.

   Deze id&#39;s zijn nodig voor elke aanvraag van de REST API van de Places Service.

![](/help/assets/places_orgid_api-key.png)

### Een JWT-token genereren

Klik op de pagina met integratiedetails op de knop **[!UICONTROL JWT]** zodat u uw integratie kunt testen door een JWT te genereren en de uitwisseling-URL op te geven.

Een JWT-token genereren:

1. Open in een teksteditor uw `private.key` bestand gemaakt dat u hierboven hebt gemaakt.
1. Kopieer de content van de sleutel op het tabblad **[!UICONTROL JWT]** en plak deze in het veld **[!UICONTROL Paste private key]**.
1. Klik op **[!UICONTROL Generate JWT]**.
1. Klik in de sectie **[!UICONTROL Sample CURL command]** op **[!UICONTROL Copy]** en plak de content in uw opdrachtprompt of terminalvenster.
1. Voer de opdracht uit door op **[!UICONTROL Enter]** op uw toetsenbord.
1. Zoek de `"token_type": "bearer"` en de `"access_token"` waarde.

   De waarde van het toegangstoken van de toonder is wat u in uw de dienstAPI van Plaatsen verzoeken zult gebruiken.

>[!IMPORTANT]
>
>Adobe-toegangstokens zijn geldig **alleen** gedurende 24 uur, dus sla het voorbeeldCURL bevel (stap 5) op. Als het toegangstoken niet meer geldig is, moet u het token opnieuw genereren.
