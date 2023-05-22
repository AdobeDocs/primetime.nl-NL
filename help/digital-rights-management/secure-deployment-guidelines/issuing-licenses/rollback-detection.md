---
description: Als uw implementatie van Adobe Primetime DRM bedrijfsregels gebruikt die de client vereisen om de status te handhaven (bijvoorbeeld het interval van het afspeelvenster), raadt Adobe aan dat de server de terugdraaiingsteller bijhoudt en AIR of SWF lijst toestaat.
title: Terugdraaidetectie
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---


# Terugdraaidetectie {#rollback-detection}

Als uw implementatie van Adobe Primetime DRM bedrijfsregels gebruikt die de client vereisen om de status te handhaven (bijvoorbeeld het interval van het afspeelvenster), raadt Adobe aan dat de server de terugdraaiingsteller bijhoudt en AIR of SWF lijst toestaat.

De rollback teller wordt verzonden naar de server in de meeste verzoeken van de cliënt. Als voor uw implementatie van Primetime DRM de terugdraaiteller niet nodig is, kan deze worden genegeerd. Anders raadt Adobe aan dat de server de willekeurige machine-id opslaat, die wordt verkregen met [MachineToken.getUniqueId()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getUniqueId())en de huidige tellerwaarde in een database.

Voor meer informatie over hoe te om de het terugschroeven van prijzen te verhogen en te volgen, zie [ClientState](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/ClientState.html) en terugdraaidetectie.