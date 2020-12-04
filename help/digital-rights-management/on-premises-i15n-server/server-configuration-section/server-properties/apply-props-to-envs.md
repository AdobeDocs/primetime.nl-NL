---
description: 'U moet servereigenschappen vormen om op uw milieu te wijzen. U kunt dit op een van de volgende manieren doen '
seo-description: 'U moet servereigenschappen vormen om op uw milieu te wijzen. U kunt dit op een van de volgende manieren doen '
seo-title: Eigenschappen toepassen op serveromgevingen
title: Eigenschappen toepassen op serveromgevingen
uuid: a1ee0d6c-b5e7-4689-b7c8-b155176faf1c
translation-type: tm+mt
source-git-commit: d8e4c39c297d69b154baf0b4d67cf09b5cf0a9d4
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---


# Eigenschappen toepassen op serveromgevingen{#apply-properties-to-server-environments}

U moet servereigenschappen vormen om op uw milieu te wijzen. U kunt dit op een van de volgende manieren doen:

* [!DNL flashaccess-i15n.properties] - Voorbeelden die in elk van de  [!DNL .war] bestanden zijn opgenomen

* [!DNL AdobeInitial.properties] - Voorbeeld in de  [!DNL /shared] map op de dvd

   U kunt dit bestand als volgt gebruiken om de eigenschappen die in het WAR-bestand zijn ingesteld, te overschrijven:

   1. De overschrijvende eigenschapswaarden instellen in [!DNL AdobeInitial.properties]
   1. Plaats [!DNL AdobeInitial.properties] op het klassepad.

   >[!NOTE]
   >
   >Adobe raadt u aan het [!DNL AdobeInitial.properties]-bestand te gebruiken, aangezien u hiermee WAR-bestanden van uw toepassing kunt bijwerken zonder het risico te lopen dat de vorige configuratie van eigenschappen die u in het [!DNL flashaccess-i15n.properties]-bestand hebt ingesteld, verloren gaat.

* Het Java System-eigenschapmechanisme.

U kunt afzonderlijke eigenschappen toepassen op deze specifieke serveromgevingen:

* *Ontwikkeling*
* *Staging*
* *Productie*

Met deze mogelijkheid kunt u hetzelfde WAR-bestand gebruiken voor alle serveromgevingen. Als u eigenschappen wilt toepassen op specifieke omgevingen, voegt u twee onderstrepingstekens (&#39; `__`&#39;) plus een van de volgende omgevingscodes toe aan de eigenschap *name*:

    * &quot;DEV&quot;
    * &quot;STAGE&quot;
    * &quot;PROD&quot;

<!--<a id="example_A7A58E3EE8DA4114B4F7A9EEB69D50CA"></a>-->

Stel bijvoorbeeld het logniveau in op `INFO` voor uw productie- en testservers en op `DEBUG` voor uw ontwikkelingsserver:

```
log.Level=INFO  
log.Level__DEV=DEBUG 
```

De server gebruikt deze zoekvolgorde voor eigenschappen:

1. `propertyname_environment` in  [!DNL AdobeInitial.properties]

1. `propertyname_environment` in  [!DNL flashaccess-15n.properties]

1. `propertyname_environment` in Java System-eigenschappen
1. `propertyname` in  [!DNL AdobeInitial.properties]

1. `propertyname` in  [!DNL flashaccess-15n.properties]

1. `propertyname` in Java System-eigenschappen

>[!NOTE]
>
>U moet de de milieunaam van de server als bezit van het Systeem van Java specificeren wanneer het beginnen van de server. Wanneer u bijvoorbeeld Tomcat start met [!DNL catalina.bat], stelt u de omgevingsvariabele `CATALINA_OPTS` als volgt in:
>-DENVIRONMENT_NAME=[ DEV | FASE | PROD ]
