---
description: Het flashaccess-global.xml-configuratiebestand bevat instellingen die van toepassing zijn op alle huurders van de licentieserver.
title: Globaal configuratiebestand
exl-id: 3e74bce6-1634-469f-9d02-1121e9d50687
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 0%

---

# Globaal configuratiebestand{#global-configuration-file}

Het flashaccess-global.xml-configuratiebestand bevat instellingen die van toepassing zijn op alle huurders van de licentieserver.

U moet het configuratiebestand plaatsen in het dialoogvenster [!DNL LicenseServer.ConfigRoot] directory.

Zie de [!DNL configs] voor een voorbeeld van een globaal configuratiebestand.

Het algemene configuratiebestand bevat:

* Caching — Controles caching van configuratiedossiers in geheugen.

   Zie *Configuratiebestanden bijwerken* voor informatie over de cacheinstellingen.
* Logboekregistratie — Geeft het logniveau op en hoe vaak logbestanden worden gewist.
* HSM-wachtwoord — Alleen vereist als een HSM wordt gebruikt om serverreferenties op te slaan.

Zie de opmerkingen in het voorbeeld van het algemene configuratiebestand dat zich in Primetime DRM bevindt `<DVD>`\Adobe Primetime DRM Server for Protected Streaming\configureert voor meer informatie.
