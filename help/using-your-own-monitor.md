---
title: Uw eigen monitor gebruiken
description: U kunt ook uw controleservices gebruiken en integreren met de Places Service met behulp van de API's voor de uitbreiding Plaatsen Service.
exl-id: 8ca4d19b-0f23-4291-b335-af47f03179fa
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
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

1. Geef de locatie-updates die zijn verkregen van de Core location services van de iOS door aan de Places extension.

1. Gebruik de API voor het plaatsen van extensies van `getNearbyPointsOfInterest` om de array van `ACPPlacesPoi` -objecten rond de huidige locatie op te halen.

   ```objective-c
   - (void) locationManager: (CLLocationManager*) manager didUpdateLocations: (NSArray<CLLocation*>*) locations {
       [ACPPlaces getNearbyPointsOfInterest:currentLocation limit:10 callback: ^ (NSArray<ACPPlacesPoi*>* _Nullable nearbyPoi) {
           [self startMonitoringGeoFences:nearbyPoi];
       }];
   }
   ```

1. Haal de informatie uit de verkregen `ACPPlacesPOI` -objecten en begin met het controleren van deze API&#39;s.

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

1. Met de API voor plaatsing van `getNearbyPointsOfInterest` plaatst u de lijst met `PlacesPoi` -objecten op de huidige locatie.

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

1. Extraheer de gegevens uit de verkregen `PlacesPOI` -objecten en begin met het controleren van deze API&#39;s.

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


Het aanroepen van de API `getNearbyPointsOfInterest` leidt tot een netwerkaanroep die de locatie rondom de huidige locatie ophaalt.

>[!IMPORTANT]
>
>U moet de API spaarzaam of slechts roepen wanneer er significante plaatsverandering van de gebruiker is.

## Geofence-gebeurtenissen posten

### iOS

Roep in iOS de `processGeofenceEvent` Places API in de gedelegeerde `CLLocationManager` aan. Deze API informeert u of de gebruiker een bepaald gebied is binnengekomen of vertrokken.

```objective-c
- (void) locationManager:(CLLocationManager *)manager didEnterRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeEntry];
}

- (void) locationManager:(CLLocationManager *)manager didExitRegion:(CLRegion *)region {
    [ACPPlaces processRegionEvent:region forRegionEventType:ACPRegionEventTypeExit];
}
```

### Android

Roep in Android de methode `processGeofence` aan samen met de juiste overgangsgebeurtenis in de ontvanger van de Geofence-uitzending. Mogelijk wilt u de lijst met ontvangen geofences samenstellen om dubbele items/uitgangen te voorkomen.

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
