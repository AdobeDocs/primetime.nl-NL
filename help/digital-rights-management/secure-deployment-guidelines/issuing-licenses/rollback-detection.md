---
description: Als in uw implementatie van Adobe Primetime DRM bedrijfsregels worden gebruikt die de client vereisen om de status te behouden (bijvoorbeeld het interval voor het afspeelvenster), raadt Adobe aan dat de server de terugdraaiteller bijhoudt en dat AIR of SWF het weergeven van lijsten toestaat.
seo-description: Als in uw implementatie van Adobe Primetime DRM bedrijfsregels worden gebruikt die de client vereisen om de status te behouden (bijvoorbeeld het interval voor het afspeelvenster), raadt Adobe aan dat de server de terugdraaiteller bijhoudt en dat AIR of SWF het weergeven van lijsten toestaat.
seo-title: Terugdraaidetectie
title: Terugdraaidetectie
uuid: f161ed41-488a-478a-b6a8-468cf6d11e89
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---


# Terugdraaidetectie {#rollback-detection}

Als in uw implementatie van Adobe Primetime DRM bedrijfsregels worden gebruikt die de client vereisen om de status te behouden (bijvoorbeeld het interval voor het afspeelvenster), raadt Adobe aan dat de server de terugdraaiteller bijhoudt en dat AIR of SWF het weergeven van lijsten toestaat.

De rollback teller wordt verzonden naar de server in de meeste verzoeken van de cliënt. Als voor uw implementatie van Primetime DRM de terugdraaiteller niet nodig is, kan deze worden genegeerd. Anders raadt Adobe aan dat de server de willekeurige machine-id opslaat, die wordt verkregen met [MachineToken.getUniqueId()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getUniqueId()), en de huidige tellerwaarde in een database.

Voor meer informatie over hoe te om de het terugschroeven van prijzenteller te verhogen en te volgen, zie [CliëntState](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/ClientState.html) en de opsporing van het Terugschroeven van prijzen.