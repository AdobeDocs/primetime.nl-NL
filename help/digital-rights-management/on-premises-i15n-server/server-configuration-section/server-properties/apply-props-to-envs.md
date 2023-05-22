---
description: U moet servereigenschappen vormen om op uw milieu te wijzen. U kunt dit op een van de volgende manieren doen
title: Eigenschappen toepassen op serveromgevingen
exl-id: 0c78011a-e8c8-43a8-8c2d-a5c4ed54a8d7
source-git-commit: 0019a95fa9ca6d21249533d559ce844897ab67cf
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# Eigenschappen toepassen op serveromgevingen{#apply-properties-to-server-environments}

U moet servereigenschappen vormen om op uw milieu te wijzen. U kunt dit op een van de volgende manieren doen:

* [!DNL flashaccess-i15n.properties] - Monsters die in elk van de [!DNL .war] bestanden

* [!DNL AdobeInitial.properties] - Monster in de [!DNL /shared] map op de dvd

   U kunt dit bestand als volgt gebruiken om de eigenschappen die in het WAR-bestand zijn ingesteld, te overschrijven:

   1. De waarden van de eigenschap voor overschrijven instellen in [!DNL AdobeInitial.properties]
   1. Plaatsen [!DNL AdobeInitial.properties] op het klassepad.

   >[!NOTE]
   >
   >Adobe raadt u aan gebruik te maken van de [!DNL AdobeInitial.properties] bestand, omdat u hiermee WAR-bestanden van uw toepassing kunt bijwerken zonder het risico te lopen dat de vorige configuratie van eigenschappen die u in het dialoogvenster hebt ingesteld, verloren gaan [!DNL flashaccess-i15n.properties] bestand.

* Het Java System-eigenschapmechanisme.

U kunt afzonderlijke eigenschappen toepassen op deze specifieke serveromgevingen:

* *Ontwikkeling*
* *Staging*
* *Productie*

Met deze mogelijkheid kunt u hetzelfde WAR-bestand gebruiken voor alle serveromgevingen. Als u eigenschappen wilt toepassen op specifieke omgevingen, voegt u twee onderstrepingstekens toe (&#39; `__`&#39;) plus een van de volgende omgevingscodes aan de eigenschap *name*:

* `DEV`
* `STAGE`
* `PROD`

<!--<a id="example_A7A58E3EE8DA4114B4F7A9EEB69D50CA"></a>-->

Als u bijvoorbeeld het logniveau wilt instellen op `INFO` voor uw productie- en staging-servers en voor `DEBUG` voor uw ontwikkelingsserver:

```
log.Level=INFO  
log.Level__DEV=DEBUG 
```

De server gebruikt deze zoekvolgorde voor eigenschappen:

1. `propertyname_environment` in [!DNL AdobeInitial.properties]

1. `propertyname_environment` in [!DNL flashaccess-15n.properties]

1. `propertyname_environment` in Java System-eigenschappen
1. `propertyname` in [!DNL AdobeInitial.properties]

1. `propertyname` in [!DNL flashaccess-15n.properties]

1. `propertyname` in Java System-eigenschappen

>[!NOTE]
>
>U moet de de milieunaam van de server als bezit van het Systeem van Java specificeren wanneer het beginnen van de server. Bijvoorbeeld wanneer u Tomcat start met [!DNL catalina.bat]stelt u de `CATALINA_OPTS` omgevingsvariabele, als hieronder:
>-DENVIRONMENT_NAME=[ DEV | FASE | PROD ]
