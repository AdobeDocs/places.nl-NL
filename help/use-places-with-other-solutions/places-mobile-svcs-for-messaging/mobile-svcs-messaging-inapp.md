---
title: Meldingen in de app
description: Deze sectie toont u hoe te om de Dienst van Plaatsen met Overseinen in-App te gebruiken.
exl-id: c655e64b-0737-44d5-b453-2ac02fb9cbcc
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '653'
ht-degree: 1%

---

# Meldingen in de app {#places-push-messaging}

De volgende informatie toont u hoe te om in-App berichten te vormen om van de gebeurtenissen van de Dienst van Plaatsen teweeg te brengen.

>[!IMPORTANT]
>
>De berichten moeten op een treffer van de Analyse zijn.

## Bericht in de app

Met Mobile Services kunt u locatiegegevens die naar Analytics worden verzonden, gebruiken als de triggergebeurtenis(sen) en/of -voorwaarde voor een bericht in de app. Als in-app berichten van SDK in brand worden gestoken en niet op gegevens hoeven te wachten die door Analytics worden verwerkt, kunnen de berichten in echt - tijd verschijnen zodra de trekker voorkomt.

### Lokale meldingen

Hier volgt een lijst met de beschikbare berichttypen in de app:

* Volledig scherm
* Melding
* Lokale meldingen

Deze typen zijn in-app berichten omdat ze door de SDK worden geactiveerd. Lokale meldingen zien er uit en voelen zich als pushmeldingen omdat ze worden weergegeven wanneer de app op de achtergrond wordt uitgevoerd. Met deze meldingen worden ook realtime meldingen verzonden wanneer gebruikers uw API&#39;s invoeren of afsluiten terwijl de app op de achtergrond wordt uitgevoerd.

### Vereisten

Voordat u begint, begrijpt u hoe u een bericht in de app verzendt en maakt in Mobile Services en hoe triggers werken. Zie voor meer informatie [Maak een bericht in de app.](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/inapp-messages/t-in-app-message.html)

## Regels in Experience Platform Launch

U kunt regels voor Experience Platforms Launch maken die de gegevens die u wilt gebruiken als onderdeel van de triggerregels voor berichten in de app naar Analytics verzenden. U kunt gegevens uit de extensies Plaatsen in uw Experience Platform Launch gebruiken als gebeurtenissen en/of voorwaarden, afhankelijk van uw gebruiksscenario.

* Locatiegegevens gebruiken als de activeringsgebeurtenis.

   U kunt bijvoorbeeld gegevens naar Analytics verzenden wanneer een gebruiker een POI invoert.

* Locatiegegevens gebruiken als voorwaarde voor een activeringsgebeurtenis.

   Als u bijvoorbeeld een aangepaste metagegevenstag in de Plaatsingsservice hebt gemaakt voor het weer bij verschillende POI&#39;s, kunt u die metagegevens gebruiken als een parameter voor de regelvoorwaarde. Hoewel u deze voorwaarde kunt gebruiken met een gebeurtenis van het POI-item die eerder is beschreven, kunt u de voorwaarde ook gebruiken als context voor elke gebeurtenis.

Nadat de regel opstelling met de juiste gebeurtenis en voorwaardenparameters is, voltooi uw regelconfiguratie door de actie te vormen om gegevens naar Analytics te verzenden.

## Een handeling maken

Een handeling maken:

1. Selecteer **[!UICONTROL Adobe Analytics]** extensie.
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Action type]** de optie **[!UICONTROL Track.]**
1. Typ een naam voor de handeling.
1. In het rechterdeelvenster, in **[!UICONTROL Context Data]** selecteert u het sleutelwaardepaar om de contextgegevens in te stellen die naar Analytics worden verzonden.

U kunt bijvoorbeeld `poiname` als sleutel en `{%%Last Entered POI Name}` als de waarde.

>[!TIP]
>
>De regels voor analyseverwerking kunnen worden ingesteld om deze contextgegevens op te halen. Zie voor meer informatie [Verwerkingsregels](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-processing-rules.html). In het voorbeeld in *Een handeling maken*, verzendt de actie de `poiname` als context om de gebeurtenis van de POI ingang te beschrijven die naar Analytics wordt verzonden.

![een handeling maken](/help/assets/configure-action.png)

Hier is een voorbeeld van de volledige regel:

![voltooide regel](/help/assets/create-a-rule.png)

## Een bericht in de app maken in Mobile Services

Als deel van uw parameters van de Trekker, kunt u het publiek voor het bericht met gegevens van de Dienst van Plaatsen op één van de volgende manieren tot stand brengen:

* Locatiespecifieke acties zoals een entry of een exit gebruiken.
* Het gebruiken van meta-gegevens POI die als contextgegevens worden verzonden om het doel van uw publiek te beperken.

   Deze optie kan worden gebruikt met een locatiespecifieke actie, zoals ingang, of het kan als context aan een andere gebeurtenis zoals een lancering of een knoopklik worden gebruikt.

   Hier is een voorbeeld van hoe te om een in-app bericht te vormen om gebruikers welkom te heten die POI ingaan die heeft **[!UICONTROL Adobe]** in de naam:

   ![triggerparameters](/help/assets/trigger-parameters.png)

* Parameters in de rubrieken Plaatsen in het dialoogvenster *Triggers en reizigers* pagina in Mobile Services werkt niet met gegevens van de Places Service.

   Die parameters zijn slechts voor het gegevensbestand van de Dienst van Verouderde Plaatsen dat in de Mobiele Diensten werd gecreeerd.
