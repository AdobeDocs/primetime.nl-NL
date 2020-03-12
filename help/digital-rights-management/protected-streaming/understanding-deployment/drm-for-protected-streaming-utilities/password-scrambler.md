---
description: Met het hulpprogramma Password Scrambler versleutelt u een wachtwoord voor de Adobe Primetime DRM-server voor beveiligde streamingconfiguratiebestanden.
seo-description: Met het hulpprogramma Password Scrambler versleutelt u een wachtwoord voor de Adobe Primetime DRM-server voor beveiligde streamingconfiguratiebestanden.
seo-title: Wachtwoordsprambler
title: Wachtwoordsprambler
uuid: 56df0f49-f3fd-464d-b4ba-25e1b497158a
translation-type: tm+mt
source-git-commit: 105dedcfe47a5f454a067e66a95827e638290742

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

Alle wachtwoorden die u in de bestanden [!DNL flashaccess-global.xml] [!DNL flashaccess-tenant.xml] en bestanden hebt opgegeven, moeten worden versleuteld.

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>Het hulpprogramma Password Scrambler in de Primetime DRM-server voor beveiligde streaming is niet uitwisselbaar met de schuifregelaar die wordt geleverd bij de Referentie-implementatieserver.