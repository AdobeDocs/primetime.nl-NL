---
title: Een domeinserver instellen
description: Een domeinserver instellen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
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
