---
title: Ongeveer bevel-lijn hulpmiddelen configuratiedossiers
description: Ongeveer bevel-lijn hulpmiddelen configuratiedossiers
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 0%

---


# Ongeveer bevel-lijn hulpmiddelen configuratiedossiers{#about-command-line-tools-configuration-files}

De bevel-lijn hulpmiddelen zoeken [!DNL flashaccesstools.properties] in de folder waarin u de hulpmiddelen in werking stelt. U kunt echter de optie `-c` gebruiken wanneer u een opdrachtregelprogramma uitvoert om een andere locatie op te geven voor de standaardmap [!DNL flashaccesstools.properties]. U kunt `-c` ook gebruiken om een verschillend configuratiedossier te specificeren.

De bevel-lijn hulpmiddelen configuratiedossiers gebruiken het *formaat van het bezitsdossier van Java*, waarvoor de volgende regels van toepassing zijn:

* Escape-backslashes met een extra backslash.

   Op een Windows-computer moet u bijvoorbeeld [!DNL C:\credentials.pfx] of `C:/credentials.pfx` invoeren om het bestand [!DNL C:\\credentials.pfx] op te geven. Als u een bestand op een Windows-netwerkserver wilt opgeven, moet u `\\\\server\\folder\\filename.pfx` invoeren
* Alleen *Latin-1*-tekens opnemen.

   Als u niet-*Latin-1* tekens wilt gebruiken, moet u de juiste Unicode-escapereeks gebruiken. U kunt desgewenst het [!DNL native2ascii] hulpmiddel (inbegrepen met Java) op uw ingangen van het configuratiedossier toepassen.
