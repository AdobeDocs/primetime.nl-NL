---
description: U kunt de zichtbaarheid van gesloten bijschriften bepalen. Wanneer de zichtbaarheid is ingeschakeld, wordt de geselecteerde track weergegeven.
title: Zichtbaarheid van ondertiteling beheren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# Zichtbaarheid van ondertiteling beheren{#control-closed-caption-visibility}

U kunt de zichtbaarheid van gesloten bijschriften bepalen. Wanneer de zichtbaarheid is ingeschakeld, wordt de geselecteerde track weergegeven.

>[!TIP]
>
>Als u wijzigt welke track huidig is, blijft de zichtbaarheidsinstelling ongewijzigd.

Als Closed Caption-tekst wordt weergegeven wanneer de speler de zoekmodus opent, wordt de tekst niet meer weergegeven nadat de zoekactie is voltooid. In plaats daarvan geeft Browser-TVSDK na een paar seconden de volgende Closed Caption-tekst in de video weer na de eindzoekpositie.

>[!TIP]
>
>De zichtbaarheidswaarden voor gesloten bijschriften worden beheerd met `MediaPlayer.VISIBLE` en `MediaPlayer.INVISIBLE`.

1. Gebruik de `MediaPlayer.ccVisibility` eigenschap voor toegang tot de huidige zichtbaarheidsinstelling voor de gesloten bijschriften.
