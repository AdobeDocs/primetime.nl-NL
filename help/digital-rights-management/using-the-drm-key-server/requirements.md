---
seo-title: Vereisten voor het gebruik van Primetime DRM Key Server
title: Vereisten voor het gebruik van Primetime DRM Key Server
uuid: 769f9e10-7a3e-4a38-b30d-18181b666bb4
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5
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
   >64-bits PKCS11 wordt nu ondersteund in OpenJDK 8: [https://openjdk.java.net/jeps/131](https://openjdk.java.net/jeps/131) en Oracle JDK: [https://bugs.java.com/bugdatabase/view_bug.do?bug_id=6880559](https://bugs.java.com/bugdatabase/view_bug.do?bug_id=6880559).

* [Apache Tomcat 7](https://tomcat.apache.org)
* Door Adobe afgegeven referenties
* Referenties uitgegeven door Microsoft (voor Xbox 360-clients)