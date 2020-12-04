---
description: 'null'
seo-description: 'null'
seo-title: Ongeveer bevel-lijn hulpmiddelen configuratiedossiers
title: Ongeveer bevel-lijn hulpmiddelen configuratiedossiers
uuid: 8220921f-1fe9-439c-8134-dc16c2e3601b
translation-type: tm+mt
source-git-commit: 0143d98185b9a63ef978aba18e2f3c8728333155
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 0%

---


# Ongeveer bevel-lijn hulpmiddelen configuratiedossiers{#about-command-line-tools-configuration-files}

De bevel-lijn hulpmiddelen zoeken [!DNL flashaccesstools.properties] in de folder waarin u de hulpmiddelen in werking stelt. U kunt echter de optie `-c` gebruiken wanneer u een opdrachtregelprogramma uitvoert om een andere locatie op te geven voor de standaardmap [!DNL flashaccesstools.properties]. U kunt `-c` ook gebruiken om een verschillend configuratiedossier te specificeren.

De bevel-lijn hulpmiddelen configuratiedossiers gebruiken het *formaat van het bezitsdossier van Java*, waarvoor de volgende regels van toepassing zijn:

* Escape-backslashes met een extra backslash.

   Op een Windows-computer moet u bijvoorbeeld [!DNL C:\credentials.pfx] of `C:/credentials.pfx` invoeren om het bestand &lt;a0/> op te geven. [!DNL C:\\credentials.pfx] Als u een bestand op een Windows-netwerkserver wilt opgeven, moet u `\\\\server\\folder\\filename.pfx` invoeren
* Alleen *Latin-1*-tekens opnemen.

   Als u niet-*Latin-1* tekens wilt gebruiken, moet u de juiste Unicode-escapereeks gebruiken. U kunt desgewenst het [!DNL native2ascii] hulpmiddel (inbegrepen met Java) op uw ingangen van het configuratiedossier toepassen.
