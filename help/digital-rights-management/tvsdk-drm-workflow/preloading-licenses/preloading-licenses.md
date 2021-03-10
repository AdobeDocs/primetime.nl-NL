---
title: Licenties vooraf laden voor offline afspelen, overzicht
description: Licenties vooraf laden voor offline afspelen, overzicht
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 0%

---


# Licenties voor offline afspelen vooraf laden {#pre-loading-licenses-for-offline-playback}

U kunt de licenties vooraf laden die nodig zijn om inhoud af te spelen die is beveiligd met Primetime DRM. Met vooraf geladen licenties kunnen gebruikers de inhoud weergeven, ongeacht of ze een actieve internetverbinding hebben.

Voor het vooraf laden is een internetverbinding vereist *do*. U kunt `DRMManager.loadVoucher()` van tevoren gebruiken om licenties vooraf te laden. Later, wanneer de client de gewenste inhoud wil afspelen, is het DRM-systeem vooraf voorbereid en kan de beveiligde inhoud direct worden afgespeeld.
