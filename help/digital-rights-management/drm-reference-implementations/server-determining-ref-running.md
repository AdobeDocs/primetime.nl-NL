---
description: 'null'
seo-description: 'null'
seo-title: Bepalen of Referentie-implementatie-licentieserver correct wordt uitgevoerd
title: Bepalen of Referentie-implementatie-licentieserver correct wordt uitgevoerd
uuid: afd82d6d-a11c-48ff-b48c-8f81d4b406a0
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---


# Bepalen of Referentie-implementatielicentieserver correct {#determining-if-reference-implementation-license-server-runs-properly} wordt uitgevoerd

Er zijn verscheidene manieren om te bepalen of uw Server van de Vergunning van de Implementatie van de Verwijzing correct is begonnen. U kunt de [!DNL catalina.log] logboeken bekijken kan niet voldoende zijn, aangezien de vergunningsserver aan zijn eigen logboekdossiers registreert. Voer de onderstaande stappen uit om ervoor te zorgen dat de implementatie van de referentie correct is gestart.

* Controleer het [!DNL AdobeFlashAccess.log]-bestand. Dit is waar de Implementatie van de Verwijzing logboekinformatie schrijft. De locatie van dit logbestand wordt aangegeven door het [!DNL log4j.xml]-bestand en kan worden gewijzigd om naar elke gewenste locatie te wijzen. Standaard is het logbestand gekopieerd naar de werkmap waar u catalina uitvoert.

* Ga naar de volgende URL: [!DNL https:// flashaccess/license/v4]*uw server:serverpoort*. U moet de tekst &quot;Licentieserver is correct ingesteld&quot; zien.

Een andere manier om te testen of de server correct wordt uitgevoerd, is het verpakken van een segment van de testinhoud, het instellen van een videovoorbeeldspeler en het vervolgens afspelen.

De volgende procedure beschrijft dit proces:

1. Ga naar de [!DNL \Reference Implementation\Command Line Tools] omslag.

   Zie [De opdrachtregelprogramma&#39;s installeren](../drm-reference-implementations/command-line-tools/install-command-line-tools.md) voor informatie over het installeren van de opdrachtregelprogramma&#39;s.

1. Typ het volgende bevel om een eenvoudig anoniem beleid te creëren DRM:

   ```
       java -jar libs\AdobePolicyManager.jar new policy_test.pol -x
   ```

   Zie [Het lijngebruik van het Bevel](../drm-reference-implementations/command-line-tools/configure-command-line-tools/policy-manager/policy-manager-command-line-usage.md) op hoe te om beleid DRM met de Manager van het Beleid te creëren DRM.

1. Stel de eigenschap `encrypt.license.serverurl` in het bestand [!DNL flashaccesstools.properties] in op de URL van de licentieserver.

   Bijvoorbeeld, [!DNL https:// localhost:8080/]. Het [!DNL flashaccesstools.properties]-bestand bevindt zich in de map [!DNL \Reference Implementation\Command Line Tools].

1. Typ de volgende opdracht om een segment van de inhoud in een pakket te plaatsen:

```
       java -jar libs\AdobePackager.jar  
       <i class="+ topic ph hi-d="" i "="">
         test_input_FLV  
        <i class="+ topic ph hi-d="" i "="">
       output_file  
               -p policy_test.pol 
       </i class="+ topic> 
       </i class="+ topic>
```

1. Kopieer de twee gegenereerde bestanden naar de map [!DNL webapps\ROOT\Content] op de Tomcat-server.
1. Ga naar [!DNL Reference Implementation\Sample Video Players\Desktop\Flash Player\Release] folder en kopieer de inhoud aan  [!DNL webapps\ROOT\SVP\] omslag op de server van Tomcat.

1. Installeer Flash Player versie 10.1 of hoger.
1. Open een webbrowser en ga naar de volgende URL: [!DNL        https:// localhost:8080/SVP/player.html]

1. Ga naar de volgende URL en klik vervolgens op **[!UICONTROL Play]**: [!DNL https:// localhost:8080/Content/] *`your_encrypted_FLV`*.

1. Als de video niet kan worden afgespeeld, controleert u of foutcodes worden weergegeven in het logboekvenster van de Sample Video Player of worden toegevoegd aan het [!DNL AdobeFlashAccess.log]-bestand.

   U kunt nu zoeken naar de locatie van het logbestand [!DNL AdobeFlashAccess.log] in het bestand log4j.xml en dit vervolgens wijzigen. Standaard wordt het logbestand gekopieerd naar de werkmap waarin u catalina uitvoert.

