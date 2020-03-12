---
seo-title: Rechten afspelen
title: Rechten afspelen
uuid: 90f2a7a6-6637-4d10-9afe-6d2e77fc4185
translation-type: tm+mt
source-git-commit: ed1430bdcb590a53fa69b324ef340ad636b2fa7c

---


# Rechten afspelen {#play-rights}

In de volgende tabel worden de voorkeuren voor afspeelrechten beschreven:

| Voorkeur | Beschrijving |
|--- |--- |
| Afspeelvenster | De duur van een licentie is geldig (in minuten) nadat de gebruiker de beveiligde inhoud voor het eerst afspeelt. |
| Uitvoerbeveiliging | Bepaalt of uitvoer naar externe renderingapparaten moet worden beveiligd. De analoge en digitale output kan onafhankelijk worden gespecificeerd. |
| Beperkingen | Blacklist of client versions not allowed to play content. Alle kolommen zijn optioneel. |
| DRM | Hiermee geeft u een lijst op met DRM-versies die beveiligde inhoud niet mogen afspelen. |
| Runtime | Hier geeft u een lijst op met versies bij uitvoering die geen beveiligde inhoud mogen afspelen. |
| Minimaal beveiligingsniveau |  |
| DRM | Minimaal DRM-beveiligingsniveau vereist om beveiligde inhoud af te spelen. |
| Runtime | Minimale runtime beveiligingsniveau vereist om beveiligde inhoud af te spelen. |
| Toegestane toepassingen | Whitelist of client applications allowed to play content. Wanneer geen toepassingen worden opgegeven, is een SWF- of AIR-toepassing toegestaan. |
| SWF | Lijst met SWF-URL&#39;s die beveiligde inhoud mogen afspelen. |
| AIR | Lijst met AIR-toepassingen die beveiligde inhoud mogen afspelen. Uitgever-id is vereist. De overige velden zijn optioneel. |

Flash Access Manager ondersteunt beleid dat meerdere afspeelrechten bevat. Als u een beleid wilt maken met meer dan één Play Right-optie, gebruikt u de knop &quot;Extra rechts afspelen toevoegen&quot; en vult u de gewenste kenmerken in voor elk Play Right-item.

Wanneer de klant een licentie gebruikt, gebruikt de client het eerste Play Right waarvoor de licentie aan alle vereisten voldoet. U kunt meerdere spelrechten gebruiken om verschillende beperkingen voor verschillende besturingssystemen op te geven. Het is bijvoorbeeld mogelijk één recht op te geven met Uitvoerbeveiliging vereist voor Windows (door DRM-versies op Macintosh en Linux op te nemen) en een tweede recht op te geven met Uitvoerbeveiliging &quot;Gebruik indien beschikbaar&quot; op andere platforms (door DRM-versies op Windows op te nemen).
