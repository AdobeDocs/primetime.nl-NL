---
title: Niet-SWF toepassing toestaan
description: Niet-SWF toepassing toestaan
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# Niet-SWF toepassing toestaan {#non-swf-application-isting}

AIR was het eerste platform waarop speciale toepassingen kunnen worden aangeboden en de naam van de eigenschap die u gebruikt voor het lijsten van gewenste personen van niet-SWF toepassingen (Adobe AIR, iOS, Android, enz.) behoudt de oorspronkelijke naam: `policy.allowedAIRApplication.n`. Hierdoor kan de inhoud worden afgespeeld door alle niet-Flash toepassingen die vóór publicatie zijn ondertekend met een ondertekeningscertificaat. Dit wordt bedoeld als *Toepassings-id*. U kunt de toepassings-id extraheren met de [!DNL AdobePublisherIDUtility.jar] gebruiken. Op deze manier kan de aanbieding worden afgedwongen op elke client die Primetime DRM ondersteunt.

De toepassings-id wordt afgeleid van de openbare sleutel van het ondertekenende certificaat waarmee een bepaalde toepassing wordt ondertekend. Als de openbare sleutel in het certificaat ooit vervalt, kan alle vorige inhoud alleen worden afgespeeld op apps die met het oude certificaat zijn ondertekend, niet worden afgespeeld op de nieuwe app (die met het nieuwe certificaat is ondertekend).

Als u in een situatie verkeert waarin een inhoudsbibliotheek is toegestaan die is opgenomen in toepassingen die zijn ondertekend met een bepaald ondertekeningscertificaat, en dat certificaat verloopt en u een nieuw certificaat krijgt (met een ander openbaar/privé-sleutelpaar), wordt uw oude inhoud niet afgespeeld op uw nieuwe app *tenzij* Voer een van de volgende handelingen uit:

* Een `PolicyUpdateList` op uw licentieserver om het inkomende beleid te overschrijven en een nieuw item voor de Lijst van gewenste personen Application in te voegen met de digest van uw nieuwe ondertekenende certificaat.
* Werk de logica van de licentieserver bij om het inkomende beleid te overschrijven en voeg een nieuwe ingang van de Lijst van gewenste personen van de Toepassing in.
* Vraag of uw ondertekenende certificaatuitgever u een nieuw certificaat uitgeeft dat hetzelfde openbare/persoonlijke sleutelpaar gebruikt als het vorige certificaat.
* Als u inhoud HDS/HLS levert die van verwijzingen voorzien een eindpunt URL om terug te winnen `DRMMetadata`kunt u de `DRMMetadata` (het gebruiken van Primetime DRM Java SDK) om een nieuw Beleid in te voegen DRM dat een bijgewerkte ingang van de Lijst van gewenste personen van de Toepassing bevat.

* Verpak al uw oude inhoud opnieuw met een nieuw DRM-beleid met de samenvatting van uw nieuwe ondertekenende certificaat.

Zie `policy.allowedAIRApplication.n` in *Configuratieeigenschappen* voor meer informatie.

>[!NOTE]
>
>Als je een iOS-toepassing wilt aanbieden, moet je een speciale aanpak volgen. Zie [iOS-toepassing lijsten van gewenste personen](../../../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-allowlist-your-ios-application.md) in de *TVSDK voor iOS-programmeergids*.
