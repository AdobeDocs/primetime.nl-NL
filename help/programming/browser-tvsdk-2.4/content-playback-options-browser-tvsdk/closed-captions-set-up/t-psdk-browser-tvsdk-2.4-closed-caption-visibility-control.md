---
description: U kunt de zichtbaarheid van gesloten bijschriften bepalen. Wanneer de zichtbaarheid is ingeschakeld, wordt de geselecteerde track weergegeven.
title: Zichtbaarheid van ondertiteling beheren
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---


# Zichtbaarheid van een gesloten bijschrift besturen{#control-closed-caption-visibility}

U kunt de zichtbaarheid van gesloten bijschriften bepalen. Wanneer de zichtbaarheid is ingeschakeld, wordt de geselecteerde track weergegeven.

>[!TIP]
>
>Als u wijzigt welke track huidig is, blijft de zichtbaarheidsinstelling ongewijzigd.

Als Closed Caption-tekst wordt weergegeven wanneer de speler de zoekmodus opent, wordt de tekst niet meer weergegeven nadat de zoekactie is voltooid. In plaats daarvan geeft Browser-TVSDK na een paar seconden de volgende Closed Caption-tekst in de video weer na de eindzoekpositie.

>[!TIP]
>
>De zichtbaarheidswaarden voor gesloten bijschriften worden bepaald met `MediaPlayer.VISIBLE` en `MediaPlayer.INVISIBLE`.

1. Gebruik de eigenschap `MediaPlayer.ccVisibility` om toegang te krijgen tot de huidige zichtbaarheidsinstelling voor de gesloten bijschriften.

