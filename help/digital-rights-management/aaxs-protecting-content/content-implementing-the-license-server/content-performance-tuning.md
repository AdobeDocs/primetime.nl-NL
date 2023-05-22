---
title: Prestaties afstemmen
description: Prestaties afstemmen
copied-description: true
exl-id: f6b2338e-a209-4881-a599-ded5f1498daf
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---

# Prestaties afstemmen{#performance-tuning}

Gebruik de volgende tips om de prestaties te verbeteren:

* Het gebruiken van een netwerk HSM kan beduidend langzamer zijn dan het gebruiken van direct-verbonden HSM.
* Voor betere prestaties, kunt u naar keuze inheemse steun voor cryptografische verrichtingen toelaten door de platform-specifieke bibliotheken op te stellen die in de &quot;derde/cryptoj&quot;omslag van SDK worden gevestigd. Als u native ondersteuning wilt inschakelen, voegt u de bibliotheek voor uw platform (jsafe.dll voor Windows of libjsafe.so voor Linux) toe aan het pad.

   >[!NOTE]
   >
   >Als u meerdere webtoepassingen uitvoert in hetzelfde Tomcat-exemplaar en als u `jsafe.dll` alleen de eerste webtoepassing die het pad laadt, kan het pad `jsafe.dll` bibliotheek. Daarom krijgt alleen de eerste webtoepassing het voordeel van de native ondersteuning. In dergelijke gevallen, om de prestaties van alle Webtoepassingen te verbeteren, plaats `cryptoj.jar`buiten het WAR-bestand. In het dialoogvenster `<tomcat_installation_folder>/lib` directory.

* Een 64-bits besturingssysteem, zoals de 64-bits versie van Red Hat® of Windows, biedt veel betere prestaties dan een 32-bits besturingssysteem.
