---
seo-title: De meegeleverde Offline Packager Primetime gebruiken
title: De meegeleverde Offline Packager Primetime gebruiken
uuid: 16b535a9-81b5-43bc-9e42-a64eb6649d9a
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# De meegeleverde Offline Packager Primetime gebruiken{#use-the-included-primetime-offline-packager}

Uw Primetime Java Packager wordt vooraf geconfigureerd met de meeste instellingen die u nodig hebt voor het verpakken van inhoud. Er zijn slechts een paar gebieden om bij te werken om aan de slag te gaan.

## Eigenschappen van Packager bijwerken {#section_99904D35E99944A28FF43D924E516CC2}

Context voor de huidige taak

* Werk de volgende eigenschappen van de pakketsoftware bij voordat u het configuratiebestand gebruikt om de inhoud te verpakken:

### Door gebruiker opgegeven eigenschappen van XML-configuratiebestand

| Eigenschapnaam | Beschrijving |
|---|---|
| `policy_file` | pad naar beleidsbestand. Adobe biedt verschillende vooraf geconfigureerde beleidsregels waaruit u kunt kiezen. |
| `pkgr_pfx` | Pad naar inloggegevens van Packager. U moet hier uw eigen door Adobe uitgegeven pakketreferentie ( [!DNL .pfx]) leveren. |
| `pkgr_pfx_pwd` | Wachtwoord voor inloggegevens van Packager. Hier moet u het wachtwoord opgeven voor de door Adobe uitgegeven pakketreferentie. |

## Pakket maken met opdrachtregel {#section_DFBE462679E34D62963BE201FD3321F9}

Voordat u inhoud gaat verpakken, moet u controleren of alle vereiste informatie in het configuratiebestand is opgenomen.

* Als u inhoud wilt verpakken met uw configuratiebestand, gebruikt u de volgende syntaxis op de opdrachtregel:

```
java -jar OfflinePackager.jar -conf_path [configuration filename]
```

Voorbeeldconfiguratiebestanden om uw inhoud in een HLS- of HDS-indeling in te pakken, worden geleverd, benoemd [!DNL config_hds.xml] en [!DNL config.hls.xml].

De HDS- of HLS-inhoud wordt uitgevoerd naar de [!DNL /output] map onder de map Protection Kit. Alle artefacten die naar deze map worden geschreven, moeten op een HTTP-webserver worden gehost om te worden afgespeeld.
