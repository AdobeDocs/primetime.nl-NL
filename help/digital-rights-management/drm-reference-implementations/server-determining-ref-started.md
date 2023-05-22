---
title: Controleren of de licentieserver correct is gestart
description: Controleren of de licentieserver correct is gestart
copied-description: true
exl-id: 05995a75-9468-4237-9091-a07606297772
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 0%

---

# Controleren of de licentieserver correct is gestart {#check-whether-the-license-server-started-properly}

Er zijn verscheidene manieren om te bepalen of uw Server van de Vergunning van de Implementatie van de Verwijzing correct is begonnen. Eén manier is om de [!DNL catalina.log] logbestanden, maar dit is mogelijk niet voldoende, aangezien de licentieserver zich aanmeldt bij zijn eigen logbestanden.
1. Controleer uw [!DNL AdobeFlashAccess.log] bestand.

   Op deze manier schrijft de licentieserver van de Reference Implementation loggegevens. De locatie van dit logbestand wordt aangegeven door uw [!DNL log4j.xml] en kan worden gewijzigd om naar een willekeurige locatie te verwijzen. Standaard wordt het logbestand gekopieerd naar de werkmap waar u uw `catalina` Tomcat-script.
1. Ga naar volgende URL, en verifieer dat de tekst &quot;de Server van de Vergunning opstelling correct&quot;wordt getoond:
   [!DNL ht<span></span>tps://localhost:8080/flashaccess/license/v4]
