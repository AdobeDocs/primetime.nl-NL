---
seo-title: HSM-voorkeuren
title: HSM-voorkeuren
uuid: 1b97d582-d4b6-48cd-9c24-2d13493571e9
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---


# HSM-voorkeuren {#hsm-preferences}

Voorkeuren op dit tabblad hoeven alleen te worden opgegeven als het selectievakje **[!UICONTROL Enable HSM]** is ingeschakeld op het tabblad Packager. In de volgende tabel worden deze voorkeuren beschreven:

| Voorkeur | Beschrijving |
|---|---|
| Sun PKCS#11 Config-bestandsnaam | Het volledige pad naar het configuratiebestand van de Sun PKCS#11-provider. Zie de Java PKCS#11 Reference Guide op de website van Sun voor meer informatie over de inhoud van dit configuratiebestand. |
| Wachtwoord voor partitie | Het wachtwoord voor de verdeling HSM die in het PKCS#11 configuratiedossier wordt gespecificeerd. |
| Certificaatalias licentieserver | Alias for Adobe-issued license server certificate stored on HSM. Dit certificaat wordt gebruikt om de CEK tijdens het verpakken te coderen. Geef dit op in plaats van *Licentieservercertificaat* op het tabblad Packager. |
| Alias transportcertificaat licentieserver | Alias voor door Adobe uitgegeven servertransportcertificaat dat is opgeslagen op HSM. Dit certificaat wordt gebruikt om communicatie tussen de client en de licentieserver te beveiligen. Specificeer dit in plaats van *Certificaat van het Vervoer van de Server van de Vergunning* in het lusje van de Packager. |
| Credentiële alias van Packager | Alias for Adobe-issued packager credential (certificate and private key) stored on HSM. Hiermee worden de metagegevens tijdens het verpakken ondertekend. Geef dit op in plaats van *Packager Credential* op het tabblad Packager. |
| Credentiële alias licentieserver | Alias for Adobe-issued license server credential (certificate and private key) stored on HSM. Deze referentie wordt gebruikt om de Lijsten van de Update van het Beleid te ondertekenen. Geef dit op in plaats van *Referentie licentieserver* op het tabblad Lijst voor beleidsupdates. (Deze alias is waarschijnlijk hetzelfde als *Certificaat van licentieserver Alias*.) |

