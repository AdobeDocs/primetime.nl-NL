---
title: Wachtwoorden voorbereiden met Java
description: Wachtwoorden voorbereiden met Java
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '22'
ht-degree: 0%

---

# Wachtwoorden voorbereiden met Java{#prepare-passwords-using-java}

Voer de `ScrambleUtil.class` met Java:

1. Navigeren naar `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl/scrambler/ refimpl/scrambler/`
1. Typ vanaf de opdrachtregel:

   ```
   java -classpath [DRM SDK DVD]/SDK/adobe-flashaccess-sdk.jar;  
       com.adobe.flashaccess.refimpl.util.ScrambleUtil your_pfx_password
   ```
