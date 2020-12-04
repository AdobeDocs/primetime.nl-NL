---
description: 'null'
seo-description: 'null'
seo-title: Een domeinserver instellen
title: Een domeinserver instellen
uuid: bf85305e-9a00-4bc0-ba36-c870979456e4
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '95'
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
