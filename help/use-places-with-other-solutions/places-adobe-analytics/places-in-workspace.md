---
title: Rapport over locatiegegevens in Analytics Workspace
description: Deze sectie bevat informatie over het rapporteren van locatiegegevens in de Analytics Workspace.
exl-id: 45ca3c80-71b7-41de-9b00-645504061935
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# Rapport over locatiegegevens in de werkruimte Analytics {#places-in-workspace}

In dit document ziet u hoe u gegevens over uw locatie kunt rapporteren in de werkruimte Analytics. Elke stap bevat een overzicht op hoog niveau, met details die worden verstrekt door naar andere documentatiepagina&#39;s te verwijzen.

## Vereisten

Dit document gaat uit van het volgende:

1. De extensie Plaatsen is geïmplementeerd in uw toepassing.

   Voor meer informatie over het uitvoeren van de uitbreiding van Plaatsen, zie [Extensies plaatsen](/help/places-ext-aep-sdks/places-extension/places-extension.md).

1. De Adobe Analytics-gebruiker is een beheerder en heeft toegang tot verwerkingsregels.

   Zie voor meer informatie over verwerkingsregels [Overzicht van verwerkingsregels](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.html).

1. In het bezit van de Lancering, zijn de gegevenselementen gecreeerd voor de variabelen van de Dienst van Plaatsen die u wilt.

   Voor meer informatie over gegevenselementen in Lancering, zie [Een gegevenselement definiëren](/help/use-places-launch-workflow/define-data-elements.md).


## 1. Een opstartregel maken

Creeer een regel die SDK zal veroorzaken om gegevens naar Analytics te verzenden wanneer het apparaat POI ingaat. Het maken van dit soort regels wordt beschreven op het tabblad [POI-invoer- en afsluitgegevens naar Analytics verzenden](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md) pagina.

In dit voorbeeld zijn voor de handeling van de regel de volgende waarden gedefinieerd voor de analyseaanvraag:

* **[!UICONTROL Action]** wordt opgegeven als waarde van **[!UICONTROL Places Entry]**.

* De toets met contextgegevens **[!UICONTROL poi.name]** is ingesteld op de waarde van het gegevenselement **[!UICONTROL {%%POI Name%%}]**.

![Een handeling instellen](/help/assets/pt-setAction.png)

## 2. Maak analytische variabelen

Om de contextgegevens (verzonden in stap 1) in kaart te brengen, moeten de variabelen eerst voor de het rapportreeks van Analytics worden gecreeerd. Zie voor meer informatie over het maken van variabelen in Analytics [Conversievariabelen (eVars)](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/evar.html).

In dit voorbeeld, een omzettingsvariabele, **[!UICONTROL Evar2]**, is gemaakt en heeft een naam **[!UICONTROL Places POI Name]**. Voor elke locatievariabele die u in de rapportage wilt weergeven, moeten extra variabelen worden gemaakt.

![&quot;Een analytische variabele maken&quot;](/help/assets/aa-evar.png)

## 3. Verwerkingsregels instellen

Deze stap is nodig om contextgegevens (stap 1) toe te wijzen aan analytische variabelen (stap 2). Voor meer informatie over het creëren van verwerkingsregels, zie [Overzicht van verwerkingsregels](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.html).

In dit voorbeeld is een verwerkingsregel gemaakt om de waarde van de contextgegevens toe te wijzen **[!UICONTROL poi.name]** in **[!UICONTROL Places POI Name (eVar2)]**. Voor elke gemaakte locatievariabele moeten aanvullende verwerkingsregels worden gemaakt.

![&quot;Een verwerkingsregel maken&quot;](/help/assets/aa-processing-rule.png)

## 4. Genereer een rapport in Workspace

Deze stap toont een basisrapport in de Werkruimte van Analytics om de gegevens te bekijken die in stappen 1-3 worden verzameld. Voor meer informatie over hoe te om de Werkruimte van de Analyse te gebruiken, zie [Overzicht van de analysewerkruimte](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/home.html).

In dit voorbeeld heeft het rapport de volgende instellingen:

* Metrisch - **[!UICONTROL Occurrences]**

* DIMENSION - **[!UICONTROL Action Name]**

   * Verbroken door Dimension - **[!UICONTROL Places POI Name]**

![&quot;Een rapport maken in de werkruimte&quot;](/help/assets/aa-workspace.png)
