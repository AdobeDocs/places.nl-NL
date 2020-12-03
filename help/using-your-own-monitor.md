---
title: Uw eigen monitor gebruiken
description: U kunt ook uw controleservices gebruiken en integreren met de Places Service met behulp van de API's voor de uitbreiding Plaatsen Service.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 1%

---


# Uw eigen monitor gebruiken {#using-your-monitor}

U kunt ook uw controleservices gebruiken en integreren met de Places-service met behulp van de Places-API&#39;s.

## Geofences registreren

Als u besluit om uw controlediensten te gebruiken, registreer de geofences van POIs rond uw huidige plaats door de volgende stappen te voltooien:

### iOS

Voer in iOS de volgende stappen uit:

1. Geef de locatie-updates die zijn verkregen van de Core location services van iOS door aan de Places extensie.

1. Gebruik de API voor `getNearbyPointsOfInterest` Plaatsen-extensie om de array met `ACPPlacesPoi` objecten rond de huidige locatie op te halen.

   ```objective-c
   - (void) locationManager: (CLLocationManager*) manager didUpdateLocations: (NSArray<CLLocation*>*) locations {
       [ACPPlaces getNearbyPointsOfInterest:currentLocation limit:10 callback: ^ (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi) {
           [self startMonitoringGeoFences:nearbyPoi];
       }];
   }
   ```

1. Haal de informatie uit de verkregen `ACPPlacesPOI` objecten en begin met het controleren van die POI&#39;s.

   ```objective-c
   - (void) startMonitoringGeoFences: (NSArray*) newGeoFences {
       // verify if the device supports monitoring geofences
       // check for location permission
   
       for (ACPPlacesPoi * currentRegion in newGeoFences) {
           // make the circular region
           CLLocationCoordinate2D center = CLLocationCoordinate2DMake(currentRegion.latitude, currentRegion.longitude);
           CLCircularRegion* currentCLRegion = [[CLCircularRegion alloc] initWithCenter:center
                                                                                 radius:currentRegion.radius
                                                                             identifier:currentRegion.identifier];
           currentCLRegion.notifyOnExit = YES;
           currentCLRegion.notifyOnEntry = YES;
   
           // start monitoring the new region
           [_locationManager startMonitoringForRegion:currentCLRegion];
       }
   }
   ```

### Android

1. Geef de locatie-updates die zijn verkregen van de Google Play-services of de Android-locatieservices door aan de Places Extension.

1. Gebruik de API voor extensie `getNearbyPointsOfInterest` Plaatsen om de lijst met `PlacesPoi` objecten rond de huidige locatie op te halen.

   ```java
   LocationCallback callback = new LocationCallback() {
       @Override
       public void onLocationResult(LocationResult locationResult) {
           super.onLocationResult(locationResult);
   
           Places.getNearbyPointsOfInterest(currentLocation, 10, new AdobeCallback<List<PlacesPOI>>() {
               @Override
               public void call(List<PlacesPOI> pois) {
                   starMonitoringGeofence(pois);
               }
           });
       }
   };
   ```

1. Haal de gegevens uit de verkregen `PlacesPOI` objecten en begin met het controleren van die POI&#39;s.

   ```java
   private void startMonitoringFences(final List<PlacesPOI> nearByPOIs) {
       // check for location permission
       for (PlacesPOI poi : nearByPOIs) {
           final Geofence fence = new Geofence.Builder()
               .setRequestId(poi.getIdentifier())
               .setCircularRegion(poi.getLatitude(), poi.getLongitude(), poi.getRadius())
               .setExpirationDuration(Geofence.NEVER_EXPIRE)
               .setTransitionTypes(Geofence.GEOFENCE_TRANSITION_ENTER |
                                   Geofence.GEOFENCE_TRANSITION_EXIT)
               .build();
           geofences.add(fence);
       }
   
       GeofencingRequest.Builder builder = new GeofencingRequest.Builder();
       builder.setInitialTrigger(GeofencingRequest.INITIAL_TRIGGER_ENTER);
       builder.addGeofences(geofences);
       builder.build();
       geofencingClient.addGeofences(builder.build(), geoFencePendingIntent)
   }
   ```


Het aanroepen van de `getNearbyPointsOfInterest` API resulteert in een netwerkaanroep die de locatie rondom de huidige locatie ophaalt.

>[!IMPORTANT]
>
>U moet de API spaarzaam of slechts roepen wanneer er significante plaatsverandering van de gebruiker is.

## Geofence-gebeurtenissen posten

### iOS

Roep in iOS de API `processGeofenceEvent` Places in de `CLLocationManager` gedelegeerde. Deze API informeert u of de gebruiker een bepaald gebied is binnengekomen of vertrokken.

```objective-c
- (void) locationManager:(CLLocationManager *)manager didEnterRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
}

- (void) locationManager:(CLLocationManager *)manager didExitRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeExit];
}
```

### Android

Roep in Android de `processGeofence` methode aan samen met de toepasselijke overgangsgebeurtenis in de ontvanger van de Geofence-uitzending. Mogelijk wilt u de lijst met ontvangen geofences beheren om dubbele items/uitgangen te voorkomen.

```java
void onGeofenceReceived(final Intent intent) {
    // do appropriate validation steps for the intent
    ...

    // get GeofencingEvent from intent
    GeofencingEvent geoEvent = GeofencingEvent.fromIntent(intent);

    // get the transition type (entry or exit)
    int transitionType = geoEvent.getGeofenceTransition();

    // validate your geoEvent and get the necessary Geofences from the list
    List<Geofence> myGeofences = geoEvent.getTriggeringGeofences();

    // process region events for your geofences
    for (Geofence geofence : myGeofences) {
        Places.processGeofence(geofence, transitionType);
    }
}
```
