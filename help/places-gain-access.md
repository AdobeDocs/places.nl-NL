---
title: Toegang tot de Places-service
description: Deze sectie verstrekt informatie over hoe te om een gebruiker aan de Dienst en het Experience Platform Launch van Plaatsen toe te voegen, zodat de gebruiker tot de Dienst van Plaatsen kan toegang hebben.
exl-id: f388945e-cf26-4694-9697-9fe564ae4b69
source-git-commit: c9058e9b70c2ef97151078f43913963471730bd2
workflow-type: tm+mt
source-wordcount: '871'
ht-degree: 0%

---

# Toegang tot de Places-service {#adding-user-launch-places}

De Dienst van Plaatsen is nu beschikbaar binnen de Inzameling van Gegevens UI. U kunt tot de Inzameling van Gegevens van het snelle toegangsmenu toegang hebben op [Adobe Experience Cloud home](https://experience.adobe.com).

![snelmenu](/help/assets/quickaccess.png)

U hebt ook toegang tot Gegevensverzameling via het menu Adobe Experience Platform:

![Menu Experience Platform](/help/assets/solutionaccessmenu.png)

Als uw gebruikers-id toegang heeft, ziet u het pictogram Plaatsingsservice in het linkerdeelvenster onder Gegevensbeheer in gegevensverzameling, zoals hieronder wordt aangegeven:

![Gegevensverzameling, linkerdeelvenster](/help/assets/places_in_data_collection.png)

Als u de Plaatsingsservice niet op deze locatie ziet, neemt u contact op met een beheerder in uw organisatie om uw gebruikersnaam toe te voegen aan Adobe Experience Platform in de Admin Console.

## Een gebruiker toevoegen om toegang te krijgen tot de service Plaatsen en de gegevensverzameling van Adobe Experience Platform te ervaren

Plaatsen worden nu opgenomen in Adobe Experience Platform. Gebruikers toegang geven tot de [Plaatsingsservice](https://experience.adobe.com/#/data-collection/places), moeten ze als gebruiker aan Adobe Experience Platform in de Admin Console worden toegevoegd. Om gebruikers toegang tot de Inzameling van Gegevens van het Experience Platform met de vereiste toestemmingen te verlenen om mobiele eigenschappen te vormen en Plaatsen met de SDK van Adobe Experience Platform te gebruiken, moeten zij ook aan de Inzameling van Gegevens van Adobe Experience Platform in de Admin Console worden toegevoegd en de volgende toestemmingen voor de Inzameling van Gegevens van Adobe Experience Platform worden gegeven:

* Alle machtigingen onder Eigenschaprechten:
   * Goedkeuren
   * Ontwikkelen
   * Eigenschap bewerken
   * Omgevingen beheren
   * Extensies beheren
   * Publicatie
* Eigenschappen beheren onder Bedrijfsrechten

Als dit de eerste keer is dat u een gebruiker toevoegt, voert u de volgende stappen uit om gebruikers toe te voegen aan Adobe Experience Platform Data Collection en Adobe Experience Platform. Als u eerder gebruikers hebt toegevoegd, worden mogelijk meerdere profielen weergegeven, zodat u het juiste profiel selecteert.

>[!IMPORTANT]
>
>Alleen org-beheerders hebben toegang tot de Admin Console en voegen de gebruikers toe.

### 1. Controleren of Adobe Experience Platform en Adobe Experience Platform Data Collection zijn ingericht

1. Meld u aan bij uw Experience Cloud-organisatie. [Adobe Experience Cloud home](https://experience.adobe.com).
1. Klik in de rechterbovenhoek op de Experience Cloud-shell-switch om een vervolgkeuzemenu weer te geven.

   ![shellswitch](/help/assets/places_shell_switcher1.png)

1. Klik onder aan de lijst op **[!UICONTROL Admin Console]**. (Een koppeling naar de **[!UICONTROL Admin Console]** kunt u ook vinden in de sectie Snelle toegang).

   Als u niet ziet **[!UICONTROL Admin Console]** in de lijst bent u geen beheerder. U moet contact opnemen met uw org-beheerder om deze procedure te voltooien.

1. Als u in de Admin Console toegang hebt tot meerdere organisaties, controleert u of de juiste organisatie rechtsboven op de pagina is geselecteerd.

   Dit is de organisatie waaraan u uw gebruikers zult toevoegen. Als de juiste organisatie niet is geselecteerd, klikt u op de organisatie en selecteert u de juiste organisatie in de vervolgkeuzelijst.

   >[!IMPORTANT]
   >
   >Als de gewenste organisatie niet in de drop-down lijst is, betekent het dat u geen admin toegang tot die organisatie hebt.

1. Klik in de Admin Console op het tabblad Producten en controleer of de kaarten voor **[!UICONTROL Adobe Experience Platform Data Collection]** en **[!UICONTROL Adobe Experience Platform]** worden weergegeven.

   ![](/help/assets/places_provisioned1.png)

   Deze twee producten worden automatisch voorzien aan alle organisaties, zodat zouden zij aanwezig moeten zijn.


### 2. Gebruiker toevoegen aan deze producten

#### Gebruikers toevoegen om toegang te verlenen tot de gebruikersinterface van de Plaatsingsservice

1. Klik op het tabblad Producten op de knop **[!UICONTROL Adobe Experience Platform]** kaart.
2. Een gebruiker kan aan om het even welk profiel binnen worden toegevoegd **[!UICONTROL Adobe Experience Platform]** om toegang te krijgen tot Plaatsen, hoeven geen specifieke toestemmingen te worden geplaatst.
3. Kies een profiel (als er meerdere zijn) en klik erop om het te openen.
4. Klik op blauw **Gebruiker toevoegen** vult u de gebruiker in met de Adobe-id en naam en klikt u vervolgens op Opslaan om de toevoeging te voltooien.

#### Gebruiker toevoegen aan gegevensverzameling

1. Klik op het tabblad Producten op de knop **[!UICONTROL Adobe Experience Platform Data Collection]** kaart.
2. Standaard een profiel met de naam **Standaardgegevensverzameling, alle toegang** wordt gemaakt. Als u een gebruiker aan dit profiel toevoegt, zorgt u ervoor dat deze de juiste machtigingen heeft om met Plaatsen Service en Gegevensverzameling te werken. Als u een ander profiel kiest, controleert u of de machtigingen die hierboven zijn vermeld, zijn opgenomen.
3. Kies een profiel (als er meerdere zijn) en klik erop om het te openen.
4. Klik op blauw **Gebruiker toevoegen** vult u de gebruiker in met de Adobe-id en naam en klikt u vervolgens op Opslaan om de toevoeging te voltooien.

#### Voeg een gebruiker als ontwikkelaar voor de Dienst van Plaatsen toe.

Voor gebruikers die ook toegang tot de REST API van de Dienst van Plaatsen nodig hebben, moet u hen toevoegen als Ontwikkelaar.
1. Klik op het tabblad Producten op de knop **[!UICONTROL Adobe Experience Platform]** kaart.
2. Als de gebruiker al is toegevoegd aan **[!UICONTROL Adobe Experience Platform]** Kies hetzelfde eerder gebruikte profiel en klik op het profiel via de bovenstaande instructies.
3. Klik in het profiel op de knop **Ontwikkelaars** tab
4. Klik op blauw **Ontwikkelaar toevoegen** vult u de gebruiker in met de Adobe-id en naam en klikt u vervolgens op Opslaan om de toevoeging te voltooien.

Nadat de bovenstaande stappen zijn voltooid, ontvangt de gebruiker een e-mail met de kennisgeving dat hij of zij toegang heeft tot **[!UICONTROL Adobe Experience Platform]** en **[!UICONTROL Adobe Experience Platform Data Collection]**. Ze kunnen zich vervolgens aanmelden bij de [Adobe Experience Cloud](https://experience.adobe.com) voor deze organisatie en toegang de Dienst van Plaatsen en de Inzameling van Gegevens. Als u ook de stappen uitvoert **[!UICONTROL Add a developer]**, kan de gebruiker zich ook aanmelden bij de [Adobe Developer Console](https://developer.adobe.com/console/home) om een project te creëren dat toegang tot de REST API van de Dienst van Plaatsen zou verlenen.
