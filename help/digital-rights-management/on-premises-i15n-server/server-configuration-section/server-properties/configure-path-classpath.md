---
title: Het pad en het klassepad configureren
description: Het pad en het klassepad configureren
copied-description: true
exl-id: e6e9f837-4e3d-43e1-971d-3fa0ccaeff39
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---

# Het pad en het klassepad configureren{#configure-the-path-and-classpath}

De [!DNL flashaccess.war] contains [!DNL jsafeWithNative.jar], de Crypto-J bibliotheek. De laatste vereist een extra native bibliotheek om cryptobewerkingen uit te voeren.

1. Native toevoegen [!DNL jsafe] bibliotheek naar uw pad.

   * **Linux / [!DNL libjsafe.so] -** De map met [!DNL libjsafe.so] moet op de Weg (de inheemse bibliotheken Crypto-J zijn ook beschikbaar voor andere platforms) zijn. Stel bijvoorbeeld [!DNL libjsafe.so] op `LD_LIBRARY_PATH`.

   * **Windows / [!DNL jsafe.dll] -** De tegenhanger van Windows naar [!DNL libjsafe.so] is [!DNL jsafe.dll].
   Deze bibliotheken zijn beschikbaar in het dialoogvenster [!DNL thirdparty] bibliotheekmap.
1. Een van de [!DNL adobe-flashaccess-certs] jar files on the classpath.

       Dit JAR-bestand is niet opgenomen in het WAR-bestand. moet u het uitdrukkelijk aan klassenpad toevoegen.
   
   * Ontwikkelingsservers - alleen te gebruiken [!DNL adobe-flashaccess-certs-prerelease.jar].
   * Productieservers - alleen te gebruiken [!DNL adobe-flashaccess- certs.jar]

De distributie omvat een [!DNL shared] map die zowel het jar-bestand als een vooraf geconfigureerde map bevat [!DNL AdobeInitial.properties] bestand. Adobe raadt u aan deze items toe te voegen aan de `common.loader` via de [!DNL catalina.properties] bestand. Bijvoorbeeld:

```
common.loader=<Any Pre-Existing Values>,${catalina.home}/shared/classes,${catalina.home}/shared/lib/*.jar
```
