---
title: Rapport over locatiegegevens in Analytics Workspace
description: Deze sectie bevat informatie over het rapporteren van locatiegegevens in de Analytics Workspace.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 6%

---


# Rapport over locatiegegevens in de werkruimte Analytics {#places-in-workspace}

In dit document ziet u hoe u gegevens over uw locatie kunt rapporteren in de werkruimte Analytics. Elke stap bevat een overzicht op hoog niveau, met details die worden verstrekt door naar andere documentatiepagina&#39;s te verwijzen.

## Vereisten

Dit document gaat uit van het volgende:

1. De extensie Plaatsen is geïmplementeerd in uw toepassing.

   Zie Extensies [plaatsen voor meer informatie over het implementeren van de extensie Plaatsen](/help/places-ext-aep-sdks/places-extension/places-extension.md).

1. De Adobe Analytics-gebruiker is een beheerder en heeft toegang tot verwerkingsregels.

   Zie Overzicht [van](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)verwerkingsregels voor meer informatie over verwerkingsregels.

1. In het bezit van de Lancering, zijn de gegevenselementen gecreeerd voor de variabelen van de Dienst van Plaatsen die u wilt.

   Zie Een gegevenselement [](/help/use-places-launch-workflow/define-data-elements.md)definiëren voor meer informatie over gegevenselementen in Launch.


## 1. Een opstartregel maken

Creeer een regel die SDK zal veroorzaken om gegevens naar Analytics te verzenden wanneer het apparaat POI ingaat. Het creëren van dit soort regel wordt beschreven op de [Send POI ingang en uitgangsgegevens aan de pagina van Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md) .

In dit voorbeeld zijn voor de handeling van de regel de volgende waarden gedefinieerd voor de analyseaanvraag:

* **[!UICONTROL Action]** wordt opgegeven als waarde **[!UICONTROL Places Entry]**.

* De contextgegevenssleutel **[!UICONTROL poi.name]** wordt ingesteld op de waarde van het gegevenselement **[!UICONTROL {%%POI Name%%}]**.

![&quot;Een handeling instellen&quot;](/help/assets/pt-setAction.png)

## 2. Analysevariabelen maken

Om de contextgegevens (verzonden in stap 1) in kaart te brengen, moeten de variabelen eerst voor de het rapportreeks van Analytics worden gecreeerd. Zie [Conversievariabelen (Vars)](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-conversion-variables-evar.html)voor meer informatie over het maken van variabelen in Analytics.

In dit voorbeeld is een conversievariabele **[!UICONTROL Evar2]** gemaakt en benoemd **[!UICONTROL Places POI Name]**. Voor elke locatievariabele die u in de rapportage wilt weergeven, moeten extra variabelen worden gemaakt.

![&quot;Een analytische variabele maken&quot;](/help/assets/aa-evar.png)

## 3. Verwerkingsregels maken

Deze stap is nodig om contextgegevens (stap 1) toe te wijzen aan analytische variabelen (stap 2). Voor meer informatie bij het creëren van verwerkingsregels, zie het overzicht [van de](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)Regels van de Verwerking.

In dit voorbeeld is een verwerkingsregel gemaakt om de waarde van de contextgegevens in **[!UICONTROL poi.name]** kaart te brengen **[!UICONTROL Places POI Name (eVar2)]**. Voor elke gemaakte locatievariabele moeten aanvullende verwerkingsregels worden gemaakt.

![&quot;Een verwerkingsregel maken&quot;](/help/assets/aa-processing-rule.png)

## 4. Een rapport genereren in Workspace

Deze stap toont een basisrapport in de Werkruimte van Analytics om de gegevens te bekijken die in stappen 1-3 worden verzameld. Zie Overzicht [van de](https://docs.adobe.com/content/help/en/analytics/analyze/analysis-workspace/analysis-workspace-features.html)analytische werkruimte voor meer informatie over het gebruik van de analytische werkruimte.

In dit voorbeeld heeft het rapport de volgende instellingen:

* Metrisch - **[!UICONTROL Occurrences]**

* Dimension - **[!UICONTROL Action Name]**

   * Verbroken door Dimension - **[!UICONTROL Places POI Name]**

![&quot;Een rapport maken in de werkruimte&quot;](/help/assets/aa-workspace.png)
