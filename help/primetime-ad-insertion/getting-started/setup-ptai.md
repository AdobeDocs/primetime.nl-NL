---
title: Adobe Primetime-Ad Insertion instellen
description: Adobe Primetime Ad Insertion instellen
exl-id: 3720c4b3-08d0-48b8-bb4b-24449e453263
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---

# Adobe Primetime-Ad Insertion instellen {#ptai-setup}

Het proces voor het instellen van Primetime Ad Insertion ziet er als volgt uit:

1. Integreer uw Advertentieserver in Primetime Ad Insertion door in de console van de Ad Insertion van Primetime te registreren en opstellings omleidingsregels. Zie voor meer informatie [Advertentieserver integreren](/help/primetime-ad-insertion/getting-started/integrate-ad-server.md).

1. Vorm kanalen of platforms in de console van Ad Insertion Primetime om adequate rapporteringsdimensies te verzekeren.

1. Vorm en integreer uw CDN in Ad Insertion Primetime. Zie voor meer informatie [De CDN integreren](integrate-cdn.md).

1. Bepaal of just-in-time en opnieuw verpakken vereist is voor uw advertentieworkflow. Neem contact op met uw ondersteuningsvertegenwoordiger voor Primetime om de service in te schakelen.

1. Werk uw toepassing bij om de [Bootstrap API](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md) om verzoeken om Primetime Ad Insertion in te dienen en te ontvangen, en uw toepassing te vormen om te steunen. Zie voor meer informatie [Advertentie bijhouden](set-up-ad-tracking.md).

1. Test uw toepassing om te controleren of deze correct en correct wordt afgespeeld met behulp van de [Foutopsporingsgereedschappen](/help/primetime-ad-insertion/performance-monitoring-debugging-reporting/troubleshoot-and-debug.md).

1. Test uw toepassingen om ervoor te zorgen dat de beacons voor het bijhouden van advertenties en de afdruk correct worden geactiveerd met de [Rapportage](/help/primetime-ad-insertion/performance-monitoring-debugging-reporting/reporting-and-billing.md).
