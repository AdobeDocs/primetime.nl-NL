---
seo-title: Prestaties afstemmen
title: Prestaties afstemmen
uuid: bb5321a0-48ef-49cb-aaf0-00d7ab9562fe
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Prestaties afstemmen{#performance-tuning}

Gebruik de volgende tips om de prestaties te verbeteren:

* Het gebruiken van een netwerk HSM kan beduidend langzamer zijn dan het gebruiken van direct-verbonden HSM.
* Voor betere prestaties, kunt u naar keuze inheemse steun voor cryptografische verrichtingen toelaten door de platform-specifieke bibliotheken op te stellen die in de &quot;derde/cryptoj&quot;omslag van SDK worden gevestigd. Als u native ondersteuning wilt inschakelen, voegt u de bibliotheek voor uw platform (jsafe.dll voor Windows of libjsafe.so voor Linux) toe aan het pad.

   >[!NOTE] {class=&quot;- topic/note &quot;}
   >
   >Als u meerdere webtoepassingen uitvoert in dezelfde Tomcat-instantie en `jsafe.dll` het pad heeft, kan alleen de eerste webtoepassing die de `jsafe.dll` bibliotheek laadt, deze laden. Daarom krijgt alleen de eerste webtoepassing het voordeel van de native ondersteuning. Plaats in dergelijke gevallen `cryptoj.jar`buiten het WAR-bestand om de prestaties van alle webtoepassingen te verbeteren. Bijvoorbeeld in de `<tomcat_installation_folder>/lib` map.

* Een 64-bits besturingssysteem, zoals de 64-bits versie van Red Hat® of Windows, biedt veel betere prestaties dan een 32-bits besturingssysteem.

