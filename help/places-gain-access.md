---
title: 'Toegang tot de Places-service '
description: Deze sectie verstrekt informatie over hoe te om een gebruiker aan de Dienst en het Experience Platform Launch van Plaatsen toe te voegen, zodat de gebruiker tot de Dienst van Plaatsen kan toegang hebben.
translation-type: tm+mt
source-git-commit: 26538602a73e806a4822705c7a3aa44d76351030
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 8%

---

# Toegang tot de Places-service {#adding-user-launch-places}

U hebt toegang tot de Plaatsen Service via het snelmenu op de [Adobe Experience Cloud-startpagina](https://experience.adobe.com).
Als je gebruikersnaam toegang heeft, wordt het pictogram Plaatsen service weergegeven zoals hieronder wordt aangegeven:

![snelmenu](/help/assets/quickaccess.png)

U kunt ook het menu Plaatsen openen via het menu Adobe Experience Platform:

![Menu Experience Platform](/help/assets/solutionaccessmenu.png)

Als u de Dienst van Plaatsen in één van beiden van deze menu&#39;s ziet, contacteer een beheerder in uw organisatie om uw gebruikersnaam aan de Dienst van de Kern van Plaatsen in de Admin Console toe te voegen.

## Een gebruiker toevoegen aan de service Plaatsen en het Experience Platform Launch

Om gebruikers toe te staan om tot het [Experience Platform Launch UI](https://launch.adobe.com)toegang te hebben, moeten zij aan de Dienst van de Kern van Plaatsen in de Admin Console als gebruiker worden toegevoegd. Om gebruikers toegang tot Experience Platform Launch te verlenen, mobiele eigenschappen te vormen, en Plaatsen met de SDK van Adobe Experience Platform te gebruiken, moeten zij aan Experience Platform Launch in de Admin Console worden toegevoegd en de volgende toestemmingen voor Experience Platform Launch worden gegeven:

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

   Als u **Beheer** niet ziet in de lijst, bent u geen beheerder. U moet contact opnemen met uw org-beheerder om deze procedure te voltooien.

1. Klik op de **[!UICONTROL Admin Console]** kaart op de pagina Beheer Experience Cloud op **[!UICONTROL Take me there]**.

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
   * Experience Platform Launch heeft een standaardprofiel met de naam *Launch - (org-naam)* .

      Als u eerder gebruikers aan Experience Platform Launch hebt toegevoegd, worden mogelijk meerdere profielen weergegeven.

1. Selecteer het juiste profiel:

   a. Klik op de naam van het standaardprofiel.

   b. Klik op het **[!UICONTROL Permissions]** tabblad.

   c. Klik op **[!UICONTROL Edit]** naast **[!UICONTROL Property Rights]**.

   d. Klik in het linkerdeelvenster op **[!UICONTROL + Add all]**.

   Met deze stap worden alle beschikbare machtigingen naar de lijst met opgenomen machtigingen verplaatst.

   e. Klik **[!UICONTROL Company Rights]**.

   f. Klik in het linkerdeelvenster op **[!UICONTROL + Manage Properties]**.

   g. Klik **[!UICONTROL Save]**.

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

   b. On the **[!UICONTROL Adobe Experience Platform Launch]** card, verify the following:

   * Onder aan de kaart worden twee punten weergegeven.
   * De stip aan de linkerkant is zwart.

      Als de punt aan de rechterkant zwart is, kunt u alleen ontwikkelaars toevoegen. Als u een gebruiker wilt toevoegen, klikt u op de stip aan de linkerkant.
   c. Klik **[!UICONTROL + Add Users]**.

   d. Voer de Adobe ID van de gebruiker in.

   e. Voer een van de volgende stappen uit:

   * Als u een nieuwe gebruiker toevoegt, klikt u **[!UICONTROL New user]** en voert u de voor- en achternaam van de gebruiker in.
   * Als u een bestaande gebruiker toevoegt, klikt u op de weergegeven gebruikersnaam.

   f. Selecteer in de **[!UICONTROL Please select a profile for this product]** vervolgkeuzelijst het profiel dat u eerder hebt bewerkt.

   g. Klik **[!UICONTROL Save]**.

1. Voeg een gebruiker toe aan **[!UICONTROL Places Core Services]**.

   >[!TIP]
   >
   >Momenteel hebben alle gebruikers van de Plaatsingsservice dezelfde machtigingen, dus u hoeft de machtigingen niet te bewerken.

   a. On the **[!UICONTROL Places Core Services]** card, verify the following:

   * Onder aan de kaart worden twee punten weergegeven.
   * De stip aan de linkerkant is zwart.

   b. Klik **[!UICONTROL + Assign Users]**.

   c. Voer de Adobe ID van de gebruiker in.

   d. Voer een van de volgende stappen uit:

   * Als u een nieuwe gebruiker toevoegt, klikt u **[!UICONTROL New user]** en voert u de voor- en achternaam van de gebruiker in.
   * Als u een bestaande gebruiker toevoegt, klikt u op de weergegeven gebruikersnaam.

   e. Selecteer het profiel Plaatsen in de **[!UICONTROL Please select a profile for this product]** vervolgkeuzelijst.

   f. Klik **[!UICONTROL Save]**.

### Een ontwikkelaar toevoegen

Voor gebruikers die ook toegang tot de Dienst API van het Web nodig hebben, moet u hen als Ontwikkelaar toevoegen.

Een ontwikkelaar toevoegen:

1. Controleer op de **[!UICONTROL Places Core Services]**-kaart het volgende:

   * Onder aan de kaart worden twee punten weergegeven.
   * Klik op de stip aan de rechterkant, zodat deze onder aan de kaart **[!UICONTROL Assign Developers]** wordt weergegeven.

1. Klik op **[!UICONTROL + Assign Developers]**.

1. Voer de Adobe ID van de gebruiker in.

1. Voer een van de volgende stappen uit:

   * Als u een nieuwe gebruiker toevoegt, klikt u op **[!UICONTROL New user]** en voert u de voor- en achternaam van de gebruiker in.
   * Als u een bestaande gebruiker toevoegt, klikt u op de weergegeven gebruikersnaam.

1. Selecteer het profiel Plaatsen in de **[!UICONTROL Please select a profile for this product]** vervolgkeuzelijst.

1. Klik op **Opslaan**.

Gebruikers ontvangen een e-mail met de melding dat zij toegang hebben tot Experience Platform Launch. They can can log in to the [Experience Platform Launch](https://launch.adobe.com) or the [Places Service](https://places.adobe.com) UIs for this organization. Als u stap 4 in de procedure **Een ontwikkelaar toevoegen** hebt voltooid, kan de gebruiker zich ook aanmelden bij de [Adobe I/O-console](https://console.adobe.io) om een Places-integratie te maken en de REST-API van Places te gebruiken.
