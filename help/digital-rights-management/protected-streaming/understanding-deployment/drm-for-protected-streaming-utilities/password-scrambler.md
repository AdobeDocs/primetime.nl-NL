---
description: Met het hulpprogramma Password Scrambler versleutelt u een wachtwoord voor de Adobe Primetime DRM-server voor beveiligde streamingconfiguratiebestanden.
seo-description: Met het hulpprogramma Password Scrambler versleutelt u een wachtwoord voor de Adobe Primetime DRM-server voor beveiligde streamingconfiguratiebestanden.
seo-title: Wachtwoordsprambler
title: Wachtwoordsprambler
uuid: 56df0f49-f3fd-464d-b4ba-25e1b497158a
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '112'
ht-degree: 0%

---


# Wachtwoordsprambler {#password-scrambler}

Met het hulpprogramma Password Scrambler versleutelt u een wachtwoord voor de Adobe Primetime DRM-server voor beveiligde streamingconfiguratiebestanden.

Typ de volgende tekst om de schuifregelaar uit te voeren:

```
Scrambler.bat  
<i class="+ topic ph hi-d="" i "="">
  password 
</i class="+ topic>
```

of

```
java -jar libs/flashaccess-scrambler.jar  
<i class="+ topic ph hi-d="" i "="">
  password  
</i class="+ topic>
```

Het hulpprogramma geeft het volgende bericht weer:

```
Encrypted password:  
<i class="+ topic ph hi-d="" i "="">
  scrambled-password 
</i class="+ topic>
```

Alle wachtwoorden die u in de [!DNL flashaccess-global.xml] en [!DNL flashaccess-tenant.xml] dossiers hebt gespecificeerd moeten worden gecodeerd.

>[!NOTE]
>
>Het hulpprogramma Password Scrambler in de Primetime DRM-server voor beveiligde streaming is niet uitwisselbaar met de schuifregelaar die wordt geleverd bij de Referentie-implementatieserver.