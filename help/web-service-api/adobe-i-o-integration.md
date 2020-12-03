---
title: Overzicht van Adobe I/O-integratie
description: Informatie over het maken van een Adobe I/O-integratie.
translation-type: tm+mt
source-git-commit: c22efc36f2eac6b20fc555d998c3988d8c31169e
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

   Voor meer informatie, zie *Voeg een gebruiker of een ontwikkelaar aan uw de Dienst van Plaatsen en profielen* van het Experience Platform Launch in de Toegang van [de Aanwinst tot de Dienst](/help/places-gain-access.md)van Plaatsen toe.

* U bent als ontwikkelaar toegevoegd aan de Dienst van de Kern van Plaatsen in uw organisatie.

   Voor meer informatie bij het toevoegen van ontwikkelaars zie *Voeg een gebruiker of een ontwikkelaar aan uw de Dienst en profielen* van Experience Platforms Launch van Plaatsen in de Toegang van [de Aanwinst tot de Dienst](/help/places-gain-access.md)van Plaatsen toe.

   Zie [Ontwikkelaars](https://helpx.adobe.com/enterprise/using/manage-developers.html)beheren voor meer informatie over de rol van ontwikkelaar.

### REST API-aanvragen

Voor elke aanvraag voor de REST API van de Places Service zijn de volgende items vereist:

* Een organisatie-id
* Een API-sleutel
* Een token voor toonder

Integratie met Adobe I/O biedt deze items en een manier om de token aan te vragen met behulp van een JSON Web Token (JWT).

* Voor meer informatie over JWTs, zie [Inleiding aan Tokens](https://jwt.io/introduction/)van het Web JSON.
* Als u een integratie voor de Plaatsen-service wilt maken, raadpleegt u de sectie *De integratie* van Plaatsen maken hieronder.
* Zie Overzicht [van](https://www.adobe.io/apis/cloudplatform/console/authentication/gettingstarted.html)Adobe I/O-verificatie voor meer informatie over API-sleutelintegratie, het genereren van een JWT en openbare-sleutelcertificaten.

>[!IMPORTANT]
>
>Als u zich niet bij de console van Adobe I/O kunt aanmelden, of als de Dienst van Plaatsen geen optie op de *Create pagina* van Integraties is, zie de vereisten *van de* Organisatie in het overzicht [van API van de Diensten van het](/help/web-service-api/places-web-services.md)Web.

## De integratie van de Plaatsen-service maken

Voer de volgende taken uit om een integratie met de Plaatsen-service te maken:

### Een combinatie van openbare en persoonlijke sleutels genereren

Om de integratie van de Dienst van Plaatsen tot stand te brengen, hebt u een openbare en privé zeer belangrijke paar nodig. Deze paren kunnen worden aangeschaft of u kunt uw eigen zelfondertekende toetsen genereren.

Uw eigen zelfondertekende toetsen genereren:

1. Kopieer en plak in een terminalvenster elk van de volgende regels en druk op **[!UICONTROL Enter]** nadat u elke regel hebt geplakt:

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

   Zie [OpenSSL voor meer informatie over OpenSSL](https://www.openssl.org/).

   >[!IMPORTANT]
   >
   >De gegevens die u opgeeft, worden in de toetsen opgenomen.

1. Navigeer naar de map waarin de bestanden `.key` en `.crt` bestanden zich bevinden.

   For example, in MacOS, go to **[!UICONTROL Macintosh HD]** > **[!UICONTROL users]** > **[!UICONTROL (your user name)]** > **[!UICONTROL Keys]**.

De volgende video begeleidt u door het proces om het belangrijkste paar te produceren:

![integratievideo](/help/assets/places_integration_video.gif)

### De integratie van Plaatsen Service maken in de Adobe I/O-console

Om een integratie van de Dienst van Plaatsen tot stand te brengen:

1. Ga naar [https://console.adobe.io](https://console.adobe.io) en meld u aan met uw Adobe ID.
1. Klik in de sectie **Snel starten** op Integratie **** maken.
1. Selecteer **[!UICONTROL Access an API]** en klik op **[!UICONTROL Continue]**.

   **[!UICONTROL Access an API]** is de standaardlocatie.

1. Als u toegang hebt tot meer dan één organisatie van de Experience Cloud, selecteer de organisatie van de drop-down lijst op het hoogste recht.
1. Selecteer onder **[!UICONTROL Experience Cloud]** de optie **[!UICONTROL Places Service]** als de Adobe-service die u wilt integreren en klik op **[!UICONTROL Continue]**.
1. Selecteer **[!UICONTROL New integration]** en klik op **[!UICONTROL Continue]**.
1. Voer in het scherm Een nieuwe integratie maken een naam en beschrijving in.
1. Sleep het hierboven gemaakte `xxxx_public.crt` bestand naar de **[!UICONTROL Public keys certificates]** dropzone.
1. Selecteer een productprofiel.

   Neem contact op met de systeembeheerder als u niet zeker weet welk profiel u moet selecteren.
1. Klik onder aan de pagina op **[!UICONTROL Create integration]**.
1. Controleer na een paar seconden in het scherm *Integration created* of het volgende bericht wordt weergegeven:

   `Your integration has been created.`

1. De pagina met integratiedetails wordt weergegeven met de naam van de integratie bovenaan.

   Het **[!UICONTROL Overview]** tabblad wordt standaard weergegeven en geeft de API-sleutel, uw organisatie-id, de technische account-id en andere gegevens over uw integratie weer.

### De organisatie-id en de API-sleutel opnemen

1. Klik op de pagina met integratiedetails op het **[!UICONTROL Services]** tabblad en bevestig dat dit onder **[!UICONTROL Places Service]** wordt weergegeven **[!UICONTROL Configured Services]**.
1. Zoek op het **[!UICONTROL Overview]** tabblad de API-sleutel (client-id) en de organisatie-id en neem deze op.

   Deze id&#39;s zijn nodig voor elke aanvraag van de REST API van de Places Service.

![](/help/assets/places_orgid_api-key.png)

### Een JWT-token genereren

Klik op de pagina met integratiedetails op het **[!UICONTROL JWT]** tabblad zodat u uw integratie kunt testen door een JWT te genereren en de URL voor de uitwisseling op te geven.

Een JWT-token genereren:

1. Open in een teksteditor het hierboven gemaakte `private.key` bestand.
1. Kopieer de content van de sleutel op het tabblad **[!UICONTROL JWT]** en plak deze in het veld **[!UICONTROL Paste private key]**.
1. Klik op **[!UICONTROL Generate JWT]**.
1. Klik in de sectie **[!UICONTROL Sample CURL command]** op **[!UICONTROL Copy]** en plak de content in uw opdrachtprompt of terminalvenster.
1. Voer de opdracht uit door op het **[!UICONTROL Enter]** toetsenbord te drukken.
1. Zoek de `"token_type": "bearer"` en de `"access_token"` waarde.

   De waarde van het toegangstoken van de toonder is wat u in uw de dienstAPI van Plaatsen verzoeken zult gebruiken.

>[!IMPORTANT]
>
>De tokens van de Adobe toegang zijn **slechts** 24 uur geldig, zodat sparen het bevel van steekproefCURL (stap 5). Als het toegangstoken niet meer geldig is, moet u het token opnieuw genereren.