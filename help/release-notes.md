---
title: Aanvullende informatie
description: Opmerkingen bij de release voor Plaatsen Service.
exl-id: 76da9548-4e32-4b23-9a15-7012973915f3
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '1490'
ht-degree: 3%

---

# Aanvullende informatie {#release-notes}

## 8 juli 2020

* **Hiermee worden monitorextensies geplaatst en geplaatst**

   * Extensies voor monitoren plaatsen en plaatsen zijn toegevoegd voor [Native toepassingen Reageren](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#react-native)
   * Extensies voor monitoren plaatsen en plaatsen zijn toegevoegd voor [Cordova-toepassingen](https://aep-sdks.gitbook.io/docs/resources/upgrading-to-aep/current-sdk-versions#cordova)
   * Zie voor meer informatie: [Extensie Plaatsen gebruiken](https://experienceleague.adobe.com/docs/places/using/places-ext-aep-sdks/places-extension/places-extension.html)


## 12 mei 2020

* **Places Service**

   * Ongelimiteerde POI&#39;s voor importeren uit een CSV-bestand met de knop POI&#39;s importeren
   * Meerdere invoegtoepassingen selecteren en waarden voor metagegevens bulksgewijs bewerken of toevoegen

## 6 mei 2020

* **PlaatstMonitor 2.2.1**

   * **Android**

      * Verbeterde logboekregistratie

## 5 mei 2020


* **PlaatstMonitor 2.1.3**

   * **iOS**

      * Verbeterde logboekregistratie

## 20 februari 2020

* **ACPPlaces 1.3.1 (iOS)**

   * Plaatst uitbreiding meldt nu versieinformatie aan de gebeurtenishub in de Kern SDK.
   * De informatie van het POI-lidmaatschap van het apparaat heeft nu een standaardtijd-aan-leven van één uur van de tijd het wordt verzameld. Zie voor meer informatie [De tijd-om-live voor het lidmaatschap van Plaatsen wijzigen](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)


* **Plaatsen 1.4.1 (Android)**

   * Plaatst uitbreiding meldt nu versieinformatie aan de gebeurtenishub in de Kern SDK.
   * De informatie van het POI-lidmaatschap van het apparaat heeft nu een standaardtijd-aan-leven van één uur van de tijd het wordt verzameld. Zie voor meer informatie [De tijd-om-live voor het lidmaatschap van Plaatsen wijzigen](places-ext-aep-sdks/places-extension/places-extension.md#places-ttl)

## 27 januari 2020

* **PlaatstMonitor 2.2.0**

   * **Android**

      * Roep de API voor nieuwe locaties aan om de status van de locatievergunning te verzamelen wanneer de app wordt gestart en wanneer de autorisatie verandert terwijl de app wordt uitgevoerd.
      * Toegevoegde setRequestLocationPermission API en verouderde setLocationPermission API.

## 9 januari 2020

* **Plaatsen 1.4.0**

   * **Android**

      * Een nieuwe API toegevoegd, `setAuthorizationStatus`, om de status van de apparaatautorisatie voor Plaatsen Services in te stellen. De waarde wordt opgeslagen en gebruikt in de gedeelde status Plaatsen.

## 4 december 2019

* **PlacesMonitor 2.1.2**

   * **iOS**

      * De Plaatsen van de vraag API om CLAuthorizationStatus van apparaat te verzamelen wanneer het verandert.

## 3 december 2019

* **ACPPlaces 1.3.0**

   * **iOS**

      * Een nieuwe API toegevoegd, `setAuthorizationStatus`, om de status van de apparaatautorisatie voor Plaatsen Services in te stellen. De waarde wordt opgeslagen en gebruikt in de gedeelde status Plaatsen.

## 25 november 2019

* **PlaatstMonitor 2.1.1**

   * **iOS**

      * Vaste instructies voor importeren van Cocoapods-projecten met de optie Meerdere podprojecten.

## 22 november 2019

* **PlaatstMonitor 2.1.1**

   * **Android**

      * De monitor herkent nu het opstarten van een Android-apparaat en registreert, indien nodig, de geofences opnieuw met het besturingssysteem op basis van de huidige locatie van het apparaat.
      * Probleem verholpen waarbij soms entry/exit-gebeurtenissen werden genegeerd.

## 9 oktober 2019

* **PlaatstMonitor 2.1.0**

   * **iOS**

      * Een nieuwe API toegevoegd, `setRequestAuthorizationLevel`, om het type locatieautorisatieverzoek in te stellen waarvoor de gebruiker wordt gevraagd.


   * **Android**

      * Een nieuwe API toegevoegd, `setLocationPermission`om het type locatietoestemming in te stellen waarvoor de gebruiker wordt gevraagd.
      * De monitor Plaatsen ondersteunt nu Android 10.

## 8 aug. 2019

De volgende updates zijn aangebracht in deze release:

### UI-updates

Hier volgt een lijst met updates van de interface Plaatsen:

#### Nieuwe functies

* Er is een nieuwe lijstweergave toegevoegd met de POI&#39;s zonder de kaart.
* Opties voor filteren van inhoud toegevoegd voor de stad, de staat, het land en de metagegevens.
* De eerste bibliotheek in een organisatie wordt automatisch gemaakt.
* POI-sortering toegevoegd aan de lijstweergave.

#### UI-updates

* Het deelvenster Lijst en Details is verplaatst naar de rechterkant van de gebruikersinterface.
* Een nieuw deelvenster met zoekopdrachten toegevoegd boven aan de gebruikersinterface.
* Als er slechts één bibliotheek aanwezig is, wordt deze bibliotheek automatisch geselecteerd wanneer u een POI maakt.
* Bibliotheekbeheer is verplaatst naar een pop-upvenster.
* Een POI-telling toegevoegd naast de filters.

## 6 aug. 2019

De volgende updates zijn aangebracht in deze release:

### Extension 2.0.0 voor monitor starten

* Bijgewerkt van de installatie-instructies voor Android en iOS voor Places Monitor 2.0.

## 31 juli 2019

De volgende updates zijn aangebracht in deze release:

### Plaatst monitor 2.0.0

* De status van de controle blijft nu bestaan tussen lanceringen.
* De behandeling van callback, die uit een verzoek van de plaatstoestemming voortkwam vereist niet meer u om PlacesActivity uit te breiden.
* Een bestaande API is gewijzigd, zodat ontwikkelaars alle Plaatsgegevens van het apparaat kunnen wissen:

  Oude API: `public static void stop();`

  Nieuwe API: `public static void stop (final boolean clearData);`

* Het gebruik van de `getNearbyPointsOfInterest` API om foutscenario&#39;s effectiever af te handelen.

## 25 juli 2019

De volgende updates zijn aangebracht in deze release:

### ACPPlacesMonitor 2.0.0

* Om alle gegevens van Plaatsen van het apparaat te ontruimen,

  in ACPPlacesMonitor een bestaande API vervangen `+ (void) stop;` with`+ (void) stop: (BOOL) clearData;`.

* Het gebruik van ACPPlaces is bijgewerkt `getNearbyPointsOfInterest` API om foutscenario&#39;s effectiever af te handelen.

## 22 juli 2019

De volgende updates zijn aangebracht in deze release:

### Android-plaatsen 1.3.0

* Er is een nieuwe API toegevoegd die alle Plaatsgerelateerde gegevens van de gedeelde status, het geheugen in de app en de gedeelde voorkeur wist.
* Probleem verholpen waarbij de gedeelde status niet werd bijgewerkt tijdens het starten van de toepassing.
* Het probleem waarbij `getNearbyPointsOfInterest` callback heeft foutcode geretourneerd `SERVER_RESPONSE_ERROR instead of CONNECTIVITY_ERROR` op internet.
* `getNearbyPointsOfInterest` API (zonder errorCallback) heeft de `successCallback` opgeroepen met een lege poilijst, als er een fout optreedt bij het ophalen van de nabijgelegen aandachtspunten.

## 19 juli 2019

De volgende updates zijn aangebracht in deze release:

**iOS Plaatsen 1.2.0**

Er is een nieuwe API toegevoegd waarmee alle Plaatsgerelateerde gegevens worden gewist uit de gedeelde status, het geheugen in de app en `NSUserDefaults`.

## 25 juni 2019

De volgende updates zijn aangebracht in deze release:

**iOS-monitor 1.0.2**

* Verbeteringen van de kwaliteit van het leven, waaronder betere documentatie en logboekregistratie in de code.

## 17 juni 2019

De volgende updates zijn aangebracht in deze release:

**iOS Plaatsen 1.1.0**

* Er is een nieuwe API toegevoegd om een foutcode te retourneren als er een fout optreedt bij het ophalen van nabijgelegen plaatsen.
* Wanneer de privacystatus verandert in de optie Weigeren, worden alle gegevens met betrekking tot Plaatsen nu van het apparaat gewist.
* Probleem verholpen waarbij Plaatsen-gebeurtenissen na een eerste keer starten soms verloren gingen als gevolg van slechte netwerkomstandigheden.
* Probleem verholpen waarbij bij het snel achter elkaar verwerken van POI-entry-gebeurtenissen tokenvervanging via Rules Engine soms naar de onjuiste POI wordt verwezen.

## 30 mei 2019

**Android-plaatjesmonitor 1.0.1**

* Probleem verholpen waarbij een entry-gebeurtenis voor POI&#39;s werd voorkomen wanneer de Plaatsen-controle werd gestart.

## 28 mei 2019

Oplossing voor de volgende problemen in de interface Plaatsen:

* Bijgewerkt de Schakelaar van de Oplossing in Plaatsen om met de rest van Experience Cloud te richten.
* Probleem verholpen waarbij de rangorde werd opgeslagen in gevallen waarin geen wijzigingen in de rangorde werden aangebracht.
* De minimale toegestane straal in de gebruikersinterface is verhoogd tot 10 meter.
* Probleem verholpen waarbij, als u alle getallen in het veld verwijdert, het straalveld weer werd ingesteld op 20 meter.

## 17 mei 2019

De volgende updates zijn aangebracht in deze release:

**Android-plaatsen 1.2.0**

* Er is een nieuwe API toegevoegd om een afzonderlijke Geofence te verwerken.
* Opgeloste problemen om meerdere opeenvolgende gebeurtenissen bij binnenkomst te voorkomen.

**Android-plaatjesmonitor 1.0.0**

De eerste release van de Places Monitor voor Android.

De Monitor van Plaatsen beheert de OS-vlakke Plaats APIs en communiceert direct met de uitbreiding van Plaatsen. Als beide extensies zijn geïnstalleerd, kunnen klanten regio&#39;s controleren die zich buiten de verpakking bevinden in hun toepassing.
Voor meer informatie over de Monitor van Plaatsen, klik hier.


## 2 mei 2019

**Android-plaatsen 1.1.0**

* Introduceerde een nieuwe API voor getNearByPlaces, die een errorCallback heeft en met een errorCode wordt geroepen die op de reden voor de fout wijst.
* Met de extensie Plaatsen worden de gebeurtenissen nu in de wachtrij geplaatst totdat een configuratie wordt verkregen.
* Toegevoegde ondersteuning voor configuraties met behoud van de omgeving.
* Bug Fix: corrigeer de toetsen voor de entry/exit-gebeurtenissen van het gebied
* De opslag van de laatst bekende locatie respecteert nu de privacystatus van de gebruiker


## 9 april 2019

De volgende updates zijn aangebracht in deze release:

**iOS-monitor 1.0.1**

* Toegevoegde volledige dekking van de eenheidstest.
* CI-integratie (CircleCI)
* Integratie van codecov (codecov)

## 25 maart 2019

iOS-monitor 1.0.0

Eerste release van de Places Monitor voor iOS.

De Monitor van Plaatsen beheert de OS-vlakke Plaats APIs en communiceert direct met de uitbreiding van Plaatsen. Als beide extensies zijn geïnstalleerd, kunnen klanten regio&#39;s controleren die zich buiten de verpakking bevinden in hun toepassing.

## 28 februari 2019

### Bètaversie

Dit is de eerste versie van de Dienst van Plaatsen, een reeks hulpmiddelen die klanten toestaat om de ervaringen van hun gebruikers met echte plaatsgegevens te verrijken. Voor de eerste release is het belangrijkste gebruiksgeval dat mobiele apps aangepaste locatiegegevens kunnen ophalen en op die gegevens kunnen reageren via Adobe Experience Platform Launch.

### Belangrijkste kenmerken

Hier volgen de belangrijkste functies van deze release:

#### Gebruikersinterface voor Plaatsingsservice

We hebben een beheerinterface beschikbaar gemaakt waarin u uw belangenbehartigingen (POI&#39;s) kunt weergeven en beheren. U kunt ook uw POI&#39;s ordenen in bibliotheken. Naast standaardmetagegevens zoals plaats, staat en categorie, ondersteunen we ook de mogelijkheid om aangepaste metagegevens toe te voegen aan uw persoonlijke expressies.

* Ga naar [https://places.adobe.com](https://places.adobe.com).
* Ga als volgt te werk om aan de slag te gaan met de interface: [Aan de slag](/help/getting-started.md).

#### Extensie plaatsen

Met de extensie Plaatsen kunt u de bibliotheken van de Plaatsingsservice toevoegen aan uw mobiele app en de bijbehorende POI&#39;s bewerken. Gebruikend de regelbouwer in Experience Platform Launch, kunt u acties teweegbrengen om in brand te steken wanneer de gebruikers POIs ingaan en weggaan.

In de extensie Plaatsen:

* U kunt kiezen welke POI-bibliotheken u in uw app wilt opnemen.
* Gebeurtenissen van de regel die op POI ingang of uitgang teweegbrengen.
* Creeer gegevenselementen die aan huidige POI van de gebruiker richten.

Zie voor meer informatie over de extensie Plaatsen [Extensie Plaatsen](/help/places-ext-aep-sdks/places-extension/places-extension.md).

#### Plaatst API&#39;s

U kunt de Plaatsen APIs gebruiken om het volgende te doen:

* Ontwikkelaars toestaan hun lijst met MOI&#39;s te vullen en bij te werken.
* Bouw uw eigen UI of integreer met een bestaand POI gegevensbestand.
* Met de batch-eindpunten van de API Plaatsen kunt u een grote hoeveelheid POI&#39;s importeren.

  U kunt het meegeleverde Python-hulpprogramma gebruiken om de bulkimport te voltooien.

Voor meer informatie over de Plaatsen APIs, zie [Webservice-API](/help/web-service-api/places-web-services.md).

### Binnenkort beschikbaar

#### Analytics Integration

De uitbreiding van de Analyse wordt bijgewerkt om de gegevens van de plaatscontext van uw gegevensbestand van de Dienst van Plaatsen aan alle uitgaande vraag van Analytics automatisch toe te voegen wanneer een gebruiker in POI (passieve vraag) is. Deze update zal ook regelverwezenlijking toestaan om de spoorvraag van de Analyse in brand te steken bij POI ingang of uitgang (Actieve vraag).
