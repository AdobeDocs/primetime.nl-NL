---
title: De Adobe Primetime DRM-server implementeren voor beveiligde streaming
description: De Adobe Primetime DRM-server implementeren voor beveiligde streaming
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---


# De Adobe Primetime DRM-server implementeren voor beveiligde streaming{#deploying-the-adobe-primetime-drm-server-for-protected-streaming}

Voordat u de Adobe Primetime DRM-server kunt implementeren voor beveiligde streaming, moet u de versies van Java en Tomcat hebben geïnstalleerd zoals vermeld in het onderwerp Vereisten.

Het pakket Primetime DRM Server for Protected Streaming bevat [!DNL flashaccesserver.war]. Als u:

* Als u dit WAR-bestand wilt implementeren, moet u het kopiëren naar de map [!DNL webapps] van Tomcat.
* Als u eerder het WAR-bestand hebt geïmplementeerd, moet u mogelijk de onverpakte WAR-map verwijderen ( [!DNL flashaccessserver] in de map [!DNL webapps] van Tomcat).

* Als u wilt voorkomen dat Tomcat WAR-bestanden uitpakt, bewerkt u het [!DNL server.xml]-bestand in de map [!DNL conf] van Tomcat en configureert u het `unpackWARs`-kenmerk door dit in te stellen op `false`.

>[!NOTE]
>
>Als u Tomcat hebt geconfigureerd om [!DNL commons-logging.jar] op te nemen in het System classpath (niet vereist voor de Primetime DRM Server voor Protected Streaming), moet u komma&#39;s registreren configureren om Log4J te gebruiken.

De server gebruikt optioneel een platformspecifieke bibliotheek ( [!DNL jsafe.dll] op Microsoft Windows of [!DNL libjsafe.so] op Linux voor optimale prestaties. U kunt de desbetreffende bibliotheek voor uw platform kopiëren van [!DNL thirdparty/cryptoj/]*platform* naar een locatie die is opgegeven door de omgevingsvariabele `PATH` of `LD_LIBRARY_PATH` in Linux.

>[!NOTE]
>
>Gebruik de 64-bits versie alleen als zowel het besturingssysteem als de JDK 64-bits ondersteuning bieden. Anders moet u de 32-bits versie gebruiken.

