---
description: 'null'
seo-description: 'null'
seo-title: Bepalen of de Vergunning Server van de Vergunning van de Implementatie van de Verwijzing behoorlijk loopt
title: Bepalen of de Vergunning Server van de Vergunning van de Implementatie van de Verwijzing behoorlijk loopt
uuid: 84d32c94-7594-464e-a883-5338b52de2bf
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# Bepalen of de Vergunning Server van de Vergunning van de Implementatie van de Verwijzing behoorlijk loopt {#determining-if-reference-implementation-license-server-is-running-properly}

Er zijn verschillende manieren om te bepalen of uw server correct is gestart. Het weergeven van de [!DNL catalina.log] logbestanden is mogelijk niet voldoende, aangezien de licentieserver zich aanmeldt bij zijn eigen logbestanden. Voer de onderstaande stappen uit om ervoor te zorgen dat de implementatie van de referentie correct is gestart.

* Controleer het [!DNL AdobeFlashAccess.log] bestand. Dit is waar de Implementatie van de Verwijzing logboekinformatie schrijft. De locatie van dit logbestand wordt aangegeven door het [!DNL log4j.xml] bestand en kan worden gewijzigd zodat deze naar elke gewenste locatie verwijst. Standaard wordt het logbestand uitgevoerd naar de werkmap waar u Catalina hebt uitgevoerd.

* Navigeer naar de volgende URL: `https:///flashaccess/license/v4<your server:server port>`. U moet de tekst &quot;Licentieserver is correct ingesteld&quot; zien.

Een andere manier om te testen of de server correct wordt uitgevoerd, is een pakket met testinhoud maken, een voorbeeldvideospeler instellen en deze afspelen. De volgende procedure beschrijft dit proces:

1. Navigate to the [!DNL \Reference Implementation\Command Line Tools] folder. Zie De opdrachtregelprogramma&#39;s [installeren voor informatie over het installeren van de opdrachtregelprogramma&#39;s](../aaxs-reference-implementations/command-line-tools/aaxs-ref-impl-command-line-overview.md#installing-the-command-line-tools).

1. Creeer een eenvoudig anoniem beleid door het volgende bevel te gebruiken:

   ```
       java -jar libs\AdobePolicyManager.jar new policy_test.pol -x
   ```

   Voor meer informatie bij het creëren van beleid gebruikend de Manager van het Beleid, zie het lijngebruik [van het](../aaxs-reference-implementations/command-line-tools/policy-manager/command-line-usage.md)Bevel.

1. Stel de `encrypt.license.serverurl` eigenschap in het [!DNL flashaccesstools.properties] bestand in op de URL van de licentieserver (bijvoorbeeld `https:// localhost:8080/`). Het [!DNL flashaccesstools.properties] bestand bevindt zich onder de [!DNL \Reference Implementation\Command Line Tools] map.

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

1. Kopieer de twee gegenereerde bestanden naar de Tomcat- [!DNL webapps\ROOT\Content] map.
1. Navigeer naar `Reference Implementation\Sample Video Players\Desktop\Flash Player\Release` en kopieer de inhoud naar de `webapps\ROOT\SVP\` map Tomcat.
1. Installeer Flash Player 10.1 of hoger.
1. Open de webbrowser en navigeer naar de volgende URL:

   `https:// localhost:8080/SVP/player.html`
1. Navigeer naar de volgende URL en klik vervolgens op de knop Afspelen:

   `https:// localhost:8080/Content/<your_encrypted_FLV>`
1. Als de video niet kan worden afgespeeld, controleert u of er foutcodes zijn geschreven in het logboekvenster van Sample Video Player of in het `AdobeFlashAccess.log` bestand. De locatie van het `AdobeFlashAccess.log` logbestand wordt aangegeven door het bestand log4j.xml en kan worden gewijzigd om naar elke gewenste locatie te wijzen. Standaard wordt het logbestand geschreven naar de werkmap waar u catalina hebt uitgevoerd.
