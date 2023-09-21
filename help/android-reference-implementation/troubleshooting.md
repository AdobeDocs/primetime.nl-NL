---
title: Problemen oplossen
description: Problemen oplossen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '46'
ht-degree: 0%

---

# Problemen oplossen{#troubleshooting}

* Voor sommige oudere apparaten met API-niveau 10 of ouder kan Logcat het logapparaat niet openen vanwege een machtigingsprobleem. De volgende uitzondering wordt weergegeven: `java.lang.Exception: logcat returns error: Unable to open log device '/dev/log/main': Permission denied` **Oplossing:**

   1. Openen [!DNL AndroidManifest.xml] onder de [!DNL CatalogActivity] project in de werkruimte.

   1. Voeg de volgende machtigingen toe aan de [!DNL `AndroidManfest.xml`] bestand:

      ```
      android.permission.READ_LOGS
      ```
