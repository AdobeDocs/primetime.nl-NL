---
title: Overzicht van Adobe Access Server for Protected Streaming implementeren
description: Overzicht van Adobe Access Server for Protected Streaming implementeren
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---


# Overzicht van Adobe Access Server voor beveiligde streaming implementeren {#deploying-the-adobe-access-server-for-protected-streaming-overview}

Voordat u de Adobe Access Server for Protected Streaming gaat implementeren, moet u controleren of u de versies van Java en Tomcat hebt geïnstalleerd die in de sectie Vereisten worden vermeld.

Het Adobe Access Server for Protected Streaming-pakket bevat [!DNL flashaccesserver.war]. Als u dit WAR-bestand wilt implementeren, kopieert u het naar de map [!DNL webapps] van Tomcat. Als u eerder het WAR-bestand hebt geïmplementeerd, moet u mogelijk de onverpakte WAR-map ( [!DNL flashaccessserver] in de map [!DNL webapps] van Tomcat) handmatig verwijderen. Om te voorkomen dat Tomcat WAR-bestanden uitpakt, bewerkt u het [!DNL server.xml]-bestand in de map [!DNL conf] van Tomcat en stelt u het `unpackWARs`-kenmerk in op `false`.

>[!NOTE]
>
>Als u Tomcat hebt geconfigureerd om [!DNL commons-logging.jar] op te nemen in het System classpath (niet vereist voor de Adobe Access Server voor Protected Streaming), moet het vastleggen van komma&#39;s zodanig worden geconfigureerd dat Log4J wordt gebruikt.

De server gebruikt optioneel een platformspecifieke bibliotheek ( [!DNL jsafe.dll] op Microsoft Windows of [!DNL libjsafe.so] op Linux) voor optimale prestaties. Kopieer de desbetreffende bibliotheek voor uw platform van [!DNL thirdparty/cryptoj/]*platform* naar een locatie die is opgegeven door de omgevingsvariabele `PATH` (of `LD_LIBRARY_PATH` in Linux).

>[!NOTE]
>
>De 64-bits versie moet alleen worden gebruikt als zowel het besturingssysteem als JDK 64-bits ondersteunen, anders de 32-bits versie gebruiken.

