---
seo-title: Niet-SWF-toepassing staat lijst toe
title: Niet-SWF-toepassing staat lijst toe
uuid: d4f93b15-e556-4749-95ab-f7f58b1061d7
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---


# Niet-SWF-toepassing staat lijst toe {#non-swf-application-allowlisting}

AIR was het eerste platform waarop een toepassing met functies kan worden weergegeven, en de naam van de eigenschap die u gebruikt om niet-SWF-toepassingen in de lijst toe te staan (Adobe AIR, iOS, Android, enz.) behoudt de oorspronkelijke naam: `policy.allowedAIRApplication.n`. Hierdoor kan de inhoud worden afgespeeld door alle niet-Flash-toepassingen die vóór publicatie zijn ondertekend met een ondertekeningscertificaat. Dit wordt de *toepassings-id* genoemd. U kunt de toepassings-id extraheren met het [!DNL AdobePublisherIDUtility.jar] gereedschap. Op deze manier kan de aanbieding worden afgedwongen op elke client die Primetime DRM ondersteunt.

De toepassings-id wordt afgeleid van de openbare sleutel van het ondertekenende certificaat waarmee een bepaalde toepassing wordt ondertekend. Als de openbare sleutel in het certificaat ooit vervalt, kan alle vorige inhoud alleen worden afgespeeld op apps die met het oude certificaat zijn ondertekend, niet worden afgespeeld op de nieuwe app (die met het nieuwe certificaat is ondertekend).

Als u in een situatie verkeert waarin een inhoudsbibliotheek is toegestaan die wordt vermeld aan toepassingen die zijn ondertekend met een bepaald ondertekeningscertificaat, en dat certificaat verloopt en u een nieuw certificaat krijgt (met een ander openbaar/privé-sleutelpaar), wordt uw oude inhoud niet afgespeeld op uw nieuwe app *tenzij* u een van de volgende handelingen uitvoert:

* Gebruik een `PolicyUpdateList` licentie op uw licentieserver om het inkomende beleid te overschrijven en voeg een nieuwe Application Allow list entry in met de digest van uw nieuwe ondertekenende certificaat.
* Werk de logica van uw licentieserver bij om het inkomende beleid te overschrijven en voeg een nieuwe Application toe toe lijstingang.
* Vraag of uw ondertekenende certificaatuitgever u een nieuw certificaat uitgeeft dat hetzelfde openbare/persoonlijke sleutelpaar gebruikt als het vorige certificaat.
* Als u inhoud HDS/HLS levert die van verwijzingen voorzien een URL eindpunt om terug te winnen `DRMMetadata`, kunt u regenerate `DRMMetadata` (gebruiken Primetime DRM Java SDK) om een nieuw beleid in te voegen DRM dat een bijgewerkte Toepassing bevat staat lijstingang toe.

* Verpak al uw oude inhoud opnieuw met een nieuw DRM-beleid met de samenvatting van uw nieuwe ondertekenende certificaat.

Zie `policy.allowedAIRApplication.n` in de eigenschappen *van de* Configuratie voor details.

>[!NOTE]
>
>Voor het aanbieden van een iOS-toepassing is een speciale aanpak vereist. Zie De lijst met uw iOS-toepassingen [](../../../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-allowlist-your-ios-application.md) toestaan in de *TVSDK voor de programmagids* van iOS.
