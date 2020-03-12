---
seo-title: Een domeinserver instellen
title: Een domeinserver instellen
uuid: b262ea86-f465-4ed1-b278-122d4dafc881
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Een domeinserver instellen {#set-up-a-domain-server}

Om de domeinserver op een bestaande installatie van de vergunningsserver te vormen, voer de volgende taken uit:

1. Open het [!DNL flashaccess-refimpl.properties] bestand onder [!DNL tomcat/lib].

1. Vul onder de `Domain CA certificate` optie de gegevens van het Domain CA-certificaat in. Dit certificaat wordt gebruikt voor het accepteren van de domeintokens.
1. Vul onder de `Domain CA credential` optie de `Domain CA credential certificate (PFX)` details in. Dit certificaat wordt gebruikt voor het ondertekenen van domeincertificaten en tokens.

1. Geef de waarde op voor `DomainServerlURL`. Als deze waarde ONGELDIG is, kan de domeinauthentificatie slagen. Wanneer u echter verbinding maakt met het domein, treedt een fout met het domein toe.

