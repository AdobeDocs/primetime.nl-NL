---
description: 'null'
seo-description: 'null'
seo-title: Eerste configuratie van Flash Access Manager
title: Eerste configuratie van Flash Access Manager
uuid: e9041f7c-b098-4121-88bf-ff3e6369e01b
translation-type: tm+mt
source-git-commit: 4f196bbd079edeb1a423afee6b4b7e249d380f40
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 0%

---


# Eerste configuratie van Flash Access Manager {#initial-flash-access-manager-setup}

Ga als volgt te werk om Flash Access Manager in te stellen:

1. Stel de Server van Packager op. Deze server mag alleen beschikbaar zijn voor gebruikers binnen uw firewall (implementeer deze software niet op een computer met een openbaar profiel). Zie [De licentieserver implementeren en mapverpakker](../../aaxs-reference-implementations/deploying-license-server-and-wfp/deploying-license-server-wfp-overview.md) controleren voor meer informatie over het implementeren van de server.

   * Kopieer [!DNL flashaccess-packager.war] naar de webapps-map van Tomcat.
   * Kopieer [!DNL flashaccess-refimpl-packager.properties] van bronnen naar een locatie op het klassepad.
   * Start de server. Er worden enkele fouten weergegeven die te wijten zijn aan problemen in het eigenschappenbestand. dit wordt verwacht omdat de eigenschappen nog niet zijn ingevuld .

1. Installeer de Flash Access Manager AIR-toepassing door het [!DNL .air]-bestand te starten (AIR 1.5 of hoger vereist).
1. Start de AIR-toepassing Flash Access Manager.

   Als uw server ergens anders dan `https://localhost:8080*` wordt uitgevoerd, worden fouten weergegeven die aangeven dat de toepassing geen verbinding met de server kan maken. Sluit het foutendialoogvenster en vul de correcte URL voor de Server-URL van Packager in op het tabblad Voorkeuren. Als de server wordt uitgevoerd met de opgegeven URL en het eigenschappenbestand zich op het klassepad bevindt, wordt het scherm Voorkeuren gevuld met de waarden in het eigenschappenbestand. Nadat u de URL van de pakketserver hebt ingesteld, onthoudt de AIR-toepassing deze instelling en hoeft u deze instelling niet in te voeren wanneer u de toepassing de volgende keer start.
1. Vul de waarden in op het tabblad Voorkeuren en klik op **[!UICONTROL Save]**.
1. Als u de Gecontroleerde Omslagen wilt gebruiken, zult u de server moeten opnieuw beginnen om van de fouten terug te krijgen u in Stap 3 zag. Als de voorkeuren correct zijn geconfigureerd, worden er tijdens het opstarten geen fouten weergegeven.

