---
title: Eigenschappen van Java-systemen
description: Eigenschappen van Java-systemen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 0%

---

# Eigenschappen van Java-systemen {#java-system-properties}

De volgende twee eigenschappen van het Systeem van Java kunnen naar keuze worden geplaatst om de plaats van configuratie en logboekdossiers voor de vergunningsserver te wijzigen:

* *LicenseServer.ConfigRoot* — Map met alle configuratiebestanden voor de licentieserver. Raadpleeg voor meer informatie over de inhoud van deze bestanden &quot;[Configuratiebestanden van de licentieserver](../../aaxs-protected-streaming/aaxs-license-server-config-files/aaxs-configuration-directory-structure.md)&quot;. Indien niet ingesteld, is de standaardwaarde *CATALINA_BASE/licenseserver*.
* *LicenseServer.LogRoot* — Directory of the &quot;logs&quot; folder, where license server application logs are written. Indien niet ingesteld, is de standaardwaarde *LicenseServer.ConfigRoot*.

Als u [!DNL catalina.bat] of [!DNL catalina.sh] om Tomcat te starten, kunnen deze systeemeigenschappen eenvoudig worden ingesteld met de functie `JAVA_OPTS` omgevingsvariabele. Alle Java-opties die hier zijn ingesteld, worden gebruikt wanneer Tomcat wordt gestart. Stel bijvoorbeeld:

```
JAVA_OPTS=-DLicenseServer.ConfigRoot="absolute-path-to-config-folder" -DLicenseServer.LogRoot="absolute-path-to-log-folder"
```
