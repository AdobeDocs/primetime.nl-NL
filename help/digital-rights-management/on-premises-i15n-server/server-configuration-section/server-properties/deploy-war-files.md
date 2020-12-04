---
seo-title: WAR-bestanden implementeren
title: WAR-bestanden implementeren
uuid: 435a6a6e-c981-46fb-bca9-7f5f34eecd6a
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
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

