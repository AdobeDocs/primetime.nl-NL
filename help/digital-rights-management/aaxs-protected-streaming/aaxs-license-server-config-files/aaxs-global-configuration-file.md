---
title: Globaal configuratiebestand
description: Globaal configuratiebestand
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---

# Globaal configuratiebestand{#global-configuration-file}

Het flashaccess-global.xml-configuratiebestand bevat instellingen die van toepassing zijn op alle huurders van de licentieserver. Dit bestand moet zich bevinden in *LicenseServer.ConfigRoot*. Zie de configs folder voor een voorbeeld globaal configuratiedossier. Het algemene configuratiebestand bevat het volgende:

* Caching — Controles caching van configuratiedossiers in geheugen. Zie &quot;Configuratiebestanden bijwerken&quot; voor een uitleg van de cacheinstellingen.
* Logboekregistratie — Geeft het logniveau op en hoe vaak logbestanden worden gewist.
* HSM-wachtwoord — Alleen vereist als een HSM wordt gebruikt om serverreferenties op te slaan.

Zie de opmerkingen in het algemene configuratiebestand van het voorbeeld in `<AdobeAccessDVD>\Adobe Access Server for Protected Streaming\configs` voor meer informatie .
