---
description: Soms kan de inhoud niet worden afgespeeld. Dit kan door elk aantal situaties worden veroorzaakt, zoals fouten in de netwerkstack van de browser, de transportlaag, het besturingssysteem, de Flash Player-runtime of het Primetime DRM-systeem.
seo-description: Soms kan de inhoud niet worden afgespeeld. Dit kan door elk aantal situaties worden veroorzaakt, zoals fouten in de netwerkstack van de browser, de transportlaag, het besturingssysteem, de Flash Player-runtime of het Primetime DRM-systeem.
seo-title: Overzicht van Trigfouten
title: Overzicht van Trigfouten
uuid: 44b4ab0e-5f08-44b0-bcb5-a869f6add69b
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---


# Fouten bij bijsnijden {#triaging-errors}

Soms kan de inhoud niet worden afgespeeld. Dit kan door elk aantal situaties worden veroorzaakt, zoals fouten in de netwerkstack van de browser, de transportlaag, het besturingssysteem, de Flash Player-runtime of het Primetime DRM-systeem.

De eerste kenmerkende stap is te bepalen als het probleem zich zonder encryptie DRM manifesteert die in de vergelijking wordt geïntroduceerd. Poging om de inhoud te verpakken, maar geef de pakketsoftware de opdracht om de inhoud niet te coderen. Als het probleem nog bestaat, is het waarschijnlijk een kwestie die de inhoud coderen of verpakken, of ergens in de netwerkinfrastructuur. Als het probleem verdwijnt wanneer de inhoud zonder codering in een pakket wordt geplaatst, is het afspelen mogelijk te wijten aan een DRM-probleem en dient u de client/server te triggeren.

Primetime DRM (buiten Primetime Cloud DRM) is al jaren op de markt. Als dusdanig, is er een rijkdom aan gemeenschap-gebaseerde informatie over het oplossen van problemen en het vormen Primetime DRM. Adobe heeft een forum verschaft voor Primetime DRM-gebruikers (voorheen Adobe Access genoemd) om problemen en resoluties samen te voegen en te delen. Controleer of je probleem eerder is besproken: [https://forums.adobe.com/community/adobe_access](https://forums.adobe.com/community/adobe_access)

## Trigger voor clientfouten {#section_D0EBAEB0C27F4B01BD44124DEE62F6BA}

Als de inhoud niet wordt afgespeeld, raadpleegt u het rechterdeelvenster van de Sample Video Players, waarin `DRMErrorEvent` wordt geregistreerd die zich voordoet. Als er een foutgebeurtenis is, heeft deze betrekking op een van de Flash Player Runtime-fouten:

* [Naslaggids voor DRM-foutberichten](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages) voor clients of
* [AS3 Flash-runtimefouten](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/runtimeErrors.html)  (DRM-problemen beginnen bij 3300)

