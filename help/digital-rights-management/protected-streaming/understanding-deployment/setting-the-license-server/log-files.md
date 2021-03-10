---
description: De logbestanden die worden gegenereerd door de Adobe Primetime DRM-server voor beveiligde streaming-toepassing bevinden zich in de map die is opgegeven door LicenseServer.LogRoot.
title: Logbestanden
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---


# Logbestanden{#log-files}

De logbestanden die worden gegenereerd door de Adobe Primetime DRM-server voor beveiligde streaming-toepassing bevinden zich in de map die is opgegeven door LicenseServer.LogRoot.

>[!NOTE]
>
>Als de huidige logbestanden worden verwijderd of verplaatst terwijl de server wordt uitgevoerd, wordt het logbestand mogelijk niet opnieuw gemaakt. Daarom kunnen sommige logboekinformatie worden geschrapt.

## Logmapstructuur {#section_F490A483D60145ADBC21038914C39203}

Logmappen zijn gestructureerd voor gebruiksgemak. De logmap heeft de volgende structuur:

```
<i class="+ topic ph hi-d="" i "="">
 LicenseServer.LogRoot/ 
 flashaccess-global.log 
     flashaccessserver/ 
         flashaccess-partition.log 
         tenants/ 
             
 <i class="+ topic ph hi-d="" i "="">
  tenantname/ 
                  flashaccess-tenant.log
 </i class="+ topic>
</i class="+ topic>
```

## Globaal logbestand {#section_1CFA90748142439C9F3BE380969539DA}

Het algemene logbestand `flashaccess-global.log` bevindt zich in *LicenseServer.LogRoot*. Het logboek kan logboekberichten omvatten die de Adobe Primetime DRM Java SDK of logboekberichten tijdens de tijd kunnen hebben geproduceerd dat de server is geïnitialiseerd.

## Partitielogbestand {#section_5660137CD6AA40519E72A4315534846B}

Het verdelingslogboekdossier, `flashaccess-partition.log`, wordt gevestigd in `<LicenseServer.LogRoot>/flashaccesserver` folder. Het omvat logboekberichten die tijdens de verwerking van een vergunningsverzoek zijn geproduceerd.

## Aanraaklogbestand {#section_F0257CC0831647F18A746B4F02E3E910}

Het logbestand `flashaccess-tenant.log` van elke huurder bevindt zich in `<LicenseServer.LogRoot>/flashaccesserver/tenants/<tenantname>`. Het huurderslogboek omvat controleinformatie die elke vergunning beschrijft die voor deze huurder wordt geproduceerd.
