---
title: WAR-bestanden implementeren
description: WAR-bestanden implementeren
copied-description: true
exl-id: 9f491596-2a02-4a55-9baa-86407e389d20
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '64'
ht-degree: 0%

---

# WAR-bestanden implementeren{#deploy-the-war-files}

1. Kopieer het WAR-bestand naar Tomcat&#39;s [!DNL webapps] directory.

   * Individualisatieserver: [!DNL flashaccess.war]
   * Server voor sleutelgeneratie: [!DNL flashaccess-kgs.war]

1. Kopieer de [!DNL ROOT] map van het pakket dat door Adobe wordt geleverd naar de [!DNL webapps] directory.

   De Individualization-server moet ook de host zijn voor de [!DNL crossdomain.xml] bestand. (De [!DNL ROOT] map bevat de [!DNL crossdomain.xml] bestand; [!DNL ROOT] moet in alle hoofdletters staan.) Dit bestand is niet vereist op de server voor sleutelgeneratie.
