---
seo-title: Het pad en het klassepad configureren
title: Het pad en het klassepad configureren
uuid: cf10fafa-125e-450c-83ae-60b990dab6b5
translation-type: tm+mt
source-git-commit: d8e4c39c297d69b154baf0b4d67cf09b5cf0a9d4

---


# Het pad en het klassepad configureren{#configure-the-path-and-classpath}

Het [!DNL flashaccess.war] bevat [!DNL jsafeWithNative.jar], de Crypto-J bibliotheek. De laatste vereist een extra native bibliotheek om cryptobewerkingen uit te voeren.

1. Voeg de native [!DNL jsafe] bibliotheek toe aan het pad.

   * **Linux /[!DNL libjsafe.so]-** De map die de map bevat, [!DNL libjsafe.so] moet zich op het pad bevinden (native Crypto-J-bibliotheken zijn ook beschikbaar voor andere platforms). Stel bijvoorbeeld in [!DNL libjsafe.so] op `LD_LIBRARY_PATH`.

   * **Windows /[!DNL jsafe.dll]-** De tegenhanger in Windows [!DNL libjsafe.so] is de juiste [!DNL jsafe.dll].
   Deze bibliotheken zijn beschikbaar in de [!DNL thirdparty] bibliotheekmap.
1. Plaats een van de [!DNL adobe-flashaccess-certs] jar-bestanden op het klassepad.

       Dit JAR-bestand is niet opgenomen in het WAR-bestand. moet u het uitdrukkelijk aan klassenpad toevoegen.
   
   * Ontwikkelingsservers - alleen gebruiken [!DNL adobe-flashaccess-certs-prerelease.jar].
   * Productieservers - alleen te gebruiken [!DNL adobe-flashaccess- certs.jar]

De distributie omvat een [!DNL shared] omslag die zowel het jar dossier als een pre-gevormd [!DNL AdobeInitial.properties] dossier omvat. Adobe raadt u aan deze items `common.loader` via het [!DNL catalina.properties] bestand toe te voegen. Bijvoorbeeld:

```
common.loader=<Any Pre-Existing Values>,${catalina.home}/shared/classes,${catalina.home}/shared/lib/*.jar
```


