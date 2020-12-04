---
seo-title: Apparaatid's gebruiken
title: Apparaatid's gebruiken
uuid: 2832c158-fade-4bbf-ae89-f95ce9dfc369
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---


# Apparaatid&#39;s gebruiken{#using-machine-identifiers}

Alle verzoeken van de Toegang van Adobe (met uitzondering van verzoeken die FMRMS verenigbaarheid steunen) bevatten informatie over het machinetoken dat aan de cliënt tijdens individualisering wordt uitgegeven. De machine-token bevat een machine-id, een id die tijdens de individualisatie is toegewezen. Gebruik deze id om het aantal machines te tellen waarvan een gebruiker een vergunning heeft gevraagd of zich bij een domein heeft aangesloten.

Er zijn twee manieren om het herkenningsteken te gebruiken. De `getUniqueId()` methode keert een koord terug dat aan het apparaat tijdens individualisering wordt toegewezen. U kunt de tekenreeksen opslaan in een database en zoeken op id. Deze id verandert echter als de gebruiker de vaste schijf opnieuw formatteert en opnieuw individualiseert. Deze id heeft ook een andere waarde voor Adobe® AIR® en Adobe® Flash® Player in verschillende browsers op dezelfde computer.

Om machines nauwkeuriger te tellen, kunt u `getBytes()` gebruiken om het volledige herkenningsteken op te slaan. Om te bepalen of de machine eerder is gezien, krijg alle herkenningstekens voor een gebruikersnaam en vraag `matches()` om te controleren of om het even welke gelijke. Omdat de methode `matches()` moet worden gebruikt om de waarden te vergelijken die door `MachineId.getBytes` worden teruggekeerd, is deze optie slechts praktisch wanneer er een klein aantal te vergelijken waarden zijn (bijvoorbeeld, de machines verbonden aan een bepaalde gebruiker).
