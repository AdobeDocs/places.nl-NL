---
title: 'Toegang tot de Places-service '
description: Deze sectie verstrekt informatie over hoe te om een gebruiker aan de Dienst van Plaatsen toe te voegen en de Lancering van het Platform van de Ervaring, zodat de gebruiker tot de Dienst van Plaatsen kan toegang hebben.
translation-type: tm+mt
source-git-commit: 5a21e734c0ef56c815389a9f08b445bedaae557a

---

# Toegang tot de Places-service {#adding-user-launch-places}

U hebt toegang tot de Plaatsen Service via het snelmenu op de [Adobe Experience Cloud-startpagina](https://experience.adobe.com).
Als je gebruikersnaam toegang heeft, wordt het pictogram Plaatsen service weergegeven zoals hieronder wordt aangegeven:

![snelmenu](/help/assets/quick-access.png)

U kunt ook de Places Service openen vanuit het menu Adobe Experience Platform:

![Het menu Experience Platform](/help/assets/exp-platform-menu-sm.png)

Als u de Plaatsingsservice in geen van deze menu&#39;s ziet, neemt u contact op met een beheerder in uw organisatie om uw gebruikers-id toe te voegen aan de Dienst Plaatsen Core in de beheerconsole.

## Een gebruiker toevoegen aan de Service Places en de Start van het Platform van de Ervaring

Om gebruikers toegang te geven tot de gebruikersinterface [voor het starten van het](https://launch.adobe.com)ervaringsplatform, moeten zij als gebruiker worden toegevoegd aan de Dienst van de Kern van Plaatsen in de Console Admin. Om gebruikers toegang te geven tot de Start van het Experience Platform, mobiele eigenschappen te configureren en Plaatsen te gebruiken met de SDK van het Adobe Experience Platform, moeten ze worden toegevoegd aan de Launch van het Experience Platform in de beheerconsole en de volgende machtigingen krijgen voor het starten van het Experience Platform:

* Alle eigendomsrechten:
   * Ontwikkelen
   * Goedkeuren
   * Publiceren
   * Extensies beheren
   * Omgevingen beheren
* Eigenschappen beheren onder Bedrijfsrechten

Als dit de eerste keer is dat u een gebruiker toevoegt, voert u de volgende stappen uit om gebruikers toe te voegen aan Experience Platform Launch and Places Service. Als u eerder gebruikers hebt toegevoegd, worden mogelijk meerdere profielen weergegeven, zodat u het juiste profiel selecteert.

>[!IMPORTANT]
>
>Alleen org-beheerders hebben toegang tot de beheerconsole en kunnen de gebruikers toevoegen.

### 1. Controleren of de service Plaatsen en het startprogramma van het ervaringsplatform zijn ingericht

1. Meld u aan bij uw Experience Cloud-organisatie.
1. Klik in de rechterbovenhoek op de schelpschakelaar van Experience Cloud.

   ![shellswitch](/help/assets/places_shell_switcher1.png)

1. Klik onder **[!UICONTROL Platform]** op **[!UICONTROL Administration]**.

   Als u **Beheer** niet ziet in de lijst, bent u geen beheerder. U moet contact opnemen met uw org-beheerder om deze procedure te voltooien.

1. Klik op de **[!UICONTROL Admin Console]** kaart op de pagina Experience Cloud Administration **[!UICONTROL Take me there]**.

1. Als u in de beheerconsole toegang hebt tot meerdere organisaties, controleert u of de juiste organisatie in de rechterbovenhoek van de pagina is geselecteerd.

   Dit is de organisatie waaraan u uw gebruikers zult toevoegen. Als de juiste org niet is geselecteerd, klikt u op de org en selecteert u de org in de vervolgkeuzelijst.

   >[!IMPORTANT]
   >
   >Als u geen toegang tot een organisatie hebt, betekent het dat u geen admin toegang tot die organisatie hebt.

1. Controleer of de kaarten voor **[!UICONTROL Adobe Experience Platform Launch]** en **[!UICONTROL Places Core Services]** worden weergegeven.

   ![](/help/assets/places_provisioned1.png)

   Als zij worden getoond, zijn de Dienst van Plaatsen en de Lancering van het Platform van de Ervaring provisioned voor uw organisatie. Als ze niet worden weergegeven, moeten ze worden ingericht voor uw organisatie.


### 2. Profiel instellen en machtigingen toevoegen

1. Stel een opstartprofiel voor het ervaringsplatform in, waarmee de gebruikers die aan het profiel zijn toegevoegd, de functie Experience Platform Launch en de mobiele eigenschappen kunnen gebruiken met de Experience Platform SDK.

   a. Klik in de menubalk op **[!UICONTROL Product]**.

   b. Klik in het linkerdeelvenster in de lijst met producten op **[!UICONTROL Adobe Experience Platform Launch]**.

   * Het (de) profiel(en) van de Lancering van het Platform van de Ervaring verschijnen op het recht.
   * De Lancering van het Platform van de ervaring heeft een standaardprofiel genoemd *Lancering - (org naam)* .

      Als u eerder gebruikers hebt toegevoegd aan Experience Platform Launch, worden mogelijk meerdere profielen weergegeven.

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

### 3. Een gebruiker of ontwikkelaar toevoegen aan uw profielen Plaatsen Service en Experience Platform Launch

U kunt een gebruiker en/of een ontwikkelaar toevoegen aan uw profielen van de Dienst van Plaatsen en van de Ervaring Platform van de Lancering.

### Een gebruiker toevoegen

U voegt als volgt een gebruiker toe aan de Startprofielen Places Service en Experience Platform:

1. Voeg een gebruiker aan het profiel van de Lancering van het Platform van de Ervaring toe.

   a. Klik in de menubalk op **[!UICONTROL Overview]**.

   b. On the **[!UICONTROL Adobe Experience Platform Launch]** card, verify the following:

   * Onder aan de kaart worden twee punten weergegeven.
   * De stip aan de linkerkant is zwart.

      Als de punt aan de rechterkant zwart is, kunt u alleen ontwikkelaars toevoegen. Als u een gebruiker wilt toevoegen, klikt u op de stip aan de linkerkant.
   c. Klik **[!UICONTROL + Add Users]**.

   d. Voer de Adobe-id van de gebruiker in.

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

   c. Voer de Adobe-id van de gebruiker in.

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
