---
description: In deze sectie worden de functies beschreven die beschikbaar zijn in verschillende versies van Flash Player en TVSDK.
seo-description: In deze sectie worden de functies beschreven die beschikbaar zijn in verschillende versies van Flash Player en TVSDK.
seo-title: RBOP-clientondersteuning
title: RBOP-clientondersteuning
uuid: d1d0f788-7bc1-488c-807e-be47f83725e9
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# RBOP-clientondersteuning {#rbop-client-support}

In deze sectie worden de functies beschreven die beschikbaar zijn in verschillende versies van Flash Player en TVSDK.

**Foutverzending** - De TVSDK-platforms die hieronder worden vermeld, verzenden een DRM-runtime-fout wanneer de resolutie van de afgespeelde inhoud groter is dan de resolutie die is toegestaan voor de apparaatconfiguratie die is gedefinieerd in het DRM-beleid:

* Flash Player-versies 18 tot en met 20
* Android, versies
* iOS - Versies

>[!NOTE]
>
>* Alle Flash- en mobiele platforms ondersteunen Error Dispatch, maar alleen de TVSDK-clients die hierboven worden vermeld, verwerken RBOP-gerelateerde fouten.
>* RBOP-gerelateerde [DRM-clientfouten](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages): >
   >    * **3371** - Onjuiste resolutie op basis van productiebeschermingsbeperkingen in de licentie.
   >    * **3372** - De resolutie van de inhoud is groter dan de maximale resolutie die is opgegeven in de beperking voor uitvoerbeveiliging. (Dit kan voorkomen als iemand probeert inhoud te injecteren die voor een ander apparaat is bedoeld.)
   >    * **3373** - De resolutie van de inhoud is groter dan de resolutie die wordt opgegeven door de momenteel actieve uitvoerbeveiligingsbeperking. (Dit betekent dat we moeten afnemen.)
>



**Automatisch downschalen** - De techniek voor het verkleinen varieert per platform en Flash Player-versie:

* Flash Player versie 21: Ondersteunt RBOP met Automatisch downscalen (intelligente bitsnelheidsomschakeling)
* Firefox-versie 38 en hoger in Windows (met Access CDM): Adobe downloadt automatisch een hogere bitsnelheidsstream naar een lagere stream (in tegenstelling tot het downloaden van een lagere stream).

>[!NOTE]
>
>Deze platforms onderschalen video automatisch en tonen de inhoud bij een resolutie die lager is dan of gelijk aan wat door het beleid DRM wordt gespecificeerd. Met deze functie wordt inhoud altijd afgespeeld op de client, zolang er een beschikbare stream beschikbaar is die voldoet aan de DRM-beleidsbeperkingen.

**Oudere uitvoerbeveiliging** - Clients die Flash Players gebruiken vóór versie 18 kunnen alleen oudere OP-beperkingen verwerken. Clients met Flash Player versie 18 en hoger kunnen verouderde of RBOP-beperkingen afhandelen. Als u RBOP-beperkingen instelt, moet u ook oudere OP-beperkingen voor oudere clients instellen. Voor cliënten die RBOP steunen, de beperkingen van RBOP trekken erfenis OP beperkingen.
