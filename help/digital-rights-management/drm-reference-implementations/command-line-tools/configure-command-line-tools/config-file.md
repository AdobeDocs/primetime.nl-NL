---
title: Ongeveer bevel-lijn hulpmiddelen configuratiedossiers
description: Ongeveer bevel-lijn hulpmiddelen configuratiedossiers
copied-description: true
exl-id: 0ec4917e-7c70-4b84-86ac-c34c8a522018
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 0%

---

# Ongeveer bevel-lijn hulpmiddelen configuratiedossiers{#about-command-line-tools-configuration-files}

De opdrachtregelprogramma&#39;s zoeken naar [!DNL flashaccesstools.properties] in de map waarin u de gereedschappen uitvoert. U kunt echter de opdracht `-c` als u een opdrachtregelprogramma uitvoert om een andere locatie voor de standaardinstelling op te geven [!DNL flashaccesstools.properties]. U kunt ook `-c` om een ander configuratiebestand op te geven.

De bevel-lijn hulpmiddelen configuratiedossiers gebruiken *Java, eigenschappenbestand* formaat waarvoor de volgende regels gelden:

* Escape-backslashes met een extra backslash.

   Op een Windows-computer kunt u bijvoorbeeld het [!DNL C:\credentials.pfx] bestand, moet u het als [!DNL C:\\credentials.pfx] of `C:/credentials.pfx`. Als u een bestand op een Windows-netwerkserver wilt opgeven, moet u `\\\\server\\folder\\filename.pfx`
* Alleen opnemen *Latin-1* tekens.

   Niet- gebruiken *Latin-1* tekens, moet u de juiste Unicode-escape-reeks gebruiken. U kunt optioneel de opdracht [!DNL native2ascii] aan de vermeldingen in het configuratiebestand (opgenomen in Java).
