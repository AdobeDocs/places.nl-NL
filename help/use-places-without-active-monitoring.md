---
title: De Dienst van Plaatsen van het gebruik zonder actieve gebiedscontrole
description: Deze sectie verstrekt informatie over hoe de Dienst van Plaatsen van het gebruik zonder actieve gebiedscontrole.
translation-type: tm+mt
source-git-commit: 5846577f10eb1d570465ad7f888feba6dd958ec9
workflow-type: tm+mt
source-wordcount: '745'
ht-degree: 0%

---


# De Dienst van Plaatsen van het gebruik zonder actieve gebiedscontrole {#use-places-without-active-monitoring}

Het is mogelijk dat voor het gebruik van de hoofdletters en kleine letters voor uw toepassing geen actieve gebiedscontrole is vereist. De Dienst van Plaatsen kan nog worden gebruikt om de plaatsgegevens van uw gebruikers met andere producten van de Experience Platform te integreren.

## Vereiste

De ontwikkelaar verzamelt de locatie van het apparaat met behulp van de API&#39;s die worden geleverd door het besturingssysteem van het doelplatform.

>[!TIP]
>
>Zie [De extensie](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)Places Monitor gebruiken als er actieve gebiedscontrole nodig is voor de gebruiksgevallen van uw app.

De service Plaatsen gebruiken zonder controle van het actieve gebied:

## 1. De locatie van de gebruiker verzamelen

De ontwikkelaar van de app moet de huidige locatie van het apparaat verzamelen met behulp van de `CoreLocation.framework` (iOS) of de `Location` API&#39;s van Google Play Services (Android).

Raadpleeg de volgende documentatie voor meer informatie:

- [CoreLocation](https://developer.apple.com/documentation/corelocation) (Apple)
- [Locatie-API&#39;s in Google Play Services](https://developer.android.com/training/location) (Google)

## 2. Nearby points of interest ophalen van de SDK

Nadat u de plaats van de gebruiker verkrijgt, kunt u het tot SDK overgaan om een lijst van nabijgelegen POIs terug te krijgen.

### Android

Hier volgt een voorbeeldimplementatie in Android die een [`BroadcastReceiver`](https://codelabs.developers.google.com/codelabs/background-location-updates-android-o/index.html?index=..%2F...index#5):

```java
public class LocationBroadcastReceiver extends BroadcastReceiver {
    static final String ACTION_LOCATION_UPDATE = "locationUpdate";
    @Override
    public void onReceive(Context context, Intent intent) {
        if (intent == null || context == null) {
            return;
        }

        final String action = intent.getAction();
        if (!ACTION_LOCATION_UPDATE.equals(action)) {
            return;
        }

        LocationResult result = LocationResult.extractResult(intent);
        if (result == null) {
            return;
        }

        Location currentLocation = result.getLastLocation();
        if (currentLocation == null) {
            return;
        }

        // ask the Places SDK for the 10 nearest Points of Interest based on the user's location
        Places.getNearbyPointsOfInterest(currentLocation, 10,
            new AdobeCallback<List<PlacesPOI>>() {
                @Override
                public void call(List<PlacesPOI> pois) {
                    // pois is the 10 nearest POIs based on the location
                }
            }, new AdobeCallback<PlacesRequestError>() {
                @Override
                public void call(PlacesRequestError placesRequestError) {
                    // Look for the placesRequestError and handle the error accordingly
                }
            }
        );
    }
}
```

### Doelstelling-C

Hier volgt een voorbeeldimplementatie voor iOS. De code toont de implementatie van de [`locationManager:didUpdateLocations:`](https://developer.apple.com/documentation/corelocation/cllocationmanagerdelegate/1423615-locationmanager?language=objc) methode in [`CLLocationManagerDelegate`](https://developer.apple.com/documentation/corelocation/cllocationmanager?language=objc):

```objectivec
- (void) locationManager:(CLLocationManager*)manager didUpdateLocations:(NSArray<CLLocation*>*)locations {
    // ask the Places SDK for the 10 nearest Points of Interest based on the user's location
    [ACPPlaces getNearbyPointsOfInterest:[locations lastObject] limit:10 callback:^(NSArray<ACPPlacesPoi *> * _Nullable nearbyPoi) {
        // nearbyPoi is the 10 nearest POIs based on the location
    } errorCallback:^(ACPPlacesRequestError result) {
        // log the error if we got one
        NSLog(@"error: %lu", (unsigned long)result);
    }];
}
```

### Swift

Hier volgt een voorbeeldimplementatie voor iOS. De code toont de implementatie van de [`locationManager(_:didUpdateLocations:)`](https://developer.apple.com/documentation/corelocation/cllocationmanagerdelegate/1423615-locationmanager) methode in [`CLLocationManagerDelegate`](https://developer.apple.com/documentation/corelocation/cllocationmanager):

```swift
func locationManager(_ manager: CLLocationManager, didUpdateLocations locations: [CLLocation]) {
    // ask the Places SDK for the 10 nearest Points of Interest based on the user's location
    ACPPlaces.getNearbyPoints(ofInterest: locations.last!, limit: 10, callback: { (nearbyPoi) in
        // nearbyPoi is the 10 nearest POIs based on the location
    }) { (error) in
        // log the error if we have one
        print("error: \(error)")
    }
}
```

## 3. Gegevens van Plaatsen koppelen aan uw analyseverzoeken

Door de `getNearbyPointsOfInterest` API aan te roepen, maakt de Plaatsen SDK alle POI-gegevens relevant voor het apparaat beschikbaar via gegevenselementen in Launch. Met de regel Gegevens [](https://aep-sdks.gitbook.io/docs/resources/user-guides/attach-data) koppelen kunnen gegevens van Plaatsen automatisch worden toegevoegd aan toekomstige verzoeken aan Analytics. Dit elimineert de behoefte aan een eenmalig vraag aan Analytics op het tijdstip dat de plaats van het apparaat wordt verzameld.

Zie [Add de Context van de Plaats aan de Verzoeken](use-places-with-other-solutions/places-adobe-analytics/run-reports-aa-places-data.md) van Analytics om meer over dit onderwerp te leren.

## Optioneel - Invoergebeurtenissen activeren wanneer de gebruiker zich in een POI bevindt

>[!TIP]
>
>De aanbevolen manier om Plaatsen-gegevens vast te leggen is om Plaatsen [bij te voegen aan uw analyseverzoeken](#attach-places-data-to-your-analytics-requests).
>
>Als het gebruiksgeval vereist dat een gebeurtenis [van het](places-ext-aep-sdks/places-extension/places-event-ref.md#processregionevent) gebiedsingang door SDK wordt teweeggebracht, zal het manueel moeten worden gedaan zoals hieronder geschetst.

De lijst die door de `getNearbyPointsOfInterest` API wordt geretourneerd, bevat [aangepaste objecten](places-ext-aep-sdks/places-extension/cust-places-objects.md) die aangeven of de gebruiker zich momenteel binnen een POI bevindt. Als de gebruiker zich in een POI bevindt, kunt u de SDK een ingangsgebeurtenis voor dat gebied laten activeren.

>[!IMPORTANT]
>
>Als u wilt voorkomen dat uw app meerdere gebeurtenissen voor het invoeren van gegevens activeert tijdens één bezoek, houdt u een lijst bij van de gebieden waarvan u weet dat de gebruiker deze heeft ingevoerd. Wanneer het verwerken van de reactie van nabijgelegen POIs van SDK, teweeg een ingangsgebeurtenis slechts wanneer het gebied niet in uw lijst is.
>
>In het volgende codevoorbeeld worden `NSUserDefaults` (iOS) en `SharedPreferences` (Android) gebruikt om de lijst met regio&#39;s te beheren:

### Android

Het volgende codevoorbeeld toont de behandeling van het resultaat dat in callback van `getNearbyPointsOfInterest`, `List<PlacesPOI>`werd verstrekt:

```java
void handleUpdatedPOIs(final List<PlacesPOI> nearbyPois) {
    // get the list of regions we know the user is already within from SharedPreferences
    SharedPreferences preferences = getApplicationContext().getSharedPreferences("places", 0);
    Set<String> regionsUserIsAlreadyIn = preferences.getStringSet("regionsUserIsAlreadyIn", new HashSet<String>());

    // loop through new placesPOIS and post entry events for pois that aren't already in our list
    // also create the new list of regions that the user is in
    Set<String> updatedRegionsUserIsIn = new HashSet<String>();
    for (PlacesPOI poi : nearbyPois) {
        // check if the user is in this poi
        if (poi.containsUser()) {
            // the user is in the poi, now we need to make sure we haven't already recorded this entry event
            if (!regionsUserIsAlreadyIn.contains(poi.getIdentifier())) {
                Geofence poiGeofence = new Geofence.Builder()
                    .setRequestId(poi.getIdentifier())
                    .setTransitionTypes(Geofence.GEOFENCE_TRANSITION_ENTER)
                    .setCircularRegion(poi.getLatitude(), poi.getLongitude(), poi.getRadius())
                    .setExpirationDuration(Geofence.NEVER_EXPIRE)
                    .build();
                Places.processGeofence(poiGeofence, Geofence.GEOFENCE_TRANSITION_ENTER);
            }

            // add the region to our new list of regions
            updatedRegionsUserIsIn.add(poi.getIdentifier());
        }
    }

    // update SharedPreferences with our new list of regions
    SharedPreferences.Editor editor = getApplicationContext().getSharedPreferences("places", 0).edit();
    editor.putStringSet("regionsUserIsAlreadyIn", updatedRegionsUserIsIn).apply();
}
```

### Doelstelling-C

Het volgende codevoorbeeld toont de behandeling van het resultaat dat in callback van `getNearbyPointsOfInterest:limit:callback:errorCallback:`, werd verstrekt `NSArray<ACPPlacesPoi *> *`:

```objectivec
- (void) handleUpdatedPOIs:(NSArray<ACPPlacesPoi *> *)nearbyPois {
   // get the list of regions we know the user is already within from user defaults
   NSArray *regionsUserIsCurrentlyWithin = [[NSUserDefaults standardUserDefaults]
                                            arrayForKey:@"regionsUserIsAlreadyIn"];

   // loop through new nearbyPoi and post entry events for pois that aren't already in our list
   // also creating the new list of known regions that the user is in
   NSMutableArray *updatedRegionsUserIsCurrentlyWithin = [@[] mutableCopy];
   for (ACPPlacesPoi *poi in nearbyPois) {
       // check if the user is in this poi
       if (poi.userIsWithin) {
           // the user is in the poi, now we need to make sure we haven't already recorded the entry event
           if (![regionsUserIsCurrentlyWithin containsObject:poi.identifier]) {
               CLCircularRegion *region = [[CLCircularRegion alloc] initWithCenter:CLLocationCoordinate2DMake(poi.latitude, poi.longitude)
                                                                            radius:poi.radius
                                                                        identifier:poi.identifier];
               [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
           }

           // add the region to our updated list
           [updatedRegionsUserIsCurrentlyWithin addObject:poi.identifier];
       }
   }

   // update user defaults with the new list
   [[NSUserDefaults standardUserDefaults] setObject:updatedRegionsUserIsCurrentlyWithin forKey:@"regionsUserIsAlreadyIn"];
}
```

### Swift

Het volgende codevoorbeeld toont de behandeling van het resultaat dat in callback van `getNearbyPoints(_ ofInterest: CLLocation, limit: UInt, callback: (([ACPPlacesPoi]?) -> Void)?, errorCallback: ((ACPPlacesRequestError) -> Void)?)`, werd verstrekt `[ACPPlacesPoi]`:

```swift
func handleUpdatedPOIs(_ nearbyPois:[ACPPlacesPoi]) {
    // get the list of regions we know the user is already within from user defaults
    let regionsUserIsCurrentlyWithin : [String] = UserDefaults.standard.array(forKey: "regionsUserIsAlreadyIn") as! [String]

    // loop through new nearbyPoi and post entry events for pois that aren't already in our list
    // also creating the new list of known regions that the user is in
    var updatedRegionsUserIsCurrentlyWithin: [String] = []
    for poi in nearbyPois {
        // check if the user is in this poi
        if poi.userIsWithin {
            // the user is in the poi, now we need to make sure we haven't already recorded the entry event
            if !regionsUserIsCurrentlyWithin.contains(poi.identifier!) {
                let region = CLCircularRegion.init(center: CLLocationCoordinate2D.init(latitude: poi.latitude, longitude: poi.longitude), radius: CLLocationDistance(poi.radius), identifier: poi.identifier!)
                ACPPlaces.processRegionEvent(region, for: .entry)
            }

            // add the region to our updated list
            updatedRegionsUserIsCurrentlyWithin.append(poi.identifier!)
        }
    }

    // update user defaults with the new list
    UserDefaults.standard.set(updatedRegionsUserIsCurrentlyWithin, forKey: "regionsUserIsAlreadyIn")
}
```

## Volledige voorbeeldimplementatie

In de onderstaande codevoorbeelden ziet u hoe u de huidige locatie van het apparaat ophaalt, de benodigde gebeurtenissen voor het invoeren activeert en ervoor zorgt dat u tijdens één bezoek niet meerdere items voor dezelfde locatie ophaalt.

Dit codevoorbeeld omvat de facultatieve stap van het [teweegbrengen van een ingangsgebeurtenissen wanneer de gebruiker in POI](#trigger-entry-events-when-the-user-is-in-a-poi)is.

>[!IMPORTANT]
>
>Deze fragmenten zijn **slechts** voorbeelden. De ontwikkelaars moeten bepalen hoe zij de functionaliteit willen uitvoeren, en het besluit zou de beste praktijken moeten overwegen zoals die door het doelwerkende systeem worden geadviseerd.

### Android

```java
public class LocationBroadcastReceiver extends BroadcastReceiver {
    static final String ACTION_LOCATION_UPDATE = "locationUpdate";
    @Override
    public void onReceive(Context context, Intent intent) {
        if (intent == null || context == null) {
            return;
        }

        final String action = intent.getAction();
        if (!ACTION_LOCATION_UPDATE.equals(action)) {
            return;
        }

        LocationResult result = LocationResult.extractResult(intent);
        if (result == null) {
            return;
        }

        Location currentLocation = result.getLastLocation();
        if (currentLocation == null) {
            return;
        }

        // ask the Places SDK for the 10 nearest Points of Interest based on the user's location
        Places.getNearbyPointsOfInterest(currentLocation, 10,
            new AdobeCallback<List<PlacesPOI>>() {
                @Override
                public void call(List<PlacesPOI> pois) {
                    // pois is the 10 nearest POIs based on the location
                    handleUpdatedPOIs(pois);
                }
            }, new AdobeCallback<PlacesRequestError>() {
                @Override
                public void call(PlacesRequestError placesRequestError) {
                    // Look for the placesRequestError and handle the error accordingly
                }
            }
        );
    }

    void handleUpdatedPOIs(final List<PlacesPOI> nearbyPois) {
        // get the list of regions we know the user is already within from SharedPreferences
        SharedPreferences preferences = getApplicationContext().getSharedPreferences("places", 0);
        Set<String> regionsUserIsAlreadyIn = preferences.getStringSet("regionsUserIsAlreadyIn", new HashSet<String>());

        // loop through new placesPOIS and post entry events for pois that aren't already in our list
        // also create the new list of regions that the user is in
        Set<String> updatedRegionsUserIsIn = new HashSet<String>();
        for (PlacesPOI poi : nearbyPois) {
            // check if the user is in this poi
            if (poi.containsUser()) {
                // the user is in the poi, now we need to make sure we haven't already recorded this entry event
                if (!regionsUserIsAlreadyIn.contains(poi.getIdentifier())) {
                    Geofence poiGeofence = new Geofence.Builder()
                        .setRequestId(poi.getIdentifier())
                        .setTransitionTypes(Geofence.GEOFENCE_TRANSITION_ENTER)
                        .setCircularRegion(poi.getLatitude(), poi.getLongitude(), poi.getRadius())
                        .setExpirationDuration(Geofence.NEVER_EXPIRE)
                        .build();
                    Places.processGeofence(poiGeofence, Geofence.GEOFENCE_TRANSITION_ENTER);
                }

                // add the region to our new list of regions
                updatedRegionsUserIsIn.add(poi.getIdentifier());
            }
        }

        // update SharedPreferences with our new list of regions
        SharedPreferences.Editor editor = getApplicationContext().getSharedPreferences("places", 0).edit();
        editor.putStringSet("regionsUserIsAlreadyIn", updatedRegionsUserIsIn).apply();
    }
}
```


### Doelstelling-C

```objectivec
- (void) locationManager:(CLLocationManager*)manager didUpdateLocations:(NSArray<CLLocation*>*)locations {
    // ask the Places SDK for the 10 nearest Points of Interest based on the user's location
    [ACPPlaces getNearbyPointsOfInterest:[locations lastObject] limit:10 callback:^(NSArray<ACPPlacesPoi *> * _Nullable nearbyPoi) {
        // nearbyPoi is the 10 nearest POIs based on the location
        [self handleUpdatedPOIs:nearbyPoi];
    } errorCallback:^(ACPPlacesRequestError result) {
        // log the error if we got one
        NSLog(@"error: %lu", (unsigned long)result);
    }];
}

- (void) handleUpdatedPOIs:(NSArray<ACPPlacesPoi *> *)nearbyPois {
   // get the list of regions we know the user is already within from user defaults
   NSArray *regionsUserIsCurrentlyWithin = [[NSUserDefaults standardUserDefaults]
                                            arrayForKey:@"regionsUserIsAlreadyIn"];

   // loop through new nearbyPoi and post entry events for pois that aren't already in our list
   // also creating the new list of known regions that the user is in
   NSMutableArray *updatedRegionsUserIsCurrentlyWithin = [@[] mutableCopy];
   for (ACPPlacesPoi *poi in nearbyPois) {
       // check if the user is in this poi
       if (poi.userIsWithin) {
           // the user is in the poi, now we need to make sure we haven't already recorded the entry event
           if (![regionsUserIsCurrentlyWithin containsObject:poi.identifier]) {
               CLCircularRegion *region = [[CLCircularRegion alloc] initWithCenter:CLLocationCoordinate2DMake(poi.latitude, poi.longitude)
                                                                            radius:poi.radius
                                                                        identifier:poi.identifier];
               [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
           }

           // add the region to our updated list
           [updatedRegionsUserIsCurrentlyWithin addObject:poi.identifier];
       }
   }

   // update user defaults with the new list
   [[NSUserDefaults standardUserDefaults] setObject:updatedRegionsUserIsCurrentlyWithin forKey:@"regionsUserIsAlreadyIn"];
}
```

### Swift

```swift
func locationManager(_ manager: CLLocationManager, didUpdateLocations locations: [CLLocation]) {
    // ask the Places SDK for the 10 nearest Points of Interest based on the user's location
    ACPPlaces.getNearbyPoints(ofInterest: locations.last!, limit: 10, callback: { (nearbyPoi) in
        // nearbyPoi is the 10 nearest POIs based on the location
        self.handleUpdatedPOIs(nearbyPoi!)
    }) { (error) in
        // log the error if we have one
        print("error: \(error)")
    }
}

func handleUpdatedPOIs(_ nearbyPois:[ACPPlacesPoi]) {
    // get the list of regions we know the user is already within from user defaults
    let regionsUserIsCurrentlyWithin : [String] = UserDefaults.standard.array(forKey: "regionsUserIsAlreadyIn") as! [String]

    // loop through new nearbyPoi and post entry events for pois that aren't already in our list
    // also creating the new list of known regions that the user is in
    var updatedRegionsUserIsCurrentlyWithin: [String] = []
    for poi in nearbyPois {
        // check if the user is in this poi
        if poi.userIsWithin {
            // the user is in the poi, now we need to make sure we haven't already recorded the entry event
            if !regionsUserIsCurrentlyWithin.contains(poi.identifier!) {
                let region = CLCircularRegion.init(center: CLLocationCoordinate2D.init(latitude: poi.latitude, longitude: poi.longitude), radius: CLLocationDistance(poi.radius), identifier: poi.identifier!)
                ACPPlaces.processRegionEvent(region, for: .entry)
            }

            // add the region to our updated list
            updatedRegionsUserIsCurrentlyWithin.append(poi.identifier!)
        }
    }

    // update user defaults with the new list
    UserDefaults.standard.set(updatedRegionsUserIsCurrentlyWithin, forKey: "regionsUserIsAlreadyIn")
}
```

Naast het in werking stellen van de de ingangsgebeurtenissen van de Dienst van Plaatsen in SDK, wegens de het teweegbrengen ingangsgebeurtenissen, kunnen alle gegevens die uw POIs bepalen door de rest van SDK via `data elements` in Experience Platform Launch worden gebruikt. Met Experience Platform Launch `rules`, kunt u dynamisch de gegevens van de Dienst van Plaatsen aan inkomende gebeurtenissen vastmaken die door SDK worden verwerkt. Bijvoorbeeld, kunt u de meta- gegevens van POI vastmaken waarin de gebruiker wordt gevestigd en de gegevens verzenden naar Analytics als contextgegevens.

Voor meer informatie, zie het [Gebruiken van de Dienst van Plaatsen met andere oplossingen](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-analytics-overview.md)van Adobe.
