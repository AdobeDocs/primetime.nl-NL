---
title: Aantal machines bij afgifte van vergunningen
description: Aantal machines bij afgifte van vergunningen
copied-description: true
exl-id: de052e98-8ae3-4e12-8f77-787293edda39
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 0%

---

# Aantal machines bij afgifte van vergunningen{#machine-count-when-issuing-licenses}

Als de bedrijfsregels vereisen dat het aantal machines voor een gebruiker wordt gevolgd, moet de Server van de Vergunning of de Server van het Domein machine IDs opslaan verbonden aan de gebruiker. De meest robuuste manier om machine IDs te volgen is de waarde op te slaan die door wordt teruggekeerd `MachineId.getBytes()` in een database. Wanneer een nieuwe aanvraag wordt ingediend, vergelijkt u de machine-id in de aanvraag met de bekende machine-id&#39;s die `MachineId.matches()`.

`MachineId.matches()` voert een vergelijking van IDs uit om te bepalen of zij de zelfde machine vertegenwoordigen. Deze vergelijking is alleen handig als er een klein aantal machine-id&#39;s is die met elkaar moeten worden vergeleken. Bijvoorbeeld, als een gebruiker vijf machines binnen hun domein wordt toegestaan, kunt u het gegevensbestand naar machine IDs zoeken verbonden aan de gebruikersbenaming van de gebruiker en een kleine reeks gegevens verkrijgen om tegen te vergelijken.

>[!NOTE]
>
>Deze vergelijking is niet praktisch voor plaatsingen die anonieme toegang toestaan. In dergelijke gevallen `MachineId.getUniqueID()` kan worden gebruikt, maar deze id is niet hetzelfde als de gebruiker toegang heeft tot inhoud van zowel Flash- als Adobe AIR®-runtimes. De id blijft ook behouden als de gebruiker de vaste schijf opnieuw formatteert.

Meer informatie over `MachineToken.getMachineId()`en `MachineId.matches()`, zie de *Referentie voor Adobe Access API*.
