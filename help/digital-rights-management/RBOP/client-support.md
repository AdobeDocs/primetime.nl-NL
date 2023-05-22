---
description: In deze sectie worden de functies beschreven die beschikbaar zijn in verschillende versies van Flash Player en TVSDK.
title: RBOP-clientondersteuning
exl-id: 1120587e-45cf-45cc-8b41-1886ab2ed2a4
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# RBOP-clientondersteuning {#rbop-client-support}

In deze sectie worden de functies beschreven die beschikbaar zijn in verschillende versies van Flash Player en TVSDK.

**Fout bij verzenden** - De TVSDK-platforms die hieronder worden vermeld, verzenden een DRM-runtime-fout wanneer de resolutie van de inhoud die wordt afgespeeld de resolutie overschrijdt die is toegestaan voor de apparaatconfiguratie die is gedefinieerd in het DRM-beleid:

* Flash Player versies 18 tot en met 20
* Android, versies
* iOS - Versies

>[!NOTE]
>
>* Alle Flash- en mobiele platformen ondersteunen Error Dispatch, maar alleen de TVSDK-clients die hierboven zijn vermeld, verwerken RBOP-gerelateerde fouten.
>* RBOP-gerelateerd [DRM-clientfouten](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages):
   >    * **3371** - Onjuiste resolutie op basis van productiebeperkingen in de licentie.
   >    * **3372** - De resolutie van de inhoud is groter dan de maximale resolutie die is opgegeven in de beperking voor uitvoerbeveiliging. (Dit kan voorkomen als iemand probeert inhoud te injecteren die voor een ander apparaat is bedoeld.)
   >    * **3373** - De resolutie van de inhoud is groter dan de resolutie die wordt opgegeven door de momenteel actieve beperking voor uitvoerbeveiliging. (Dit betekent dat we moeten afnemen.)
>


**Automatisch downschalen** - De techniek voor downscale varieert per platform en Flash Player-versie:

* Flash Player versie 21: Ondersteunt RBOP met Automatisch downscalen (intelligente bitsnelheidsomschakeling)
* Firefox-versie 38 en hoger in Windows (met Access CDM): Adobe downloadt automatisch een hogere bitsnelheidsstream naar een lagere stream (in tegenstelling tot het downloaden van een stream van een lagere kwaliteit).

>[!NOTE]
>
>Deze platforms onderschalen video automatisch en tonen de inhoud bij een resolutie die lager is dan of gelijk aan wat door het beleid DRM wordt gespecificeerd. Met deze functie wordt inhoud altijd afgespeeld op de client, zolang er een beschikbare stream beschikbaar is die voldoet aan de DRM-beleidsbeperkingen.

**Oudere uitvoerbeveiliging** - Clients die Flash Player vóór versie 18 gebruiken, kunnen alleen bestaande OP-beperkingen verwerken. Clients met Flash Player versie 18 en hoger kunnen verouderde of RBOP-beperkingen afhandelen. Als u RBOP-beperkingen instelt, moet u ook oudere OP-beperkingen voor oudere clients instellen. Voor cliënten die RBOP steunen, de beperkingen van RBOP trekken erfenis OP beperkingen.
