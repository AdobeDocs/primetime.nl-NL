---
description: 'null'
seo-description: 'null'
seo-title: Controleren of de licentieserver correct is gestart
title: Controleren of de licentieserver correct is gestart
uuid: a6a034c9-b3c4-4e26-b901-d2c132c00c52
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc

---


# Controleren of de licentieserver correct is gestart {#check-whether-the-license-server-started-properly}

Er zijn verscheidene manieren om te bepalen of uw Server van de Vergunning van de Implementatie van de Verwijzing correct is begonnen. Eén manier is om de [!DNL catalina.log] logbestanden te controleren, maar dit is mogelijk niet voldoende, aangezien de licentieserver zich aanmeldt bij zijn eigen logbestanden.
1. Controleer het [!DNL AdobeFlashAccess.log] bestand.

   Op deze manier schrijft de licentieserver van de Reference Implementation loggegevens. De locatie van dit logbestand wordt aangegeven door het [!DNL log4j.xml] bestand en kan zo worden gewijzigd dat deze naar een willekeurige locatie verwijst. Standaard wordt het logbestand gekopieerd naar de werkmap waarin u het `catalina` Tomcat-script uitvoert.
1. Ga naar volgende URL, en verifieer dat de tekst &quot;de Server van de Vergunning opstelling correct&quot;wordt getoond:
   [!DNL ht<span></span>tps://localhost:8080/flashaccess/license/v4]
