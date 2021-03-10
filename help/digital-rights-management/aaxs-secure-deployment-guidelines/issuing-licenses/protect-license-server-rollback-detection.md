---
title: Terugdraaidetectie
description: Terugdraaidetectie
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 0%

---


# Terugdraaidetectie {#rollback-detection}

Als uw implementatie van Adobe Access bedrijfsregels gebruikt die van de client vereisen dat de status behouden blijft (bijvoorbeeld het interval van het afspeelvenster), raadt Adobe u ten zeerste aan dat de server de terugdraaiingsteller bijhoudt en AIR of SWF gebruikt om een lijst toe te staan.

De rollback teller wordt verzonden naar de server in de meeste verzoeken van de cliënt. Als uw implementatie van de Toegang van Adobe niet de het terugschroeven van prijzen vereist, kan het worden genegeerd. Anders, adviseert Adobe dat de server willekeurige machine ID-verkregen gebruikend `MachineToken.getMachineId().getUniqueId()`-en de huidige tegenwaarde in een gegevensbestand opslaat. Zie ClientState in *Referentie voor API voor Adobe Access* en *Terugdraaidetectie* in *De SDK voor Adobe Access gebruiken om inhoud te beschermen* voor meer informatie over het verhogen en bijhouden van de terugdraaiteller.
