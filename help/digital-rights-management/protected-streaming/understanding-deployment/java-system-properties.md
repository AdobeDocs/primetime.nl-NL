---
description: Er zijn verscheidene eigenschappen van het Systeem van Java die u op de vergunningsserver kunt vormen om de plaats van configuratie en logboekdossiers te controleren.
title: Eigenschappen van Java-systemen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# Eigenschappen van Java-systemen{#java-system-properties}

Er zijn verscheidene eigenschappen van het Systeem van Java die u op de vergunningsserver kunt vormen om de plaats van configuratie en logboekdossiers te controleren.

U kunt de volgende eigenschappen van het Systeem van Java naar keuze vormen:

* *`LicenseServer.ConfigRoot`* — Naam van map die de configuratiebestanden voor de licentieserver bevat.

  Zie *Configuratiebestanden van de licentieserver* voor meer informatie over de inhoud van deze bestanden. Indien niet geconfigureerd, is de standaardwaarde `CATALINA_BASE/licenseserver`.

* *LicenseServer.LogRoot* — Naam van de [!DNL logs] map waarin de logbestanden van de licentieservertoepassing zich bevinden. Als u de naam van deze map niet hebt gewijzigd, wordt de naam van deze map geconfigureerd als *LicenseServer.ConfigRoot* standaard.

Als u het [!DNL catalina.bat] of [!DNL catalina.sh] om Tomcat te starten, kunt u de systeemeigenschappen configureren met de `JAVA_OPTS` omgevingsvariabele. Alle Java-opties die u configureert, worden automatisch toegepast wanneer Tomcat wordt gestart.

U kunt bijvoorbeeld de `JAVA_OPTS` omgevingsvariabele, als hieronder:

```
JAVA_OPTS=-DLicenseServer.ConfigRoot="absolute-path-to-config-folder" 
  -DLicenseServer.LogRoot="absolute-path-to-log-folder"
```
