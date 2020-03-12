---
description: 'null'
seo-description: 'null'
seo-title: Een domeinserver instellen
title: Een domeinserver instellen
uuid: bf85305e-9a00-4bc0-ba36-c870979456e4
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Een domeinserver instellen{#set-up-a-domain-server}

Een domeinserver configureren op een bestaande installatie van een licentieserver:

1. Open het [!DNL tomcat/lib] bestand in de [!DNL flashaccess-refimpl.properties] map.
1. Vul onder de `Domain CA certificate` optie het Domain CA-certificaat in.

   Dit certificaat wordt vervolgens gebruikt voor het accepteren van de domeintokens.
1. Voer onder de `Domain CA credential` optie de `Domain CA credential certificate (PFX)` details in.

   Dit certificaat wordt vervolgens gebruikt voor het ondertekenen van domeincertificaten en tokens.
1. Geef de waarde op voor `DomainServerlURL`.

   Als deze waarde aan wordt geplaatst, kan de domeinauthentificatie slagen. `NULL` Wanneer u echter verbinding maakt met het domein, kan een fout met het domein van de join-domein optreden.
