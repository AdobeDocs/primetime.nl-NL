---
title: Niet-SWF-toepassing staat lijst toe
description: Niet-SWF-toepassing staat lijst toe
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---


# Overzicht niet-SWF-toepassing toestaan {#non-swf-application-isting}

AIR was het eerste platform waarop toepassingen kunnen worden vermeld en de naam van de eigenschap die u gebruikt voor het lijsten van gewenste personen van niet-SWF-toepassingen (Adobe AIR, iOS, Android, enz.) behoudt de oorspronkelijke naam: `policy.allowedAIRApplication.n`. Hierdoor kan de inhoud worden afgespeeld door alle niet-Flash toepassingen die vóór publicatie zijn ondertekend met een ondertekeningscertificaat. Dit wordt bedoeld als *toepassings identiteitskaart*. U kunt de toepassings-id extraheren met het gereedschap [!DNL AdobePublisherIDUtility.jar]. Op deze manier kan de aanbieding worden afgedwongen op elke client die Primetime DRM ondersteunt.

De toepassings-id wordt afgeleid van de openbare sleutel van het ondertekenende certificaat waarmee een bepaalde toepassing wordt ondertekend. Als de openbare sleutel in het certificaat ooit vervalt, kan alle vorige inhoud alleen worden afgespeeld op apps die met het oude certificaat zijn ondertekend, niet worden afgespeeld op de nieuwe app (die met het nieuwe certificaat is ondertekend).

Als u in een situatie verkeert waarin een inhoudsbibliotheek is toegestaan die is opgenomen in toepassingen die zijn ondertekend met een bepaald ondertekeningscertificaat, en dat certificaat verloopt en u een nieuw certificaat krijgt (met een ander openbaar/privé-sleutelpaar), wordt uw oude inhoud niet afgespeeld op uw nieuwe app *tenzij* een van de volgende handelingen uitvoert:

* Gebruik een `PolicyUpdateList` op uw licentieserver om het inkomende beleid te overschrijven en voeg een nieuwe ingang van de Lijst van gewenste personen van de Toepassing met uw nieuwe het ondertekenen van certificaatsamenvatting in.
* Werk de logica van de licentieserver bij om het inkomende beleid te overschrijven en voeg een nieuwe ingang van de Lijst van gewenste personen van de Toepassing in.
* Vraag of uw ondertekenende certificaatuitgever u een nieuw certificaat uitgeeft dat hetzelfde openbare/persoonlijke sleutelpaar gebruikt als het vorige certificaat.
* Als u inhoud HDS/HLS levert die van een URL-eindpunt van verwijzingen voorziet om `DRMMetadata` terug te winnen, kunt u `DRMMetadata` (gebruikend Primetime DRM Java SDK) regenereren om een nieuw beleid in te voegen DRM dat een bijgewerkte ingang van de Lijst van gewenste personen van de Toepassing bevat.

* Verpak al uw oude inhoud opnieuw met een nieuw DRM-beleid met de samenvatting van uw nieuwe ondertekenende certificaat.

Zie `policy.allowedAIRApplication.n` in *Configuration properties* voor meer informatie.

>[!NOTE]
>
>Voor het aanbieden van een iOS-toepassing is een speciale aanpak vereist. Zie [Lijst van gewenste personen uw iOS-toepassing](../../../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-allowlist-your-ios-application.md) in de *TVSDK voor de gids van de iOS-programmeur*.
