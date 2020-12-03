---
title: Referentie voor monitor-API plaatsen
description: Een lijst met API's voor de Monitor van Plaatsen.
translation-type: tm+mt
source-git-commit: 5a21e734c0ef56c815389a9f08b445bedaae557a
workflow-type: tm+mt
source-wordcount: '1090'
ht-degree: 2%

---


# Referentie voor monitor-API plaatsen {#places-api-reference}

## Monitorextensie voor locaties registreren

Registreert de uitbreiding van de Monitor van Plaatsen met de Hub van de Gebeurtenis van de Kern.

### RegisterExtension (Android)

Hier volgt de syntaxis en voorbeeldcode voor deze API:

#### Syntaxis

Hier volgt de syntaxis in Java:

```java
public static void registerExtension();
```

#### Voorbeeld

Roep deze methode in de `onCreate` methode aan waar u de rest van Experience Platform SDK initialiseert.

```java
public class MobileApp extends Application {
  @Override
  public void onCreate(){
     super.onCreate();
     MobileCore.setApplication(this);
     try {
        PlacesMonitor.registerExtension();
     } catch (Exception e) {
       //Log the exception
       }
    }
 }
```

### RegisterExtension (iOS)

Hier volgt de syntaxis en voorbeeldcode voor deze API:

#### Syntaxis

Hier is de syntaxis in doelstelling-C:

```objective-c
+ (void) registerExtension;
```

#### Voorbeeld

Deze methode zou in de `didFinishLaunchingWithOptions` afgevaardigde methode van moeten worden geroepen `AppDelegate`.

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {

    [ACPCore configureWithAppId:@"launch-appID"];    
    [ACPPlaces registerExtension];    
    [ACPPlacesMonitor registerExtension];

    [ACPCore start:^{
        // do other initialization of the SDK
    }];

    return YES;
}
```

## Extensie

Hiermee wordt de huidige versie van de extensie Plaatsen Monitor geretourneerd

### ExtensionVersion (Android)

Hier volgt de syntaxis en voorbeeldcode voor deze API:

#### Syntaxis

```java
public static String extensionVersion();
```

#### Voorbeeld

```java
String placesMonitorVersion = PlacesMonitor.extensionVersion();
```

### ExtensionVersion (iOS)

Hier volgt de syntaxis en voorbeeldcode voor deze API:

#### Syntaxis

```objective-c
+ (nonnull NSString*) extensionVersion;
```

#### Voorbeeld

```objective-c
NSString *placesMonitorVersion = [ACPPlacesMonitor extensionVersion];
```

## Apparaatbewaking starten

Volg de locatie van het apparaat en controleer de nabijgelegen locaties.

### Start (Android)

Als de gebruiker geen toestemming heeft verleend om apparaatlocatie te gebruiken, vraagt de eerste aanroep naar de `start` API de gebruiker om toestemming.

Hier volgt de syntaxis en voorbeeldcode voor deze API:

#### Syntaxis

```java
public static void start();
```

#### Voorbeeld

```java
PlacesMonitor.start();
```

### Starten (iOS)

>[!IMPORTANT]
>
>Om met de controle te beginnen, moet de locatiedienst de noodzakelijke vergunning hebben:
>
>* Als de vergunning voor de Dienst van Plaatsen niet aan de toepassing is verstrekt, verzoekt de eerste vraag aan `start` API de vergunning om de Dienst van Plaatsen te gebruiken zoals die voor de toepassing wordt gevormd.
>* Afhankelijk van de mogelijkheden van uw apparaat, als de vergunning is verstrekt, volgt de Monitor van Plaatsen de plaats van de gebruiker die op de momenteel vastgestelde plaats wordt gebaseerd `ACPPlacesMonitorMode`. Standaard gebruikt de monitor `ACPPlacesMonitorModeSignificantChanges`.


>[!CAUTION]
>
>Als uw vraag om controle te beginnen wordt gemaakt alvorens SDK heeft gebeëindigd initialiserend, zou het kunnen worden genegeerd.

U kunt ervoor zorgen dat de SDK de initialisatie heeft voltooid door `start` de callback aan te roepen `ACPCore::start:`.

Hier volgt de syntaxis en voorbeeldcode voor deze API:

#### Syntaxis

```objectivec
+ (void) start;
```

#### Voorbeeld

De monitor Plaatsen wordt gestart wanneer de SDK wordt geïnitialiseerd:

```objective-c
[ACPCore start:^{
    [ACPPlacesMonitor start];
}];
```

Start de Monitor Plaatsen later tijdens de uitvoering van de app:

```objective-c
[ACPPlacesMonitor start];
```

## Apparaatbewaking stoppen

Hiermee wordt het bijhouden van de locatie van het apparaat gestopt.

### Stoppen (Android)

Hier volgt de syntaxis en voorbeeldcode voor deze API:

#### Syntaxis

```java
public static void stop();
```

#### Voorbeeld

```java
PlacesMonitor.stop();
```

### Stoppen (iOS)

Hier volgt de syntaxis en voorbeeldcode voor deze API:

#### Syntaxis

```objectivec
+ (void) stop;
```

#### Voorbeeld

```objective-c
[ACPPlacesMonitor stop];
```

## Locatie bijwerken

Gebruik deze API voor een directe update op de locatie van het apparaat. Wanneer u deze API aanroept, probeert het apparaat de locatie te bepalen met het nauwkeurigheidsniveau dat u hebt opgegeven. Dit proces verfrist ook nabijgelegen POIs die door de uitbreiding worden gecontroleerd.

### UpdateLocation (Android)

Hier volgt de syntaxis en voorbeeldcode voor deze API:

#### Syntaxis

```java
public static void updateLocation();
```

#### Voorbeeld

```java
PlacesMonitor.updateLocation();
```

### UpdateLocationNow (iOS)

#### Syntaxis

```objective-c
+ (void) updateLocationNow;
```

#### Voorbeeld

```objective-c
[ACPPlacesMonitor updateLocationNow];
```

## Toepassingslocatie, machtiging

U kunt deze API gebruiken om het type locatietoestemming in te stellen waarvoor de gebruiker wordt gevraagd en geautoriseerd voor gebruik bij de Plaatsingsservice.

### SetLocationPermission (Android)

Met deze API wordt het type aanvraag voor locatierechten ingesteld waarvoor de gebruiker wordt gevraagd om te selecteren.

>[!TIP]
>
>Deze API is alleen effectief voor apparaten die zich op Android 10 en hoger bevinden.
>
>Om de aangewezen vergunningsherinnering te plaatsen die aan de gebruiker moet worden getoond, roep deze API vóór `PlacesMonitor.start()`. Het roepen van deze methode, terwijl actief het controleren, bevordert het niveau van de plaatstoestemming aan de gevraagde toestemmingswaarde. Als het gevraagde vergunningsniveau of reeds wordt verstrekt of door de toepassingsgebruiker wordt ontkend, of als u probeert om de toestemming van `ALWAYS_ALLOW` `WHILE_USING_APP`aan te degraderen, heeft deze methode geen effect.

U kunt locatierechten instellen op een van de volgende waarden:

* `PlacesMonitorLocationPermission.WHILE_USING_APP`

   Met deze waarde wordt de gebruiker alleen tijdens het gebruik van de toepassing gevraagd om toegang te krijgen tot de apparaatlocatie. Een toepassing wordt geacht in gebruik te zijn wanneer de gebruiker de toepassing op hun apparatenscherm bekijkt, bijvoorbeeld een activiteit loopt op de voorgrond.

   >[!TIP]
   >
   >Zorg ervoor dat de gebruikerstoestemming voor ACCESS_FINE_LOCATION is ingesteld in het manifestbestand van de app.

* `PlacesMonitorLocationPermission.ALWAYS_ALLOW`

   Met deze waarde wordt de gebruiker gevraagd toegang te krijgen tot de apparaatlocatie, zelfs als de toepassing een achtergrond heeft.

   >[!TIP]
   >
   >Zorg ervoor de ACCESS_BACKGROUND_LOCATION en ACCESS_FINE_LOCATION gebruikerstoestemmingen in het duidelijke dossier van de app worden geplaatst.

   `PlacesMonitorLocationPermission.ALWAYS_ALLOW` is de standaardwaarde voor locatietoestemming.

>[!IMPORTANT]
>
>Als de gebruiker van de app de `WHILE_USING_APP` toestemming krijgt, worden geofences niet geregistreerd bij het besturingssysteem. Als gevolg hiervan activeert de extensie Plaatsen Monitor geen entry/exit-gebeurtenissen voor regio&#39;s die op de achtergrond plaatsvinden.

Hier volgt de syntaxis en voorbeeldcode voor deze API:

#### Syntaxis

```java
public static void setLocationPermission(final PlacesMonitorLocationPermission placesMonitorLocationPermission)
```

#### Voorbeeld

U kunt als volgt de `WHILE_USING_APP` machtiging aanvragen:

```java
// set the location permission
PlacesMonitor.setLocationPermission(PlacesMonitorLocationPermission.WHILE_USING_APP);
// start monitoring
PlacesMonitor.start()
```

U kunt als volgt upgraden naar `ALWAYS_ALLOW` machtiging:

```java
// upgrade the permission level
PlacesMonitor.setLocationPermission(PlacesMonitorLocationPermission.ALWAYS_ALLOW);
```

### SetRequestAuthorizationLevel (iOS)

Met deze API wordt het type aanvraag voor locatieautorisatie ingesteld waarvoor de gebruiker wordt gevraagd.

Om de aangewezen vergunningsherinnering te plaatsen die aan de gebruiker moet worden getoond, vraag `SetRequestAuthorizationLevel` alvorens `[ACPPlacesMonitor start]`. Om de aangewezen vergunningsherinnering te plaatsen die aan de gebruiker moet worden getoond, roep deze API vóór `[ACPPlacesMonitor start]`. Het roepen van deze methode terwijl actief toezicht zal het niveau van de plaatsvergunning aan de gevraagde vergunningswaarde bevorderen. Als het gevraagde vergunningsniveau of reeds wordt verstrekt of door de toepassingsgebruiker wordt ontkend of wanneer er een neerwaartse toestemming van `ACPPlacesRequestAuthorizationLevelAlways` aan `ACPPlacesRequestAuthorizationLevelWhenInUse` vergunning is, heeft deze methode geen effect.

Het machtigingsniveau kan worden ingesteld op een van de volgende waarden:

* `ACPPlacesRequestAuthorizationLevelWhenInUse`

   Verzoekt de toestemming van de gebruiker om de Dienst van Plaatsen te gebruiken terwijl app in gebruik is. De gebruikersvraag bevat de tekst van de `NSLocationWhenInUseUsageDescription` sleutel in uw app Info.plist dossier, en de aanwezigheid van die sleutel wordt vereist wanneer het roepen van deze methode. Zie de documentatie van [Apple over requestWhenInUseAuthorization](https://developer.apple.com/documentation/corelocation/cllocationmanager/1620562-requestwheninuseauthorization)voor meer informatie.

* `ACPPlacesRequestMonitorAuthorizationLevelAlways`

   Gebruik deze opsomming om de Places Service aan te vragen, zelfs als de app op de achtergrond wordt uitgevoerd. U moet over de toetsen `NSLocationAlwaysUsageDescription` en `NSLocationWhenInUseUsageDescription` toetsen in Info.plist van uw app beschikken. Met deze toetsen definieert u de tekst die tijdens de vraag van de gebruiker wordt weergegeven. Zie de documentatie van [Apple over requestAlwaysAuthorization](https://developer.apple.com/documentation/corelocation/cllocationmanager/1620551-requestalwaysauthorization)voor meer informatie.

`ACPPlacesRequestAuthorizationLevelAlways` is de standaardwaarde voor de autorisatie van het standaardverzoek.

>[!IMPORTANT]
>
>De toepassing die het gebruik van de `ACPPlacesRequestAuthorizationLevelWhenInUse` machtiging heeft toegestaan, activeert geen entry/exit-gebeurtenissen voor regio&#39;s die op de achtergrond plaatsvinden.

Hier volgt de syntaxis en voorbeeldcode voor deze API:

#### Syntaxis

```objective-c
+ (void) setRequestAuthorizationLevel: (ACPPlacesRequestAuthorizationLevel) requestAuthorizationLevel;
```

#### Voorbeeld

U kunt als volgt de `ACPPlacesRequestAuthorizationLevelWhenInUse` machtiging aanvragen:

```objective-c
// set the request authorization level
[ACPPlacesMonitor setRequestAuthorizationLevel: ACPPlacesRequestAuthorizationLevelWhenInUse];
// start monitoring
[ACPPlacesMonitor start];
```

Een upgrade naar een `ACPPlacesRequestAuthorizationLevelAlways` autorisatie uitvoeren:

```objective-c
// set the request authorization level
[ACPPlacesMonitor setRequestAuthorizationLevel: ACPPlacesRequestAuthorizationLevelAlways];
```

## Controlemodus (alleen iOS)

De controle kan aan één van de volgende waarden worden geplaatst:

* `ACPPlacesMonitorModeContinuous`

   De controleuitbreiding ontvangt en verwerkt plaatsen vaker. Deze monitoringstrategie verbruikt veel energie, maar biedt een hogere nauwkeurigheid. Zie de documentatie van [Apple over continue bewaking](https://developer.apple.com/documentation/corelocation/cllocationmanager/1423750-startupdatinglocation)voor meer informatie.

* `ACPPlacesMonitorModeSignificantChanges`

   De controleuitbreiding ontvangt en verwerkt slechts plaatsupdates nadat het apparaat een significante afstand van de eerder verwerkte plaats heeft bewogen. Deze monitoringstrategie verbruikt minder energie dan de doorlopende monitoringstrategie. Zie de documentatie van [Apple over significante bewaking voor meer informatie](https://developer.apple.com/documentation/corelocation/cllocationmanager/1423531-startmonitoringsignificantlocati)

### SetPlacesMonitorMode (iOS)

Hier volgt de syntaxis en voorbeeldcode voor deze API:

#### Syntaxis

```objective-c
+ (void) setPlacesMonitorMode: (ACPPlacesMonitorMode) monitorMode;
```

#### Voorbeeld

```objective-c
[ACPPlacesMonitor setPlacesMonitorMode:ACPPlacesMonitorModeSignificantChanges];
```
