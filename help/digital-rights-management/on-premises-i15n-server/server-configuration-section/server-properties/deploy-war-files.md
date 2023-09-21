---
title: WAR-bestanden implementeren
description: WAR-bestanden implementeren
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '64'
ht-degree: 0%

---

# WAR-bestanden implementeren{#deploy-the-war-files}

1. Het WAR-bestand kopiëren naar Tomcat [!DNL webapps] directory.

   * Individualisatieserver: [!DNL flashaccess.war]
   * Server voor sleutelgeneratie: [!DNL flashaccess-kgs.war]

1. De [!DNL ROOT] map van het pakket dat door de Adobe aan de [!DNL webapps] directory.

   De Individualization-server moet ook de host zijn voor de [!DNL crossdomain.xml] bestand. (De [!DNL ROOT] map bevat de [!DNL crossdomain.xml] bestand; [!DNL ROOT] moet in alle hoofdletters staan.) Dit bestand is niet vereist op de server voor sleutelgeneratie.
