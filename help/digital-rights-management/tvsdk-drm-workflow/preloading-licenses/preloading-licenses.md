---
title: Licenties vooraf laden voor offline afspelen
description: Licenties vooraf laden voor offline afspelen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 0%

---

# Licenties vooraf laden voor offline afspelen {#pre-loading-licenses-for-offline-playback}

U kunt de licenties vooraf laden die nodig zijn om inhoud af te spelen die is beveiligd met Primetime DRM. Met vooraf geladen licenties kunnen gebruikers de inhoud bekijken, ongeacht of ze een actieve internetverbinding hebben of niet.

Het vooraf laden proces zelf *doet* vereisen een internetverbinding. U kunt `DRMManager.loadVoucher()` voordat licenties vooraf worden geladen. Later, wanneer de client de gewenste inhoud wil afspelen, is het DRM-systeem vooraf voorbereid en kan de beveiligde inhoud direct worden afgespeeld.
