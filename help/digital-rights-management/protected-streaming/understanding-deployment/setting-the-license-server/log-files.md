---
description: De logbestanden die door de Adobe Primetime DRM-server voor beveiligde streaming-toepassing worden gegenereerd, bevinden zich in de map die is opgegeven door LicenseServer.LogRoot.
seo-description: De logbestanden die door de Adobe Primetime DRM-server voor beveiligde streaming-toepassing worden gegenereerd, bevinden zich in de map die is opgegeven door LicenseServer.LogRoot.
seo-title: Logbestanden
title: Logbestanden
uuid: 4498fe60-65af-4f99-8f9b-e85013d0c9e9
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Logbestanden{#log-files}

De logbestanden die door de Adobe Primetime DRM-server voor beveiligde streaming-toepassing worden gegenereerd, bevinden zich in de map die is opgegeven door LicenseServer.LogRoot.

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>Als de huidige logbestanden worden verwijderd of verplaatst terwijl de server wordt uitgevoerd, wordt het logbestand mogelijk niet opnieuw gemaakt. Daarom kunnen sommige logboekinformatie worden geschrapt.

## Logboekmapstructuur {#section_F490A483D60145ADBC21038914C39203}

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

Het globale logboekdossier, [!DNL flashaccess-global.log], wordt gevestigd in *LicenseServer.LogRoot*. Het logbestand kan logboekberichten bevatten die de Adobe Primetime DRM Java SDK of logberichten hebben gegenereerd tijdens de tijd dat de server is geïnitialiseerd.

## Partitielogbestand {#section_5660137CD6AA40519E72A4315534846B}

Het partitielogbestand [!DNL flashaccess-partition.log], bevindt zich in de [!DNL <LicenseServer.LogRoot>/flashaccesserver] map. Het omvat logboekberichten die tijdens de verwerking van een vergunningsverzoek zijn geproduceerd.

## Aanraaklogboek {#section_F0257CC0831647F18A746B4F02E3E910}

Het logbestand van elke huurder, [!DNL flashaccess-tenant.log], bevindt zich in [!DNL &lt;LicenseServer.LogRoot>/flashaccserver/tenants/<tenantname>]. Het huurderslogboek omvat controleinformatie die elke vergunning beschrijft die voor deze huurder wordt geproduceerd.
