---
title: Uitbreiding Places
description: Met de extensie Plaatsen kunt u op basis van de locatie van uw gebruikers werken.
translation-type: tm+mt
source-git-commit: 0ac139fce666540b36a8c82fe4c05974e12e987f
workflow-type: tm+mt
source-wordcount: '678'
ht-degree: 3%

---


# Uitbreiding Places {#places-extension}

Met de extensie Plaatsen kunt u op basis van de locatie van uw gebruikers werken. Deze extensie is de interface naar de API&#39;s van de Places Query Service. Door te luisteren naar gebeurtenissen die GPS-coördinaten en geofence region-gebeurtenissen bevatten, verzendt deze extensie nieuwe gebeurtenissen die worden verwerkt door de Rules Engine. De extensie Plaatsen haalt ook een lijst op met de dichtstbijzijnde POI voor de toepassingsgegevens die van de API&#39;s worden opgehaald en levert. De gebieden die door de API&#39;s worden geretourneerd, worden opgeslagen in cache en persistentie, waardoor een beperkte offlineverwerking mogelijk is.

## De extensie Plaatsen installeren in Adobe Experience Platform starten

1. Klik in Experience Platform Launch op het tabblad **[!UICONTROL Extensions]**.
1. Zoek op het **[!UICONTROL Catalog]** tabblad de **[!UICONTROL Places]** extensie en klik op **[!UICONTROL Install]**.
1. Selecteer de bibliotheken Plaatsen die u in deze eigenschap wilt gebruiken. Dit zijn de bibliotheken die in uw app toegankelijk zijn.
1. Klik op **[!UICONTROL Save]**.

   Wanneer u klikt **[!UICONTROL Save]**, zoekt de Experience Platform SDK de Diensten van Plaatsen naar POIs in de bibliotheken die u selecteerde. De POI-gegevens worden niet opgenomen in de download van de bibliotheek wanneer u de app maakt, maar een op locatie gebaseerde subset van POI&#39;s wordt tijdens runtime gedownload naar het apparaat van de eindgebruiker en is gebaseerd op de GPS-coördinaten van de gebruiker.

1. Voltooi het publicatieproces om de SDK-configuratie bij te werken.

   Zie [Publiceren](https://docs.adobe.com/content/help/en/launch/using/reference/publish/overview.html)voor meer informatie over publiceren in Experience Platform Launch.

### De extensie Plaatsen configureren {#configure-places-extension}

![](//help/assets/places-extension.png)

## De extensie Plaatsen toevoegen aan uw app {#add-places-to-app}

U kunt de extensie Plaatsen toevoegen aan uw Android- en iOS-toepassingen. De stappen voor het toevoegen van Plaatsen aan uw iOS- of Android-toepassing vindt u hieronder. Plaatsen zijn ook beschikbaar voor Cordova en React Native. Zie de bijbehorende koppelingen voor informatie over het toevoegen van Plaatsen aan uw toepassing wanneer u ontwikkelt met een van deze platforms:

**[Plug-in Cordova Places](https://github.com/adobe/cordova-acpplaces/blob/master/README.md)**

**[Insteekmodule Native plaatsen reageren](https://github.com/adobe/react-native-acpplaces/blob/master/README.md)**

### Android

U kunt als volgt de extensie Plaatsen met Java toevoegen aan uw app:

1. Voeg de extensie Plaatsen toe aan uw project met behulp van het grijze bestand van uw app.

   ```java
   implementation 'com.adobe.marketing.mobile:places:1.+'
   implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
   ```

1. Importeer de extensie Plaatsen in de hoofdactiviteit van de toepassing.

   ```java
   import com.adobe.marketing.mobile.Places;
   ```


### iOS

Als u de extensie Plaatsen wilt toevoegen aan uw app met Objectief-C of Swift:

1. Voeg de bibliotheken Plaatsen en [Mobiele Kern](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core) aan uw project toe. U moet de volgende pods toevoegen aan uw `Podfile`:

   ```objective-c
   pod 'ACPPlaces', '~> 1.0'
   pod 'ACPCore', '~> 2.0'    # minimum Core version for Places is 2.0.3
   ```

   Als u Cocoapods niet gebruikt, kunt u de Mobile Core en de Places bibliotheken van onze [releasepagina](https://github.com/Adobe-Marketing-Cloud/acp-sdks/releases/) op Github handmatig opnemen.

1. Cocoapods bijwerken:

   ```objective-c
   pod update
   ```

1. Open Xcode, en in uw klasse AppDelegate, voer de Kern en de kopballen van Plaatsen in:

   **Doelstelling-C**

   ```objective-c
   #import "ACPCore.h"
   #import "ACPPlaces.h"
   ```

   **Swift**

   ```swift
   import ACPCore
   import ACPPlaces
   ```

### De extensie Plaatsen registreren met Mobile Core {#register-places-mobile-core}

U moet de extensie Plaatsen registreren met Mobile Core in Android en iOS.

#### Android

Registreer de extensies Plaatsen in de `OnCreate` methode van de app:

```java
public class PlacesTestApp extends Application {

    @Override
    public void onCreate() {
        super.onCreate();
        MobileCore.setApplication(this);

        try {
            Places.registerExtension();
            MobileCore.start(null);
        } catch (Exception e) {
            Log.e("PlacesTestApp", e.getMessage());
        }
    }
}
```

#### iOS

Registreer in de `application:didFinishLaunchingWithOptions:` methode van uw app de extensie Plaatsen bij uw andere SDK-registratieaanroepen:

**Doelstelling-C**

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    // make other sdk registration calls
    [ACPPlaces registerExtension];    
    return YES;
}
```

**Swift**

```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
    // make other sdk registration calls
    ACPPlaces.registerExtension();
    return true;
}
```

### De tijd-om-live voor het lidmaatschap van Plaatsen wijzigen {#places-ttl}

Locatiegegevens kunnen snel verouderd raken, vooral als het apparaat geen updates voor de achtergrondlocatie ontvangt.

Controleer de tijd-aan-levende voor het lidmaatschapsgegevens van Plaatsen op het apparaat door het `places.membershipttl` configuratiemontages te plaatsen. De waarde die wordt doorgegeven, vertegenwoordigt het aantal seconden dat de status Plaatsen geldig blijft voor het apparaat.

#### Android

Binnen callback van `MobileCore.start()` werk de configuratie met de noodzakelijke veranderingen vóór het roepen bij `lifecycleStart`:

```java
public class PlacesTestApp extends Application {

    @Override
    public void onCreate() {
        super.onCreate();
        MobileCore.setApplication(this);

        try {
            Places.registerExtension();
            MobileCore.start(new AdobeCallback() {
                @Override
                public void call(Object o) {
                    // switch to your App ID from Launch
                    MobileCore.configureWithAppID("my-app-id");

                    final Map<String, Object> config = new HashMap<>();
                    config.put("places.membershipttl", 30);
                    MobileCore.updateConfiguration(config);

                    MobileCore.lifecycleStart(null);
                }
            });
        } catch (Exception e) {
            Log.e("PlacesTestApp", e.getMessage());
        }
    }
}
```

#### iOS

Op de eerste lijn in callback van `ACPCore`s `start:` methode, vraag `updateConfiguration:`

**Doelstelling-C**

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    // make other sdk registration calls

    const UIApplicationState appState = application.applicationState;
    [ACPCore start:^{
        [ACPCore updateConfiguration:@{@"places.membershipttl":@(30)}];

        if (appState != UIApplicationStateBackground) {
            [ACPCore lifecycleStart:nil];            
        }
    }];

    return YES;
}
```

**Swift**

```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
    // make other sdk registration calls

    let appState = application.applicationState;            
    ACPCore.start {
        ACPCore.updateConfiguration(["places.membershipttl" : 30])

        if appState != .background {
            ACPCore.lifecycleStart(nil)
        }    
    }

    return true;
}
```

## Configuratiesleutels

Om de configuratie SDK programmatically bij te werken bij runtime, gebruik de volgende informatie om uw waarden van de de uitbreidingsconfiguratie van Plaatsen te veranderen. Voor meer informatie, zie de Verwijzing [van](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/configuration/configuration-api-reference)Configuratie API.

| Sleutel | Vereist | Beschrijving |
| :--- | :--- | :--- |
| `places.libraries` | Ja | De extensiebibliotheken Plaatsen voor de mobiele app. Hier worden de bibliotheek-id en de naam van de bibliotheek opgegeven die door de mobiele app worden ondersteund. |
| `places.endpoint` | Ja | Het standaardeindpunt van de Dienst van de Vraag van Plaatsen, dat wordt gebruikt om informatie over bibliotheken en POIs te krijgen. |
| `places.membershipttl` | Nee | Standaardwaarde van 3600 (seconden in een uur). Geeft aan hoe lang, in seconden, de lidmaatschapsgegevens van Plaatsen voor het apparaat geldig blijven. |
