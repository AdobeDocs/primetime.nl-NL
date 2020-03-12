---
seo-title: WAR-bestanden implementeren
title: WAR-bestanden implementeren
uuid: 435a6a6e-c981-46fb-bca9-7f5f34eecd6a
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# WAR-bestanden implementeren{#deploy-the-war-files}

1. Kopieer het WAR-bestand naar de [!DNL webapps] directory van Tomcat.

   * Individualisatieserver: [!DNL flashaccess.war]
   * Server voor sleutelgeneratie: [!DNL flashaccess-kgs.war]

1. Kopieer de [!DNL ROOT] map uit het pakket dat door Adobe wordt geleverd naar de [!DNL webapps] map.

   De Individualization-server moet het [!DNL crossdomain.xml] bestand ook hosten. (De map [!DNL ROOT] bevat het [!DNL crossdomain.xml] bestand; [!DNL ROOT] moet in alle hoofdletters staan.) Dit bestand is niet vereist op de server voor sleutelgeneratie.

