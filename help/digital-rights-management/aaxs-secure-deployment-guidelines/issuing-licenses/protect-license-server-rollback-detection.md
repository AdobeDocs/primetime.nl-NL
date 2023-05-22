---
title: Terugdraaidetectie
description: Terugdraaidetectie
copied-description: true
exl-id: 054d3634-5ce9-4a51-ac91-e6ae60a1fd6e
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 0%

---

# Terugdraaidetectie {#rollback-detection}

Als uw implementatie van Adobe Access bedrijfsregels gebruikt die van de client vereisen dat de status behouden blijft (bijvoorbeeld het interval van het afspeelvenster), raadt Adobe u ten zeerste aan dat de server de terugdraaiingsteller bijhoudt en AIR of SWF lijst toestaat.

De rollback teller wordt verzonden naar de server in de meeste verzoeken van de cliënt. Als uw implementatie van de Toegang van Adobe niet de het terugschroeven van prijzen vereist, kan het worden genegeerd. Anders raadt Adobe aan dat de server de willekeurige machine-id opslaat, verkregen met `MachineToken.getMachineId().getUniqueId()`—en de huidige tellerwaarde in een gegevensbestand. Voor meer informatie bij het verhogen van en het volgen van de rollback teller, zie ClientState in *Referentie voor Adobe Access API* en *Terugdraaidetectie* in *De SDK van Adobe Access gebruiken voor het beschermen van inhoud*.
