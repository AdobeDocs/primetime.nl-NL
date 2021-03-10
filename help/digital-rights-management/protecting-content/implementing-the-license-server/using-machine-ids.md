---
title: Apparaatid's gebruiken
description: Apparaatid's gebruiken
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---


# Apparaatid&#39;s gebruiken{#use-machine-identifiers}

Alle Adobe Primetime DRM-aanvragen (met uitzondering van aanvragen die FMRMS-compatibiliteit ondersteunen) bevatten informatie over de computertoken die tijdens de individualisatie aan de client is uitgegeven. De machine-token bevat een machine-id. Dit is een id die tijdens de individualisatie is toegewezen. U kunt deze id gebruiken om het aantal machines te tellen waarvan een gebruiker een vergunning heeft gevraagd of zich bij een domein heeft aangesloten.

U kunt een id als volgt gebruiken:

* De `getUniqueId()` methode keert een koord terug dat aan een apparaat tijdens individualisering is toegewezen. U kunt de tekenreeksen opslaan in een database en zoeken op id. Deze id verandert echter als de gebruiker de vaste schijf opnieuw formatteert en opnieuw individualiseert. Deze id heeft ook een andere waarde voor Adobe AIR en Adobe Flash Player in verschillende browsers op dezelfde computer.
* Als u machines nauwkeuriger wilt tellen, kunt u `getBytes()` gebruiken om het volledige herkenningsteken op te slaan. Om te bepalen of de machine eerder is gezien, krijg alle herkenningstekens voor een gebruikersnaam en vraag `matches()` om te controleren of om het even welke gelijke. Omdat de methode `matches()` moet worden gebruikt om de waarden te vergelijken die door `MachineId.getBytes` worden teruggekeerd, is deze optie slechts praktisch wanneer er een klein aantal te vergelijken waarden zijn; bijvoorbeeld de machines die aan een bepaalde gebruiker zijn gekoppeld.

