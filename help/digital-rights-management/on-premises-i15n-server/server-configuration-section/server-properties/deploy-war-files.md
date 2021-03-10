---
title: WAR-bestanden implementeren
description: WAR-bestanden implementeren
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '64'
ht-degree: 0%

---


# WAR-bestanden implementeren{#deploy-the-war-files}

1. Kopieer het WAR-bestand naar de map [!DNL webapps] van Tomcat.

   * Individualisatieserver: [!DNL flashaccess.war]
   * Server voor sleutelgeneratie: [!DNL flashaccess-kgs.war]

1. Kopieer de map [!DNL ROOT] van het pakket dat door Adobe wordt geleverd naar de map [!DNL webapps].

   De Individualization-server moet ook het [!DNL crossdomain.xml]-bestand hosten. (De map [!DNL ROOT] bevat het bestand [!DNL crossdomain.xml]; [!DNL ROOT] moet zich in alle hoofdletters bevinden.) Dit bestand is niet vereist op de server voor sleutelgeneratie.

