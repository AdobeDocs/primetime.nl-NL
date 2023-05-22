---
title: Een domeinserver instellen
description: Een domeinserver instellen
copied-description: true
exl-id: eeb0d39d-58a4-4414-9123-2cf1b27b73de
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 0%

---

# Een domeinserver instellen{#set-up-a-domain-server}

Een domeinserver configureren op een bestaande installatie van een licentieserver:

1. In de [!DNL tomcat/lib] directory, open de [!DNL flashaccess-refimpl.properties] bestand.
1. Onder de `Domain CA certificate` , vult u het Domain CA-certificaat in.

   Dit certificaat wordt vervolgens gebruikt voor het accepteren van de domeintokens.
1. Onder de `Domain CA credential` -optie, voltooi de `Domain CA credential certificate (PFX)` details.

   Dit certificaat wordt vervolgens gebruikt voor het ondertekenen van domeincertificaten en tokens.
1. Geef de waarde op voor `DomainServerlURL`.

   Als deze waarde is ingesteld op `NULL`kan de domeinverificatie slagen. Wanneer u echter verbinding maakt met het domein, kan een fout met het domein van de join-domein optreden.
