---
title: De Dienst van Plaatsen van het gebruik zonder actieve gebiedscontrole
description: Deze sectie verstrekt informatie over hoe de Dienst van Plaatsen van het gebruik zonder actieve gebiedscontrole.
exl-id: 0ba7949a-447e-4754-9b45-945e58e29541
source-git-commit: 33cbef9b3226be3f013fe82d619b82e093a9752a
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 0%

---

# De Dienst van Plaatsen van het gebruik zonder actieve gebiedscontrole {#use-places-without-active-monitoring}

Het is mogelijk dat voor het gebruik van de hoofdletters en kleine letters voor uw toepassing geen actieve gebiedscontrole is vereist. De Dienst van Plaatsen kan nog worden gebruikt om de plaatsgegevens van uw gebruikers met andere producten van de Experience Platform te integreren.

## Voorwaarde

De ontwikkelaar verzamelt de locatie van het apparaat met behulp van de API&#39;s die worden geleverd door het besturingssysteem van het doelplatform.

>[!TIP]
>
>Als de het gebruiksgevallen van uw app actieve gebiedscontrole vereisen, zie {de Dienst van Plaatsen van het 0} Gebruik met uw eigen controlemethode [&#128279;](/help/using-your-own-monitor.md).

De service Plaatsen gebruiken zonder controle van het actieve gebied:

## 1. Verzamel de locatie van de gebruiker

De ontwikkelaar van de app moet de huidige locatie van het apparaat verzamelen met behulp van de `CoreLocation.framework` (iOS) of de `Location` -API&#39;s die door Google Play Services (Android) worden geleverd.

Raadpleeg de volgende documentatie voor meer informatie:

- [ CoreLocation ](https://developer.apple.com/documentation/corelocation) (Apple)
- [ Plaats APIs in de Diensten van Google Play ](https://developer.android.com/training/location) (Google)

## 2. Aangrenzende aandachtspunten van de SDK ophalen

Nadat u de plaats van de gebruiker verkrijgt, kunt u het tot SDK overgaan om een lijst van nabijgelegen POIs terug te krijgen.

### Android

Hier is een steekproefimplementatie in Android die a [`BroadcastReceiver` ](https://codelabs.developers.google.com/codelabs/background-location-updates-android-o/index.html?index=..%2F...index#5) gebruikt:

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

Hier volgt een voorbeeldimplementatie voor iOS. De code toont implementatie van de [`locationManager:didUpdateLocations:` ](https://developer.apple.com/documentation/corelocation/cllocationmanagerdelegate/1423615-locationmanager?language=objc) methode in [`CLLocationManagerDelegate` ](https://developer.apple.com/documentation/corelocation/cllocationmanager?language=objc):

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

Hier volgt een voorbeeldimplementatie voor iOS. De code toont implementatie van de [`locationManager(_:didUpdateLocations:)` ](https://developer.apple.com/documentation/corelocation/cllocationmanagerdelegate/1423615-locationmanager) methode in [`CLLocationManagerDelegate` ](https://developer.apple.com/documentation/corelocation/cllocationmanager):

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

## 3. Voeg gegevens van Plaatsen aan uw verzoeken Analytics toe

Door de API `getNearbyPointsOfInterest` aan te roepen, maakt de SDK van Plaatsen alle POI-gegevens relevant voor het apparaat beschikbaar via gegevenselementen in Launch. Door een [ regel van Gegevens van de Band ](https://aep-sdks.gitbook.io/docs/resources/user-guides/attach-data) te gebruiken, kunnen de gegevens van Plaatsen automatisch aan toekomstige verzoeken aan Analytics worden toegevoegd. Dit elimineert de behoefte aan een eenmalig vraag aan Analytics op het tijdstip dat de plaats van het apparaat wordt verzameld.

Zie [ de Context van de Plaats aan de Verzoeken van Analytics ](use-places-with-other-solutions/places-adobe-analytics/run-reports-aa-places-data.md) toevoegen om meer over dit onderwerp te leren.

## Optioneel - Invoergebeurtenissen activeren wanneer de gebruiker zich in een POI bevindt

>[!TIP]
>
>De geadviseerde manier om het gegeven van Plaatsen te vangen is [ de gegevens van Plaatsen aan uw verzoeken van Analytics ](#attach-places-data-to-your-analytics-requests) vast te maken.
>
>Als het gebruiksgeval de gebeurtenis van de a [ gebiedingang ](https://developer.adobe.com/client-sdks/documentation/places/api-reference/#processregionevent) vereist om door SDK worden teweeggebracht, zal het manueel moeten worden gedaan zoals hieronder geschetst.

De lijst die door `getNearbyPointsOfInterest` API is teruggekeerd bevat [ douanevoorwerpen ](https://developer.adobe.com/client-sdks/documentation/places/api-reference/#additional-classes-and-enums) die erop wijzen als de gebruiker momenteel binnen POI is. Als de gebruiker zich in een POI bevindt, kunt u de SDK een ingangsgebeurtenis voor dat gebied laten activeren.

>[!IMPORTANT]
>
>Als u wilt voorkomen dat uw app meerdere gebeurtenissen voor het invoeren van gegevens activeert tijdens één bezoek, houdt u een lijst bij van de gebieden waarvan u weet dat de gebruiker deze heeft ingevoerd. Wanneer het verwerken van de reactie van nabijgelegen POIs van SDK, teweeg een ingangsgebeurtenis slechts wanneer het gebied niet in uw lijst is.
>
>In het volgende codevoorbeeld worden `NSUserDefaults` (iOS) en `SharedPreferences` (Android) gebruikt om de lijst met gebieden te beheren:

### Android

Het volgende codevoorbeeld toont de behandeling van het resultaat dat in callback van `getNearbyPointsOfInterest`, a `List<PlacesPOI>` werd verstrekt:

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

Het volgende codevoorbeeld toont de behandeling van het resultaat dat in callback van `getNearbyPointsOfInterest:limit:callback:errorCallback:`, en `NSArray<ACPPlacesPoi *> *` werd verstrekt:

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

Het volgende codevoorbeeld toont de behandeling van het resultaat dat in callback van `getNearbyPoints(_ ofInterest: CLLocation, limit: UInt, callback: (([ACPPlacesPoi]?) -> Void)?, errorCallback: ((ACPPlacesRequestError) -> Void)?)`, en `[ACPPlacesPoi]` werd verstrekt:

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

Dit codevoorbeeld omvat de facultatieve stap van [ die een ingangsgebeurtenissen teweegbrengen wanneer de gebruiker in POI ](#trigger-entry-events-when-the-user-is-in-a-poi) is.

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

Naast het activeren van Places Service-entry-gebeurtenissen in de SDK, kunnen vanwege de activerende entry-gebeurtenissen alle gegevens die uw POI&#39;s definiëren, door de rest van de SDK worden gebruikt via `data elements` in Experience Platform Launch. Met Experience Platform Launch `rules` kunt u dynamisch de gegevens van de Dienst van Plaatsen aan inkomende gebeurtenissen vastmaken die door SDK worden verwerkt. Bijvoorbeeld, kunt u de meta- gegevens van POI vastmaken waarin de gebruiker wordt gevestigd en de gegevens verzenden naar Analytics als contextgegevens.

Voor meer informatie, zie [ Gebruikend de Dienst van Plaatsen met andere oplossingen van de Adobe ](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-analytics-overview.md).
