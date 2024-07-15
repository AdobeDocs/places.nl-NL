---
title: Metagegevens gebruiken met POI's
description: Deze sectie verstrekt informatie en strategieën over hoe te om meta-gegevens met POIs te gebruiken.
exl-id: e669e560-a999-43ff-aeb4-06e6308b0d5c
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# Strategieën voor het gebruik van metagegevens met POI&#39;s {#using-metadata-pois}

Wanneer u een nieuwe POI maakt in de Places Service, zijn de enige vereiste elementen Naam, Straal, Breedte en Lengte. Voor meer informatie over het creëren van POI, zie [ een POI ](/help/poi-mgmt-ui/create-a-poi-ui.md) creëren. Als u echter alleen de minimuminformatie invoert, kunt u geen extra waarde toevoegen.

POI-metagegevens kunnen op verschillende manieren worden gebruikt. Vanuit een POI-beheerstandpunt kan het toevoegen van metagegevenswaarden helpen bij het zoeken naar of het filteren van een lijst met potentieel duizenden POI&#39;s. Het creëren van meta-gegevens voor zeer belangrijke attributen met betrekking tot POI kan waarde in stroomafwaartse werkschema&#39;s opleveren. Bijvoorbeeld, kan een hotelketen die POIs voor elk bezit creeert meta-gegevens zoals willen omvatten als het hotelbezit een pool of niet heeft, of een restaurant en bar, of als zij een gym faciliteit hebben. Deze metagegevens kunnen als contextgegevens worden opgenomen in analyses en kunnen ook worden gebruikt voor gerichte aanbiedingen of berichten.

## Plaatst de meta-gegevens van de Dienst in Lancering

In Experience Platform Launch, kunt u gegevenselementen voor elk de meta-gegevensgebied tot stand brengen van de Dienst van Plaatsen dat voor het volgen of overseinendoeleinden belangrijk is.

![ gegevenselement voor de gymfaciliteit ](/help/assets/gymfacility.png)

Vervolgens kunt u een handeling maken met de extensie Analytics voor het maken van een nieuwe hit die de metagegevens bevat die u als contextgegevens wilt gebruiken.

![ actie voor de gymfaciliteit ](/help/assets/Analytics-gym.png)

## In-app-berichten in Adobe Campaign

Metagegevens kunnen worden gebruikt als filter voor lokale meldingen en in-app-berichten die in Adobe Campaign Standard zijn gedefinieerd. Het gebruik van metagegevens als filter biedt u de mogelijkheid om een relevanter bericht te maken dat in een context staat voor de werkelijke locatie.

![ het filtreren lokale berichten en in-app berichten in ACS ](/help/assets/ACS_gym_metadata.png)
