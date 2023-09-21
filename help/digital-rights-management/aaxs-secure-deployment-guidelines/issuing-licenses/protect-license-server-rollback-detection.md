---
title: Terugdraaidetectie
description: Terugdraaidetectie
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 0%

---

# Terugdraaidetectie {#rollback-detection}

Als uw implementatie van de Toegang van de Adobe bedrijfsregels gebruikt die de cliënt vereisen om staat (bijvoorbeeld, het interval van het playbackvenster) te handhaven, adviseert de Adobe hoogst dat de server spoor van het terugschroeven van prijzen houdt en AIR of SWF lijst toestaat.

De rollback teller wordt verzonden naar de server in de meeste verzoeken van de cliënt. Als uw implementatie van de Toegang van de Adobe niet het terugschroeven van prijzen vereist, kan het worden genegeerd. Anders wordt door de Adobe aangeraden dat de server de willekeurige machine-id opslaat, verkregen met `MachineToken.getMachineId().getUniqueId()`—en de huidige tellerwaarde in een gegevensbestand. Voor meer informatie bij het verhogen van en het volgen van de rollback teller, zie ClientState in *API-naslaggids voor Adobe* en *Terugdraaidetectie* in *De Adobe Access SDK gebruiken voor het beveiligen van inhoud*.
