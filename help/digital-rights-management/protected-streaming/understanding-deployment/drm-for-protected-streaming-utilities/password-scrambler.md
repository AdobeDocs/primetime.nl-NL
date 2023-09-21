---
description: Met het hulpprogramma Password Scrambler versleutelt u een wachtwoord voor de Adobe Primetime DRM-server voor beveiligde streamingconfiguratiebestanden.
title: Wachtwoordsprambler
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '92'
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

Alle wachtwoorden die u hebt opgegeven in het dialoogvenster [!DNL flashaccess-global.xml] en [!DNL flashaccess-tenant.xml] bestanden moeten worden versleuteld.

>[!NOTE]
>
>Het hulpprogramma Password Scrambler in de Primetime DRM-server voor beveiligde streaming is niet uitwisselbaar met de schuifregelaar die wordt geleverd bij de Referentie-implementatieserver.
