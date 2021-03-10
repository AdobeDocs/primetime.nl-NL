---
title: Eigenschappen van Java-systemen
description: Eigenschappen van Java-systemen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 0%

---


# Eigenschappen van Java-systemen {#java-system-properties}

De volgende twee eigenschappen van het Systeem van Java kunnen naar keuze worden geplaatst om de plaats van configuratie en logboekdossiers voor de vergunningsserver te wijzigen:

* *LicenseServer.ConfigRoot* — Directory met alle configuratiebestanden voor de licentieserver. Voor details op de inhoud van deze dossiers, zie &quot;[de configuratiedossiers van de server van de vergunning](../../aaxs-protected-streaming/aaxs-license-server-config-files/aaxs-configuration-directory-structure.md)&quot;. Als niet ingesteld, is de standaardwaarde *CATALINA_BASE/licenseserver*.
* *LicenseServer.LogRoot* — Directory of the &quot;logs&quot; folder, where license server application logs are written. Als deze niet is ingesteld, is de standaardwaarde *LicenseServer.ConfigRoot*.

Als u [!DNL catalina.bat] of [!DNL catalina.sh] gebruikt om Tomcat te beginnen, kunnen deze eigenschappen van het Systeem gemakkelijk worden geplaatst gebruikend `JAVA_OPTS` omgevingsvariabele. Alle Java-opties die hier zijn ingesteld, worden gebruikt wanneer Tomcat wordt gestart. Stel bijvoorbeeld:

```
JAVA_OPTS=-DLicenseServer.ConfigRoot="absolute-path-to-config-folder" -DLicenseServer.LogRoot="absolute-path-to-log-folder"
```

