---
title: De inhoud van het pakket testen
description: De inhoud van het pakket testen
copied-description: true
exl-id: 98456bf8-5d4d-47a7-905a-e6dac1e826ba
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 0%

---

# De inhoud van het pakket testen {#test-the-packaged-content}

U moet controleren of de verpakkingsbewerking is geslaagd met behulp van de algemeen beschikbare Adobe Primetime Desktop Player (via Flash Player). Deze speler kan alleen HDS-inhoud ondersteunen. Om HLS-inhoud te testen, is een Primetime Browser TVSDK-Toegelaten speler vereist.

1. Inhoud hosten op een webserver.
1. Start de Primetime DRM-speler (voorheen Adobe Access genoemd) op https://drmtest2.adobe.com:8080/AccessPlayer/player.html.
1. Plak de URL in uw HDS-manifest ( [!DNL .f4m]) in het navigatieveld van de speler en klik op de knop **[!UICONTROL Play]** knop.
