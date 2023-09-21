---
title: Aanvankelijke installatie van Flash Access Manager
description: Aanvankelijke installatie van Flash Access Manager
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---

# Aanvankelijke installatie van Flash Access Manager {#initial-flash-access-manager-setup}

Ga als volgt te werk om Flash Access Manager in te stellen:

1. Stel de Server van Packager op. Deze server mag alleen beschikbaar zijn voor gebruikers binnen uw firewall (implementeer deze software niet op een computer met een openbaar profiel). Voor meer informatie bij het opstellen van de server, zie [De licentieserver en de gecontroleerde mapverpakker implementeren](../../aaxs-reference-implementations/deploying-license-server-and-wfp/deploying-license-server-wfp-overview.md).

   * Kopiëren [!DNL flashaccess-packager.war] naar Tomcat&#39;s webapps-map.
   * Kopiëren [!DNL flashaccess-refimpl-packager.properties] van bronnen naar een locatie op het klassepad.
   * Start de server. Er worden enkele fouten weergegeven die te wijten zijn aan problemen in het eigenschappenbestand. Dit wordt verwacht omdat de eigenschappen nog niet zijn ingevuld.

1. Installeer de toepassing Flash Access Manager AIR door de toepassing [!DNL .air] bestand (AIR 1.5 of hoger vereist).
1. Start de AIR-toepassing Flash Access Manager.

   Als uw server ergens anders wordt uitgevoerd dan `https://localhost:8080*`Er treden fouten op die aangeven dat de toepassing geen verbinding kan maken met de server. Sluit het foutendialoogvenster en vul de correcte URL voor de Server-URL van Packager in op het tabblad Voorkeuren. Als de server wordt uitgevoerd met de opgegeven URL en het eigenschappenbestand zich op het klassepad bevindt, wordt het scherm Voorkeuren gevuld met de waarden in het eigenschappenbestand. Nadat u de URL van de pakketserver hebt ingesteld, onthoudt de AIR-toepassing deze instelling en hoeft u deze instelling niet in te voeren wanneer u de toepassing de volgende keer start.
1. Vul de waarden in op het tabblad Voorkeuren en klik op **[!UICONTROL Save]**.
1. Als u de Gecontroleerde Omslagen wilt gebruiken, zult u de server moeten opnieuw beginnen om van de fouten terug te krijgen u in Stap 3 zag. Als de voorkeuren correct zijn geconfigureerd, worden er tijdens het opstarten geen fouten weergegeven.
