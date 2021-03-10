---
description: Met het hulpprogramma Password Scrambler versleutelt u een wachtwoord voor de Adobe Primetime DRM-server voor beveiligde streamingconfiguratiebestanden.
title: Wachtwoordsprambler
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
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

Alle wachtwoorden die u in de [!DNL flashaccess-global.xml] en [!DNL flashaccess-tenant.xml] dossiers hebt gespecificeerd moeten worden gecodeerd.

>[!NOTE]
>
>Het hulpprogramma Password Scrambler in de Primetime DRM-server voor beveiligde streaming is niet uitwisselbaar met de schuifregelaar die wordt geleverd bij de Referentie-implementatieserver.