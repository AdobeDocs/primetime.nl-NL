---
title: Een domeinserver instellen
description: Een domeinserver instellen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 0%

---


# Een domeinserver instellen{#set-up-a-domain-server}

Een domeinserver configureren op een bestaande installatie van een licentieserver:

1. Open in de map [!DNL tomcat/lib] het bestand [!DNL flashaccess-refimpl.properties].
1. Vul onder de optie `Domain CA certificate` het Domain CA-certificaat in.

   Dit certificaat wordt vervolgens gebruikt voor het accepteren van de domeintokens.
1. Vul onder de optie `Domain CA credential` de `Domain CA credential certificate (PFX)`-gegevens in.

   Dit certificaat wordt vervolgens gebruikt voor het ondertekenen van domeincertificaten en tokens.
1. Geef de waarde op voor `DomainServerlURL`.

   Als deze waarde op `NULL` wordt geplaatst, kan de domeinauthentificatie slagen. Wanneer u echter verbinding maakt met het domein, kan een fout met het domein van de join-domein optreden.
