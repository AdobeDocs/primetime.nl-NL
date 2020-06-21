---
seo-title: Terugdraaidetectie
title: Terugdraaidetectie
uuid: fc80c98f-7ee5-414b-87fe-0dbb8d4f6019
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---


# Terugdraaidetectie{#rollback-detection}

Als in uw implementatie van Adobe Access bedrijfsregels worden gebruikt die vereisen dat de client de status behoudt (bijvoorbeeld het interval voor het afspeelvenster), raadt Adobe u ten zeerste aan dat de server de terugdraaiteller bijhoudt en AIR- of SWF-code gebruikt.

De rollback teller wordt verzonden naar de server in de meeste verzoeken van de cliënt. Als voor uw implementatie van Adobe Access de terugdraaiteller niet nodig is, kan deze worden genegeerd. Als dat niet het geval is, raadt Adobe de server aan de willekeurige machine-id op te slaan (verkregen met gebruik `MachineToken.getMachineId().getUniqueId()`) en de huidige tellerwaarde op te slaan in een database. Zie ClientState in de *Adobe Access API-naslaggids* en de *terugdraaidetectie* in de SDK van Adobe Access *gebruiken voor het beveiligen van inhoud* voor meer informatie over het verhogen en bijhouden van de terugdraaiteller.
