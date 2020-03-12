---
seo-title: Whitelisting niet-SWF-toepassing
title: Whitelisting niet-SWF-toepassing
uuid: d4f93b15-e556-4749-95ab-f7f58b1061d7
translation-type: tm+mt
source-git-commit: a63768e51c911914a6ba9d884e2587fa34939f9d

---


# Whitelisting niet-SWF-toepassing {#non-swf-application-whitelisting}

AIR was het eerste platform met een whitelisting van toepassingen en de naam van de eigenschap die u gebruikt voor whitelist-toepassingen die geen SWF-bestanden zijn (Adobe AIR, iOS, Android, enz.) behoudt de oorspronkelijke naam: `policy.allowedAIRApplication.n`. Hierdoor kan de inhoud worden afgespeeld door alle niet-Flash-toepassingen die vóór publicatie zijn ondertekend met een ondertekeningscertificaat. Dit wordt de *toepassings-id* genoemd. U kunt de toepassings-id extraheren met het [!DNL AdobePublisherIDUtility.jar] gereedschap. Deze whitelisting wordt afgedwongen op elke client die Primetime DRM ondersteunt.

De toepassings-id wordt afgeleid van de openbare sleutel van het ondertekenende certificaat waarmee een bepaalde toepassing wordt ondertekend. Als de openbare sleutel in het certificaat ooit vervalt, wordt alle vorige inhoud die alleen is gewhitelisteerd voor toepassingen die zijn ondertekend met het oude certificaat, niet afgespeeld op de nieuwe app (die is ondertekend met het nieuwe certificaat).

Als u in de situatie verkeert waarin een bibliotheek met inhoud is gewhitelisteerd voor toepassingen die zijn ondertekend met een bepaald ondertekeningscertificaat, en dat certificaat verloopt en u een nieuw certificaat krijgt (met een ander openbaar/privé sleutelpaar), wordt uw oude inhoud niet afgespeeld op uw nieuwe app *tenzij* u een van de volgende handelingen uitvoert:

* Gebruik een `PolicyUpdateList` bestand op uw licentieserver om het inkomende beleid te overschrijven en voeg een nieuw item van het type Application Whitelist in met de samenvatting van uw nieuwe ondertekenende certificaat.
* Werk de logica van de licentieserver bij om het inkomende beleid te overschrijven en voeg een nieuwe ingang van het whitelist van de Toepassing in.
* Vraag of uw ondertekenende certificaatuitgever u een nieuw certificaat uitgeeft dat hetzelfde openbare/persoonlijke sleutelpaar gebruikt als het vorige certificaat.
* Als u inhoud HDS/HLS levert die van verwijzingen voorzien een eindpunt URL om terug te winnen `DRMMetadata`, kunt u regenereren `DRMMetadata` (gebruikend Primetime DRM Java SDK) om een nieuw Beleid in te voegen DRM dat een bijgewerkte ingang van het Whitelist van de Toepassing bevat.

* Verpak al uw oude inhoud opnieuw met een nieuw DRM-beleid met de samenvatting van uw nieuwe ondertekenende certificaat.

Zie `policy.allowedAIRApplication.n` in de eigenschappen *van de* Configuratie voor details.

>[!NOTE]
>
>Voor een whitelisting van een iOS-toepassing is een speciale aanpak vereist. Raadpleeg [Whitelist your iOS application](../../../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-whitelist-your-ios-application.md) in the *TVSDK for iOS Programmer&#39;s Guide*.