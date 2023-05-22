---
description: De creatieve herverpakkingsdienst (CRS) zorgt ervoor dat niet-HLS en creatief behoorlijk in HLS stromen kunnen terugspelen. De manifestserver roept op CRS wanneer het een niet-HLS advertentie ontmoet.
title: Overzicht van CRS
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---


# Overzicht van CRS {#overview-of-crs}

De creatieve herverpakkingsdienst (CRS) zorgt ervoor dat niet-HLS en creatief behoorlijk in HLS stromen kunnen terugspelen. De manifestserver roept op CRS wanneer het een niet-HLS advertentie ontmoet.

>[!NOTE]
>
>CRS is standaard uitgeschakeld. Neem contact op met de technische accountmanager van Adobe om CRS voor uw account in te schakelen.
>
>Voor informatie over het inschakelen van CRS in TVSDK-apps raadpleegt u de *CRS inschakelen in TVSDK-toepassingen* onderwerp in de Gids van de Programmer voor uw platform. Voor Android 3.4, zie bijvoorbeeld [CRS inschakelen in TVSDK-toepassingen](../../programming/tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/ad-transcoding/android-3x-ad-transcoding.md)

CRS bereidt de Levende Streaming van HTTP (HLS) en creatieven voor de inhoudsstroom voor en injecteert ID3 pakketten voor cliënt-kant en het volgen. MP4-, FLV- en WebM-bestanden die zijn ontvangen van externe en externe servers, en netwerken en agentservers worden getranscodeerd naar HLS-indeling.

Wanneer Adobe Primetime en de invoeging een niet-HLS en creatief apparaat tegenkomen, stuurt het deze naar CRS voor herverpakken, wat gewoonlijk niet langer dan drie minuten duurt. CRS verzendt de getranscodeerde en creatieve gegevens naar de CDN-server voor toekomstig gebruik. Dit wordt **`just-in-time (JIT) repackaging`**. U kunt ook transcoderen en creatieve objecten voordat u ze nodig hebt  [API opnieuw verpakken](../../primetime-ad-insertion/~old-creative-repackaging-service/api-repackage.md) . Dit wordt *`asynchronous repackaging`*.

Uw Adobe Technical Account Manager kan ook bepaalde standaardgedragingen van CRS wijzigen als een ander gedrag beter geschikt is voor uw toepassing. Dit zijn:

* Prioriteit van creatieve en advertentievormen.

   De `MediaFiles` VAST/VMAP respons kan creatieve `MediaFile` typen. Standaard selecteert de manifestserver er een volgens een vaste set prioriteiten ( `application/x-mpegURL`, `application/vnd.apple.mpegURL`, `video/mp4`, `video/x-flv,video/webm`). Adobe kan de prioriteiten voor uw account wijzigen.
* Doelduur toevoegen.

   De manifestserver ontdekt het doel en de duur van de inhoud playlist en verzendt het naar CRS. Adobe kan dit gedrag wijzigen zodat CRS altijd een vaste duur gebruikt die u voor uw account opgeeft.
