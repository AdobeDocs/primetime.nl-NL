---
description: 'null'
seo-description: 'null'
seo-title: Reclamevereisten
title: Reclamevereisten
uuid: 60e299df-4f42-455a-8983-8964f7a197e1
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---


# Reclamevereisten {#advertising-requirements}

U kunt advertenties in uw VOD en levende/lineaire inhoud opnemen door Adobe Primetime en besluitvormingsinterface te gebruiken.

Primetime en besluitvorming werken samen met TVSDK om advertentiemogelijkheden te identificeren, advertenties op te lossen en opgeloste advertenties in uw videostreams in te voegen.

Als u advertenties wilt opnemen in uw video-inhoud, moet u ervoor zorgen dat de reclame en de belangrijkste video-inhoud aan de volgende vereisten voldoen:

* De HLS-versie van de advertentie-inhoud mag niet hoger zijn dan de HLS-versie van de hoofdinhoud.
* Advertenties moeten multiplexed zijn en moeten een audio-slechts vertoning bevatten, ongeacht of de belangrijkste inhoud multiplexed is.
* Afspeellijsten met bitsnelheden moeten dezelfde rendities hebben als de uitvoeringen in de afspeellijst met hoofdinhoud.
* De doelduur en de individuele fragmentduur van een advertentie kunnen de doelduur van de hoofdinhoud niet overschrijden.
* Als de hoofdinhoud een audio-enige stroom bevat, moet de reclame-inhoud ook een audio-enige stroom bevatten.
* Als de hoofdinhoud subtitelstromen bevat, moet de reclame-inhoud niet-gecodeerd zijn.
* Als de belangrijkste inhoud veelvoudige beetjetarief (MBR) is, moet de reclame inhoud ook MBR zijn.
* Als de hoofdinhoud alternatieve audiotracks heeft, moet elke advertentie ten minste één audiostream hebben.

   Als de advertentie niet minstens één audio-enige stroom heeft, wordt de advertentie overgeslagen.