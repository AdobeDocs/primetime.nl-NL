---
seo-title: Problemen oplossen
title: Problemen oplossen
uuid: b7a41ea7-86c5-442c-b751-86a9055c5e35
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e
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
