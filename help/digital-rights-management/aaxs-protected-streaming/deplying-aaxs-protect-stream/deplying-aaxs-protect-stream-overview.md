---
seo-title: Overzicht van Adobe Access Server for Protected Streaming implementeren
title: Overzicht van Adobe Access Server for Protected Streaming implementeren
uuid: 48a7e452-520a-4ff8-97e9-11210221256d
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---


# Overzicht van Adobe Access Server for Protected Streaming implementeren {#deploying-the-adobe-access-server-for-protected-streaming-overview}

Voordat u de Adobe Access Server for Protected Streaming gaat implementeren, moet u controleren of u de versies van Java en Tomcat hebt geïnstalleerd die in de sectie Vereisten worden vermeld.

Het Adobe Access Server for Protected Streaming-pakket bevat [!DNL flashaccesserver.war]. Als u dit WAR-bestand wilt implementeren, kopieert u het naar de [!DNL webapps] directory van Tomcat. Als u eerder het WAR-bestand hebt geïmplementeerd, moet u mogelijk de onverpakte WAR-map ( [!DNL flashaccessserver] in de [!DNL webapps] map van Tomcat) handmatig verwijderen. Als u wilt voorkomen dat Tomcat WAR-bestanden uitpakt, bewerkt u het [!DNL server.xml] bestand in de [!DNL conf] directory van Tomcat en stelt u het `unpackWARs` kenmerk in op `false`.

>[!NOTE]
>
>Als u Tomcat zodanig hebt geconfigureerd dat deze wordt opgenomen [!DNL commons-logging.jar] in het klassepad van het systeem (niet vereist voor de Adobe Access Server voor Beveiligde streaming), moet het vastleggen van komma&#39;s zo worden geconfigureerd dat Log4J wordt gebruikt.

De server gebruikt eventueel een platformspecifieke bibliotheek ( [!DNL jsafe.dll] op Microsoft Windows of [!DNL libjsafe.so] op Linux) voor optimale prestaties. Kopieer de desbetreffende bibliotheek voor uw platform van [!DNL thirdparty/cryptoj/]*platform *naar een locatie die door de`PATH`omgevingsvariabele (of`LD_LIBRARY_PATH`in Linux) wordt opgegeven.

>[!NOTE]
>
>De 64-bits versie moet alleen worden gebruikt als zowel het besturingssysteem als JDK 64-bits ondersteunen, anders de 32-bits versie gebruiken.

