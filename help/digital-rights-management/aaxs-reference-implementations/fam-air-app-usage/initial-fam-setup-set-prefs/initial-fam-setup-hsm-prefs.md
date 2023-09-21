---
title: HSM-voorkeuren
description: HSM-voorkeuren
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# HSM-voorkeuren {#hsm-preferences}

Voorkeuren op dit tabblad hoeven alleen te worden opgegeven als de **[!UICONTROL Enable HSM]** is geselecteerd op het tabblad Packager. In de volgende tabel worden deze voorkeuren beschreven:

| Voorkeur | Beschrijving |
|---|---|
| Sun PKCS#11 Config-bestandsnaam | Het volledige pad naar het configuratiebestand van de Sun PKCS#11-provider. Zie de Java PKCS#11 Reference Guide op de website van Sun voor meer informatie over de inhoud van dit configuratiebestand. |
| Wachtwoord voor partitie | Het wachtwoord voor de verdeling HSM die in het PKCS#11 configuratiedossier wordt gespecificeerd. |
| Certificaatalias licentieserver | Alias for Adobe-issued license server certificate stored on HSM. Dit certificaat wordt gebruikt om de CEK tijdens het verpakken te coderen. Geef dit op in plaats van *Certificaat van licentieserver* op het tabblad Packager. |
| Alias transportcertificaat voor licentieserver | Alias voor door Adobe uitgegeven servertransportcertificaat opgeslagen op HSM. Dit certificaat wordt gebruikt om communicatie tussen de client en de licentieserver te beveiligen. Geef dit op in plaats van *Vervoercertificaat licentieserver* op het tabblad Packager. |
| Credentiële alias van Packager | Alias for Adobe-issued packager credential (certificate and private key) stored on HSM. Hiermee worden de metagegevens tijdens het verpakken ondertekend. Geef dit op in plaats van *Packager Credential* op het tabblad Packager. |
| Credentiële alias licentieserver | Alias for Adobe-issued license server credential (certificate and private key) stored on HSM. Deze referentie wordt gebruikt om de Lijsten van de Update van het Beleid te ondertekenen. Geef dit op in plaats van *Credentieserverreferentie* in het tabblad Lijst voor beleidsupdates. (Deze alias is waarschijnlijk gelijk aan *Certificaatalias licentieserver*.) |
