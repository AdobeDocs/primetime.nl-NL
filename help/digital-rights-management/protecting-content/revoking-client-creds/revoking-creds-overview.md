---
seo-title: Overzicht
title: Overzicht
uuid: c6f54867-d0a3-43fd-9493-6496f1b7831a
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Overzicht{#overview}

U moet mogelijk de referenties van een client intrekken of controleren of een bepaalde set referenties al onder bepaalde voorwaarden zijn ingetrokken. Credentials kunnen worden ingetrokken als ze gecompromitteerd zijn. Wanneer deze problemen zich voordoen, worden er geen licenties meer uitgegeven aan gecompromitteerde klanten.

Voor het intrekken van gecompromitteerde clients houdt Adobe CRL&#39;s (Certificate Revocation Lists) bij. Deze CRLs wordt automatisch afgedwongen door SDK. Licentieservers kunnen clients verder beperken door bepaalde computerreferenties of bepaalde versies van DRM- en runtime-referenties te weigeren. Er `RevocationList` kan een script worden gemaakt en doorgegeven aan de SDK om de referenties van de computer in te trekken. Specifieke DRM/runtime versies kunnen op DRM-beleidsniveau worden ingetrokken door modulebeperkingen in te stellen in het afspeelrecht of globaal door modulebeperkingen in te stellen in het `HandlerConfiguration`.

De discussie is gericht op het intrekken van clientgegevens.
