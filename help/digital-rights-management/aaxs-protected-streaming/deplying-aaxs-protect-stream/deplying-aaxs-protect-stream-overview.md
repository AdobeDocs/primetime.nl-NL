---
title: Overzicht van Adobe Access Server for Protected Streaming implementeren
description: Overzicht van Adobe Access Server for Protected Streaming implementeren
copied-description: true
exl-id: fdefa13a-14ec-4301-ab39-2ceea830463d
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---

# Overzicht van Adobe Access Server for Protected Streaming implementeren {#deploying-the-adobe-access-server-for-protected-streaming-overview}

Voordat u de Adobe Access Server for Protected Streaming gaat implementeren, moet u controleren of u de versies van Java en Tomcat hebt geïnstalleerd die in de sectie Vereisten worden vermeld.

Het Adobe Access Server for Protected Streaming-pakket bevat [!DNL flashaccesserver.war]. Als u dit WAR-bestand wilt implementeren, kopieert u het naar Tomcat&#39;s [!DNL webapps] directory. Als u eerder het WAR-bestand hebt geïmplementeerd, moet u mogelijk de onverpakte WAR-map handmatig verwijderen ( [!DNL flashaccessserver] in Tomcat [!DNL webapps] directory). Als u wilt voorkomen dat Tomcat WAR-bestanden uitpakt, bewerkt u de opdracht [!DNL server.xml] bestand in Tomcat [!DNL conf] en stelt de `unpackWARs` kenmerk naar `false`.

>[!NOTE]
>
>Als u Tomcat hebt geconfigureerd om [!DNL commons-logging.jar] op het klassepad van het Systeem (niet vereist voor de Adobe Access Server voor Beschermde Streaming), moet het komma-registreren worden gevormd om Log4J te gebruiken.

De server gebruikt optioneel een platformspecifieke bibliotheek ( [!DNL jsafe.dll] in Microsoft Windows of [!DNL libjsafe.so] in Linux) voor optimale prestaties. Kopieer de juiste bibliotheek voor uw platform van [!DNL thirdparty/cryptoj/]*platform* naar een locatie die door de `PATH` omgevingsvariabele (of `LD_LIBRARY_PATH` in Linux).

>[!NOTE]
>
>De 64-bits versie moet alleen worden gebruikt als zowel het besturingssysteem als JDK 64-bits ondersteunen, anders de 32-bits versie gebruiken.
