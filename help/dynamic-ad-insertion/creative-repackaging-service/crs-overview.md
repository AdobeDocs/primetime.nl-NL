---
description: De creatieve herverpakkingsdienst (CRS) zorgt ervoor dat niet-HLS en creatief behoorlijk in HLS stromen kunnen terugspelen. De manifestserver roept op CRS wanneer het een niet-HLS advertentie ontmoet.
seo-description: De creatieve herverpakkingsdienst (CRS) zorgt ervoor dat niet-HLS en creatief behoorlijk in HLS stromen kunnen terugspelen. De manifestserver roept op CRS wanneer het een niet-HLS advertentie ontmoet.
seo-title: Overzicht van CRS
title: Overzicht van CRS
uuid: 3ae75fa7-397f-47ba-8e3d-50543ca25458
translation-type: tm+mt
source-git-commit: 4788a8de8ba47d7f448967066e1bd0fb73fdb7a8

---


# Overzicht van CRS {#overview-of-crs}

De creatieve herverpakkingsdienst (CRS) zorgt ervoor dat niet-HLS en creatief behoorlijk in HLS stromen kunnen terugspelen. De manifestserver roept op CRS wanneer het een niet-HLS advertentie ontmoet.

>[!NOTE]
>
>CRS is standaard uitgeschakeld. Neem contact op met uw technische accountmanager van Adobe om CRS voor uw account in te schakelen.
>
>Raadpleeg het onderwerp CRS *inschakelen in TVSDK-toepassingen* in de programmagids voor uw platform voor informatie over het inschakelen van CRS in TVSDK-apps. Voor Android 3.4, zie bijvoorbeeld CRS [inschakelen in TVSDK-toepassingen](../../programming/tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/ad-transcoding/android-3x-ad-transcoding.md)

CRS bereidt de Levende Streaming van HTTP (HLS) en creatieven voor de inhoudsstroom voor en injecteert ID3 pakketten voor cliënt-kant en het volgen. MP4-, FLV- en WebM-bestanden die zijn ontvangen van externe en externe servers, en netwerken en agentservers worden getranscodeerd naar HLS-indeling.

Wanneer Adobe Primetime en invoeging een niet-HLS en creatief programma tegenkomen, wordt dit naar CRS verzonden voor herverpakken. Dit duurt gewoonlijk niet langer dan drie minuten. CRS verzendt de getranscodeerde en creatieve gegevens naar de CDN-server voor toekomstig gebruik. Dit heet **`just-in-time (JIT) repackaging`**. U kunt ook transcoderen en creatieve objecten voordat ze nodig zijn met de API [voor](../../dynamic-ad-insertion/creative-repackaging-service/api-repackage.md) herverpakken. Dit heet *`asynchronous repackaging`*.

Uw technische accountmanager van Adobe kan ook bepaalde standaardgedragingen van CRS wijzigen als een ander gedrag beter geschikt is voor uw toepassing. Dit zijn:

* Prioriteit van creatieve en advertentievormen.

   De `MediaFiles` rubriek van een VAST/VMAP respons kan creatieve producten met verschillende `MediaFile` typen bevatten. Standaard selecteert de manifestserver een server op basis van een vaste reeks prioriteiten ( `application/x-mpegURL`, `application/vnd.apple.mpegURL`, `video/mp4`, `video/x-flv,video/webm`). Adobe kan de prioriteiten voor uw account wijzigen.
* Doelduur toevoegen.

   De manifestserver ontdekt het doel en de duur van de inhoud playlist en verzendt het naar CRS. Adobe kan dit gedrag zodanig wijzigen dat CRS altijd een vaste duur gebruikt die u voor uw account opgeeft.
