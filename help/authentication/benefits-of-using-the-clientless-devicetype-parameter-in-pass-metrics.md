---
title: Voordelen om de parameter Clientless deviceType in de metriek van de authentificatie te gebruiken Primetime
description: Voordelen om de parameter Clientless deviceType in de metriek van de authentificatie te gebruiken Primetime
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# Voordelen om de parameter Clientless deviceType in de metriek van de authentificatie te gebruiken Primetime {#benefits-of-using-the-clientless-devicetype-parameter-in-primetime-authentication-metrics}

>[!NOTE]
>
>De inhoud op deze pagina wordt alleen ter informatie verstrekt. Voor het gebruik van deze API is een huidige licentie van Adobe vereist. Ongeautoriseerd gebruik is niet toegestaan.

</br>

## Context

Hoewel optioneel, wordt de parameter `deviceType` van Clientless API, indien aanwezig, wordt gebruikt in de metriek van de authentificatie Primetime die door worden blootgesteld [Entitlement Service Monitoring](/help/authentication/entitlement-service-monitoring-overview.md).

Overwegende dat de verbinding tussen `deviceType` en de **uitkeringen** op de metriek van de authentificatie van Primetime werd aanvankelijk niet verklaard, is het werkingsgebied van dit technische nota om meer informatie over hen toe te voegen.

## Toelichting

De `deviceType` parameter was aanwezig in Clientless API sinds de eerste versie, maar zijn implicaties op de metriek van de authentificatie Primetime werden toegevoegd in een recentere versie.



>[!IMPORTANT]
>
>Als de parameter `deviceType` correct is ingesteld, heeft het volgende **voordeel** in Entitlement Service Monitoring: het biedt metriek aan die [uitgesplitst per apparaattype](/help/authentication/entitlement-service-monitoring-overview.md#clientless_device_type) bij gebruik van Clientless, zodat verschillende soorten analyses kunnen worden uitgevoerd voor bijvoorbeeld Roku, AppleTV, Xbox enz.


Raadpleeg voor meer informatie over de API voor de bewaking van de machtigingsservice de [boor-down boom,](/help/authentication/entitlement-service-monitoring-api.md#drill-down_tree) die de [afmetingen](/help/authentication/entitlement-service-monitoring-overview.md#esm_dimensions) (middelen) beschikbaar in ESM 2.0.

>[!NOTE]
>
>Inhoud van deze technische notitie is ook toegevoegd aan de [Clientloze API](#clientless_device_type).




## Implementatie

Om volledig van de metriek van de authentificatie van Primetime te profiteren, zijn er 2 soorten [Clientless API&#39;s](#web_srvs_summary) die momenteel worden gebruikt en die de juiste `deviceType` set:

1. API&#39;s met `regcode` als een vereiste parameter en zal de `deviceType` parameter die is ingesteld bij het maken van de `regcode`, met de volgende API-aanroep:
   - [\&lt;reggie _fqdn=&quot;&quot;>/reggie/v1/{requestorId}/regcode](#reg_serv)

1. API&#39;s met de `deviceType` als optionele parameter:
   - [\&lt;sp _fqdn=&quot;&quot;>/api/v1/checkauthing](#check_authn_token)
   - [&lt;span class=&quot;s1&quot;>](#retrieve_authn_token)
   - [\&lt;sp _fqdn=&quot;&quot;>/api/v1/authorize](#init_authz)
   - [\&lt;sp _fqdn=&quot;&quot;>/api/v1/tokens/authz](#retrieve_authz_token)
   - [\&lt;sp _fqdn=&quot;&quot;>/api/v1/tokens/media](#short_media)
   - [\&lt;sp _fqdn=&quot;&quot;>/api/v1/mediatoken](#short_media)
   - [\&lt;sp _fqdn=&quot;&quot;>/api/v1/preAuthze](#PreAuthZ_Resources)
   - [\&lt;sp _fqdn=&quot;&quot;>/api/v1/logout](#init_logout)

Onze aanbeveling is om de `deviceType` en geeft het juiste apparaattype zonder Clientless voor alle API&#39;s door.
