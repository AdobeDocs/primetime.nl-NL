---
title: Tomcat configureren
description: Tomcat configureren
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---


# Tomcat{#configure-tomcat} configureren

Wijzig op de Individualization-server het [!DNL conf/server.xml]-bestand van Tomcat om aanvullende informatie op te nemen in het toegangslogboek. U kunt deze gegevens gebruiken voor rapportagedoeleinden.

1. Zoek de configuratie voor `AccessLogValve` in [!DNL server.xml] en wijzig het patroon zoals hier getoond:

   ```
   <Valve className="org.apache.catalina.valves.AccessLogValve" 
   directory="logs" prefix="localhost_access_log." suffix=".txt" 
   pattern="%h %{x-forwarded-for}i %l %u %t &quot;%r&quot; %s %b 
   %{request-id}r" resolveHosts="false"/>
   ```

   `%{x-forwarded-for}i` Hiermee wordt de waarde van de  `x-forwarded-for` koptekst vastgelegd. Als u een Apache reverse-proxy gebruikt om aanvragen door te sturen naar de Tomcat-server, bevat deze header het IP-adres van de oorspronkelijke client, terwijl `%h` het IP-adres van de Apache-server opneemt. `%{request-id}r` zal het verzoek herkenningsteken registreren, dat aan verzoek identiteitskaart in het Van de Individualisatietoepassing logboek beantwoordt.

1. Bewerk [!DNL conf/server.xml] en stel de eigenschap `unpackwars` in op false.

   Voor zowel de servers van de Individualisering als van de Zeer belangrijke Generatie, is het een goed idee om [!DNL conf/server.xml] uit te geven en `unpackwars` te plaatsen bezit aan `false`. Anders, wanneer u WARs bijwerkt, kunt u de onverpakte omslagen van de OORLOG ook moeten zuiveren.

>[!NOTE]
>
>Toekomstige DRM-clients vereisen dat u het filter CORS (Cross-Origin Resource Sharing) dat beschikbaar is voor Tomcat inschakelt en configureert. Momenteel hebben geen DRM-clients deze vereiste.

