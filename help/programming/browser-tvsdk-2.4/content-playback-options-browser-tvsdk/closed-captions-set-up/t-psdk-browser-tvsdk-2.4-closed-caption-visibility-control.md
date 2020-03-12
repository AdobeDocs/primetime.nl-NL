---
description: U kunt de zichtbaarheid van gesloten bijschriften bepalen. Wanneer de zichtbaarheid is ingeschakeld, wordt de geselecteerde track weergegeven.
seo-description: U kunt de zichtbaarheid van gesloten bijschriften bepalen. Wanneer de zichtbaarheid is ingeschakeld, wordt de geselecteerde track weergegeven.
seo-title: Zichtbaarheid van ondertiteling beheren
title: Zichtbaarheid van ondertiteling beheren
uuid: b161a729-73f3-4019-a95e-013b42779842
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

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

1. Gebruik de `MediaPlayer.ccVisibility` eigenschap om toegang te krijgen tot de huidige zichtbaarheidsinstelling voor de gesloten bijschriften.

