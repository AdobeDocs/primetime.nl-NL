---
seo-title: Apparaatid's gebruiken
title: Apparaatid's gebruiken
uuid: 14eee414-62f1-4a9d-84bd-689ca2271d19
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Apparaatid&#39;s gebruiken{#use-machine-identifiers}

Alle Adobe Primetime DRM-aanvragen (met uitzondering van aanvragen die FMRMS-compatibiliteit ondersteunen) bevatten informatie over de computertoken die tijdens de individualisatie aan de client is uitgegeven. De machine-token bevat een machine-id. Dit is een id die tijdens de individualisatie is toegewezen. U kunt deze id gebruiken om het aantal machines te tellen waarvan een gebruiker een vergunning heeft gevraagd of zich bij een domein heeft aangesloten.

U kunt een id als volgt gebruiken:

* De `getUniqueId()` methode keert een koord terug dat aan een apparaat tijdens individualisering is toegewezen. U kunt de tekenreeksen opslaan in een database en zoeken op id. Deze id verandert echter als de gebruiker de vaste schijf opnieuw formatteert en opnieuw individualiseert. Deze id heeft ook een andere waarde voor Adobe AIR en Adobe Flash Player in verschillende browsers op dezelfde computer.
* Als u de machines nauwkeuriger wilt tellen, kunt u gebruiken `getBytes()` om het volledige herkenningsteken op te slaan. Om te bepalen of de machine eerder is gezien, krijg alle herkenningstekens voor een gebruikersnaam en vraag `matches()` om te controleren of om het even welke gelijke. Omdat de `matches()` methode moet worden gebruikt om de waarden te vergelijken die door `MachineId.getBytes`zijn teruggekeerd, is deze optie slechts praktisch wanneer er een klein aantal te vergelijken waarden zijn; bijvoorbeeld de machines die aan een bepaalde gebruiker zijn gekoppeld.

