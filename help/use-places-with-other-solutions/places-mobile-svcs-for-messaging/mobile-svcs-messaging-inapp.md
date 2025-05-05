---
title: Meldingen in de app
description: Deze sectie toont u hoe te om de Dienst van Plaatsen met Overseinen in-App te gebruiken.
exl-id: c655e64b-0737-44d5-b453-2ac02fb9cbcc
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '636'
ht-degree: 0%

---

# Meldingen in de app {#places-push-messaging}

De volgende informatie toont u hoe te om in-App berichten te vormen om van de gebeurtenissen van de Dienst van Plaatsen teweeg te brengen.

>[!IMPORTANT]
>
>De berichten moeten op een treffer van de Analyse zijn.

## Bericht in de app

Met Mobile Services kunt u locatiegegevens die naar Analytics worden verzonden, gebruiken als de triggergebeurtenis(sen) en/of -voorwaarde voor een bericht in de app. Als de berichten in-app van SDK in brand worden gestoken en niet op gegevens hoeven te wachten die door Analytics worden verwerkt, kunnen de berichten in echt - tijd verschijnen zodra de trekker voorkomt.

### Lokale meldingen

Hier volgt een lijst met de beschikbare berichttypen in de app:

* Volledig scherm
* Melding
* Lokale meldingen

Deze typen zijn in-app berichten omdat ze door de SDK worden geactiveerd. Lokale meldingen zien er uit en voelen zich als pushmeldingen omdat ze worden weergegeven wanneer de app op de achtergrond wordt uitgevoerd. Met deze meldingen worden ook realtime meldingen verzonden wanneer gebruikers uw API&#39;s invoeren of afsluiten terwijl de app op de achtergrond wordt uitgevoerd.

### Vereisten

Voordat u begint, begrijpt u hoe u een bericht in de app verzendt en maakt in Mobile Services en hoe triggers werken. Voor meer informatie, zie [ een in-app bericht creëren.](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.htmlhtml?lang=bl)

## Regels in Experience Platform Launch

U kunt regels voor Experience Platforms Launch maken die de gegevens die u wilt gebruiken als onderdeel van de triggerregels voor berichten in de app naar Analytics verzenden. U kunt gegevens van de uitbreidingen van Plaatsen in uw Experience Platform Launch als of gebeurtenissen en/of voorwaarden afhankelijk van uw gebruikscase gebruiken.

* Locatiegegevens gebruiken als de activeringsgebeurtenis.

  U kunt bijvoorbeeld gegevens naar Analytics verzenden wanneer een gebruiker een POI invoert.

* Locatiegegevens gebruiken als voorwaarde voor een activeringsgebeurtenis.

  Als u bijvoorbeeld een aangepaste metagegevenstag in de Plaatsingsservice hebt gemaakt voor het weer bij verschillende POI&#39;s, kunt u die metagegevens gebruiken als een parameter voor de regelvoorwaarde. Hoewel u deze voorwaarde kunt gebruiken met een gebeurtenis van het POI-item die eerder is beschreven, kunt u de voorwaarde ook gebruiken als context voor elke gebeurtenis.

Nadat de regel opstelling met de juiste gebeurtenis en voorwaardenparameters is, voltooi uw regelconfiguratie door de actie te vormen om gegevens naar Analytics te verzenden.

## Een handeling maken

Een handeling maken:

1. Selecteer de extensie **[!UICONTROL Adobe Analytics]** .
1. Selecteer **[!UICONTROL Track.]** in de vervolgkeuzelijst **[!UICONTROL Action type]**
1. Typ een naam voor de handeling.
1. Selecteer in het rechterdeelvenster in **[!UICONTROL Context Data]** het sleutelwaardepaar om de contextgegevens in te stellen die naar Analytics worden verzonden.

U kunt bijvoorbeeld `poiname` als de sleutel selecteren en `{%%Last Entered POI Name}` als de waarde.

>[!TIP]
>
>De regels voor analyseverwerking kunnen worden ingesteld om deze contextgegevens op te halen. Voor meer informatie, zie [ Regels van de Verwerking ](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.html?lang=nl-NL). In het voorbeeld in *creeer een actie*, zal de Actie `poiname` als context verzenden om de POI ingangsgebeurtenis te beschrijven die naar Analytics wordt verzonden.

![ creërend een actie ](/help/assets/configure-action.png)

Hier is een voorbeeld van de volledige regel:

![ voltooide regel ](/help/assets/create-a-rule.png)

## Een bericht in de app maken in Mobile Services

Als deel van uw parameters van de Trekker, kunt u het publiek voor het bericht met gegevens van de Dienst van Plaatsen op één van de volgende manieren tot stand brengen:

* Locatiespecifieke acties zoals een entry of een exit gebruiken.
* Het gebruiken van meta-gegevens POI die als contextgegevens worden verzonden om het doel van uw publiek te beperken.

  Deze optie kan worden gebruikt met een locatiespecifieke actie, zoals ingang, of het kan als context aan een andere gebeurtenis zoals een lancering of een knoopklik worden gebruikt.

  Hier is een voorbeeld van hoe u een bericht in de app configureert om gebruikers welkom te heten die een POI invoeren die **[!UICONTROL Adobe]** in de naam heeft:

  ![ trekkerparameters ](/help/assets/trigger-parameters.png)

* De parameters in de rubrieken van de Dienst van Plaatsen in de *Triggers en Traits* pagina in de Mobiele Diensten werken niet met gegevens van de Dienst van Plaatsen.

  Die parameters zijn slechts voor het gegevensbestand van de Dienst van Verouderde Plaatsen dat in de Mobiele Diensten werd gecreeerd.
