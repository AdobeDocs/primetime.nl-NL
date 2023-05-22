---
title: De Adobe Primetime DRM-server implementeren voor beveiligde streaming
description: De Adobe Primetime DRM-server implementeren voor beveiligde streaming
copied-description: true
exl-id: 814c08e6-5d09-495b-b529-cedc9b9c02a7
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---

# De Adobe Primetime DRM-server implementeren voor beveiligde streaming{#deploying-the-adobe-primetime-drm-server-for-protected-streaming}

Voordat u de Adobe Primetime DRM-server kunt implementeren voor beveiligde streaming, moet u de versies van Java en Tomcat hebben geïnstalleerd zoals vermeld in het onderwerp Vereisten.

Het pakket Primetime DRM Server for Protected Streaming bevat [!DNL flashaccesserver.war]. Als u:

* Als u dit WAR-bestand wilt implementeren, moet u het kopiëren naar Tomcat&#39;s [!DNL webapps] directory.
* Als u het WAR-bestand al eerder hebt geïmplementeerd, moet u mogelijk de onverpakte WAR-map verwijderen ( [!DNL flashaccessserver] in Tomcat [!DNL webapps] directory).

* Als u wilt voorkomen dat Tomcat WAR-bestanden uitpakt, bewerkt u de opdracht [!DNL server.xml] bestand in Tomcat [!DNL conf] en configureer de `unpackWARs` kenmerk door deze in te stellen op `false`.

>[!NOTE]
>
>Als u Tomcat hebt geconfigureerd om [!DNL commons-logging.jar] op System classpath (niet vereist voor de Primetime DRM Server voor Beschermde Streaming) dan moet u komma-registreren vormen om Log4J te gebruiken.

De server gebruikt optioneel een platformspecifieke bibliotheek ( [!DNL jsafe.dll] in Microsoft Windows of [!DNL libjsafe.so] in Linux voor optimale prestaties. U kunt de desbetreffende bibliotheek voor uw platform kopiëren van [!DNL thirdparty/cryptoj/]*platform* naar een locatie die is opgegeven door de `PATH` omgevingsvariabele of `LD_LIBRARY_PATH` op Linux.

>[!NOTE]
>
>Gebruik de 64-bits versie alleen als zowel het besturingssysteem als de JDK 64-bits ondersteuning bieden. Anders moet u de 32-bits versie gebruiken.
