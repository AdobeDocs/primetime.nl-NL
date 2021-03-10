---
title: Problemen oplossen
description: Problemen oplossen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '46'
ht-degree: 0%

---


# Problemen oplossen{#troubleshooting}

* Voor sommige oudere apparaten met API-niveau 10 of ouder kan Logcat het logapparaat niet openen vanwege een machtigingsprobleem. De volgende uitzondering wordt weergegeven: `java.lang.Exception: logcat returns error: Unable to open log device '/dev/log/main': Permission denied` **Oplossing:**

   1. Open [!DNL AndroidManifest.xml] onder het [!DNL CatalogActivity] project in de werkruimte.

   1. Voeg de volgende toestemming aan het [!DNL `AndroidManfest.xml`] dossier toe:

      ```
      android.permission.READ_LOGS
      ```
