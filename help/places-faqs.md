---
title: Veelgestelde vragen
description: Dit onderwerp verstrekt extra informatie over sommige vaak gestelde vragen.
exl-id: cee9f447-5e50-4ed8-b37b-baecbc0e9b7b
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 1%

---

# Veelgestelde vragen

Hier volgt een aantal informatie en veelgestelde vragen over Plaatsen Service.

## Migreren van trackLocation in de v4 SDK

Als u van v4 SDK migreert en een vervanging aan `trackLocation` API zoekt, te verwijzen gelieve naar de onderwerp [ Dienst van Plaatsen van het Gebruik zonder de Actieve Controle van het Gebied ](use-places-without-active-monitoring.md).

## Grootte en betrouwbaarheid

Let op: alle geofences die worden gebruikt in regio-controle vanaf een mobiele app, ongeacht het gebruik van Adobe of een andere service. De besturingssystemen raden enkele parameters aan om in gedachten te houden wanneer u geofences maakt. Voor maximale betrouwbaarheid moet de stroomsterkte ten minste 100 m bedragen. Het is oké om kleinere geofences te creëren, maar entry en exit gebeurtenissen kunnen niet worden geproduceerd, of kunnen worden geproduceerd nadat de gebruiker ophoudt zich voor een periode beweegt.

Bovendien kunnen de nauwkeurigheid en betrouwbaarheid worden verminderd op basis van hardwarecondities, zoals het uitschakelen of niet beschikbaar zijn van Wi-Fi, en ook op basis van de locatie van het apparaat in verband met het belemmeren van GPS-signalen. Zo kunnen berggebieden, stedelijke omgevingen en binnengebieden de nauwkeurigheid van de locatie van de iOS- en Android-besturingssystemen verminderen.

## Hoe activeert een exit-gebeurtenis?

De geïmplementeerde regionale toezichthouder moet een lijst van nabijgelegen POI&#39;s aanvragen. Na ontvangst moet een regio worden geregistreerd bij het besturingssysteem voor elke POI. Het besturingssysteem is nu verantwoordelijk voor het op de hoogte brengen van de SDK wanneer het apparaat een grens (entry of exit) voor een van de bewaakte gebieden overschrijdt. De SDK activeert alleen een afsluitgebeurtenis wanneer het besturingssysteem de SDK meldt dat de gebeurtenis heeft plaatsgevonden. De belangrijkste reden voor deze kennisgeving is de tijdsgevoeligheid van de locatiegegevens.

Als het besturingssysteem geen afsluitgebeurtenis kan leveren wanneer het apparaat een regio verlaat, is het veiliger voor de SDK om alleen de afsluitgebeurtenis weg te laten. Als de SDK een afsluitgebeurtenis produceert zonder dat de gebeurtenis door het besturingssysteem wordt geactiveerd, bestaat het risico dat de afsluitgebeurtenis ver buiten de periode waarin het apparaat zich bij de POI bevond, wordt verwerkt.

## Aantal POI&#39;s

In de POI van de Dienst van Plaatsen beheersinterface, kunnen de klanten tot 150 duizend punten van belang in een specifieke bibliotheek toevoegen. De klanten kunnen veelvoudige bibliotheken aan segmentgroepen POIs bepalen indien gewenst.

## Sommige notities over locatiewijziging en actieve gebiedscontrole

Het toezicht op een geografisch gebied begint onmiddellijk na de registratie voor geautoriseerde apps. U kunt een gebeurtenis echter niet direct ontvangen, omdat alleen grensovergangen een gebeurtenis genereren. Met name als de locatie van de gebruiker zich op het moment van registratie al binnen het gebied bevindt, genereert de locatiebeheerder niet automatisch een gebeurtenis. In plaats daarvan moet uw app wachten totdat de gebruiker de grens van het gebied overschrijdt voordat een gebeurtenis wordt gegenereerd en naar de gedelegeerde wordt verzonden.

Wees voorzichtig bij het opgeven van de set te controleren regio&#39;s. Regio&#39;s zijn een gedeelde systeembronnen en het totale aantal regio&#39;s dat in het hele systeem beschikbaar is, is beperkt. Om deze reden, beperkt de Plaats van de Kern tot 20 het aantal gebieden die gelijktijdig door één enkele app kunnen worden gecontroleerd. Als u deze limiet wilt overschrijden, kunt u alleen die gebieden in de directe omgeving van de gebruiker registreren.

[ zie extra informatie over de de ontwikkelaarplaats van Apple ] (https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/LocationAwarenessPG/RegionMonitoring/RegionMonitoring.html#//apple_ref/doc/uid/TP40009497-CH9-SW11)
