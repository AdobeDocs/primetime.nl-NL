---
title: Apparaatid's gebruiken
description: Apparaatid's gebruiken
copied-description: true
exl-id: 61ff9240-0c29-437e-b676-7983e2cc5f7b
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---

# Apparaatid&#39;s gebruiken{#using-machine-identifiers}

Alle verzoeken van de Toegang van Adobe (met uitzondering van verzoeken die FMRMS verenigbaarheid steunen) bevatten informatie over het machinetoken dat aan de cliënt tijdens individualisering wordt uitgegeven. De machine-token bevat een machine-id, een id die tijdens de individualisatie is toegewezen. Gebruik deze id om het aantal machines te tellen waarvan een gebruiker een vergunning heeft gevraagd of zich bij een domein heeft aangesloten.

Er zijn twee manieren om het herkenningsteken te gebruiken. De `getUniqueId()` de methode keert een koord terug dat aan het apparaat tijdens individualisering wordt toegewezen. U kunt de tekenreeksen opslaan in een database en zoeken op id. Deze id verandert echter als de gebruiker de vaste schijf opnieuw formatteert en opnieuw individualiseert. Deze id heeft ook een andere waarde voor Adobe® AIR® en Adobe® Flash® Player in verschillende browsers op dezelfde computer.

Om machines nauwkeuriger te tellen, kunt u gebruiken `getBytes()` om de volledige id op te slaan. Om te bepalen of de machine eerder is gezien, krijg alle herkenningstekens voor een gebruikersnaam en vraag `matches()` om te controleren of er een overeenkomst is. Omdat `matches()` moet worden gebruikt om de waarden te vergelijken die door `MachineId.getBytes`Deze optie is echter alleen handig wanneer er een klein aantal waarden moet worden vergeleken (bijvoorbeeld de machines die aan een bepaalde gebruiker zijn gekoppeld).
