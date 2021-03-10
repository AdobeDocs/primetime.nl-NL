---
title: Een domeinserver instellen
description: Een domeinserver instellen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---


# Een domeinserver {#set-up-a-domain-server} instellen

Om de domeinserver op een bestaande installatie van de vergunningsserver te vormen, voer de volgende taken uit:

1. Open het [!DNL flashaccess-refimpl.properties] bestand onder [!DNL tomcat/lib].

1. Vul onder de optie `Domain CA certificate` de gegevens van het Domain CA-certificaat in. Dit certificaat wordt gebruikt voor het accepteren van de domeintokens.
1. Vul onder de optie `Domain CA credential` de details `Domain CA credential certificate (PFX)` in. Dit certificaat wordt gebruikt voor het ondertekenen van domeincertificaten en tokens.

1. Geef de waarde op voor `DomainServerlURL`. Als deze waarde ONGELDIG is, kan de domeinauthentificatie slagen. Wanneer u echter verbinding maakt met het domein, treedt een fout met het domein toe.

