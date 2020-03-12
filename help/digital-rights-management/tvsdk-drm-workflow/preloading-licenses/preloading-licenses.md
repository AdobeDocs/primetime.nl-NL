---
seo-title: Licenties vooraf laden voor offline afspelen, overzicht
title: Licenties vooraf laden voor offline afspelen, overzicht
uuid: 71e5169b-7f70-4723-9f9b-fdff822c5876
translation-type: tm+mt
source-git-commit: 9bbcb228d3367fbf53de811bf2941ca653ce3b0e

---


# Licenties vooraf laden voor offline afspelen {#pre-loading-licenses-for-offline-playback}

U kunt de licenties vooraf laden die nodig zijn om inhoud af te spelen die is beveiligd met Primetime DRM. Met vooraf geladen licenties kunnen gebruikers de inhoud bekijken, ongeacht of ze een actieve internetverbinding hebben of niet.

Voor het vooraf laden *is wel* een internetverbinding vereist. U kunt licenties `DRMManager.loadVoucher()` vooraf laden. Later, wanneer de client de gewenste inhoud wil afspelen, is het DRM-systeem vooraf voorbereid en kan de beveiligde inhoud direct worden afgespeeld.
