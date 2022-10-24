---
title: Plaatsingsservice testen en valideren
description: Deze sectie bevat informatie over het testen en valideren van Plaatsen Service.
exl-id: 8dad6619-566b-4aea-b29c-a89192a66441
source-git-commit: 2b5c53887c9ed0f2a672c377121a39537ee58f01
workflow-type: tm+mt
source-wordcount: '1702'
ht-degree: 2%

---

# Recommendations to test Places Service {#test-validate-loc-svc}

Vele klanten en organisaties zullen POIs over de wereld bepalen, zodat is het belangrijk om een manier te hebben om te simuleren en te testen hoe de Dienst van Plaatsen met uw toepassing interactie aangaat. Deze informatie helpt u begrijpen hoe te om de ingangen en de uitgang van de Dienst van Plaatsen te testen en te bevestigen die correct worden teweeggebracht gebaseerd op bepaalde POIs en de huidige plaats van een gebruiker.

Omdat omgevingsvariabelen een factor kunnen zijn in het locatiesignaal en de nauwkeurigheid, raden we u aan eerst de basislijnresultaten vast te stellen door lokaal te werken met ontwikkelaarsgereedschappen en gesimuleerde locatie-items. Het doel is te bevestigen dat alle plaatsgebeurtenissen correct werken. Nadat de locatiegebeurtenissen correct zijn gevalideerd, kunnen de integratie van de oplossing (bijvoorbeeld Analytics, Target en Campaign) worden getest. Om uw testactiviteiten te helpen, zou u Slack Webhooks met een postback en ladingsGPX dossiers in uw individuele ontwikkelomgeving moeten plaatsen.

>[!IMPORTANT]
>
>Dit plan veronderstelt dat POIs in [Gebruikersinterface Plaatsingsservice](https://places.adobe.com) en de recentste versies van de uitbreiding van Plaatsen worden geïnstalleerd en correct gevormd. Als het doen van actieve gebiedscontrole, veronderstelt het ook een gebied controlerende oplossing wordt uitgevoerd. Zie voor meer informatie [Extensie Plaatsen](/help/places-ext-aep-sdks/places-extension/places-extension.md), [CoreLocation-documentatie](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) voor iOS, of [Documentatie over Android-locatie](https://developer.android.com/training/location/geofencing).

| Stap | Beschrijving | Verwacht resultaat |
|--- |--- |--- |
| 1 | Bevestig dat de juiste manifestsleutels voor Android zijn ingegaan om toegang tot spoorplaats te verlenen. | Bevestigd |
| 1 bis | Bevestig locatie-updates zijn geconfigureerd in iOS. Zorg er ook voor dat u de juiste keuzelijsten in iOS hebt ingesteld om toestemming van de gebruiker te vragen om de locatie te traceren. | Bevestigd |
| 2 | Bevestig welke bewakingsmodus is ingesteld voor iOS. De continue modus zorgt voor een grotere nauwkeurigheid en persistentie, maar zorgt ook voor een langere batterijduur. | Belangrijke wijzigingen of Doorlopende |
| 3 | Als u meerdere POI&#39;s-bibliotheken gebruikt, controleert u of de desbetreffende bibliotheken zijn geselecteerd in de extensie Plaatsen voor Experience Platform Launch. | Bevestigd |
| 4 | Controleer of de nieuwste versies van de Mobile Core- en Places-extensies via Gradle of CocoaPods met de app zijn meegeleverd. | Bevestigd - voor meer informatie over recente updates raadpleegt u de [opmerkingen bij de release.](/help/release-notes.md) |
| 5 | Bevestig dat de juiste omgevingen zijn geconfigureerd voor testen. De milieu-id van de Lancering moet overeenkomen met de ontwikkelomgeving van de Launch. | Bevestigd |
| 6 | Maak GPX-bestanden voor elke POI die u wilt testen. GPX-bestanden kunnen in de lokale ontwikkelomgeving worden gebruikt om een locatie-item te simuleren. Raadpleeg het volgende voor informatie over het maken en gebruiken van GPX-bestanden: <br>[GPX-bestanden voor iOS Simulator [gesloten]](https://stackoverflow.com/questions/17292783/gpx-files-for-ios-simulator)<br>[https://mapstogpx.com/mobiledev.php](https://mapstogpx.com/mobiledev.php)<br>[LOCATIETESTS IN MOBIELE APPS](https://qacumtester.wordpress.com/2014/02/27/location-testing-in-mobile-apps/) | GPX-bestanden worden gemaakt en geladen in het app-project. |
| 7 | Zonder iets anders te doen, zou u de toepassing van Android Studio of XCode moeten kunnen lanceren en het aangewezen alarm zien om toegang voor de het volgen plaats te verzoeken. Klik op de knop *Altijd toestaan* toestemming.<br><br>We raden u aan een echt apparaat te gebruiken dat op uw computer is aangesloten in plaats van apparaatsimulator. | De vraag van het plaatsingsverzoek zou op toepassing moeten tonen die door winde wordt geladen |
| 8 | Nadat de locatiemachtiging is geaccepteerd. De Plaatsen SDK zal de huidige plaats van het apparaat terugwinnen en de regio controlecode zou moeten beginnen de 20 dichtstbijzijnde POIs van de huidige plaats te controleren | Zie het logboekvoorbeeld onder de tabel. |
| 9 | Het schakelen tussen verschillende plaatsen in XCode of Android studio zou entry gebeurtenissen voor specifieke POIs moeten veroorzaken. De onderstaande logboeken worden verwacht bij binnenkomst in een POI. | Zie het logboekvoorbeeld onder de tabel. |
| 10 | Nadat de gebiedsmonitor nabijgelegen POIs vindt, zou u moeten testen door plaats te verzenden pingelt uit. In Lancering, creeer een nieuwe regel die de uitbreiding van Plaatsen gebruikt om op een geo-fence ingang teweeg te brengen. Maak vervolgens een nieuwe handeling met de Mobile Core om een Postback te verzenden. Door een Slack Webhaak-app te maken, kunt u locatie-items en -uitgangen zien. Voor informatie over het maken van een Slack Webhaak-app raadpleegt u [Berichten verzenden met Binnenkomende webhooks.](https://api.slack.com/messaging/webhooks) |  |
| 10 bis | In Lancering, zorg ervoor dat u gegevenselementen voor de uitbreiding van Plaatsen met inbegrip van het volgende toevoegde: <br>Huidige POI-naam<br>Huidige POI-laag<br>Huidige lengte van POI<br>Laatst ingevoerde naam<br>Laatst ingevoerd<br>Laatste invoer lang<br>Laatst afgesloten naam<br>Laatst afgesloten<br>Laatst afgesloten<br>Tijdstempel |  |
| 10 ter | Een nieuwe regel maken met een gebeurtenis = Plaatsen → Voer de POI in |  |
| 10c | Een handeling maken = Mobile Core → Postback |  |
| 10 quinquies | Gebruik de URL van Webhaak voor uw Slack-app, bijvoorbeeld https://hooks.slack.com/services/TKN5FKS68/BNFP7SVD..... |  |
| 10 sexies | De post zou vergelijkbaar zijn met: `{text: User is in POI -  {%%Last Entered POI Name%%} in {%%Last Entered POI City%%} additional information: Radius:{%%Last Entered POI Radius%%} Timestamp: {%%timestamp%%}}`. <br>Zorg ervoor dat u de specifieke gegevenselementen gebruikt die u hier hebt gemaakt. |  |
| 10 septies | Zorg ervoor dat u alle nieuwe gegevenselementen en regelwijzigingen publiceert in Launch. (Selecteer een werkende dev-bibliotheek rechtsboven in de interface Launch.) |  |
| 11 | Start en test de toepassing opnieuw door te schakelen tussen de GPX-locaties in de ontwikkelings-IDE. | U zou nu Slack berichten moeten zien die ingangen voor elke POI tonen aangezien u verschillende plaatsen in uw ontwikkelomgeving selecteert. |
|  | **SNEL SAMENVATTINGSPUNT**<br> Al deze tests kunnen lokaal worden uitgevoerd zonder dat ze naar een specifieke locatie van de opslagplaats hoeven te gaan. Het testen van de bevestiging helpt ervoor te zorgen dat uw toepassing correct wordt gevormd en de correcte toestemmingen voor de plaats heeft ontvangen. <br><br>Deze bevestiging geeft u ook vertrouwen dat de bepaalde POIs correct met uw regionaal controleimplementatie werken.  Na deze stap, zullen wij beginnen overseinen in Campagne te testen om te zien of verschijnen de juiste berichten gebaseerd op POI ingangen en uitgang. |  |
|  | **Adobe Campaign Standard In-app berichten testen met Places Service.** |  |
| 12 | Voor het belangrijkste dashboard van de Campagne vorm een nieuw in-app-Bericht (type = uitzending) |  |
| 12 bis | Selecteer **Plaatst gebeurtenistype - Invoer als trigger**. |  |
| 12 ter | Selecteren **[!UICONTROL Places Custom metadata]** als extra filter - gebruik POI type = Laatste ingevoerde POI.<br>We gebruiken **[!UICONTROL Last Entered]** als type POI, omdat in de meeste gevallen **[!UICONTROL Last Entered]** hetzelfde als **[!UICONTROL Current POI]**. <br><br>**[!UICONTROL Current POI]**mag alleen worden gebruikt in gevallen waarin er sprake is van overlappende geografische aanduidingen. In dit geval moeten deze POI&#39;s worden gerenderd en vervolgens **[!UICONTROL Current POI]**zal de hoogste gerangschikte POI uit 2 of 3 geo-fences tonen dat een gebruiker momenteel zou kunnen zijn. |  |
| 12c | Selecteer een sleutel van douanemetagegevens die u zal helpen beperken welke POIs een bericht zal ontvangen. |  |
| 12 quinquies | Voor frequentie en duur, houd aan slechts één of twee dagen, zodat als u niet van de criteria houdt, u de trekker in een kortere periode kunt verlopen. |  |
| 12 sexies | Selecteer Altijd/Eenmaal of Tot de klik doorloopt *ALTIJD* zodat u op meerdere locaties kunt testen. | Een bericht in de app wordt ALTIJD weergegeven wanneer u een locatiewijziging simuleert die voldoet aan de juiste metagegevenscriteria. |
| 12 septies | Selecteer voor de weergave een andere optie dan Lokale melding. Hierdoor is het gemakkelijker om te zien wanneer u op de voorgrond met de app test.) |  |
| 12g | Bereid/bevestig en implementeer het bericht in de app. |  |
| 13 | Sluit de toepassing af en start deze opnieuw om ervoor te zorgen dat de nieuwe campagnecriteria worden gedownload. | Vergeet niet dat de toepassingen volledig opnieuw moeten worden gestart om het nieuwe bestand met campagneregels naar het apparaat te kunnen downloaden. |
| 14 | In uw ontwikkeltoepassing, schakelaarplaatsen door de eerder gecreeerde GPX- dossiers te gebruiken. | Het bericht in de app wordt weergegeven op basis van de vorige criteria die zijn ingesteld. |
| 15 | Voor de volgende test, zullen wij in wezen de zelfde stappen kopiëren zoals voordien, maar dit keer zullen wij LOKALE VERKLARING testen. | Het verwachte resultaat is dat de lokale berichten worden getoond telkens als de passende criteria worden voldaan. |
| 16 | Vorm een nieuw in-app-Bericht (type = uitzending). |  |
| 16 bis | Selecteer **[!UICONTROL Places event type]** - **[!UICONTROL Entry as the trigger]**. |  |
| 16 ter | Selecteer de aangepaste metagegevens voor Plaatsen als een extra filter - gebruik **[!UICONTROL POI type]** = **[!UICONTROL Last Entered POI]**. |  |
| 16c | Selecteer een sleutel van douanemetagegevens die u zal helpen beperken welke POIs een bericht zal ontvangen. |  |
| 16 quinquies | Houd voor frequentie en duur slechts een of twee dagen aan, zodat u de trigger in een kortere periode kunt verlopen als u de criteria niet bevalt. |  |
| 16 sexies | Voor Altijd/Eenmaal of Tot klikken op Doorgaan, **[!UICONTROL ALWAYS]**. |  |
| 16 septies | Selecteer voor het weergavetype **[!UICONTROL Local Notification]**. |  |
| 16g | Bereid/bevestig en implementeer het bericht in de app. |  |
| 17 | Sluit in de ontwikkelomgeving uw apparaat aan en druk op **[!UICONTROL Play]** op de build. Nadat u hebt vastgesteld dat de locatie werkt, plaatst u de toepassing op de achtergrond en gaat u door met het schakelen tussen locaties in Xcode of Android Studio. U zou consoleread-outs nog moeten zien die op de locatieverandering wijzen, en u zou lokale berichten ook moeten zien die afhankelijk van de criteria in uw trekker worden getoond. (Er kan een vertraging van 1 tot 2 seconden optreden.) | Het verwachte resultaat is dat lokale meldingen worden weergegeven wanneer aan de criteria wordt voldaan. |
|  | **SAMENVATTINGSPUNT** <br>In dit stadium zouden we POI-inzendingen in onze lokale omgeving moeten zien. We zouden ook berichten van Campagne moeten zien die op het werk van POI wordt gebaseerd. Als er mislukkingen zijn, controleer om te zien of ging een bericht van Slack niet uit. Als er geen Slack-bericht is, controleert u de toepassingsconsole, omdat een nieuwe locatie-ingang mogelijk niet is opgenomen. Als de resultaten succesvol zijn, dan kunnen wij vrij zeker zijn dat de toepassing correct presteert en dat de de berichtendienst van Plaatsen en van de Campagne ook correct werkt. |  |
|  | **TESTEN OP DE SITE** <br>Niet veel zou moeten veranderen wanneer het testen op plaats. Als u de terugdraaifunctie actief houdt, kunt u beter begrijpen of het apparaat een invoer- en afsluitprocedure voor de locatie ontvangt. |  |
| 18 | Voer tests uit met apparaten die beginnen met wifi en cellulair uitgeschakeld en schakel vervolgens één keer in de POI-regio in. | Als er een mislukking is, merk op of u een geo-fence ingang en bericht in Slack krijgt. Wat is het tijdstempel op de Slack-melding? |
| 19 | Voer de test uit met alleen cellulair ingeschakeld en met de wifi uitgeschakeld. |  |
| 20 | Test met zowel mobiel als wifi ingeschakeld. |  |
|  | **SAMENVATTINGSPUNT** <br>De tests ter plaatse moeten nauw overeenkomen met de ontwikkelingstests. Houd in mening dat er sommige milieufactoren die in spel kunnen komen in het bepalen van een gebruikersplaats, zoals duur die in een POI geo-fence wordt doorgebracht, beschikbaarheid van celsignaal, en sterkte van nabijgelegen wifi toegangspunten. |  |

## Logboekvoorbeelden

**Stap 8:** iOS- en Android-logbestanden verwacht tijdens een update van de locatie

**iOS**

```
[AdobeExperienceSDK DEBUG <Places>]: Requesting 20 nearby POIs for device location (<lat>, <longitude>)
[AdobeExperienceSDK DEBUG <Places>]: Response from Places Query Service contained <n> nearby POIs   
```

**Android**

```
PlacesExtension - Dispatching nearby places event with n POIs   
```

**Stap 9:** iOS- en Android-logbestanden verwacht tijdens een gebeurtenis

**iOS**

```
[AdobeExperienceSDK TRACE <Places>]: Dispatching Places region entry event for place ID <poiId>
```

**Android**

```
PlacesExtension -  Dispatching Places Region Event for <poi name> with eventType entry
```
