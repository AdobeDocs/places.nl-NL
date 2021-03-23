---
title: 'Toegang tot de Places-service '
description: Deze sectie verstrekt informatie over hoe te om een gebruiker aan de Dienst en het Experience Platform Launch van Plaatsen toe te voegen, zodat de gebruiker tot de Dienst van Plaatsen kan toegang hebben.
translation-type: tm+mt
source-git-commit: ecf50d67d4c08e79d9c3be64480f27d435fd7fcb
workflow-type: tm+mt
source-wordcount: '1074'
ht-degree: 5%

---

# Toegang tot de Places-service {#adding-user-launch-places}

U kunt tot de Dienst van Plaatsen van het snelle toegangsmenu op [Adobe Experience Cloud huis](https://experience.adobe.com) toegang hebben.
Als je gebruikersnaam toegang heeft, wordt het pictogram Plaatsen service weergegeven zoals hieronder wordt aangegeven:

![snelmenu](/help/assets/quickaccess.png)

U kunt ook het menu Plaatsen openen via het menu Adobe Experience Platform:

![Menu Experience Platform](/help/assets/solutionaccessmenu.png)

Als u de Dienst van Plaatsen in één van beiden van deze menu&#39;s ziet, contacteer een beheerder in uw organisatie om uw gebruikersnaam aan de Dienst van de Kern van Plaatsen in de Admin Console toe te voegen.

## Een gebruiker toevoegen aan de service Plaatsen en het Experience Platform Launch

Om gebruikers toegang te geven tot [Experience Platform Launch UI](https://launch.adobe.com), moeten zij aan de Dienst van de Kern van Plaatsen in de Admin Console als gebruiker worden toegevoegd. Om gebruikers toegang tot Experience Platform Launch te verlenen, mobiele eigenschappen te vormen, en Plaatsen met de SDK van Adobe Experience Platform te gebruiken, moeten zij aan Experience Platform Launch in de Admin Console worden toegevoegd en de volgende toestemmingen voor Experience Platform Launch worden gegeven:

* Alle eigendomsrechten:
   * Ontwikkelen
   * Goedkeuren
   * Publicatie
   * Extensies beheren
   * Omgevingen beheren
* Eigenschappen beheren onder Bedrijfsrechten

Als dit de eerste keer is dat u een gebruiker toevoegt, voert u de volgende stappen uit om gebruikers toe te voegen aan Experience Platform Launch- en Plaatsingsservice. Als u eerder gebruikers hebt toegevoegd, worden mogelijk meerdere profielen weergegeven, zodat u het juiste profiel selecteert.

>[!IMPORTANT]
>
>Alleen org-beheerders hebben toegang tot de Admin Console en voegen de gebruikers toe.

### 1. Controleren of de service Plaatsen en het Experience Platform Launch zijn ingericht

1. Meld u aan bij uw Experience Cloud-organisatie.
1. Klik in de rechterbovenhoek op de Experience Cloud shell-switch.

   ![shellswitch](/help/assets/places_shell_switcher1.png)

1. Klik onder **[!UICONTROL Platform]** op **[!UICONTROL Administration]**.

   Als u **[!UICONTROL Administration]** niet ziet in de lijst, bent u geen beheerder. U moet contact opnemen met uw org-beheerder om deze procedure te voltooien.

1. In de pagina van het Beleid van de Experience Cloud, op **[!UICONTROL Admin Console]** kaart, klik **[!UICONTROL Take me there]**.

1. Als u in de Admin Console toegang hebt tot meerdere organisaties, controleert u of de juiste organisatie in de rechterbovenhoek van de pagina is geselecteerd.

   Dit is de organisatie waaraan u uw gebruikers zult toevoegen. Als de juiste org niet is geselecteerd, klikt u op de org en selecteert u de org in de vervolgkeuzelijst.

   >[!IMPORTANT]
   >
   >Als u geen toegang tot een organisatie hebt, betekent het dat u geen admin toegang tot die organisatie hebt.

1. Controleer of de kaarten voor **[!UICONTROL Adobe Experience Platform Launch]** en **[!UICONTROL Places Core Services]** worden weergegeven.

   ![](/help/assets/places_provisioned1.png)

   Als zij worden getoond, zijn de Dienst en het Experience Platform Launch van Plaatsen provisioned voor uw organisatie. Als ze niet worden weergegeven, moeten ze worden ingericht voor uw organisatie.


### 2. Profiel instellen en machtigingen toevoegen

1. Stel een profiel voor Experience Platforms Launch in, waarmee de gebruikers die aan het profiel zijn toegevoegd, Experience Platform Launch en de mobiele eigenschappen kunnen gebruiken met de SDK van het Experience Platform.

   a. Klik in de menubalk op **[!UICONTROL Product]**.

   b. Klik in het linkerdeelvenster in de lijst met producten op **[!UICONTROL Adobe Experience Platform Launch]**.

   * Het profiel of de profielen van het Experience Platform Launch worden rechts weergegeven.
   * Experience Platform Launch heeft een standaardprofiel met de naam *Starten - (org naam)*.

      Als u eerder gebruikers aan Experience Platform Launch hebt toegevoegd, worden mogelijk meerdere profielen weergegeven.

1. Selecteer het juiste profiel:

   a. Klik op de naam van het standaardprofiel.

   b. Klik op het tabblad **[!UICONTROL Permissions]**.

   c. Klik op **[!UICONTROL Edit]** naast **[!UICONTROL Property Rights]**.

   d. Klik in het linkerdeelvenster op **[!UICONTROL + Add all]**.

   Met deze stap worden alle beschikbare machtigingen naar de lijst met opgenomen machtigingen verplaatst.

   e. Klik op **[!UICONTROL Company Rights]**.

   f. Klik in het linkerdeelvenster op **[!UICONTROL + Manage Properties]**.

   g. Klik op **[!UICONTROL Save]**.

>[!IMPORTANT]
>
>Voor de Dienst van Plaatsen, is er een standaardprofiel, maar u moet geen toestemmingen toevoegen.

U hebt machtigingen toegevoegd aan het profiel dat u hebt gemaakt.

### 3. Een gebruiker of ontwikkelaar toevoegen aan de service- en Experience Platform Launch-profielen Plaatsen

U kunt een gebruiker en/of een ontwikkelaar toevoegen aan de profielen Plaatsen Service en Experience Platform Launch.

### Een gebruiker toevoegen

U voegt als volgt een gebruiker toe aan de profielen Plaatsen Service en Experience Platform Launch:

1. Voeg een gebruiker aan het profiel van het Experience Platform Launch toe.

   a. Klik in de menubalk op **[!UICONTROL Overview]**.

   b. Controleer het volgende op de **[!UICONTROL Adobe Experience Platform Launch]**-kaart:

   * Onder aan de kaart worden twee punten weergegeven.
   * De stip aan de linkerkant is zwart.

      Als de punt aan de rechterkant zwart is, kunt u alleen ontwikkelaars toevoegen. Als u een gebruiker wilt toevoegen, klikt u op de stip aan de linkerkant.
   c. Klik op **[!UICONTROL + Add Users]**.

   d. Voer de Adobe ID van de gebruiker in.

   e. Voer een van de volgende stappen uit:

   * Als u een nieuwe gebruiker toevoegt, klikt u op **[!UICONTROL New user]** en voert u de voor- en achternaam van de gebruiker in.
   * Als u een bestaande gebruiker toevoegt, klikt u op de weergegeven gebruikersnaam.

   f. Selecteer in de vervolgkeuzelijst **[!UICONTROL Please select a profile for this product]** het profiel dat u eerder hebt bewerkt.

   g. Klik op **[!UICONTROL Save]**.

1. Voeg een gebruiker aan **[!UICONTROL Places Core Services]** toe.

   >[!TIP]
   >
   >Momenteel hebben alle gebruikers van de Plaatsingsservice dezelfde machtigingen, dus u hoeft de machtigingen niet te bewerken.

   a. Controleer het volgende op de **[!UICONTROL Places Core Services]**-kaart:

   * Onder aan de kaart worden twee punten weergegeven.
   * De stip aan de linkerkant is zwart.

   b. Klik op **[!UICONTROL + Assign Users]**.

   c. Voer de Adobe ID van de gebruiker in.

   d. Voer een van de volgende stappen uit:

   * Als u een nieuwe gebruiker toevoegt, klikt u op **[!UICONTROL New user]** en voert u de voor- en achternaam van de gebruiker in.
   * Als u een bestaande gebruiker toevoegt, klikt u op de weergegeven gebruikersnaam.

   e. Selecteer het profiel Plaatsen in de vervolgkeuzelijst **[!UICONTROL Please select a profile for this product]**.

   f. Klik op **[!UICONTROL Save]**.

### Een ontwikkelaar toevoegen

Voor gebruikers die ook toegang tot de Dienst API van het Web nodig hebben, moet u hen als Ontwikkelaar toevoegen.

Een ontwikkelaar toevoegen:

1. Controleer op de **[!UICONTROL Places Core Services]**-kaart het volgende:

   * Onder aan de kaart worden twee punten weergegeven.
   * Klik op de stip aan de rechterkant, zodat **[!UICONTROL Assign Developers]** onder aan de kaart wordt weergegeven.

1. Klik op **[!UICONTROL + Assign Developers]**.

1. Voer de Adobe ID van de gebruiker in.

1. Voer een van de volgende stappen uit:

   * Als u een nieuwe gebruiker toevoegt, klikt u op **[!UICONTROL New user]** en voert u de voor- en achternaam van de gebruiker in.
   * Als u een bestaande gebruiker toevoegt, klikt u op de weergegeven gebruikersnaam.

1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Please select a profile for this product]** het serviceprofiel Plaatsen.

1. Klik op **[!UICONTROL Save]**.

Gebruikers ontvangen een e-mail met de melding dat zij toegang hebben tot Experience Platform Launch. Ze kunnen zich aanmelden bij het [Experience Platform Launch](https://launch.adobe.com) of [Plaatst Service](https://places.adobe.com) UI&#39;s voor deze organisatie. Als u stap 4 in de **[!UICONTROL Add a developer]** procedure voltooit, kan de gebruiker ook login aan [Adobe I/O console](https://console.adobe.io) om een integratie van Plaatsen tot stand te brengen en de REST API van Plaatsen te gebruiken.
