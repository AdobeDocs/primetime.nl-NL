---
title: Een domeinserver instellen
description: Een domeinserver instellen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---

# Een domeinserver instellen {#set-up-a-domain-server}

Om de domeinserver op een bestaande installatie van de vergunningsserver te vormen, voer de volgende taken uit:

1. Open de [!DNL flashaccess-refimpl.properties] bestand onder [!DNL tomcat/lib].

1. Onder de `Domain CA certificate` vult u de gegevens van het Domain CA-certificaat in. Dit certificaat wordt gebruikt voor het accepteren van de domeintokens.
1. Onder de `Domain CA credential` , vult u de `Domain CA credential certificate (PFX)` details. Dit certificaat wordt gebruikt voor het ondertekenen van domeincertificaten en tokens.

1. Geef de waarde op voor `DomainServerlURL`. Als deze waarde ONGELDIG is, kan de domeinauthentificatie slagen. Wanneer u echter verbinding maakt met het domein, treedt een fout met het domein toe.
