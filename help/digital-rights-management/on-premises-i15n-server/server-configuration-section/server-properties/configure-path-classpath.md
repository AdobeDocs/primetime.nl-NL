---
seo-title: Het pad en het klassepad configureren
title: Het pad en het klassepad configureren
uuid: cf10fafa-125e-450c-83ae-60b990dab6b5
translation-type: tm+mt
source-git-commit: d8e4c39c297d69b154baf0b4d67cf09b5cf0a9d4
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 1%

---


# Vorm de Weg en Classpath{#configure-the-path-and-classpath}

[!DNL flashaccess.war] bevat [!DNL jsafeWithNative.jar], wat de bibliotheek Crypto-J is. De laatste vereist een extra native bibliotheek om cryptobewerkingen uit te voeren.

1. Voeg de native [!DNL jsafe]-bibliotheek toe aan het pad.

   * **Linux /  [!DNL libjsafe.so] -** De map met de map  [!DNL libjsafe.so] moet zich op het pad bevinden (native Crypto-J-bibliotheken zijn ook beschikbaar voor andere platforms). Stel bijvoorbeeld [!DNL libjsafe.so] in op `LD_LIBRARY_PATH`.

   * **Windows /  [!DNL jsafe.dll] -** De tegenhanger in Windows  [!DNL libjsafe.so] is de juiste  [!DNL jsafe.dll].
   Deze bibliotheken zijn beschikbaar in de bibliotheekmap [!DNL thirdparty].
1. Plaats één van [!DNL adobe-flashaccess-certs] jar dossiers op classpath.

       Dit JAR-bestand is niet opgenomen in het WAR-bestand. moet u het uitdrukkelijk aan klassenpad toevoegen.
   
   * Ontwikkelingsservers - alleen [!DNL adobe-flashaccess-certs-prerelease.jar] gebruiken.
   * Productieservers - alleen [!DNL adobe-flashaccess- certs.jar] gebruiken

De distributie omvat een [!DNL shared] omslag die zowel het jar dossier evenals een vooraf gevormd [!DNL AdobeInitial.properties] dossier omvat. Adobe raadt u aan deze items via het [!DNL catalina.properties]-bestand toe te voegen aan het `common.loader`-bestand. Bijvoorbeeld:

```
common.loader=<Any Pre-Existing Values>,${catalina.home}/shared/classes,${catalina.home}/shared/lib/*.jar
```


