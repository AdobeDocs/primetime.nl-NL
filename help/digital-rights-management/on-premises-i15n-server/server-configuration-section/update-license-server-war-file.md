---
title: WAR-bestand van licentieserver bijwerken
description: WAR-bestand van licentieserver bijwerken
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---


# Het WAR-bestand van de licentieserver bijwerken{#update-the-license-server-war-file}

Om cliënten te steunen die via een Op Premises server van de Individualisering geïndividualiseerd zijn, moet u de certificaatwortel van het vertrouwen van de Server van de Vergunning bijwerken om de onlangs verworven Vertrouwelijkheid van IndividualisatieCA te omvatten. Een Python-script ( [!DNL addIndivCert.py]) wordt opgenomen in de map [!DNL update_license_server].

Ga als volgt te werk om de licentieserver bij te werken:

1. Kopieer de WAR-bestanden die u wilt bijwerken (voorbeelden: [!DNL flashaccess.war], [!DNL faxsks.war]).
1. Zorg ervoor dat de WAR-bestanden zijn ontgrendeld en hun machtigingen zijn ingesteld zodat ze kunnen worden gewijzigd.
1. Voer het Python-script [!DNL addIndivCert.py] uit om de WAR-bestanden van de licentieserver bij te werken.

   De invoer voor het script is als volgt:

   * `cert`: PKCS12-bestand met het certificaat Individualization CA
   * `war`: WAR-bestand dat moet worden bijgewerkt

   Het uitvoerbestand is een bijgewerkt WAR-bestand.

   ```
   ./addIndivCert.py -cert NEW_IndivCA.cer -war flashaccess.war
   ```

De WAR-bestanden worden gewijzigd. Indien nodig kunt u het Python-script naar wens bewerken. Nadat u de updates uitvoert, kunt u de dossiers van WAR normaal opstellen.
