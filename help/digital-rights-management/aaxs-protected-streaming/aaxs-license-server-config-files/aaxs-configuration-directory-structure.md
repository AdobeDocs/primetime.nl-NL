---
description: Adobe Access Server voor Beschermde Streaming vereist twee types van configuratiedossiers een globaal configuratiedossier (flashaccess-global.xml) en een dossier van de huurdersconfiguratie voor elke huurder (flashaccess-huurder.xml).
title: Configuratie-mapstructuur
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# Configuratiebestanden en configuratiestructuur van de licentieserver {#configuration-directory-structure}

Adobe Access Server voor Beschermde Streaming vereist twee soorten configuratiedossiers: een globaal configuratiedossier (flashaccess-global.xml) en een dossier van de huurdersconfiguratie voor elke huurder (flashaccess-huurder.xml).

Nadat de configuratiebestanden zijn bewerkt, raadt Adobe u aan de hulpprogramma&#39;s van de Adobe Access Server voor beveiligde streaming te gebruiken om te controleren of de bestanden de juiste indeling hebben. Zie voor meer informatie &quot;[Configuratie-validatie](../../aaxs-protected-streaming/aaxs-protected-streaming-utilities/configuration-validator.md)&quot;.

Om te voorkomen dat wachtwoorden in duidelijke tekst in de configuratiedossiers beschikbaar worden gemaakt, moeten alle wachtwoorden die in de globale en huurdersconfiguratiedossiers worden gespecificeerd worden gecodeerd. Voor meer informatie over het coderen van wachtwoorden, zie &quot;[Wachtwoordkrambler](../../aaxs-protected-streaming/aaxs-protected-streaming-utilities/password-scrambler.md)&quot;.

De configuratiemappen hebben de volgende structuur:

```
<i class="+ topic ph hi-d="" i "="">
  LicenseServer.ConfigRoot/  
  flashaccess-global.xml  
  pkcs11.cfg (optional)  
  flashaccessserver/  
   libs/ (optional)  
   tenants/  
     
 <i class="+ topic ph hi-d="" i "="">
   tenantname/  
      flashaccess-tenant.xml  
       
  <i class="+ topic ph hi-d="" i "="">
    credential.pfx (optional)  
        
   <i class="+ topic ph hi-d="" i "="">
     packagercert.cer (optional) 
   </i class="+ topic> 
  </i class="+ topic> 
 </i class="+ topic> 
</i class="+ topic>
```
