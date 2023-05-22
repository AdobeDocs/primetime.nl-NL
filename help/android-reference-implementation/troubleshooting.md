---
title: Problemen oplossen
description: Problemen oplossen
copied-description: true
exl-id: 618b1e19-d25d-435d-b118-b43455bde974
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '46'
ht-degree: 0%

---

# Problemen oplossen{#troubleshooting}

* Voor sommige oudere apparaten met API-niveau 10 of ouder kan Logcat het logapparaat niet openen vanwege een machtigingsprobleem. De volgende uitzondering wordt weergegeven: `java.lang.Exception: logcat returns error: Unable to open log device '/dev/log/main': Permission denied` **Oplossing:**

   1. Openen [!DNL AndroidManifest.xml] onder de [!DNL CatalogActivity] in de werkruimte.

   1. Voeg de volgende machtigingen toe aan de [!DNL `AndroidManfest.xml`] bestand:

      ```
      android.permission.READ_LOGS
      ```
