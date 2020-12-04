---
description: Browser TVSDK verschaft uw video-app de informatie die nodig is om te reageren op een klik van een gebruiker op een klikbare advertentie.
seo-description: Browser TVSDK verschaft uw video-app de informatie die nodig is om te reageren op een klik van een gebruiker op een klikbare advertentie.
seo-title: Klikbare advertenties
title: Klikbare advertenties
uuid: 493c3199-b5ba-4809-86eb-e80f10eb957b
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---


# Overzicht {#clickable-ads-overview}

Browser TVSDK verschaft uw video-app de informatie die nodig is om te reageren op een klik van een gebruiker op een klikbare advertentie.

Wanneer een gebruiker op een klikbare advertentie klikt, is een typisch antwoord van een videotoepassing een nieuw browser venster te openen en aan URL te navigeren verbonden aan de advertentie. Om dit te vergemakkelijken, wordt in Browser-TVSDK een melding gegenereerd die uw app kan gebruiken om het doorklikproces te beheren.

In uw app kunt u de gebruiker een besturingselement bieden waarmee deze kan klikken (bijvoorbeeld een knop) terwijl de aanklikbare advertentie wordt afgespeeld. U moet handlers maken voor gebeurtenissen die worden geactiveerd door Browser-TVSDK en die zijn gekoppeld aan de advertentie (bijv. starten, klikken en voltooien). Ten slotte moet u het specifieke gedrag implementeren dat uw app volgt na de advertentie van een gebruiker (bijvoorbeeld of u de advertentie wilt pauzeren, de URL voor doorklikken wilt weergeven enzovoort).

>[!NOTE]
>
>De referentiespeler die bij Browser-TVSDK wordt geleverd, bevat één mogelijke werkoplossing voor het verwerken van doorklikadvertenties.