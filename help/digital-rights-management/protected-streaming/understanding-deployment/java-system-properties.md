---
description: Er zijn verscheidene eigenschappen van het Systeem van Java die u op de vergunningsserver kunt vormen om de plaats van configuratie en logboekdossiers te controleren.
seo-description: Er zijn verscheidene eigenschappen van het Systeem van Java die u op de vergunningsserver kunt vormen om de plaats van configuratie en logboekdossiers te controleren.
seo-title: Eigenschappen van Java-systemen
title: Eigenschappen van Java-systemen
uuid: d8c72359-bf61-47e0-9cd5-b21225d5fe49
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Eigenschappen van Java-systemen{#java-system-properties}

Er zijn verscheidene eigenschappen van het Systeem van Java die u op de vergunningsserver kunt vormen om de plaats van configuratie en logboekdossiers te controleren.

U kunt de volgende eigenschappen van het Systeem van Java naar keuze vormen:

* *`LicenseServer.ConfigRoot`* — Naam van map die de configuratiebestanden voor de licentieserver bevat.

   Zie Configuratiebestanden *van de* licentieserver voor meer informatie over de inhoud van deze bestanden. Indien niet gevormd, is de standaardwaarde `CATALINA_BASE/licenseserver`.

* *LicenseServer.LogRoot* — Naam van de [!DNL logs] map waarin de logboekbestanden van de licentieservertoepassing zich bevinden. Als u de naam van deze map niet hebt gewijzigd, wordt de naam van deze map standaard geconfigureerd als *LicenseServer.ConfigRoot* .

Als u Tomcat gebruikt [!DNL catalina.bat] of [!DNL catalina.sh] dossier om te beginnen, kunt u de eigenschappen van het Systeem met de `JAVA_OPTS` omgevingsvariabele vormen. Alle Java-opties die u configureert, worden automatisch toegepast wanneer Tomcat wordt gestart.

U kunt bijvoorbeeld de `JAVA_OPTS` omgevingsvariabele als volgt configureren:

```
JAVA_OPTS=-DLicenseServer.ConfigRoot="absolute-path-to-config-folder" 
  -DLicenseServer.LogRoot="absolute-path-to-log-folder"
```

