---
title: Vereisten voor het gebruik van Primetime DRM Key Server
description: Vereisten voor het gebruik van Primetime DRM Key Server
copied-description: true
exl-id: a5c0db05-15a1-45b0-abb9-11f857f5e34c
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---

# Inleiding {#introduction}

Primetime DRM Key Server is een multi-huurder Key Server voor externe iOS en/of Xbox 360-sleutellevering. Als Remote Key Delivery is ingeschakeld in een beleid voor iOS, moet een Primetime DRM Key Server worden geïmplementeerd om het afspelen van inhoud op iOS-clients mogelijk te maken. Primetime DRM Key Server is altijd vereist voor Xbox 360.

## Vereisten voor het gebruik van Primetime DRM Key Server {#requirements-for-using-primetime-drm-key-server}

De minimale vereisten voor het gebruik van Primetime DRM Key Server zijn:

* [Java JRE 1.6](https://www.oracle.com/technetwork/java/javase/downloads/index.html) of hoger. (Als u HSM wilt gebruiken in Windows 64-bits, is JRE 8 vereist)

   >[!NOTE]
   >
   >64-bits PKCS11 wordt nu ondersteund in OpenJDK 8: [https://openjdk.java.net/jeps/131](https://openjdk.java.net/jeps/131)en Oracle JDK: [https://bugs.java.com/bugdatabase/view_bug.do?bug_id=6880559](https://bugs.java.com/bugdatabase/view_bug.do?bug_id=6880559).

* [Apache Tomcat 7](https://tomcat.apache.org)
* Door Adobe afgegeven referenties
* Credentials uitgegeven door Microsoft (voor Xbox 360-clients)
