---
title: Bepalen of Referentie-implementatie-licentieserver correct wordt uitgevoerd
description: Bepalen of Referentie-implementatie-licentieserver correct wordt uitgevoerd
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Bepalen of Referentie-implementatie-licentieserver correct wordt uitgevoerd {#determining-if-reference-implementation-license-server-runs-properly}

Er zijn verscheidene manieren om te bepalen of uw Server van de Vergunning van de Implementatie van de Verwijzing correct is begonnen. U kunt de [!DNL catalina.log] logbestanden zijn mogelijk niet voldoende, aangezien de licentieserver zich aanmeldt bij zijn eigen logbestanden. Voer de onderstaande stappen uit om ervoor te zorgen dat de implementatie van de referentie correct is gestart.

* Controleer uw [!DNL AdobeFlashAccess.log] bestand. Dit is waar de Implementatie van de Verwijzing logboekinformatie schrijft. De locatie van dit logbestand wordt aangegeven door uw [!DNL log4j.xml] en kan worden gewijzigd om naar elke gewenste locatie te verwijzen. Standaard is het logbestand gekopieerd naar de werkmap waar u catalina uitvoert.

* Ga naar de volgende URL: [!DNL https:// flashaccess/license/v4]*uw server:serverpoort*. U moet de tekst &quot;Licentieserver is correct ingesteld&quot; zien.

Een andere manier om te testen of de server correct wordt uitgevoerd, is het verpakken van een segment van de testinhoud, het instellen van een videovoorbeeldspeler en het vervolgens afspelen.

De volgende procedure beschrijft dit proces:

1. Ga naar de [!DNL \Reference Implementation\Command Line Tools] map.

   Zie [De opdrachtregelprogramma&#39;s installeren](../drm-reference-implementations/command-line-tools/install-command-line-tools.md) voor het installeren van de opdrachtregelprogramma&#39;s.

1. Typ het volgende bevel om een eenvoudig anoniem beleid te creëren DRM:

   ```
       java -jar libs\AdobePolicyManager.jar new policy_test.pol -x
   ```

   Zie [Gebruik van opdrachtregels](../drm-reference-implementations/command-line-tools/configure-command-line-tools/policy-manager/policy-manager-command-line-usage.md) over het maken van DRM-beleid met DRM-beleidsbeheer.

1. Stel de `encrypt.license.serverurl` eigenschap in de [!DNL flashaccesstools.properties] bestand naar de URL van de licentieserver.

   Bijvoorbeeld: [!DNL https:// localhost:8080/]. De [!DNL flashaccesstools.properties] bestand bevindt zich in het dialoogvenster [!DNL \Reference Implementation\Command Line Tools] map.

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

1. Kopieer de twee gegenereerde bestanden naar de [!DNL webapps\ROOT\Content] op de Tomcat-server.
1. Ga naar de [!DNL Reference Implementation\Sample Video Players\Desktop\Flash Player\Release] en kopieer de inhoud naar de [!DNL webapps\ROOT\SVP\] op de Tomcat-server.

1. Installeer Flash Player versie 10.1 of hoger.
1. Open een webbrowser en ga naar de volgende URL: [!DNL        https:// localhost:8080/SVP/player.html]

1. Ga naar de volgende URL en klik vervolgens op **[!UICONTROL Play]**: [!DNL https:// localhost:8080/Content/] *`your_encrypted_FLV`*.

1. Als de video niet kan worden afgespeeld, controleert u of er foutcodes worden weergegeven in het logboekvenster van de Sample Video Player of toegevoegd aan de component [!DNL AdobeFlashAccess.log] bestand.

   U kunt nu zoeken naar de locatie van het dialoogvenster [!DNL AdobeFlashAccess.log] logbestand in het bestand log4j.xml en wijzig het vervolgens. Standaard wordt het logbestand gekopieerd naar de werkmap waarin u catalina uitvoert.
