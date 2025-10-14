---
title: Het creëren van een regel voor uw bezit van de Dienst van Plaatsen
description: De Plaatsen SDK houdt spoor van de huidige plaats, controleert gevormde POIs rond de huidige plaats, en volgt de ingang en uitgangsgebeurtenissen voor deze POIs.
exl-id: dd5aa7ac-55f9-44dc-8632-e483ef3b91a0
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 11%

---

# In- en uitreisregels maken {#create-entry-exit-rules}

Met de extensie Plaatsen en een oplossing voor gebiedscontrole geïnstalleerd in uw mobiele toepassing, kunt u regels in Adobe Experience Platform Launch tot stand brengen die of geconditioneerde plaatsgegevens met inbegrip van plaats ingang en uitgangsgebeurtenissen worden teweeggebracht.

## Regels

U kunt een regel configureren, die bestaat uit een gebeurtenis, een voorwaarde en een handeling. Elke regel bestaat uit de volgende elementen:

* Een of meer gebeurtenissen
* (Optioneel) Voorwaarden
* Een of meer handelingen

### Plaatst Service-gebeurtenissen

De Dienst van Plaatsen biedt de volgende gebeurtenissen aan waarop u een regel kunt in werking stellen:

* **ga POI** in, die door de Plaatsen SDK wordt teweeggebracht wanneer uw klant POI ingaat die u vormde.
* **Uitgang POI**, die door de Plaatsen SDK wordt teweeggebracht wanneer uw klant POI weggaat die u vormde.

### Servicevoorwaarden plaatsen

De voorwaarden bepalen de criteria dat de gegevens verbonden aan de gebeurtenis, of de gedeelde staat van een uitbreiding op dat geval, moeten voldoen om de te nemen actie. U kunt bijvoorbeeld een voorwaarde zodanig instellen dat een handeling wordt geactiveerd wanneer een product een keer wordt binnengebracht in een koffiewinkel, alleen in de stad San Francisco.

In de SDK van Plaatsen blijven de volgende statussen behouden:

* Huidige POI, die verwijst naar de POI waarin uw klant zich momenteel bevindt.
* Laatst afgesloten POI, die verwijst naar de meest recente POI die uw klant heeft verlaten.
* Laatst ingevoerde POI, die verwijst naar de meest recente POI die uw klant heeft ingevoerd.

Elke POI bevat de volgende gegevenselementen:

* ID
* Naam
* Breedte/lengte
* Straal
* Metagegevens zoals plaats, land, staat, categorie

### Acties

Handelingen bepalen wat de toepassing moet doen als reactie op de voorwaarde dat aan de regel is voldaan voor de geactiveerd gebeurtenis. Bijvoorbeeld, wanneer uw klant uw POI ingaat, kunt u een welkome bericht vormen om op hun mobiel apparaat te tonen.

## Een regel maken: een voorbeeld

>[!CAUTION]
>
>In dit voorbeeld wordt ervan uitgegaan dat u een POI-bibliotheek van alle koffiebars in de Verenigde Staten hebt gemaakt. Voor meer informatie over het creëren van POIs en bibliotheken, zie [&#x200B; een POI &#x200B;](/help/poi-mgmt-ui/create-a-poi-ui.md) creëren en *een Bibliotheek* in [&#x200B; leiden veelvoudige bibliotheken &#x200B;](https://experienceleague.adobe.com/docs/places/using/poi-mgmt-ui/manage-libraries-in-the-places-ui.html?lang=nl-NL).

De volgende procedure is een voorbeeld van hoe u een regel kunt maken die een post terugstuurt naar de Slack wanneer u een koffiewinkel in San Francisco betreedt.

De gebeurtenis, de voorwaarde en de handeling worden op de volgende manieren gedefinieerd:

* **Gebeurtenis**: De ingangsgebeurtenis van Plaatsen.
* **Voorwaarde**: De stad voor de **Huidige POI** is San Francisco
* **Actie**: Verzend een postback naar Slack de naam van de koffiewinkel die uw klant inging.

### Voorwaarde

Voordat u een regel maakt, moet u een gegevenselement in Adobe Experience Platform Launch maken. De elementen van gegevens bevolken automatisch de noodzakelijke informatie over uw POI in het postbackbericht.

Een gegevenselement maken in Experience Platform Launch:

1. Klik de **Elementen van Gegevens** tabel.
1. Klik **toevoegen het Element van Gegevens**.
1. Typ een naam, bijvoorbeeld, **Huidige naam van de koffiewinkel**.
1. In de **drop-down lijst van de Uitbreiding**, uitgezochte **Plaatsen - Beta**.
1. In **Element van Gegevens**, uitgezochte **Stad**.
1. In de juiste ruit, uitgezochte **Huidige POI**.
1. Klik **sparen**.

### Een regel maken in het Experience Platform Launch voor Plaatsen

![&#x200B; creërend een regel &#x200B;](/help/assets/placesrule.png)

1. Klik in Experience Platform Launch op het tabblad **[!UICONTROL Rules]**.
1. Klik op **[!UICONTROL Add Rule]**.
1. Typ een naam voor de regel, bijvoorbeeld **[!UICONTROL Track entry for coffee shop in SF]** .

### Een gebeurtenis maken

1. Klik in de sectie Gebeurtenissen op **[!UICONTROL + Add]** . Gebeurtenissen bepalen wanneer de regel moet worden geactiveerd.
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Extension]** de optie **[!UICONTROL Places – Beta]**.
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Event Type]** de optie **[!UICONTROL Enter POI]**.
1. Voer in **[!UICONTROL Name]** een naam in voor de gebeurtenis, bijvoorbeeld **[!UICONTROL Entering a coffee shop]**.
1. Klik op **[!UICONTROL Keep Changes]**.

### Een voorwaarde maken

1. Klik in de sectie Voorwaarden op **[!UICONTROL +Add]** . De voorwaarden bepalen aan welke criteria moet worden voldaan om de actie te ondernemen.
1. Selecteer Standaard in **[!UICONTROL Logic Type]**. Hiermee kunnen handelingen worden uitgevoerd als aan de voorwaarde is voldaan.
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Extension]** de optie **[!UICONTROL Places – Beta]**.
1. In **[!UICONTROL Condition Type]** selecteert u **[!UICONTROL City]**.
1. Typ een voorwaardennaam, bijvoorbeeld **[!UICONTROL Coffee shop in SF]** .
1. Klik in het rechterdeelvenster op **[!UICONTROL Current POI]** en selecteer in de vervolgkeuzelijst **[!UICONTROL San Francisco]** als een van uw steden.
1. Klik op **[!UICONTROL Keep Changes]**.

### Een handeling maken

1. Klik in de sectie **[!UICONTROL Actions]** op **[!UICONTROL + Add]** .
1. Laat in de vervolgkeuzelijst **[!UICONTROL Extension]** de standaardoptie **[!UICONTROL Mobile Core]** geselecteerd.
1. Selecteer een actietype, bijvoorbeeld **[!UICONTROL Send Postback]** .

   a. Typ in **[!UICONTROL URL]** de postback-URL voor de Slack, bijvoorbeeld `https://hooks.slack.com/services/` .

   b. Schakel het selectievakje **[!UICONTROL Add Post Body]** in als u een berichttekst wilt verzenden.

   c. Voeg in **[!UICONTROL Post Body]** de tekst van de post toe, bijvoorbeeld: `{ "text": "A customer has entered" }`

   c. Typ bijvoorbeeld een inhoudstype **[!UICONTROL application/json]** .

   d. Selecteer een time-outwaarde, bijvoorbeeld **[!UICONTROL 5]** .

1. Klik op **[!UICONTROL Keep Changes]**.

### Publish the rule

1. Als u de regel wilt activeren, moet u deze publiceren. Voor meer informatie over het publiceren van uw regel in Experience Platform Launch, zie [&#x200B; het Publiceren &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/tags/publish/overview.html?lang=nl-NL).

### Buiten entry&#39;s en exit&#39;s denken

Het gebruiken van de diensten van Plaatsen de geo-fence ingangen en de uitgang om regels in Experience Platform Launch teweeg te brengen is ongelooflijk krachtig, maar u kunt plaatsgegevens als voorwaarde voor andere gebeurtenissen ook gebruiken om in brand te steken. U kunt bijvoorbeeld een gebeurtenistrigger voor Mobile Core Track Action hebben die klaar is om te worden geactiveerd op basis van een bepaalde trackAction-aanroepgebeurtenis in uw app. Op basis van deze gebeurtenis kunt u aanvullende locatievoorwaarden aan de gebeurtenis toevoegen voordat een actie wordt uitgevoerd. Bijvoorbeeld, open omhoog een in-app onderzoek wanneer een aankoop `trackAction` gebeurtenis voorkomt, maar **slechts** als de huidige plaats van de gebruiker specifieke meta-gegevens van de Dienst van Plaatsen omvat.

![&#x200B; creeer een voorwaarde &#x200B;](/help/assets/places-condition.png)
