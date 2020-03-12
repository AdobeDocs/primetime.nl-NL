---
seo-title: Aan de slag
title: Aan de slag
uuid: 2002cf94-c8a7-4820-a560-6d9f7f33ee97
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# Aan de slag {#getting-started}

Dit document bevat de stappen voor een snelle installatie en implementatie van een Adobe Primetime DRM-ecosysteem dat progressief downloaden gebruikt om inhoud te distribueren, en de Primetime DRM-server voor beveiligde streaming voor licentiedistributie. De volgende hulplijnen bevatten aanvullende informatie over elke stap:

* *De Primetime DRM-server gebruiken voor het beschermen van inhoud*
* *De Primetime DRM-server gebruiken voor beveiligde streaming*

De Primetime DRM-server voor beveiligde streaming is een server met minimale functionaliteit die geen broncode bevat. Voor een wijzigbare server met volledige bron van Java, zie het *Gebruiken van de gids van de Implementaties* van de Verwijzing van Primetime DRM. Als u een Referentie-licentieserver instelt, die de stap *Setup vervangt en Primetime DRM Server voor Protected Streaming (Licentieserver)* implementeert.

## Vereisten {#prerequisites}

Voer de volgende taken uit voordat u aan de slag gaat:

* Twee Windows- of Linux-computers ophalen:

   * Eén computer wordt de licentieserver.
   * Eén computer wordt de Content Server.

* Installeer de volgende toepassingen op beide computers:

   * Tomcat 6.0.18
   * Java 1.6

## Certificaten verkrijgen {#obtain-certificates}

Nadat de SDK-software is geleverd, ontvangt de aangewezen systeembeheerder van het bedrijfscertificaat een uitnodiging om het registratieproces voor het Adobe Primetime DRM-certificaat te voltooien. Zie de *Inschrijvingsgids* voor primetime DRM-certificaten voor meer informatie.

1. De beheerder wijst minstens één persoon aan om als aanvrager van het Certificaat te handelen.
1. De aanvrager van het Certificaat produceert een privé sleutel en een CSR.
1. De aanvrager dient een certificaataanvraag in.
1. De beheerder van het Bedrijf keurt het verzoek goed.
1. De Adobe-certificaatbeheerder bevestigt de verzending.
1. Requester ontvangt het certificaat, bindt het certificaat met de privé sleutel, en stelt het certificaat op. zoals beschreven in .

   Zie de handleiding Adobe Primetime DRM Server *implementeren voor beveiligde streaming* voor meer informatie over het implementeren van het certificaat.
1. De stappen 3 tot en met 6 moeten voor elk certificaattype worden ingevuld.

   Voor de versie van de Productie Primetime DRM, moet de aanvrager afzonderlijke verzoeken om de Server van de Vergunning, het Verpakken, en de certificaten van het Vervoer indienen, die voor twee jaar geldig zijn.

   Klanten die de Primetime DRM-evaluatieversie of proefversie gebruiken, hebben slechts één certificaat nodig dat respectievelijk 1 jaar / 90 dagen geldig is.