---
title: Licenties vooraf laden voor offline afspelen, overzicht
description: Licenties vooraf laden voor offline afspelen, overzicht
copied-description: true
exl-id: 0d49c0e4-821b-4354-b92d-bbe2c07e467b
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 0%

---

# Licenties vooraf laden voor offline afspelen {#pre-loading-licenses-for-offline-playback}

U kunt de licenties vooraf laden die nodig zijn om inhoud af te spelen die is beveiligd met Primetime DRM. Met vooraf geladen licenties kunnen gebruikers de inhoud weergeven, ongeacht of ze een actieve internetverbinding hebben.

Het vooraf laden proces zelf *doet* vereisen een internetverbinding. U kunt `DRMManager.loadVoucher()` voordat licenties vooraf worden geladen. Later, wanneer de client de gewenste inhoud wil afspelen, is het DRM-systeem vooraf voorbereid en kan de beveiligde inhoud direct worden afgespeeld.
