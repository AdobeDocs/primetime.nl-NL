---
seo-title: Aantal machines bij afgifte van vergunningen
title: Aantal machines bij afgifte van vergunningen
uuid: d57f8b0b-0363-4b26-bd71-76f4abe5b68f
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Aantal machines bij afgifte van vergunningen{#machine-count-when-issuing-licenses}

Als de bedrijfsregels vereisen dat het aantal machines voor een gebruiker wordt gevolgd, moet de Server van de Vergunning of de Server van het Domein machine IDs opslaan verbonden aan de gebruiker. De meest robuuste manier om machine IDs te volgen is de waarde op te slaan die door de `MachineId.getBytes()` methode in een gegevensbestand is teruggekeerd. Wanneer een nieuwe aanvraag wordt ingediend, vergelijkt u de machine-id in de aanvraag met de bekende machine-id&#39;s die `MachineId.matches()`worden gebruikt.

`MachineId.matches()` voert een vergelijking van IDs uit om te bepalen of zij de zelfde machine vertegenwoordigen. Deze vergelijking is alleen handig als er een klein aantal machine-id&#39;s is die met elkaar moeten worden vergeleken. Bijvoorbeeld, als een gebruiker vijf machines binnen hun domein wordt toegestaan, kunt u het gegevensbestand naar machine IDs zoeken verbonden aan de gebruikersbenaming van de gebruiker en een kleine reeks gegevens verkrijgen om tegen te vergelijken.

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>Deze vergelijking is niet praktisch voor plaatsingen die anonieme toegang toestaan. In dergelijke gevallen `MachineId.getUniqueID()` kan deze id echter wel worden gebruikt als de gebruiker toegang krijgt tot inhoud van zowel Flash- als Adobe AIR®-runtimes. De id blijft ook behouden als de gebruiker de vaste schijf opnieuw formatteert.

Zie de `MachineToken.getMachineId()`Adobe Access API-naslaggids voor `MachineId.matches()`meer informatie over *en* informatie.
