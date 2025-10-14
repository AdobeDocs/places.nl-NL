---
title: Adobe Developer Project - overzicht
description: Informatie over het maken van een Adobe Developer API-project.
exl-id: d7d31938-6c0e-40f8-a9d3-30af96043119
source-git-commit: 3d477c6133b74a7e6380d0db1af5125aaa844035
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 1%

---

# Plaatst API toegangsoverzicht en eerste vereisten {#developer-prereqs}

Deze informatie laat u zien hoe u een project maakt in de Adobe Developer Console en een toegangstoken genereert die wordt gebruikt in aanvragen voor de Plaatsen-API.

## Vereisten voor gebruikerstoegang

Verifieer met de beheerder van het Systeem van uw organisatie dat de volgende taken zijn voltooid:

* U bent toegevoegd aan de organisatie.
* U bent toegevoegd aan een profiel in de Adobe Experience Platform.

  Voor meer informatie, zie *een gebruiker of een ontwikkelaar aan uw de dienstprofielen van Plaatsen en van het Experience Platform Launch* in [&#x200B; toegang van de Aanwinst tot de Dienst van Plaatsen &#x200B;](/help/places-gain-access.md) toevoegen.

### REST API-aanvragen

Voor elke aanvraag voor de REST API van de Places Service zijn de volgende items vereist:

* Een organisatie-id
* Een API-sleutel (ook wel een client-id genoemd)
* Clientgeheim
* Een token voor toonder

Een Project met de [&#x200B; console van Adobe Developer &#x200B;](https://developer.adobe.com/console) verstrekt deze punten.

* Om een Project voor de Dienst API van Plaatsen tot stand te brengen, zie *Creërend de sectie van het Project van de Dienst van Plaatsen* hieronder.

>[!IMPORTANT]
>
>Als u niet login aan [&#x200B; de console van Adobe Developer &#x200B;](https://developer.adobe.com/console) kunt, of als de Dienst van Plaatsen geen optie op *is creeer de pagina van Integraties*, zie *vereisten van de Organisatie* in [&#x200B; de diensten API van het Web overzicht &#x200B;](/help/web-service-api/places-web-services.md).

## Een Service API-project voor plaatsen maken

Voer de volgende handelingen uit om een Project for Places Service API te maken:

1. Login aan [&#x200B; website van Adobe Developer &#x200B;](https://developer.adobe.com) met uw Adobe ID.
2. Klik op **[!UICONTROL Console]** rechtsboven op de pagina.
3. Als u aan meer dan één organisatie van de Adobe wordt toegewezen, selecteer de correcte organisatie van de drop-down lijst in de hogere juiste hoek van de pagina.
4. Klik op de knop **[!UICONTROL Create new project]**.
5. Klik op **[!UICONTROL Add API]** in de sectie Aan de slag met uw nieuwe project.
6. Als u de API Plaatsen wilt selecteren, schuift u de pagina omlaag naar de kaart Plaatsen en klikt u op het selectievakje rechtsboven op de kaart.
7. Klik op de knop **[!UICONTROL Next]**.
8. Selecteer de optie OAuth Server-aan-Server (als er een keus is).
9. Geef de referentie een naam en klik op **[!UICONTROL Next]** .
10. Selecteer een profiel (een profiel moet werken als er meerdere zijn).
11. Klik op **[!UICONTROL Save and configure API]**.
12. Klik in het linkerdeelvenster op de koppeling **[!UICONTROL OAuth Server-to-Server]** onder CREDENTIALS
13. Deze pagina bevat het volgende:
    * Een manier om een toegangstoken te produceren dat in de REST API verzoeken van de Dienst van Plaatsen moet worden gebruikt.
    * Bekijk een krullbevel voor een voorbeeld hoe u een toegangstoken van uw eigen code kunt produceren.
    * Client-id weergeven (ook API-sleutel genoemd)
    * Het clientgeheim weergeven
    * De organisatie-id weergeven
    * Al deze zijn vereist in de aanvragen aan de REST API van de Dienst van Plaatsen.
14. U kunt de naam van het project wijzigen in een beschrijvende naam door op de projectnaam in het pad linksboven in het venster te klikken
15. Klik vervolgens op de knop **[!UICONTROL Edit project]** rechtsboven op de pagina.

>[!IMPORTANT]
>
>De de toegangstokens van de Adobe zijn geldig **slechts** voor 24 uren, zodat sparen het bevel van steekproefCURL (stap 5). Als het toegangstoken niet meer geldig is, moet u het teken opnieuw produceren.
