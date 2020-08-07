---
seo-title: De Adobe Primetime DRM-server implementeren voor beveiligde streaming
title: De Adobe Primetime DRM-server implementeren voor beveiligde streaming
uuid: 83ef8237-0026-4677-b42b-ea4b6de19630
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---


# De Adobe Primetime DRM-server implementeren voor beveiligde streaming{#deploying-the-adobe-primetime-drm-server-for-protected-streaming}

Voordat u de Adobe Primetime DRM-server kunt implementeren voor beveiligde streaming, moet u de versies van Java en Tomcat hebben geïnstalleerd zoals vermeld in het onderwerp Vereisten.

Het pakket Primetime DRM Server for Protected Streaming bevat [!DNL flashaccesserver.war]. Als u:

* Als u dit WAR-bestand wilt implementeren, moet u het kopiëren naar de [!DNL webapps] directory van Tomcat.
* Als u eerder het WAR-bestand hebt geïmplementeerd, moet u mogelijk de onverpakte WAR-map ( [!DNL flashaccessserver] in de [!DNL webapps] map van Tomcat) verwijderen.

* Als u wilt voorkomen dat Tomcat WAR-bestanden uitpakt, bewerkt u het [!DNL server.xml] bestand in de [!DNL conf] directory van Tomcat en configureert u het `unpackWARs` kenmerk door dit in te stellen op `false`.

>[!NOTE]
>
>Als u Tomcat hebt gevormd om [!DNL commons-logging.jar] op het Klassepad van het Systeem (niet die voor de Server Primetime DRM voor Beschermde Streaming wordt vereist) te omvatten, dan moet u komma-registreren vormen om Log4J te gebruiken.

De server gebruikt eventueel een platformspecifieke bibliotheek ( [!DNL jsafe.dll] op Microsoft Windows of [!DNL libjsafe.so] op Linux voor optimale prestaties. U kunt de juiste bibliotheek voor uw platform kopiëren van [!DNL thirdparty/cryptoj/]*platform *naar een locatie die is opgegeven door de`PATH`omgevingsvariabele of`LD_LIBRARY_PATH`op Linux.

>[!NOTE]
>
>Gebruik de 64-bits versie alleen als zowel het besturingssysteem als de JDK 64-bits ondersteuning bieden. Anders moet u de 32-bits versie gebruiken.

