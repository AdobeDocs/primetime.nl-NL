---
seo-title: WAR-bestand van licentieserver bijwerken
title: WAR-bestand van licentieserver bijwerken
uuid: 0cde53d6-185d-4bf2-84fc-0c31d17904a8
translation-type: tm+mt
source-git-commit: 1547eb3dd220fafc08df923f40504736c16a866c
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---


# Het WAR-bestand van de licentieserver bijwerken{#update-the-license-server-war-file}

Om cliënten te steunen die via een Op Premises server van de Individualisering geïndividualiseerd zijn, moet u de certificaatwortel van het vertrouwen van de Server van de Vergunning bijwerken om de onlangs verworven Vertrouwelijkheid van IndividualisatieCA te omvatten. Een Python-script ( [!DNL addIndivCert.py]) staat in de map [!DNL update_license_server].

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
