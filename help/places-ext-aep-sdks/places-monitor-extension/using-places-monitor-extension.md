---
title: De extensie Plaatsen gebruiken
description: Informatie over het installeren, configureren en gebruiken van de extensie Places Monitor.
translation-type: tm+mt
source-git-commit: 7fdaace59886225b7fd9b0eba8cc6c2a139fa2d7
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 6%

---


# De extensie Plaatsen gebruiken {#using-places-monitor-extension}

Als u de extensie Plaatsen Monitor wilt gebruiken, voert u de volgende taken uit:

## De extensie Plaatsen in Experience Platform Launch installeren

1. Klik in Experience Platform Launch op het tabblad **[!UICONTROL Extensions]**.
1. Zoek op het **[!UICONTROL Catalog]** tabblad de **[!UICONTROL Places Monitor]** extensie en klik op **Installeren**.
1. Klik op **[!UICONTROL Save]**.
1. Volg het publicatieproces om de SDK-configuratie bij te werken.

### De extensie Plaatsen Monitor configureren {#configure-places-monitor-extension}

Er zijn geen configuratietaken voor de uitbreiding van de Monitor van Plaatsen.

![configureren van de Monitor](/help/assets/configure_places_monitor.png)Plaatsen ‌

## De extensie Plaatsen toevoegen aan uw app {#add-monitor-extension-to-app}

Hieronder vindt u aanwijzingen voor het toevoegen van de extensie Plaatsen Monitor aan uw Android- of iOS-toepassing.

De extra platformsteun voor de uitbreiding van de Monitor van Plaatsen omvat:
**[Monitor Cordova-locaties](https://github.com/adobe/cordova-acpplaces-monitor/blob/master/README.md)**

**[Monitor van native locaties reageren](https://github.com/adobe/react-native-acpplaces-monitor/blob/master/README.md)**

**[Monitor voor dynamische locaties](https://github.com/adobe/flutter_acpplaces_monitor/blob/master/README.md)**


### Android

Voer in Android de volgende stappen uit:

#### Java

1. Voeg de extensie Places Monitor en de extensie Plaatsen toe aan uw project met behulp van het grijze bestand van uw app.

1. Neem ook de nieuwste Google Location-services op in het onbewerkte bestand.

   ```java
   implementation 'com.adobe.marketing.mobile:places:1.+'
   implementation 'com.adobe.marketing.mobile:places-monitor:1.+'
   implementation 'com.adobe.marketing.mobile:sdk-core:1.+'
   implementation 'com.google.android.gms:play-services-location:16.0.0'
   ```

1. Importeer de extensie Plaatsen in de hoofdactiviteit van de toepassing.

   ```java
   import com.adobe.marketing.mobile.PlacesMonitor;
   ```

### iOS

Voer in iOS de volgende stappen uit:

1. Voeg de bibliotheek aan uw project via uw Cocoapods toe `Podfile` door toe te voegen `pod 'ACPPlacesMonitor'`.
1. Importeer de bibliotheken in het deelvenster Plaatsen en het deelvenster Plaatsen:

#### Doelstelling-C

```objectivec
#import "ACPCore.h"
#import "ACPPlaces.h"
#import "ACPPlacesMonitor.h"
```

#### Swift

```swift
import ACPCore
import ACPPlaces
import ACPPlacesMonitor
```


## De monitor Plaatsen registreren en starten {#register-start-places-monitor}

U moet de Places Monitor registreren en starten in Android of iOS.

## Android

Voer in Android de volgende stappen uit:

### Java

In de `OnCreate` methode van uw app registreert u de extensies van de Monitor van Plaatsen:

```java
public class MobileApp extends Application {
    @Override
    public void onCreate() {
        super.onCreate();
        MobileCore.setApplication(this);
        MobileCore.ConfigureWithAppId("yourAppId");
        try {
            PlacesMonitor.registerExtension(); //Register PlacesMonitor with Mobile Core
            Places.registerExtension(); //Register Places with Mobile Core
            MobileCore.start(null);
            PlacesMonitor.start();//Start monitoring the geo-fences
        } catch (Exception e) {
            //Log the exception
        }
    }
}
```

>[!IMPORTANT]
>
>Plaatscontrole is afhankelijk van de extensie Plaatsen. Wanneer u de uitbreiding Places Monitor (Plaatsen bijhouden) handmatig installeert, moet u ook de `places.aar`-bibliotheek aan het project toevoegen.

## iOS

Meld u aan bij Mobile Core in uw iOS-app`application:didFinishLaunchingWithOptions`en plaats `PlacesMonitor` deze:

### Doelstelling-C

```objectivec
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary*)launchOptions {
    [ACPCore configureWithAppId:@"yourAppId"];
    [ACPPlaces registerExtension];
    [ACPPlacesMonitor registerExtension];
    [ACPCore start:^{            
        // do other initialization required for the SDK
        [ACPPlacesMonitor start];
    }];

    return YES;
}
```

#### Swift

```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
    ACPCore.configure(withAppId: "yourAppId")
    ACPPlaces.registerExtension()       
    ACPPlacesMonitor.registerExtension()
    ACPCore.start({
        // do other initialization required for the SDK
        ACPPlacesMonitor.start()
    })

    // Override point for customization after application launch.        
    return true
}
```

>[!IMPORTANT]
>
>Plaatscontrole is afhankelijk van de extensie Plaatsen. When manually installing the Places Monitor extension, ensure that you also add the `libACPPlaces_iOS.a` library to your project.


## Machtigingen toevoegen aan het manifest

### Android

**Java**

Als u voor alle versies van Android wilt declareren dat uw toepassing locatierechten nodig heeft, voegt u een `<uses-permission>` element in uw toepassingsmanifest toe als een onderliggend element van het `<manifest>` element op hoofdniveau. Voor Android-toepassingen die zijn gericht op API-niveau 29 en hoger, neemt u de machtiging ACCESS_BACKGROUND_LOCATION op om de toepassing toegang te geven tot een locatie op de achtergrond.

```java
<manifest xmlns:android="http://schemas.android.com/apk/res/android" package="com.adobe.placesapp">
  <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
    // Only for Android apps targeting API level 29 and above
  <uses-permission android:name="android.permission.ACCESS_BACKGROUND_LOCATION" />
  <application>        
    ...    
  </application>
</manifest>
```


## Locatie-updates op de achtergrond inschakelen  {#enable-location-updates-background}

iOS ondersteunt het leveren van locatiegebeurtenissen voor apps die zijn opgeschort of niet meer actief zijn. Als u locatie-updates wilt ontvangen op de achtergrond voor de extensie Places Monitor, configureert u de mogelijkheid voor Locatie-updates voor uw app in `Xcode.background-location-updates`.

![de Monitor Plaatsen gebruiken](/help/assets/using-the-places-monitor_1.png)

## De plist-toetsen configureren

De volgende toetsen moeten in het `Info.plist` bestand van uw app worden opgenomen:

* `NSLocationWhenInUseUsageDescription` - in de tekst moet worden beschreven waarom de toepassing toegang tot de locatie-informatie van de gebruiker aanvraagt terwijl deze op de voorgrond wordt uitgevoerd.
* `NSLocationAlwaysAndWhenInUseUsageDescription` - in de tekst moet worden beschreven waarom de toepassing te allen tijde toegang tot de locatie-informatie van de gebruiker aanvraagt.

>[!TIP]
>
>Als uw app iOS 10 en lager ondersteunt, is de `NSLocationAlwaysUsageDescription` toets ook vereist.

![](/help/assets/using-the-places-monitor_2.png)
