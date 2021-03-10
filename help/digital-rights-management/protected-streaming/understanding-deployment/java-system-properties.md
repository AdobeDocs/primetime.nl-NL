---
description: Er zijn verscheidene eigenschappen van het Systeem van Java die u op de vergunningsserver kunt vormen om de plaats van configuratie en logboekdossiers te controleren.
title: Eigenschappen van Java-systemen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---


# Java-systeemeigenschappen{#java-system-properties}

Er zijn verscheidene eigenschappen van het Systeem van Java die u op de vergunningsserver kunt vormen om de plaats van configuratie en logboekdossiers te controleren.

U kunt de volgende eigenschappen van het Systeem van Java naar keuze vormen:

* *`LicenseServer.ConfigRoot`* — Naam van map die de configuratiebestanden voor de licentieserver bevat.

   Zie *Configuratiebestanden van de licentieserver* voor meer informatie over de inhoud van deze bestanden. Indien niet gevormd, is de standaardwaarde `CATALINA_BASE/licenseserver`.

* *LicenseServer.LogRoot* : naam van de  [!DNL logs] map waarin de logboekbestanden van de licentieservertoepassing zich bevinden. Als u de naam van deze map niet hebt gewijzigd, wordt de naam van deze map standaard geconfigureerd als *LicenseServer.ConfigRoot*.

Als u het [!DNL catalina.bat] of [!DNL catalina.sh] dossier gebruikt om Tomcat te beginnen, kunt u de eigenschappen van het Systeem met `JAVA_OPTS` omgevingsvariabele vormen. Alle Java-opties die u configureert, worden automatisch toegepast wanneer Tomcat wordt gestart.

U kunt bijvoorbeeld de omgevingsvariabele `JAVA_OPTS` als volgt configureren:

```
JAVA_OPTS=-DLicenseServer.ConfigRoot="absolute-path-to-config-folder" 
  -DLicenseServer.LogRoot="absolute-path-to-log-folder"
```

