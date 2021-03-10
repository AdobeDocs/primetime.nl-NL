---
title: Adobe Primetime-verificatie (optioneel)
description: Adobe Primetime-verificatie (optioneel)
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---


# Adobe Primetime-verificatie (optioneel) {#adobe-primetime-authentication-optional}

Als het DRM-beleid dat wordt gebruikt om de inhoud te verpakken een anoniem beleid is, wordt een licentie uitgegeven voor alle licentieaanvragen. Primetime Cloud DRM biedt eventueel ook ondersteuning voor verificatie via Adobe Primetime-verificatie. Als deze functie is ingeschakeld, wordt geen licentie uitgegeven tenzij het clientapparaat eerst een Primetime-verificatietoken heeft verworven en deze lokaal via de juiste client-API ( `setAuthenticationToken`) heeft ingesteld voor het instellen van aangepaste verificatietokens. Raadpleeg voor meer informatie over het integreren van Primetime-verificatie in uw verificatieworkflow: [Adobe Primetime-verificatie.](https://tve.helpdocsonline.com/home)

Als in het DRM-beleid tijdens het aanschaffen van licenties wordt aangegeven dat Pri-metime verificatie is vereist, parseert en valideert de licentieserver de Primetime-verificatie Short Media Token. Als het DRM-beleid een `ResourceID` of `RequestorID` opgeeft, valideert de licentieserver ook het token op basis van deze eigenschappen. Als deze niet zijn ingesteld, geeft de licentieserver de eigenschap(pen) tijdens de tokenvalidatie op als &quot;null&quot;. Alleen als de tokenvalidatie succesvol is, wordt een licentie afgegeven; anders zal de client een 3328 DRMErrorEvent met een 305 subfout-code (Gebruiker niet geautoriseerd) verzenden.

De parameters van de authentificatie van Primetime moeten in het beleid worden gespecificeerd dat wordt gebruikt om de inhoud te verpakken die bestemd is om authentificatie te vereisen Primetime.

De relevante eigenschappen zijn:

```
#policy.customProp.1=adobePass.required=<TRUE or FALSE> 
#policy.customProp.1=adobePass.requestorID=<Requestor ID String> 
#policy.customProp.1=adobePass.resourceID=<Resource ID String>
```

>[!NOTE]
>
>Wanneer u Primetime-verificatie gebruikt in combinatie met de functie voor rotatie van licenties (DRM), moet u er rekening mee houden dat de Primetime-verificatie Short Media Token (SMT) een korte geldigheidsdatum heeft. Als uw toepassing van plan is om de Rotatie van de Vergunning te gebruiken (b.v., om *Blackouts* gebruikscase te steunen), moet de toepassing zich hiervan bewust zijn en zijn authentificatie Short Media Token van Primetime vóór het roteren van zijn vergunning verfrissen.