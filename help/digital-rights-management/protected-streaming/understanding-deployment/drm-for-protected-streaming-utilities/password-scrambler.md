---
description: Met het hulpprogramma Password Scrambler versleutelt u een wachtwoord voor de Adobe Primetime DRM-server voor beveiligde streamingconfiguratiebestanden.
title: Wachtwoordsprambler
exl-id: 9cedd3e5-01db-4ea9-bf23-8767987fc26c
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
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
