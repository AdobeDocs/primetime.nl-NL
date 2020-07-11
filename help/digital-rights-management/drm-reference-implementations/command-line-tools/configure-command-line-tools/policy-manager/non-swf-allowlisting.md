---
seo-title: Niet-SWF-toepassing staat lijst toe
title: Niet-SWF-toepassing staat lijst toe
uuid: d4f93b15-e556-4749-95ab-f7f58b1061d7
translation-type: tm+mt
source-git-commit: 58bb3bedc5b0ac63afd96eb6101d9ad779e6deed
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---


# Niet-SWF-toepassing staat lijst toe {#non-swf-application-isting}

AIR was het eerste platform waarop toepassingen kunnen worden vermeld en de naam van de eigenschap die u gebruikt voor het lijsten van gewenste personen van niet-SWF-toepassingen (Adobe AIR, iOS, Android, enz.) behoudt de oorspronkelijke naam: `policy.allowedAIRApplication.n`. Hierdoor kan de inhoud worden afgespeeld door alle niet-Flash-toepassingen die vóór publicatie zijn ondertekend met een ondertekeningscertificaat. Dit wordt de *toepassings-id* genoemd. U kunt de toepassings-id extraheren met het [!DNL AdobePublisherIDUtility.jar] gereedschap. Op deze manier kan de aanbieding worden afgedwongen op elke client die Primetime DRM ondersteunt.

De toepassings-id wordt afgeleid van de openbare sleutel van het ondertekenende certificaat waarmee een bepaalde toepassing wordt ondertekend. Als de openbare sleutel in het certificaat ooit vervalt, kan alle vorige inhoud alleen worden afgespeeld op apps die met het oude certificaat zijn ondertekend, niet worden afgespeeld op de nieuwe app (die met het nieuwe certificaat is ondertekend).

Als u in een situatie verkeert waarin een inhoudsbibliotheek is toegestaan die wordt vermeld aan toepassingen die zijn ondertekend met een bepaald ondertekeningscertificaat, en dat certificaat verloopt en u een nieuw certificaat krijgt (met een ander openbaar/privé-sleutelpaar), wordt uw oude inhoud niet afgespeeld op uw nieuwe app *tenzij* u een van de volgende handelingen uitvoert:

* Gebruik een `PolicyUpdateList` licentie op uw licentieserver om het inkomende beleid te overschrijven en voeg een nieuwe Application Lijst van gewenste personen-vermelding in met de samenvatting van uw nieuwe ondertekeningscertificaat.
* Werk de logica van de licentieserver bij om het inkomende beleid te overschrijven en voeg een nieuwe ingang van de Lijst van gewenste personen van de Toepassing in.
* Vraag of uw ondertekenende certificaatuitgever u een nieuw certificaat uitgeeft dat hetzelfde openbare/persoonlijke sleutelpaar gebruikt als het vorige certificaat.
* Als u inhoud HDS/HLS levert die van verwijzingen voorzien een eindpunt URL om terug te winnen `DRMMetadata`, kunt u regenereren `DRMMetadata` (gebruikend Primetime DRM Java SDK) om een nieuw Beleid in te voegen DRM dat een bijgewerkte ingang van de Lijst van gewenste personen van de Toepassing bevat.

* Verpak al uw oude inhoud opnieuw met een nieuw DRM-beleid met de samenvatting van uw nieuwe ondertekenende certificaat.

Zie `policy.allowedAIRApplication.n` in de eigenschappen *van de* Configuratie voor details.

>[!NOTE]
>
>Voor het aanbieden van een iOS-toepassing is een speciale aanpak vereist. Raadpleeg de [Lijst van gewenste personen van uw iOS-toepassing](../../../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-allowlist-your-ios-application.md) in de *TVSDK for iOS Programmer&#39;s Guide*.
