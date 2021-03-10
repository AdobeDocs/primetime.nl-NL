---
title: Bepalen of de Vergunning Server van de Vergunning van de Implementatie van de Verwijzing behoorlijk loopt
description: Bepalen of de Vergunning Server van de Vergunning van de Implementatie van de Verwijzing behoorlijk loopt
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---


# Bepalen of de Vergunning Server van de Vergunning van de Implementatie van de Verwijzing behoorlijk {#determining-if-reference-implementation-license-server-is-running-properly} loopt

Er zijn verschillende manieren om te bepalen of uw server correct is gestart. Het weergeven van de [!DNL catalina.log]-logbestanden is mogelijk niet voldoende, aangezien de licentieserver zich aanmeldt bij zijn eigen logbestanden. Voer de onderstaande stappen uit om ervoor te zorgen dat de implementatie van de referentie correct is gestart.

* Controleer het [!DNL AdobeFlashAccess.log]-bestand. Dit is waar de Implementatie van de Verwijzing logboekinformatie schrijft. De locatie van dit logbestand wordt aangegeven door het [!DNL log4j.xml]-bestand en kan worden gewijzigd om naar elke gewenste locatie te wijzen. Standaard wordt het logbestand uitgevoerd naar de werkmap waar u catalina hebt uitgevoerd.

* Navigeer naar de volgende URL: `https:///flashaccess/license/v4<your server:server port>`. U moet de tekst &quot;Licentieserver is correct ingesteld&quot; zien.

Een andere manier om te testen of de server correct wordt uitgevoerd, is een pakket met testinhoud maken, een voorbeeldvideospeler instellen en deze afspelen. De volgende procedure beschrijft dit proces:

1. Navigeer naar de map [!DNL \Reference Implementation\Command Line Tools]. Zie [De opdrachtregelprogramma&#39;s installeren](../aaxs-reference-implementations/command-line-tools/aaxs-ref-impl-command-line-overview.md#installing-the-command-line-tools) voor informatie over het installeren van de opdrachtregelprogramma&#39;s.

1. Creeer een eenvoudig anoniem beleid door het volgende bevel te gebruiken:

   ```
       java -jar libs\AdobePolicyManager.jar new policy_test.pol -x
   ```

   Voor meer informatie bij het creëren van beleid gebruikend de Manager van het Beleid, zie [Gebruik van de lijn van het Bevel](../aaxs-reference-implementations/command-line-tools/policy-manager/command-line-usage.md).

1. Stel de eigenschap `encrypt.license.serverurl` in het bestand [!DNL flashaccesstools.properties] in op de URL van de licentieserver (bijvoorbeeld `https:// localhost:8080/`). Het [!DNL flashaccesstools.properties] dossier wordt gevestigd onder [!DNL \Reference Implementation\Command Line Tools] omslag.

1. Verpak inhoud door het volgende bevel te gebruiken:

   ```java
       java -jar libs\AdobePackager.jar  
   <i class="+ topic ph hi-d="" i "="">
   test_input_FLV  
   <i class="+ topic ph hi-d="" i "="">
   output_file  
               -p policy_test.pol 
   </i class="+ topic> 
   </i class="+ topic>
   ```

1. Kopieer de twee gegenereerde bestanden naar de Tomcat-map [!DNL webapps\ROOT\Content].
1. Navigeer naar `Reference Implementation\Sample Video Players\Desktop\Flash Player\Release` en kopieer de inhoud naar de map Tomcat `webapps\ROOT\SVP\`.
1. Installeer Flash Player 10.1 of hoger.
1. Open de webbrowser en navigeer naar de volgende URL:

   `https:// localhost:8080/SVP/player.html`
1. Navigeer naar de volgende URL en klik vervolgens op de knop Afspelen:

   `https:// localhost:8080/Content/<your_encrypted_FLV>`
1. Als de video niet kan worden afgespeeld, controleert u of er foutcodes zijn geschreven in het logboekvenster van Sample Video Player of in het bestand `AdobeFlashAccess.log`. De locatie van het logbestand `AdobeFlashAccess.log` wordt aangegeven door het bestand log4j.xml en kan worden gewijzigd om naar elke gewenste locatie te wijzen. Standaard wordt het logbestand geschreven naar de werkmap waar u catalina hebt uitgevoerd.
