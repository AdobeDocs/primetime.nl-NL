---
description: 'null'
seo-description: 'null'
seo-title: Een certificaat goedkeuren (accountbeheerder of secundaire beheerder)
title: Een certificaat goedkeuren (accountbeheerder of secundaire beheerder)
uuid: 5b95e2e8-abe9-4aef-bcb4-9b98ba6604d1
translation-type: tm+mt
source-git-commit: b4b50471ab0ba98329862322a61bf73aa9e471d5

---


# Een certificaat goedkeuren (accountbeheerder of secundaire beheerder){#approve-a-certificate-account-or-secondary-administrator}

1. Meld u aan bij de site voor certificaatinschrijving.
1. Selecteer het **[!UICONTROL Certificates]** tabblad.
1. Controleer het verzoek om te controleren of het verzoek geldig is.
1. Als de aanvraag geldig is, klikt u op **[!UICONTROL Approve]**.

   U kunt ook een opmerking toevoegen. Er wordt een e-mail naar de aanvrager verzonden met de mededeling dat het verzoek is goedgekeurd door een van de bedrijfsbeheerders. Er wordt een kopie van deze e-mail verzonden naar het bedrijf en Adobe-beheerders.

1. Als de aanvraag niet geldig is, klikt u **[!UICONTROL Reject]** en voert u een opmerking in het bevestigingsdialoogvenster in.

   Er wordt een e-mail naar de aanvrager verzonden waarin wordt verklaard dat het verzoek door een van de bedrijfsbeheerders is afgewezen. Een kopie van deze e-mail wordt naar de bedrijfsbeheerders verzonden.

Als een beheerder een certificaataanvraag goedkeurt, controleert Adobe de identiteit van de aanvrager. Adobe neemt contact op met de aanvrager via het telefoonnummer dat in het profiel wordt vermeld.

De Adobe-beheerder probeert binnen een periode van drie dagen tweemaal contact op te nemen met de aanvrager. Als de Adobe-beheerder geen contact kan opnemen met de Requester, geeft hij of zij een bericht waarin om een call-back wordt gevraagd of geven een tijdstip op waarop hij of zij opnieuw zal bellen. Als de Adobe-beheerder de aanvrager niet kan bereiken, wordt een e-mail verzonden naar de beheerders.

>[!NOTE]
>
>Alleen de accountbeheerder en de secundaire beheerder kunnen het telefoonnummer van het bedrijf en de provocering van de aanvrager wijzigen.

Als de identiteit van de aanvrager wordt geverifieerd, ontvangt de aanvrager een e-mail met het PKCS#7-bestand ( [!DNL p7b]).

De aanvrager kan de PKCS#7-inhoud uit de hoofdtekst van de e-mail kopiëren en deze opslaan in een bestand of het bestand gebruiken dat aan de e-mail is gekoppeld. Adobe raadt u aan om bij het opslaan van het PKSC#7-bestand de basisnaam te gebruiken waarmee u de persoonlijke sleutel en het CSR-bestand hebt gegenereerd.

>[!NOTE]
>
>Het bestand dat naar de aanvrager wordt verzonden, bevat alleen het certificaat. Het bestand bevat geen gegevens van persoonlijke sleutels.

