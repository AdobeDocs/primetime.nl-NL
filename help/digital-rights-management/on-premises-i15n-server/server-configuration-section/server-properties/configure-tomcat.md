---
title: Tomcat configureren
description: Tomcat configureren
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# Tomcat configureren{#configure-tomcat}

Pas op de Individualization-server Tomcat&#39;s aan [!DNL conf/server.xml] dossier om extra informatie in het toegangslogboek te omvatten. U kunt deze gegevens gebruiken voor rapportagedoeleinden.

1. Zoek de configuratie voor de `AccessLogValve` in [!DNL server.xml] en wijzig het patroon zoals hieronder getoond:

   ```
   <Valve className="org.apache.catalina.valves.AccessLogValve" 
   directory="logs" prefix="localhost_access_log." suffix=".txt" 
   pattern="%h %{x-forwarded-for}i %l %u %t &quot;%r&quot; %s %b 
   %{request-id}r" resolveHosts="false"/>
   ```

   `%{x-forwarded-for}i` registreert de waarde van `x-forwarded-for` header. Als u een Apache reverse-proxy gebruikt om verzoeken door te sturen naar de Tomcat-server, bevat deze header het IP-adres van de oorspronkelijke client, terwijl `%h` neemt het IP-adres van de Apache-server op. `%{request-id}r` zal het verzoek herkenningsteken registreren, dat aan verzoek identiteitskaart in het Van de Individualisatietoepassing logboek beantwoordt.

1. Bewerken [!DNL conf/server.xml] en stelt de `unpackwars` eigenschap in op false.

   Voor zowel de servers van de Individualisering als van de Zeer belangrijke Generatie, is het een goed idee om uit te geven [!DNL conf/server.xml] en stelt de `unpackwars` eigenschap aan `false`. Anders, wanneer u WARs bijwerkt, kunt u de onverpakte omslagen van de OORLOG ook moeten zuiveren.

>[!NOTE]
>
>Toekomstige DRM-clients vereisen dat u het filter CORS (Cross-Origin Resource Sharing) dat beschikbaar is voor Tomcat inschakelt en configureert. Momenteel hebben geen DRM-clients deze vereiste.
