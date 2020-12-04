---
description: Adobe Access Server voor Beschermde Streaming vereist twee types van configuratiedossiers een globaal configuratiedossier (flashaccess-global.xml) en een dossier van de huurdersconfiguratie voor elke huurder (flashaccess-huurder.xml).
seo-description: Adobe Access Server voor Beschermde Streaming vereist twee types van configuratiedossiers een globaal configuratiedossier (flashaccess-global.xml) en een dossier van de huurdersconfiguratie voor elke huurder (flashaccess-huurder.xml).
seo-title: Configuratie-mapstructuur
title: Configuratie-mapstructuur
uuid: c6cfc734-6b7c-4502-9bdb-c7aaca156e0e
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---


# Configuratiebestanden van de licentieserver en configuratiemapstructuur {#configuration-directory-structure}

Voor de Adobe Access Server for Protected Streaming zijn twee typen configuratiebestanden vereist: een globaal configuratiedossier (flashaccess-global.xml) en een dossier van de huurdersconfiguratie voor elke huurder (flashaccess-huurder.xml).

Nadat u de configuratiebestanden hebt bewerkt, raadt Adobe u aan de hulpprogramma&#39;s van de Adobe Access Server voor beveiligde streaming te gebruiken om te controleren of de bestanden de juiste indeling hebben. Voor meer informatie, zie &quot;[Validator van de Configuratie](../../aaxs-protected-streaming/aaxs-protected-streaming-utilities/configuration-validator.md)&quot;.

Om te voorkomen dat wachtwoorden in duidelijke tekst in de configuratiedossiers beschikbaar worden gemaakt, moeten alle wachtwoorden die in de globale en huurdersconfiguratiedossiers worden gespecificeerd worden gecodeerd. Voor meer informatie bij het coderen van wachtwoorden, zie &quot;[Wachtwoord Scrambler](../../aaxs-protected-streaming/aaxs-protected-streaming-utilities/password-scrambler.md)&quot;.

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

