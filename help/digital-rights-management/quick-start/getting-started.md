---
title: Aan de slag
description: Aan de slag
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---


# Aan de slag {#getting-started}

Dit document bevat de stappen voor een snelle installatie en implementatie van een Adobe Primetime DRM-ecosysteem dat gebruikmaakt van Progressief downloaden om inhoud te distribueren, en de Primetime DRM-server voor Protected Streaming voor licentiedistributie. De volgende hulplijnen bevatten aanvullende informatie over elke stap:

* *De Primetime DRM-server gebruiken voor het beschermen van inhoud*
* *De Primetime DRM-server gebruiken voor beveiligde streaming*

De Primetime DRM-server voor beveiligde streaming is een server met minimale functionaliteit die geen broncode bevat. Zie de handleiding *Using the Primetime DRM Reference Implementations* voor een wijzigbare server met volledige Java-bron. Als u een Referentie-licentieserver instelt, die de stap *Primetime DRM-server instellen en implementeren voor beveiligde streaming (licentieserver)* vervangt.

## Vereisten {#prerequisites}

Voer de volgende taken uit voordat u aan de slag gaat:

* Twee Windows- of Linux-computers ophalen:

   * Eén computer wordt de licentieserver.
   * Eén computer wordt de Content Server.

* Installeer de volgende toepassingen op beide computers:

   * Tomcat 6.0.18
   * Java 1.6

## Certificaten verkrijgen {#obtain-certificates}

Nadat de SDK-software is geleverd, ontvangt de aangewezen systeembeheerder van het bedrijfscertificaat een uitnodiging om het registratieproces van Adobe Primetime DRM Certificate Enrollment te voltooien. Voor meer informatie, zie *Primetime Gids van de Inschrijving van het Certificaat DRM*.

1. De beheerder wijst minstens één persoon aan om als aanvrager van het Certificaat te handelen.
1. De aanvrager van het Certificaat produceert een privé sleutel en een CSR.
1. De aanvrager dient een certificaataanvraag in.
1. De beheerder van het Bedrijf keurt het verzoek goed.
1. De beheerder van het Adobe-certificaat bevestigt de verzending.
1. Requester ontvangt het certificaat, bindt het certificaat met de privé sleutel, en stelt het certificaat op. zoals beschreven in .

   Zie de handleiding *Adobe Primetime DRM Server implementeren voor beveiligde streaming* voor meer informatie over het implementeren van het certificaat.
1. De stappen 3 tot en met 6 moeten voor elk certificaattype worden ingevuld.

   Voor de versie van de Productie Primetime DRM, moet de aanvrager afzonderlijke verzoeken om de Server van de Vergunning, het Verpakken, en de certificaten van het Vervoer indienen, die voor twee jaar geldig zijn.

   Klanten die de Primetime DRM-evaluatieversie of proefversie gebruiken, hebben slechts één certificaat nodig dat respectievelijk 1 jaar / 90 dagen geldig is.