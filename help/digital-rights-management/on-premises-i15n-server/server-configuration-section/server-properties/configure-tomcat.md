---
seo-title: Tomcat configureren
title: Tomcat configureren
uuid: 5f23aa33-29d7-4b41-87a4-59dc5b433de4
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Tomcat configureren{#configure-tomcat}

Voor de server van de Individualisering, wijzig het [!DNL conf/server.xml] dossier van Tomcat om extra informatie in het toegangslogboek te omvatten. U kunt deze gegevens gebruiken voor rapportagedoeleinden.

1. Zoek de configuratie voor de `AccessLogValve` insteekmodule [!DNL server.xml] en wijzig het patroon zoals u hier ziet:

   ```
   <Valve className="org.apache.catalina.valves.AccessLogValve" 
   directory="logs" prefix="localhost_access_log." suffix=".txt" 
   pattern="%h %{x-forwarded-for}i %l %u %t &quot;%r&quot; %s %b 
   %{request-id}r" resolveHosts="false"/>
   ```

   `%{x-forwarded-for}i` zal de waarde van de `x-forwarded-for` kopbal registreren. Als u een Apache reverse-proxy gebruikt om verzoeken door te sturen naar de Tomcat-server, bevat deze header het IP-adres van de oorspronkelijke client, terwijl het IP-adres van de Apache-server wordt `%h` vastgelegd. `%{request-id}r` zal het verzoek herkenningsteken registreren, dat aan verzoek identiteitskaart in het Van de Individualisatietoepassing logboek beantwoordt.

1. Bewerk [!DNL conf/server.xml] `unpackwars` de eigenschap en stel deze in op false.

   Voor zowel de servers van de Individualisering als van de Zeer belangrijke Generatie, is het een goed idee om het [!DNL conf/server.xml] bezit uit te geven `unpackwars` en te plaatsen aan `false`. Anders, wanneer u WARs bijwerkt, kunt u de onverpakte omslagen van de OORLOG ook moeten zuiveren.

>[!NOTE]
>
>Toekomstige DRM-clients vereisen dat u het filter CORS (Cross-Origin Resource Sharing) dat beschikbaar is voor Tomcat inschakelt en configureert. Momenteel hebben geen DRM-clients deze vereiste.

