---
title: De meegeleverde Offline Packager Primetime gebruiken
description: De meegeleverde Offline Packager Primetime gebruiken
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---

# De meegeleverde Offline Packager Primetime gebruiken{#use-the-included-primetime-offline-packager}

Uw Primetime Java Packager wordt vooraf geconfigureerd met de meeste instellingen die u nodig hebt voor het verpakken van inhoud. Er zijn slechts een paar gebieden om bij te werken om aan de slag te gaan.

## Eigenschappen van Packager bijwerken {#section_99904D35E99944A28FF43D924E516CC2}

Context voor de huidige taak

* Werk de volgende eigenschappen van de pakketsoftware bij voordat u het configuratiebestand gebruikt om de inhoud te verpakken:

### Door gebruiker opgegeven eigenschappen van XML-configuratiebestand

| Eigenschapnaam | Beschrijving |
|---|---|
| `policy_file` | pad naar beleidsbestand. De Adobe voorziet in verschillende vooraf geconfigureerde beleidslijnen waaruit kan worden gekozen. |
| `pkgr_pfx` | Pad naar inloggegevens van Packager. U moet uw eigen door de Adobe uitgegeven pakketreferentie opgeven ( [!DNL .pfx]) hier. |
| `pkgr_pfx_pwd` | Wachtwoord voor gegevens van Packager. U moet het wachtwoord hier aan uw Adobe-uitgegeven pakketreferentie verstrekken. |

## Pakket maken met opdrachtregel {#section_DFBE462679E34D62963BE201FD3321F9}

Voordat u inhoud gaat verpakken, moet u controleren of alle vereiste informatie in het configuratiebestand is opgenomen.

* Als u inhoud wilt verpakken met uw configuratiebestand, gebruikt u de volgende syntaxis op de opdrachtregel:

```
java -jar OfflinePackager.jar -conf_path [configuration filename]
```

Voorbeeldconfiguratiebestanden om uw inhoud in een HLS- of HDS-indeling in te pakken, krijgen een naam [!DNL config_hds.xml] en [!DNL config.hls.xml].

De HDS- of HLS-inhoud wordt uitgevoerd naar de [!DNL /output] map onder de directory Protection Kit. Alle artefacten die naar deze map worden geschreven, moeten op een HTTP-webserver worden gehost om te worden afgespeeld.
