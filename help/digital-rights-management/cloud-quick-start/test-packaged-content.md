---
title: De inhoud van het pakket testen
description: De inhoud van het pakket testen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 0%

---

# De inhoud van het pakket testen {#test-the-packaged-content}

U moet controleren of de pakketbewerking is geslaagd met behulp van de algemeen beschikbare Adobe Primetime Desktop Player (via Flash Player). Deze speler kan alleen HDS-inhoud ondersteunen. Om HLS-inhoud te testen, is een Primetime Browser TVSDK-Toegelaten speler vereist.

1. Inhoud hosten op een webserver.
1. Start de Primetime DRM-speler (voorheen Adobe Access genoemd) op https://drmtest2.adobe.com:8080/AccessPlayer/player.html.
1. Plak de URL in uw HDS-manifest ( [!DNL .f4m]) in het navigatieveld van de speler en klik op de knop **[!UICONTROL Play]** knop.
