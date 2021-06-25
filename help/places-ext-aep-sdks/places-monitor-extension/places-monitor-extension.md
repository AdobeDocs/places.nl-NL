---
title: Hiermee wordt de extensie Monitor geplaatst
description: De extensie Plaatsen Monitor handelt de interactie met het besturingssysteem af om de POI's die het dichtst bij de gebruiker staan, te registreren en te controleren.
exl-id: 254b33a0-79c4-4d51-8835-16e60f5c055e
source-git-commit: 8dcd777acf5d578b748afae9aa609c2349ea94a9
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 0%

---

# Hiermee wordt de extensie Monitor geplaatst {#places-monitor-extension}

De extensie Plaatsen Monitor handelt de interactie met het besturingssysteem af om de POI&#39;s die het dichtst bij de gebruiker staan, te registreren en te controleren. Deze uitbreiding wint POIs terug die van de uitbreiding van Plaatsen moeten worden geregistreerd en gaat de ingang en uitgangsberichten tot de uitbreiding van Plaatsen over. Deze berichten zullen in de regels van het Experience Platform Launch als gebeurtenissen beschikbaar zijn.

De extensie Monitor is optioneel omdat sommige klanten gebieden al controleren met het besturingssysteem. Als dit het geval is, zorg ervoor dat u de de uitbreiding APIs van Plaatsen toevoegt om dichtstbijzijnde POIs van het gegevensbestand van de Dienst van Plaatsen te ontvangen en ook de ingang en uitgangsgebeurtenissen over te gaan zodat de aangewezen acties kunnen worden genomen.

## Hiermee plaatst u monitorvervorming

Op 31 augustus 2021 wordt de extensie Plaatsen Monitor voor de Adobe Experience Platform Mobile SDK&#39;s afgekeurd. De extensie Plaatsen Monitor ontvangt na 31 augustus geen verdere updates of ondersteuning.

Klanten die de extensie Plaatsen gebruiken, kunnen deze extensie blijven gebruiken, met dien verstande dat er geen aanvullende updates of ondersteuning beschikbaar zijn via Adobe.

De vervanging van de extensie Plaatsen Monitor heeft geen negatieve of negatieve invloed op de extensie Plaatsen Service, die verder wordt ondersteund met verbeteringen en updates.

Klanten die op overgang vanaf de uitbreiding van de Monitor van Plaatsen aan hun eigen controlemethode kijken zouden de documentatie voor moeten herzien: [Gebruik Plaatsingsservice met uw eigen monitoroplossing](https://experienceleague.adobe.com/docs/places/using/using-your-own-monitor.html?lang=en). In dit document wordt uitgelegd hoe u communiceert met de Places Service door [Core Location Services](https://developer.apple.com/documentation/corelocation) op iOS of [Location Services](https://developers.google.com/android/reference/com/google/android/gms/location/package-summary) van Google Play te implementeren.
