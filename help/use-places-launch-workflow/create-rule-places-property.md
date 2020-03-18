---
title: Het creëren van een regel voor uw bezit van de Dienst van Plaatsen
description: 'De Plaatsen SDK houdt spoor van de huidige plaats, controleert gevormde POIs rond de huidige plaats, en volgt de ingang en uitgangsgebeurtenissen voor deze POIs. '
translation-type: tm+mt
source-git-commit: c22efc36f2eac6b20fc555d998c3988d8c31169e

---


# In- en uitreisregels maken {#create-entry-exit-rules}

Met de extensie Plaatsen en de extensies Places Monitor die in uw mobiele toepassing zijn geïnstalleerd, kunt u in Adobe Experience Platform Launch regels maken die getriggerde of geconditioneerde locatiegegevens bevatten, zoals gebeurtenissen voor het in- en uitschakelen van de locatie.

## Regels

U kunt een regel configureren, die bestaat uit een gebeurtenis, een voorwaarde en een handeling. Elke regel bestaat uit de volgende elementen:

* Een of meer gebeurtenissen
* (Optioneel) Voorwaarden
* Een of meer handelingen

### Plaatst Service-gebeurtenissen

De Dienst van Plaatsen biedt de volgende gebeurtenissen aan waarop u een regel kunt in werking stellen:

* **Ga POI** in, die door Plaatsen SDK wordt teweeggebracht wanneer uw klant POI ingaat die u vormde.
* **Sluit POI**, die door Plaatsen SDK wordt teweeggebracht wanneer uw klant POI weggaat die u vormde.

### Servicevoorwaarden plaatsen

De voorwaarden bepalen de criteria dat de gegevens verbonden aan de gebeurtenis, of de gedeelde staat van een uitbreiding op dat geval, moeten voldoen om de te nemen actie. U kunt bijvoorbeeld een voorwaarde zodanig instellen dat een handeling wordt geactiveerd wanneer een product een keer wordt binnengebracht in een koffiewinkel, alleen in de stad San Francisco.

In de SDK van Plaatsen blijven de volgende statussen behouden:

* Huidige POI, die verwijst naar de POI waarin uw klant zich momenteel bevindt.
* Laatst afgesloten POI, die verwijst naar de meest recente POI die uw klant heeft verlaten.
* Laatst ingevoerde POI, die verwijst naar de meest recente POI die uw klant heeft ingevoerd.

Elke POI bevat de volgende gegevenselementen:

* ID
* Naam
* Breedtegraad/lengtegraad
* Straal
* Metagegevens zoals plaats, land, staat, categorie

### Handelingen

Handelingen bepalen wat de toepassing moet doen als reactie op de voorwaarde dat aan de regel is voldaan voor de geactiveerd gebeurtenis. Bijvoorbeeld, wanneer uw klant uw POI ingaat, kunt u een welkome bericht vormen om op hun mobiel apparaat te tonen.

## Een regel maken: een voorbeeld

>[!CAUTION]
>
>In dit voorbeeld wordt ervan uitgegaan dat u een POI-bibliotheek van alle koffiebars in de Verenigde Staten hebt gemaakt. For more information about creating POIs and libraries, see [Create a POI](/help/poi-mgmt-ui/create-a-poi-ui.md) and *Create a Library* in [Manage multiple libraries](https://docs.adobe.com/content/help/en/places/using/poi-mgmt-ui/manage-libraries-in-the-places-ui.html).

De volgende procedure is een voorbeeld van hoe te om een regel tot stand te brengen die een post naar Slack terugstuurt wanneer u een koffiewinkel in San Francisco ingaat.

De gebeurtenis, de voorwaarde en de handeling worden op de volgende manieren gedefinieerd:

* **Gebeurtenis**: Plaatst gebeurtenis entry.
* **Voorwaarde**: De stad voor de **Huidige POI** is San Francisco
* **Actie**: Stuur een postback naar Slack met de naam van de koffiewinkel die uw klant heeft ingevoerd.

### Vereiste

Voordat u een regel maakt, moet u een gegevenselement maken in Adobe Experience Platform Launch. De elementen van gegevens bevolken automatisch de noodzakelijke informatie over uw POI in het postbackbericht.

Een gegevenselement maken bij het starten van het Experience Platform:

1. Klik op het tabblad **Gegevenselementen** .
1. Klik op Gegevenselement **** toevoegen.
1. Typ een naam, bijvoorbeeld de naam **van de** huidige koffiewinkel.
1. Selecteer **Plaatsen - bèta in de vervolgkeuzelijst** Extensie ****.
1. Selecteer **Plaats** in **Gegevenselement**.
1. Selecteer **Huidige POI** in het rechterdeelvenster.
1. Klik op **Opslaan**.

### Creeer een regel in de Lancering van het Platform van de Ervaring voor de Dienst van Plaatsen

![regel maken](/help/assets/placesrule.png)

1. Klik in Experience Platform Launch op het tabblad **[!UICONTROL Rules]**.
1. Klik op **[!UICONTROL Add Rule]**.
1. Typ bijvoorbeeld een naam voor de regel **[!UICONTROL Track entry for coffee shop in SF]**.

### Een gebeurtenis maken

1. Klik in de sectie Gebeurtenissen op **[!UICONTROL + Add]**. Gebeurtenissen bepalen wanneer de regel moet worden geactiveerd.
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Extension]** de optie **[!UICONTROL Places – Beta]**.
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Event Type]** de optie **[!UICONTROL Enter POI]**.
1. Voer in **[!UICONTROL Name]** een naam in voor de gebeurtenis, bijvoorbeeld **[!UICONTROL Entering a coffee shop]**.
1. Klik op **[!UICONTROL Keep Changes]**.

### Een voorwaarde maken

1. Klik in de sectie Voorwaarden op **[!UICONTROL +Add]**. De voorwaarden bepalen aan welke criteria moet worden voldaan om de actie te ondernemen.
1. Selecteer Standaard in **[!UICONTROL Logic Type]**. Hiermee kunnen handelingen worden uitgevoerd als aan de voorwaarde is voldaan.
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Extension]** de optie **[!UICONTROL Places – Beta]**.
1. In **[!UICONTROL Condition Type]** selecteert u **[!UICONTROL City]**.
1. Typ bijvoorbeeld de naam van een voorwaarde **[!UICONTROL Coffee shop in SF]**.
1. Klik in het rechterdeelvenster op **[!UICONTROL Current POI]** en selecteer in de vervolgkeuzelijst **[!UICONTROL San Francisco]** als een van uw steden.
1. Klik op **[!UICONTROL Keep Changes]**.

### Een handeling maken

1. Klik in de **[!UICONTROL Actions]** sectie op **[!UICONTROL + Add]**.
1. Laat in de **[!UICONTROL Extension]** vervolgkeuzelijst de standaardoptie **[!UICONTROL Mobile Core]** geselecteerd.
1. Selecteer bijvoorbeeld een handelingstype **[!UICONTROL Send Postback]**.

   a. Typ in **[!UICONTROL URL]**, bijvoorbeeld, de postback-URL voor Slack `https://hooks.slack.com/services/`.

   b. Als u een berichttekst wilt verzenden, schakelt u het **[!UICONTROL Add Post Body]** selectievakje in.

   c. Voeg in **[!UICONTROL Post Body]** dit voorbeeld de berichttekst toe: `{ "text": "A customer has entered" }`

   c. Typ bijvoorbeeld een inhoudstype **[!UICONTROL application/json]**.

   d. Selecteer bijvoorbeeld een time-outwaarde **[!UICONTROL 5]**.

1. Klik op **[!UICONTROL Keep Changes]**.

### De regel publiceren

1. Als u de regel wilt activeren, moet u deze publiceren. Voor meer informatie over het publiceren van uw regel in de Lancering van het Platform van de Ervaring, zie het [Publiceren](https://docs.adobe.com/content/help/en/launch/using/reference/publish/overview.html).

### Buiten entry&#39;s en exposities denken

Het gebruiken van de dienst van Plaatsen de geo-fence ingangen en de uitgang om regels in de Lancering van het Platform van de Ervaring teweeg te brengen is ongelooflijk krachtig, maar u kunt plaatsgegevens als voorwaarde voor andere gebeurtenissen ook gebruiken om in brand te steken. U kunt bijvoorbeeld een gebeurtenistrigger voor Mobile Core Track Action hebben die klaar is om te worden geactiveerd op basis van een bepaalde trackAction-aanroepgebeurtenis in uw app. Op basis van deze gebeurtenis kunt u aanvullende locatievoorwaarden aan de gebeurtenis toevoegen voordat een actie wordt uitgevoerd. Open bijvoorbeeld een enquête in de app wanneer een aankoopgebeurtenis `trackAction` plaatsvindt, maar **alleen** als de huidige locatie van de gebruiker specifieke metagegevens van de Places-service bevat.

![een voorwaarde maken](/help/assets/places-condition.png)