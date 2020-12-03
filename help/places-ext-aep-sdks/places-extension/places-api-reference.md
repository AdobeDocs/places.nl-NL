---
title: Plaatst API-referentie
description: Informatie over de API-referenties in Plaatsen.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 31%

---


# Plaatst API-referentie {#places-api-reference}

Hier volgt informatie over de API-verwijzingen in de extensie Plaatsen:

## Een regiogebeurtenis verwerken

Wanneer een apparaat een van de vooraf gedefinieerde grenzen van de Plaatsingsservice van uw app overschrijdt, worden het gebied en het gebeurtenistype voor verwerking aan de SDK doorgegeven.

### ProcessGeofence (Android)

Verwerk een `Geofence` regiogebeurtenis voor de opgegeven toepassing `transitionType`.

Geef het `transitionType` door van `GeofencingEvent.getGeofenceTransition()`. Momenteel `Geofence.GEOFENCE_TRANSITION_ENTER` en `Geofence.GEOFENCE_TRANSITION_EXIT` worden ondersteund.

**Syntaxis**

Hier volgt de syntaxis voor deze methode:

```java
public static void processGeofence(final Geofence geofence, final int transitionType);
```

**Voorbeeld**

Roep deze methode aan in uw `IntentService` account die is geregistreerd voor het ontvangen van geofence-gebeurtenissen van Android.

Hier volgt een codevoorbeeld voor deze methode:

```java
public class GeofenceTransitionsIntentService extends IntentService {

    public GeofenceTransitionsIntentService() {
        super("GeofenceTransitionsIntentService");
    }

    protected void onHandleIntent(Intent intent) {
        GeofencingEvent geofencingEvent = GeofencingEvent.fromIntent(intent);

        List<Geofence> geofences = geofencingEvent.getTriggeringGeofences();

        if (geofences.size() > 0) {
          // Call the Places API to process information
          Places.processGeofence(geofences.get(0), geofencingEvent.getGeofenceTransition());
        }
    }
}
```

### ProcessRegionEvent (iOS)

Deze methode zou in de `CLLocationManager` afgevaardigde moeten worden geroepen, die vertelt of de gebruiker een specifiek gebied is ingegaan of vertrokken.

**Syntaxis**

Hier volgt de syntaxis voor deze methode:

```objectivec
+ (void) processRegionEvent: (nonnull CLRegion*) region forRegionEventType: (ACPRegionEventType) eventType;
```

**Voorbeeld**

Hier volgt het codevoorbeeld voor deze methode:


```objectivec
- (void) locationManager:(CLLocationManager *)manager didEnterRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
}

- (void) locationManager:(CLLocationManager *)manager didExitRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeExit];
}
```

### ProcessGeofencingEvent (Android)

Proces allemaal `Geofences` tegelijk `GeofencingEvent` .

**Syntaxis**

```java
public static void processGeofenceEvent(final GeofencingEvent geofencingEvent);
```

**Voorbeeld**

Roep deze methode aan in uw `IntentService` systeem dat is geregistreerd voor het ontvangen van geofence-gebeurtenissen van Android

```java
public class GeofenceTransitionsIntentService extends IntentService {

    public GeofenceTransitionsIntentService() {
        super("GeofenceTransitionsIntentService");
    }

    protected void onHandleIntent(Intent intent) {
        GeofencingEvent geofencingEvent = GeofencingEvent.fromIntent(intent);
        // Call the Places API to process information
        Places.processGeofenceEvent(geofencingEvent);
    }
}
```

## Dichtbij gelegen interessepunten ophalen

Retourneert een geordende lijst van nabijgelegen POI&#39;s in een callback. Een overbelaste versie van deze methode retourneert een foutcode als er iets fout is gegaan met de resulterende netwerkaanroep.

### GetNearbyPointsOfInterest (Android)

Hier volgt de syntaxis voor deze methode:

**Syntaxis**

```java
public static void getNearbyPointsOfInterest(final Location location, final int limit,
                                             final AdobeCallback<List<PlacesPOI>> callback);

public static void getNearbyPointsOfInterest(final Location location, final int limit,
                                             final AdobeCallback<List<PlacesPOI>> callback,
                                             final AdobeCallback<PlacesRequestError> errorCallback);
```

**Voorbeeld**

Hier volgt het codevoorbeeld voor deze methode:

```java
// getNearbyPointsOfInterest without an error callback
Places.getNearbyPointsOfInterest(currentLocation, 10, new AdobeCallback<List<PlacesPOI>>() {
    @Override
    public void call(List<PlacesPOI> pois) {
        // do required processing with the returned nearbyPoi array
        startMonitoringPois(pois);
    }
});

// getNearbyPointsOfInterest with an error callback
Places.getNearbyPointsOfInterest(currentLocation, 10,
    new AdobeCallback<List<PlacesPOI>>() {
        @Override
        public void call(List<PlacesPOI> pois) {
            // do required processing with the returned nearbyPoi array
            startMonitoringPois(pois);
        }
    }, new AdobeCallback<PlacesRequestError>() {
        @Override
        public void call(PlacesRequestError placesRequestError) {
            // look for the placesRequestError and handle the error accordingly
            handleError(placesRequestError);
        }
    }
);
```

### GetNearbyPointsOfInterest (iOS)

**Syntaxis**

```objectivec
+ (void) getNearbyPointsOfInterest: (nonnull CLLocation*) currentLocation
                             limit: (NSUInteger) limit
                          callback: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi)) callback;

+ (void) getNearbyPointsOfInterest: (nonnull CLLocation*) currentLocation
                             limit: (NSUInteger) limit
                          callback: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi)) callback
                     errorCallback: (nullable void (^) (ACPPlacesRequestError result)) errorCallback;
```

**Voorbeeld**

```objectivec
// getNearbyPointsOfInterest without an error callback
[ACPPlaces getNearbyPointsOfInterest:location
                               limit:10     
                            callback:^(NSArray<ACPPlacesPoi*>* nearbyPoi) {
    // do required processing with the returned nearbyPoi array
    [self startMonitoringPois:nearbyPOI];
}];

// getNearbyPointsOfInterest with an error callback
[ACPPlaces getNearbyPointsOfInterest:location limit:10
    callback:^(NSArray<ACPPlacesPoi *> * _Nullable nearbyPoi) {
        // do required processing with the returned nearbyPoi array
        [self startMonitoringPois:nearbyPOI];
    } errorCallback:^(ACPPlacesRequestError result) {
        // look for the error and handle accordingly
        [self handleError:result];
    }
];
```

## Huidige apparaatpunten ophalen

Verzoekt een lijst van POIs waarin het apparaat momenteel om binnen gekend is te zijn en keert hen in een callback terug.

### GetCurrentPointsOfInterest (Android)

Hier volgt de syntaxis voor deze methode:

**Syntaxis**

```java
public static void getCurrentPointsOfInterest(final AdobeCallback<List<PlacesPOI>> callback);
```

**Voorbeeld**

Hier volgt het codevoorbeeld voor deze methode:

```java
Places.getCurrentPointsOfInterest(new AdobeCallback<List<PlacesPOI>>() {
    @Override
    public void call(List<PlacesPOI> pois) {
        // use the obtained POIs that the device is within
        processUserWithinPois(pois);        
    }
});
```

### GetCurrentPointsOfInterest (iOS)

**Syntaxis**

Hier volgt de syntaxis voor deze methode:

```objectivec
+ (void) getCurrentPointsOfInterest: (nullable void (^) (NSArray<ACPPlacesPoi*>* _Nullable userWithinPoi)) callback;
```

**Voorbeeld**

Hier volgt het codevoorbeeld voor deze methode:

```objectivec
[ACPPlaces getCurrentPointsOfInterest:^(NSArray<ACPPlacesPoi*>* userWithinPoi) {
    // do required processing with the returned userWithinPoi array
    [self processUserWithinPois:userWithinPoi];
}];
```


## De locatie van het apparaat ophalen

Verzoekt de locatie van het apparaat, zoals eerder bekend, door de extensie Plaatsen.

>[!TIP]
>
>De extensie Plaatsen kent alleen locaties die via aanroepen naar aan zijn verschaft. `GetNearbyPointsOfInterest`


### GetLastKnownLocation (Android)

**Syntaxis**

Hier volgt de syntaxis voor deze methode:

```java
public static void getLastKnownLocation(final AdobeCallback<Location> callback);
```

**Voorbeeld**

Hier volgt het codevoorbeeld voor deze methode:

```java
Places.getLastKnownLocation(new AdobeCallback<Location>() {
    @Override
    public void call(Location lastLocation) {
        // do something with the last known location
        processLastKnownLocation(lastLocation);        
    }
});
```

### GetLastKnownLocation (iOS)

**Syntaxis**

Hier volgt de syntaxis voor deze methode:

```objectivec
+ (void) getLastKnownLocation: (nullable void (^) (CLLocation* _Nullable lastLocation)) callback;
```

**Voorbeeld**

Hier volgt het codevoorbeeld voor deze methode:

```objectivec
[ACPPlaces getLastKnownLocation:^(CLLocation* lastLocation) {
    // do something with the last known location
    [self processLastKnownLocation:lastLocation];
}];
```

## Gegevens aan clientzijde wissen


### Wissen (Android)

Hiermee wist u de clientgegevens voor de extensie Plaatsen in de gedeelde status, lokale opslag en in het geheugen.

**Syntaxis**

Hier volgt de syntaxis voor deze methode:

```java
public static void clear();
```

**Voorbeeld**

Hier volgt het codevoorbeeld voor deze methode:

```java
Places.clear();
```

### clear (iOS)

Hiermee wist u de clientgegevens voor de extensie Plaatsen in gedeelde staat, lokale opslag en in het geheugen.

**Syntaxis**

Hier volgt de syntaxis voor deze methode:

```objectivec
+ (void) clear;
```

**Voorbeeld**

Hier volgt het codevoorbeeld voor deze methode:

```objectivec
[ACPPlaces clear];
```

## Status van locatietoestemming instellen

### setAuthorizationStatus (Android)

*Beschikbaar vanaf Plaatsen v1.4.0*

Hiermee stelt u de machtigingsstatus in de extensie Plaatsen in.

De opgegeven status wordt opgeslagen in de gedeelde status Plaatsen en is alleen ter referentie.
Het aanroepen van deze methode heeft geen invloed op de eigenlijke status van de locatietoestemming voor dit apparaat.

**Syntaxis**

Hier volgt de syntaxis voor deze methode:

```java
public static void setAuthorizationStatus(final PlacesAuthorizationStatus status);
```

**Voorbeeld**

Hier volgt het codevoorbeeld voor deze methode:

```java
Places.setAuthorizationStatus(PlacesAuthorizationStatus.ALWAYS);
```

### setAuthorizationStatus (iOS)

*Beschikbaar vanaf ACPPlaces v1.3.0*

Hiermee stelt u de machtigingsstatus in de extensie Plaatsen in.

De opgegeven status wordt opgeslagen in de gedeelde status Plaatsen en is alleen ter referentie.
Het aanroepen van deze methode heeft geen invloed op de eigenlijke status van de locatietoestemming voor dit apparaat.

Wanneer de status van de apparaatautorisatie verandert, wordt de `locationManager:didChangeAuthorizationStatus:` methode van de autorisatie `CLLocationManagerDelegate` aangeroepen. Vanuit deze methode moet u de nieuwe `CLAuthorizationStatus` waarde doorgeven aan de ACPPlaces- `setAuthorizationStatus:` API.

**Syntaxis**

Hier volgt de syntaxis voor deze methode:

```objectivec
+ (void) setAuthorizationStatus: (CLAuthorizationStatus) status;
```

**Voorbeeld**

Hier volgt het codevoorbeeld voor deze methode:

```objectivec
- (void) locationManager: (CLLocationManager*) manager didChangeAuthorizationStatus: (CLAuthorizationStatus) status {    
    [ACPPlaces setAuthorizationStatus:status];
}
```
