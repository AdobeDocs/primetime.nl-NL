---
description: Soms kan de inhoud niet worden afgespeeld. Om het even welk aantal situaties kan dit, met inbegrip van fouten in de browser netwerkstapel, vervoerlaag, Werkend Systeem, runtime van de Flash Player, of systeem Primetime DRM veroorzaken.
title: Overzicht van Trigfouten
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Trigfouten {#triaging-errors}

Soms kan de inhoud niet worden afgespeeld. Om het even welk aantal situaties kan dit, met inbegrip van fouten in de browser netwerkstapel, vervoerlaag, Werkend Systeem, runtime van de Flash Player, of systeem Primetime DRM veroorzaken.

De eerste kenmerkende stap is te bepalen als het probleem zich zonder encryptie DRM manifesteert die in de vergelijking wordt geïntroduceerd. Poging om de inhoud te verpakken, maar geef de pakketsoftware de opdracht om de inhoud niet te coderen. Als het probleem nog bestaat, is het waarschijnlijk een kwestie die de inhoud coderen of verpakken, of ergens in de netwerkinfrastructuur. Als het probleem verdwijnt wanneer de inhoud zonder codering in een pakket wordt geplaatst, is het afspelen mogelijk te wijten aan een DRM-probleem en dient u de client/server te triggeren.

Primetime DRM (buiten Primetime Cloud DRM) is al jaren op de markt. Als dusdanig, is er een rijkdom aan gemeenschap-gebaseerde informatie over het oplossen van problemen en het vormen Primetime DRM. Adobe biedt een forum voor Primetime DRM-gebruikers (voorheen Adobe Access genoemd) om problemen en resoluties samen te voegen en te delen. Controleer of je probleem eerder is besproken: [https://forums.adobe.com/community/adobe_access](https://forums.adobe.com/community/adobe_access)

## Testen van clientfouten {#section_D0EBAEB0C27F4B01BD44124DEE62F6BA}

Als de inhoud niet wordt afgespeeld, raadpleegt u het rechterdeelvenster van de Sample Video Players, waarin eventuele `DRMErrorEvent` dat gebeurt. Als er een foutgebeurtenis is, heeft deze betrekking op een van de fouten bij uitvoering van de Flash Player:

* [Verwijzing naar DRM-foutbericht voor client](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages); of
* [AS3-runtimefouten Flash](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/runtimeErrors.html) (DRM-problemen beginnen op 3300)
