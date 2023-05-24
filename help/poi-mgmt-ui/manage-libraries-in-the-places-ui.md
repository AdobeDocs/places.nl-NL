---
title: Bibliotheken beheren in de gebruikersinterface van de Plaatsingsservice
description: Beheer uw bibliotheken met behulp van de gebruikersinterface van de Plaatsingsservice.
exl-id: 2fb999b4-854a-430f-bb89-4c786d1a89cc
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 23%

---

# Bibliotheken beheren {#manage-libraries-places-ui}

Een bibliotheek is een verzameling van POI&#39;s. U kunt tot 150.000 POIs in een bibliotheek hebben, en er kunnen tot 100 bibliotheken per organisatie van Experience Cloud zijn.

Er zijn verschillende manieren om uw onderzoeksposten in bibliotheken te organiseren afhankelijk van wat voor uw organisatie het nuttigst is. Sommige klanten maken wellicht liever een aparte bibliotheek voor elke mobiele app, terwijl andere klanten bibliotheken kunnen gebruiken om specifieke typen inhoud, zoals koffiewinkels, parken, hotels, te groeperen. Een groot entertainmentbedrijf kan bijvoorbeeld een bibliotheek hebben die zijn buitenlocaties in een bibliotheek en hun winkels in een andere bibliotheek omvat. Een stadsregering zou een bibliotheek kunnen hebben die alle gebouwen in de stad omvat en een andere bibliotheek die alle parken in de stad omvat.

Bibliotheken worden als volgt gedefinieerd:

| Toetsen: | Beschrijving: |
| :--- | :--- |
| Id | een unieke id die bij het maken aan de bibliotheek is toegewezen |
| Naam | een vriendelijke naam die aan een bibliotheek wordt gegeven |
| Rang | Deze classificaties kunnen worden genegeerd als er geen overlappende geofences in uw organisatie voorkomen. Als er overlappende POI&#39;s zijn, raden wij u aan elke geofence in een afzonderlijke bibliotheek te plaatsen, zodat deze ten opzichte van elkaar gewogen kunnen worden. Een gebruiker kan slechts in één geofence tegelijk zijn. <br><br>De hoogste rangschikking van de geofences waarin een gebruiker zich bevindt, bepaalt zijn of haar huidige geofencelidmaatschap. Als er geofences zijn die dezelfde bibliotheekrangschikking hebben, is de kleinste geofence de huidige geofence van de gebruiker. <br><br>De SDK houdt ook rekening met de *laatst ingevoerde* en *laatst verlaten* POI&#39;s, zodat u volledige controle hebt over hoe u uw regels wilt activeren op basis van gebruikersinteractie met uw POI&#39;s. |

## Een bibliotheek maken

1. Meld u aan bij Plaatsen met uw Adobe ID.
1. Klik in de rechterbovenhoek op **[!UICONTROL ...]**  > **[!UICONTROL Manage Libraries]**.
1. Klik op **[!UICONTROL New]**.
1. Typ de naam.
1. Klik op **[!UICONTROL Confirm]**.

## De positie van een bibliotheek wijzigen in de gebruikersinterface Plaatsen

1. Meld u aan bij Plaatsen met uw Adobe ID.
1. Klik in de rechterbovenhoek op **[!UICONTROL ...]**  > **[!UICONTROL Manage Libraries]**.
1. Klik op het pictogram links van de bibliotheeknaam en sleep de bibliotheek naar de nieuwe rang.

## De naam van een bibliotheek wijzigen

1. Meld u aan bij Plaatsen met uw Adobe ID.
1. Klik in de rechterbovenhoek op **[!UICONTROL ...]** > **[!UICONTROL Manage Libraries]**.
1. Zoek de bibliotheek die u wilt verwijderen.
1. Klik op **[!UICONTROL ...]** en selecteer **[!UICONTROL Rename]**.
1. Werk de naam bij en klik op **[!UICONTROL Save]**.

## Een bibliotheek verwijderen

1. Meld u aan bij Plaatsen met uw Adobe ID.
1. Klik in de rechterbovenhoek op **[!UICONTROL ...]** > **[!UICONTROL Manage Libraries]**.
1. Zoek de bibliotheek die u wilt verwijderen.
1. Klik op **[!UICONTROL ...]** en selecteer **[!UICONTROL Delete]**.
