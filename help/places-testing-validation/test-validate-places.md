---
title: Plaatsingsservice testen en valideren
description: Deze sectie bevat informatie over het testen en valideren van Plaatsen Service.
translation-type: tm+mt
source-git-commit: 5a21e734c0ef56c815389a9f08b445bedaae557a

---


# Aanbevelingen voor het testen van Plaatsen {#test-validate-loc-svc}

Vele klanten en organisaties zullen POIs over de wereld bepalen, zodat is het belangrijk om een manier te hebben om te simuleren en te testen hoe de Dienst van Plaatsen met uw toepassing interactie aangaat. Deze informatie helpt u begrijpen hoe te om de ingangen en de uitgang van de Dienst van Plaatsen te testen en te bevestigen die correct worden teweeggebracht gebaseerd op bepaalde POIs en de huidige plaats van een gebruiker.

Omdat omgevingsvariabelen een factor kunnen zijn in het locatiesignaal en de nauwkeurigheid, raden we u aan eerst de basislijnresultaten vast te stellen door lokaal te werken met ontwikkelaarsgereedschappen en gesimuleerde locatie-items. Het doel is te bevestigen dat alle plaatsgebeurtenissen correct werken. Nadat de locatiegebeurtenissen correct zijn gevalideerd, kunnen de integratie van de oplossing (bijvoorbeeld Analytics, Target en Campaign) worden getest. Om uw testactiviteiten te helpen, zou u Slack Webhooks met een postback en ladingsGPX dossiers in uw individuele ontwikkelomgeving moeten plaatsen.

>[!IMPORTANT]
>
>Dit plan veronderstelt dat POIs in de Dienst UI [](https://places.adobe.com) van Plaatsen is gecreeerd en de recentste versies van de uitbreiding van Plaatsen en de uitbreiding van de Monitor van Plaatsen worden geïnstalleerd en correct gevormd. Voor meer informatie, zie de uitbreiding [van](/help/places-ext-aep-sdks/places-extension/places-extension.md) Plaatsen en de uitbreiding [van de Monitor van](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)Plaatsen.

| Stap | Beschrijving | Verwacht resultaat |
|--- |--- |--- |
| 1 | Bevestig dat de juiste manifestsleutels voor Android zijn ingegaan om toegang tot spoorplaats te verlenen. Voor meer informatie, zie toestemmingen [toevoegen aan manifest](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.html#add-permissions-to-the-manifest). | Bevestigd |
| 1a | De locatie-updates worden geconfigureerd in iOS. Zorg er ook voor dat u de juiste keuzelijsten hebt ingesteld in iOS om toestemming van de gebruiker te vragen om de locatie te traceren. Zie Locatie-updates op de achtergrond [inschakelen voor meer informatie.](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/using-places-monitor-extension.html#enable-location-updates-background) | Bevestigd |
| 2 | Bevestig welke controlemodus is ingesteld voor iOS. De continue modus zorgt voor een grotere nauwkeurigheid en persistentie, maar zorgt ook voor een langere batterijduur. Zie [Controlemodus (alleen iOS) voor meer informatie.](https://docs.adobe.com/content/help/en/places/using/places-ext-aep-sdks/places-monitor-extension/places-monitor-api-reference.html#monitoring-mode-ios-only) | Belangrijke wijzigingen of Doorlopende |
| 3 | Als u meerdere POI&#39;s-bibliotheken gebruikt, controleert u of de desbetreffende bibliotheken zijn geselecteerd in de extensie Plaatsen voor het starten van het Experience Platform. | Bevestigd |
| 4 | Bevestig dat de nieuwste versies van de extensies Mobile Core en Places/Places Monitor via Gradle of CocoaPods met de app zijn meegeleverd. | Bevestigd - raadpleeg de [releaseopmerkingen voor meer informatie over recente updates.](/help/release-notes.md) |
| 5 | Bevestig dat de juiste omgevingen zijn geconfigureerd voor testen. De milieu-id van de Lancering moet overeenkomen met de ontwikkelomgeving van de Launch. | Bevestigd |
| 6 | Maak GPX-bestanden voor elke POI die u wilt testen. GPX-bestanden kunnen in de lokale ontwikkelomgeving worden gebruikt om een locatie-item te simuleren. Raadpleeg het volgende voor informatie over het maken en gebruiken van GPX-bestanden: <br>[GPX-bestanden voor iOS-simulator [gesloten]](https://stackoverflow.com/questions/17292783/gpx-files-for-ios-simulator)<br>[https://mapstogpx.com/mobiledev.](https://mapstogpx.com/mobiledev.php)<br>[phpLOCATION TESTING IN MOBILE APPS](https://qacumtester.wordpress.com/2014/02/27/location-testing-in-mobile-apps/) | GPX-bestanden worden gemaakt en geladen in het app-project. |
| 7 | Zonder iets anders te doen, zou u de toepassing van Android Studio of XCode moeten kunnen lanceren en het aangewezen alarm zien om toegang voor de het volgen plaats te verzoeken. Klik op de machtiging *Altijd toestaan* .<br><br>We raden u aan een echt apparaat te gebruiken dat op uw computer is aangesloten in plaats van apparaatsimulator. | De vraag van het plaatsingsverzoek zou op toepassing moeten tonen die door winde wordt geladen |
| 8 | Nadat de locatiemachtiging is geaccepteerd. De Plaatsen SDK zal de huidige plaats van het apparaat terugwinnen en de uitbreiding van de Monitor van Plaatsen zal beginnen de 20 dichtste POIs van de huidige plaats te controleren | Zie het logboekvoorbeeld onder de tabel. |
| 9 | Het schakelen tussen verschillende plaatsen in XCode of Android studio zou entry gebeurtenissen voor specifieke POIs moeten veroorzaken. De onderstaande logboeken worden verwacht bij binnenkomst in een POI. | Zie het logboekvoorbeeld onder de tabel. |
| 10 | Nadat u de Monitor van Plaatsen dichtbij POIs ziet, zou u moeten testen door plaats te verzenden pingelt uit. In Lancering, creeer een nieuwe regel die de uitbreiding van Plaatsen gebruikt om op een geo-fence ingang teweeg te brengen. Maak vervolgens een nieuwe handeling met de Mobile Core om een Postback te verzenden. Door een Slack Webhaak-app te maken, kunt u locatie-items en -uitgangen zien. Zie Berichten [verzenden met binnenkomende webhooks voor informatie over het maken van een Slack Webhaak-app.](https://api.slack.com/messaging/webhooks) |  |
| 10a | In Lancering, zorg ervoor dat u gegevenselementen voor de uitbreiding van Plaatsen met inbegrip van het volgende toevoegde: <br>Huidige POI-<br>naamHuidige POI<br>latHuidige POI<br>longLaatste ingevoerde<br>naamLaatste ingevoerde<br>laatste ingevoerde<br>langeLaatst afgesloten<br>naamLaatste afgesloten<br>laatste afgesloten<br>lange tijdstempel |  |
| 10b | Een nieuwe regel maken met een gebeurtenis = Plaatsen → Voer de POI in |  |
| 10c | Een handeling maken = Mobile Core → Postback |  |
| 10d | Gebruik de URL van de Webhaak voor uw Slack-app, bijvoorbeeld https://hooks.slack.com/services/TKN5FKS68/BNFP7SVD..... |  |
| 10e | De post zou vergelijkbaar zijn met: `{text: User is in POI -  {%%Last Entered POI Name%%} in {%%Last Entered POI City%%} additional information: Radius:{%%Last Entered POI Radius%%} Timestamp: {%%timestamp%%}}`. <br>Zorg ervoor dat u de specifieke gegevenselementen gebruikt die u hier hebt gemaakt. |  |
| 10f | Zorg ervoor dat u alle nieuwe gegevenselementen en regelwijzigingen publiceert in Launch. (Selecteer een werkende dev-bibliotheek rechtsboven in de interface Launch.) |  |
| 11 | Start en test de toepassing opnieuw door te schakelen tussen de GPX-locaties in de ontwikkelings-IDE. | U zou Slack- berichten nu moeten zien die ingangen voor elke POI tonen aangezien u verschillende plaatsen in uw ontwikkelomgeving selecteert. |
|  | **SNELLE SAMENVATTING **<br>POINTAAl deze tests kunnen lokaal worden uitgevoerd zonder naar een specifieke plaats van de POI te moeten gaan. Het testen van de bevestiging helpt ervoor te zorgen dat uw toepassing correct wordt gevormd en de correcte toestemmingen voor de plaats heeft ontvangen.<br><br>Deze bevestiging geeft u ook vertrouwen dat de bepaalde POIs correct met de uitbreiding van de Monitor van Plaatsen werken.  Na deze stap, zullen wij beginnen overseinen in Campagne te testen om te zien of verschijnen de juiste berichten gebaseerd op POI ingangen en uitgang. |  |
|  | **Adobe Campagne Standard In-App Messaging testen met Places Service.** |  |
| 12 | Voor het belangrijkste dashboard van de Campagne vorm een nieuw in-app-Bericht (type = uitzending) |  |
| 12a | Selecteer in triggers het gebeurtenistype **Plaatsen - Invoer als trigger**. |  |
| 12b | Selecteer **[UICONTROL Plaatst de meta-gegevens]** van de Plaatsen van de Douane als extra filter - gebruik POI type = Laatste ingevoerde POI.<br>Wij gebruiken **[!UICONTROL Last Entered]** als het type van POI omdat in de meeste gevallen het zelfde als **[!UICONTROL Last Entered]** zal zijn **[!UICONTROL Current POI]**. <br><br>**[!UICONTROL Current POI]** mag alleen worden gebruikt in gevallen waarin er sprake is van overlappende geografische aanduidingen. In dit geval, moeten deze POIs worden RANKED en dan **[!UICONTROL Current POI]** zal de top gerangschikte POI uit de 2 of 3 geo-fences tonen die een gebruiker momenteel zou kunnen zijn. |  |
| 12c | Selecteer een sleutel van douanemetagegevens die u zal helpen beperken welke POIs een bericht zal ontvangen. |  |
| 12d | Voor frequentie en duur, houd aan slechts één of twee dagen, zodat als u niet van de criteria houdt, u de trekker in een kortere periode kunt verlopen. |  |
| 12e | Selecteer Altijd/Eenmaal of Tot de klik doorloopt, *ALTIJD* zodat u op meerdere locaties kunt testen. | Een bericht in de app wordt ALTIJD weergegeven wanneer u een locatiewijziging simuleert die voldoet aan de juiste metagegevenscriteria. |
| 12f | Selecteer voor de weergave een andere optie dan Lokale melding. Hierdoor is het gemakkelijker om te zien wanneer u op de voorgrond met de app test.) |  |
| 12g | Bereid/bevestig en implementeer het bericht in de app. |  |
| 13 | Sluit de toepassing af en start deze opnieuw om ervoor te zorgen dat de nieuwe campagnecriteria worden gedownload. | Vergeet niet dat de toepassingen volledig opnieuw moeten worden gestart om het nieuwe bestand met campagneregels naar het apparaat te kunnen downloaden. |
| 14 | In uw ontwikkeltoepassing, schakelaarplaatsen door de eerder gecreeerde GPX- dossiers te gebruiken. | Het bericht in de app wordt weergegeven op basis van de vorige criteria die zijn ingesteld. |
| 15 | Voor de volgende test, zullen wij in wezen de zelfde stappen kopiëren zoals voordien, maar dit keer zullen wij LOKALE VERKLARING testen. | Het verwachte resultaat is dat de lokale berichten worden getoond telkens als de passende criteria worden voldaan. |
| 16 | Vorm een nieuw in-app-Bericht (type = uitzending). |  |
| 16a | Selecteer in triggers de optie **[!UICONTROL Places event type]** - **[!UICONTROL Entry as the trigger]**. |  |
| 16b | Selecteer de metagegevens Aangepaste locaties als een aanvullend filter - gebruik **[!UICONTROL POI type]** = **[!UICONTROL Last Entered POI]**. |  |
| 16c | Selecteer een sleutel van douanemetagegevens die u zal helpen beperken welke POIs een bericht zal ontvangen. |  |
| 16d | Houd voor frequentie en duur slechts een of twee dagen aan, zodat u de trigger in een kortere periode kunt verlopen als u de criteria niet bevalt. |  |
| 16e | Voor Altijd/Eenmaal of Tot doorklikken. **[!UICONTROL ALWAYS]**. |  |
| 16f | Selecteer voor het weergavetype **[!UICONTROL Local Notification]**. |  |
| 16g | Bereid/bevestig en implementeer het bericht in de app. |  |
| 17 | Sluit in de ontwikkelomgeving uw apparaat aan en druk op **[!UICONTROL Play]** de build. Nadat u hebt vastgesteld dat de locatie werkt, plaatst u de toepassing op de achtergrond en gaat u door met het schakelen tussen locaties in Xcode of Android Studio. U zou consoleread-outs nog moeten zien die op de locatieverandering wijzen, en u zou lokale berichten ook moeten zien die afhankelijk van de criteria in uw trekker worden getoond. (Er kan een vertraging van 1 tot 2 seconden optreden.) | Het verwachte resultaat is dat lokale meldingen worden weergegeven wanneer aan de criteria wordt voldaan. |
|  | **SAMENVATTINGSPUNT** Op dit <br>moment zouden we POI-items moeten zien in onze lokale omgeving. We zouden ook berichten van Campagne moeten zien die op het werk van POI wordt gebaseerd. Als er fouten zijn, controleer om te zien of ging een Slack- bericht niet uit. Als er geen Slack-bericht is, controleert u de toepassingsconsole, omdat een nieuwe locatie-ingang mogelijk niet is opgenomen. Als de resultaten succesvol zijn, dan kunnen wij vrij zeker zijn dat de toepassing correct presteert en dat de de berichtendienst van Plaatsen en van de Campagne ook correct werkt. |  |
|  | **ON-SITE TESTING** <br>Niet veel hoeft te veranderen wanneer het testen op locatie wordt uitgevoerd. Als u de terugdraaifunctie actief houdt, kunt u beter begrijpen of het apparaat een invoer- en afsluitprocedure voor de locatie ontvangt. |  |
| 18 | Voer tests uit met apparaten die beginnen met wifi en cellulair uitgeschakeld en schakel vervolgens één keer in de POI-regio in. | Als er een mislukking is, merk op of u een geo-fence ingang en bericht in Slack krijgt. Wat is het tijdstempel op de kennisgeving van Slack? |
| 19 | Voer de test uit met alleen cellulair ingeschakeld en met de wifi uitgeschakeld. |  |
| 20 | Test met zowel mobiel als wifi ingeschakeld. |  |
|  | **SUMMARY POINT** <br>On-site tests moeten nauw overeenkomen met de ontwikkelingstests. Houd in mening dat er sommige milieufactoren die in spel kunnen komen in het bepalen van een gebruikersplaats, zoals duur die in een POI geo-fence wordt doorgebracht, beschikbaarheid van celsignaal, en sterkte van nabijgelegen wifi toegangspunten. |  |

## Logboekvoorbeelden

**Stap 8:** Logbestanden voor iOS en Android verwacht tijdens een update van de locatie

**iOS**

```
[AdobeExperienceSDK DEBUG <com.adobe.placesMonitor>]: Authorization status changed: Always
[AdobeExperienceSDK DEBUG <Places>]: Requesting 20 nearby POIs for device location (<lat>, <longitude>)
[AdobeExperienceSDK DEBUG <Places>]: Response from Places Query Service contained <n> nearby POIs
[AdobeExperienceSDK DEBUG <com.adobe.placesMonitor>]: Received a new list of POIs from Places: (
<ACPPlacePoi: 0x600002b75a40> Name: <poi name>; ID:<poi id>; Center: (<lat>, <long>); Radius: <radius>
..
..)   
```

**Android**

```
PlacesMonitor - All location settings are satisfied to monitor location
PlacesMonitor - PlacesMonitorInternal : New location obtained: <latitude> <longitude> Attempting to get the near by pois
PlacesExtension - Dispatching nearby places event with n POIs
PlacesMonitor - Attempting to Monitor POI with id <poi id> name <poi name> latitude <lat> longitude <longitude>
PlacesMonitor - Attempting to Monitor POI with id <poi id> name <poi name> latitude <lat> longitude <longitude>
PlacesMonitor - Attempting to Monitor POI with id <poi id> name <poi name> latitude <lat> longitude <longitude>
...
...
PlacesMonitor - Successfully added n fences for monitoring
```

**Stap 9:** Logbestanden voor iOS en Android verwacht tijdens een gebeurtenis

**iOS**

```
[AdobeExperienceSDK TRACE <Places>]: Dispatching Places region entry event for place ID <poiId>
```

**Android**

```
PlacesExtension -  Dispatching Places Region Event for <poi name> with eventType entry
```
