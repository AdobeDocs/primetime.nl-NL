---
seo-title: Eigenschappen van Java-systemen
title: Eigenschappen van Java-systemen
uuid: ad1f3d9b-7d95-4e19-a0f8-fd7d4dd4dc32
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Eigenschappen van Java-systemen {#java-system-properties}

De volgende twee eigenschappen van het Systeem van Java kunnen naar keuze worden geplaatst om de plaats van configuratie en logboekdossiers voor de vergunningsserver te wijzigen:

* *LicenseServer.ConfigRoot* — Directory die alle configuratiebestanden voor de licentieserver bevat. Zie &quot;Configuratiebestanden[van de](../../aaxs-protected-streaming/aaxs-license-server-config-files/aaxs-configuration-directory-structure.md)licentieserver&quot; voor meer informatie over de inhoud van deze bestanden. Als niet geplaatst, is het gebrek *CATALINA_BASE/licenseserver*.
* *LicenseServer.LogRoot* — Directory of the &quot;logs&quot; folder, where license server application logs are written. Als deze niet is ingesteld, is de standaardwaarde *LicenseServer.ConfigRoot*.

Als u Tomcat gebruikt [!DNL catalina.bat] of [!DNL catalina.sh] om te beginnen, kunnen deze eigenschappen van het Systeem gemakkelijk worden geplaatst gebruikend de `JAVA_OPTS` omgevingsvariabele. Alle Java-opties die hier zijn ingesteld, worden gebruikt wanneer Tomcat wordt gestart. Stel bijvoorbeeld:

```
JAVA_OPTS=-DLicenseServer.ConfigRoot="absolute-path-to-config-folder" -DLicenseServer.LogRoot="absolute-path-to-log-folder"
```

