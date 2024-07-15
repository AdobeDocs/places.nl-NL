---
title: Toegang tot de Places-service
description: Deze sectie verstrekt informatie over hoe te om een gebruiker aan de Dienst en het Experience Platform Launch van Plaatsen toe te voegen, zodat de gebruiker tot de Dienst van Plaatsen kan toegang hebben.
exl-id: f388945e-cf26-4694-9697-9fe564ae4b69
source-git-commit: c9058e9b70c2ef97151078f43913963471730bd2
workflow-type: tm+mt
source-wordcount: '865'
ht-degree: 0%

---

# Toegang tot de Places-service {#adding-user-launch-places}

De Dienst van Plaatsen is nu beschikbaar binnen de Inzameling van Gegevens UI. U kunt tot de Inzameling van Gegevens van het snelle toegangsmenu op [ huis van Adobe Experience Cloud ](https://experience.adobe.com) toegang hebben.

![ snel toegangsmenu ](/help/assets/quickaccess.png)

U hebt ook toegang tot Gegevensverzameling via het menu Adobe Experience Platform:

![ het menu van het Experience Platform ](/help/assets/solutionaccessmenu.png)

Als uw gebruikers-id toegang heeft, ziet u het pictogram Plaatsingsservice in het linkerdeelvenster onder Gegevensbeheer in gegevensverzameling, zoals hieronder wordt aangegeven:

![ Verzameling van Gegevens verlaten paneel ](/help/assets/places_in_data_collection.png)

Als u de Plaatsingsservice niet op deze locatie ziet, neemt u contact op met een beheerder in uw organisatie om uw gebruikersnaam toe te voegen aan Adobe Experience Platform in de Admin Console.

## Een gebruiker toevoegen om toegang te krijgen tot de service Plaatsen en de gegevensverzameling van Adobe Experience Platform te ervaren

Plaatsen worden nu opgenomen in Adobe Experience Platform. Om gebruikers toe te staan om tot de [ Dienst van Plaatsen ](https://experience.adobe.com/#/data-collection/places) toegang te hebben, moeten zij aan Adobe Experience Platform in de Admin Console als gebruiker worden toegevoegd. Om gebruikers toegang tot de Inzameling van Gegevens van het Experience Platform met de vereiste toestemmingen te verlenen om mobiele eigenschappen te vormen en Plaatsen met de SDK van Adobe Experience Platform te gebruiken, moeten zij ook aan de Inzameling van Gegevens van Adobe Experience Platform in de Admin Console worden toegevoegd en de volgende toestemmingen voor de Inzameling van Gegevens van Adobe Experience Platform worden gegeven:

* Alle machtigingen onder Eigenschaprechten:
   * Goedkeuren
   * Ontwikkelen
   * Eigenschap bewerken
   * Omgevingen beheren
   * Extensies beheren
   * Publish
* Eigenschappen beheren onder Bedrijfsrechten

Als dit de eerste keer is dat u een gebruiker toevoegt, voert u de volgende stappen uit om gebruikers toe te voegen aan Adobe Experience Platform Data Collection en Adobe Experience Platform. Als u eerder gebruikers hebt toegevoegd, worden mogelijk meerdere profielen weergegeven, zodat u het juiste profiel selecteert.

>[!IMPORTANT]
>
>Alleen org-beheerders hebben toegang tot de Admin Console en voegen de gebruikers toe.

### 1. Controleer of Adobe Experience Platform en Adobe Experience Platform Data Collection zijn ingericht

1. Login aan uw organisatie van het Experience Cloud, [ huis Adobe Experience Cloud ](https://experience.adobe.com).
1. Klik in de rechterbovenhoek op de shell-switch van het Experience Cloud om een vervolgkeuzemenu weer te geven.

   ![ shell schakelaar ](/help/assets/places_shell_switcher1.png)

1. Klik onder aan de lijst op **[!UICONTROL Admin Console]** . (Een koppeling naar de **[!UICONTROL Admin Console]** vindt u ook in de sectie Snelle toegang.)

   Als u **[!UICONTROL Admin Console]** niet ziet in de lijst, bent u geen beheerder. U moet contact opnemen met uw org-beheerder om deze procedure te voltooien.

1. Als u in de Admin Console toegang hebt tot meerdere organisaties, controleert u of de juiste organisatie rechtsboven op de pagina is geselecteerd.

   Dit is de organisatie waaraan u uw gebruikers zult toevoegen. Als de juiste organisatie niet is geselecteerd, klikt u op de organisatie en selecteert u de juiste organisatie in de vervolgkeuzelijst.

   >[!IMPORTANT]
   >
   >Als de gewenste organisatie niet in de drop-down lijst is, betekent het dat u geen admin toegang tot die organisatie hebt.

1. Klik in de Admin Console op het tabblad Producten en controleer of de kaarten voor **[!UICONTROL Adobe Experience Platform Data Collection]** en **[!UICONTROL Adobe Experience Platform]** worden weergegeven.

   ![](/help/assets/places_provisioned1.png)

   Deze twee producten worden automatisch voorzien aan alle organisaties, zodat zouden zij aanwezig moeten zijn.


### 2. Gebruikers aan deze producten toevoegen

#### Gebruikers toevoegen om toegang te verlenen tot de gebruikersinterface van de Plaatsingsservice

1. Klik op de kaart **[!UICONTROL Adobe Experience Platform]** op het tabblad Producten.
2. Een gebruiker kan aan om het even welk profiel binnen **[!UICONTROL Adobe Experience Platform]** worden toegevoegd om tot Plaatsen toegang te krijgen, te hoeven geen specifieke toestemmingen worden geplaatst.
3. Kies een profiel (als er meerdere zijn) en klik erop om het te openen.
4. Klik de blauwe **toevoegen Gebruiker** knoop, vult de gebruiker met hun AdobeID en naam in, dan klik sparen om de toevoeging te voltooien.

#### Gebruiker toevoegen aan gegevensverzameling

1. Klik op de kaart **[!UICONTROL Adobe Experience Platform Data Collection]** op het tabblad Producten.
2. Door gebrek genoemd een profiel **Verzameling Standaard van Gegevens Alle Toegang** zal gecreeerd zijn. Als u een gebruiker aan dit profiel toevoegt, zorgt u ervoor dat deze de juiste machtigingen heeft om met Plaatsen Service en Gegevensverzameling te werken. Als u een ander profiel kiest, controleert u of de machtigingen die hierboven zijn vermeld, zijn opgenomen.
3. Kies een profiel (als er meerdere zijn) en klik erop om het te openen.
4. Klik de blauwe **toevoegen Gebruiker** knoop, vult de gebruiker met hun AdobeID en naam in, dan klik sparen om de toevoeging te voltooien.

#### Voeg een gebruiker als ontwikkelaar voor de Dienst van Plaatsen toe.

Voor gebruikers die ook toegang tot de REST API van de Dienst van Plaatsen nodig hebben, moet u hen toevoegen als Ontwikkelaar.
1. Klik op de kaart **[!UICONTROL Adobe Experience Platform]** op het tabblad Producten.
2. Als de gebruiker al via de bovenstaande instructies aan de kaart van **[!UICONTROL Adobe Experience Platform]** is toegevoegd, kiest u hetzelfde eerder gebruikte profiel en klikt u erop.
3. Binnen het profiel, klik op het **lusje van Ontwikkelaars**
4. Klik de blauwe **toevoegen knoop van de Ontwikkelaar**, vult de gebruiker met hun AdobeID en naam in, dan klik sparen om de toevoeging te voltooien.

Na het voltooien van de bovenstaande stappen ontvangt de gebruiker een e-mail met het bericht dat hij of zij toegang heeft tot **[!UICONTROL Adobe Experience Platform]** en **[!UICONTROL Adobe Experience Platform Data Collection]** . Zij kunnen dan login aan [ Adobe Experience Cloud ](https://experience.adobe.com) voor deze organisatie en de Dienst van toegangsplaatsen en de Inzameling van Gegevens. Als u ook de stappen **[!UICONTROL Add a developer]** voltooit, kan de gebruiker zich aan [ Adobe Developer Console ](https://developer.adobe.com/console/home) ook aanmelden om een Project tot stand te brengen dat toegang tot de REST API van de Dienst van Plaatsen zou verlenen.
