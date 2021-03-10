---
description: De manifestserver steunt uitgever-toegelaten WebVTT titels voor alle videoformaten HLS. Wanneer het verzoeken ontvangt om advertenties in WebVTT getitelde inhoud op te nemen, doet het correct.
title: Ondersteuning voor WebVTT-bijschriften
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---


# Ondersteuning voor WebVTT-bijschriften {#support-for-webvtt-captions}

De manifestserver steunt uitgever-toegelaten WebVTT titels voor videoformaten HLS/DASH. Wanneer het verzoeken ontvangt om advertenties in WebVTT getitelde inhoud op te nemen, doet het correct.

Als de uitgever ondertitels WebVTT in de inhoud omvat, verzendt de manifestserver de cliënt een inhoudsstroom met titels. WebVTT moet door de uitgever voor de manifestserver worden toegelaten om titels te steunen. Wanneer de cliënt toegelaten titels WebVTT heeft, en een verzoek naar de manifestserver verzendt, manipuleert de manifestserver de chronologie en het spoor WebVTT en keert inhoud met gestikte advertenties en titels aan de cliënt terug.

De workflow voor VOD-inhoudsstromen is als volgt:

1. De cliënt verzendt een inhoudsstroom met WebVTT titels die aan de manifestserver worden toegelaten.
1. De manifestserver manipuleert de chronologie om advertenties in de inhoudsstroom te stikken.
1. De manifestserver manipuleert het spoor WebVTT om titels aan de inhoud (met inbegrip van advertenties) toe te voegen.
1. De manifestserver levert de inhoudsstroom aan de cliënt, met opgenomen advertenties en titels.

>[!NOTE]
>
>Als een WebVTT bijschriftsegment binnen een mid-roll advertentie valt, ziet de kijker dat bijschrift vóór en na dat midden-rol en onderbreking spelen. In een bijschriftsegment van 10 seconden met een halverwege rol van 30 seconden en een 5 seconden durende markering ziet de kijker dat bijschriftsegment gedurende 5 seconden voor het midden en het einde en gedurende 5 seconden na het midden.

>[!NOTE]
>
>Als een client vraagt dat een video wordt afgespeeld in een specifieke taal zoals Engels en vervolgens wordt gevraagd de video af te spelen in het Frans, kan de manifestserver niet detecteren dat de client heeft verzocht de taal te wijzigen in het Frans. Omdat de client niet met de manifestserver communiceert, voegt de manifestserver het bijschrift van de advertentie in de videostream in met behulp van de eerste taal die in het master bestand M3U8 van de advertentie is opgegeven.
