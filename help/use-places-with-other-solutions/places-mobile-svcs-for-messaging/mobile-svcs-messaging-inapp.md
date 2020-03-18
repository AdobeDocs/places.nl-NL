---
title: Meldingen in de app
description: Deze sectie toont u hoe te om de Dienst van Plaatsen met Overseinen in-App te gebruiken.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b

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
* Waarschuwing
* Lokale meldingen

Deze typen zijn in-app berichten omdat ze door de SDK worden geactiveerd. Lokale meldingen zien er uit en voelen zich als pushmeldingen omdat ze worden weergegeven wanneer de app op de achtergrond wordt uitgevoerd. Met deze meldingen worden ook realtime meldingen verzonden wanneer gebruikers uw API&#39;s invoeren of afsluiten terwijl de app op de achtergrond wordt uitgevoerd. Voor meer informatie zie de uitbreiding [van de Monitor van](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)Plaatsen.

### Vereisten

Voordat u begint, begrijpt u hoe u een bericht in de app verzendt en maakt in Mobile Services en hoe triggers werken. Zie Een bericht in de app [maken voor meer informatie.](https://docs.adobe.com/content/help/en/mobile-services/using/messaging-ug/inapp-messages/t-in-app-message.html)

## Regels voor het starten van het Experience Platform

U kunt de regels van de Lancering van het Platform van de Ervaring tot stand brengen die de gegevens verzenden die u als deel van uw in-app berichttrekkerregels aan Analytics wilt kunnen gebruiken. U kunt gegevens van de uitbreidingen van Plaatsen in uw regels van de Lancering van het Platform van de Ervaring als of gebeurtenissen en/of voorwaarden afhankelijk van uw gebruiksgeval gebruiken.

* Locatiegegevens gebruiken als de activeringsgebeurtenis.

   U kunt bijvoorbeeld gegevens naar Analytics verzenden wanneer een gebruiker een POI invoert.

* Locatiegegevens gebruiken als voorwaarde voor een activeringsgebeurtenis.

   Als u bijvoorbeeld een aangepaste metagegevenstag in de Plaatsingsservice hebt gemaakt voor het weer bij verschillende POI&#39;s, kunt u die metagegevens gebruiken als een parameter voor de regelvoorwaarde. Hoewel u deze voorwaarde kunt gebruiken met een gebeurtenis van het POI-item die eerder is beschreven, kunt u de voorwaarde ook gebruiken als context voor elke gebeurtenis.

Nadat de regel opstelling met de juiste gebeurtenis en voorwaardenparameters is, voltooi uw regelconfiguratie door de actie te vormen om gegevens naar Analytics te verzenden.

## Een handeling maken

Een handeling maken:

1. Selecteer de **[!UICONTROL Adobe Analytics]** extensie.
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Action type]** de optie **[!UICONTROL Track.]**
1. Typ een naam voor de handeling.
1. In de juiste ruit, binnen **[!UICONTROL Context Data]**, selecteer het zeer belangrijk-waardepaar om de contextgegevens te plaatsen die naar Analytics zullen worden verzonden.

U kunt bijvoorbeeld selecteren `poiname` als de sleutel en `{%%Last Entered POI Name}` als de waarde.

>[!TIP]
>
>De regels voor analyseverwerking kunnen worden ingesteld om deze contextgegevens op te halen. Zie [Verwerkingsregels](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-processing-rules.html)voor meer informatie. In het voorbeeld in *Een handeling* maken verzendt de handeling de gebeurtenis `poiname` als de context voor het beschrijven van de gebeurtenis POI-invoer die naar Analytics wordt verzonden.

![een handeling maken](/help/assets/configure-action.png)

Hier is een voorbeeld van de volledige regel:

![voltooide regel](/help/assets/create-a-rule.png)

## Een bericht in de app maken in Mobile Services

Als deel van uw parameters van de Trekker, kunt u het publiek voor het bericht met gegevens van de Dienst van Plaatsen op één van de volgende manieren tot stand brengen:

* Locatiespecifieke acties zoals een entry of een exit gebruiken.
* Het gebruiken van meta-gegevens POI die als contextgegevens worden verzonden om het doel van uw publiek te beperken.

   Deze optie kan worden gebruikt met een locatiespecifieke actie, zoals ingang, of het kan als context aan een andere gebeurtenis zoals een lancering of een knoopklik worden gebruikt.

   Hier is een voorbeeld van hoe te om een in-app bericht te vormen om gebruikers te verwelkomen die POI ingaan die **[!UICONTROL Adobe]** in de naam heeft:

   ![triggerparameters](/help/assets/trigger-parameters.png)

* De parameters in de rubrieken van de Dienst van Plaatsen in de *Triggers en de pagina van Traits* in de Mobiele Diensten werken niet met gegevens van de Dienst van Plaatsen.

   Die parameters zijn slechts voor het gegevensbestand van de Dienst van Verouderde Plaatsen dat in de Mobiele Diensten werd gecreeerd.