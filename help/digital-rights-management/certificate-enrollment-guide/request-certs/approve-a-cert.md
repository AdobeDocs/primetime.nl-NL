---
description: 'null'
seo-description: 'null'
seo-title: Een certificaat goedkeuren (accountbeheerder of secundaire beheerder)
title: Een certificaat goedkeuren (accountbeheerder of secundaire beheerder)
uuid: 5b95e2e8-abe9-4aef-bcb4-9b98ba6604d1
translation-type: tm+mt
source-git-commit: b4b50471ab0ba98329862322a61bf73aa9e471d5
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---


# Certificaat goedkeuren (Account of Secundaire Beheerder){#approve-a-certificate-account-or-secondary-administrator}

1. Meld u aan bij de site voor certificaatinschrijving.
1. Selecteer het tabblad **[!UICONTROL Certificates]**.
1. Controleer het verzoek om te controleren of het verzoek geldig is.
1. Als het verzoek geldig is, klik **[!UICONTROL Approve]**.

   U kunt ook een opmerking toevoegen. Er wordt een e-mail naar de aanvrager verzonden met de mededeling dat het verzoek is goedgekeurd door een van de bedrijfsbeheerders. Een exemplaar van deze e-mail wordt verzonden naar het bedrijf en de beheerders van de Adobe.

1. Als het verzoek niet geldig is, klikt u op **[!UICONTROL Reject]** en voert u een opmerking in het bevestigingsdialoogvenster in.

   Er wordt een e-mail naar de aanvrager verzonden waarin wordt verklaard dat het verzoek door een van de bedrijfsbeheerders is afgewezen. Een kopie van deze e-mail wordt naar de bedrijfsbeheerders verzonden.

Wanneer een beheerder een certificaataanvraag goedkeurt, verifieert Adobe de identiteit van de aanvrager. Adobe neemt contact op met de aanvrager bij het telefoonnummer dat in zijn profiel wordt vermeld.

De beheerder van Adobe probeert tweemaal binnen een periode van drie dagen contact op te nemen met Requester. Als de beheerder van de Adobe geen Vraag kan contacteren, verlaten zij een bericht verzoekend een vraag-terug of zij verstrekken een tijd wanneer zij opnieuw zullen roepen. Als de beheerder van de Adobe niet Requester kan bereiken, wordt een e-mail verzonden naar de beheerders.

>[!NOTE]
>
>Alleen de accountbeheerder en de secundaire beheerder kunnen het telefoonnummer van het bedrijf en de provocering van de aanvrager wijzigen.

Als de identiteit van de aanvrager wordt geverifieerd, ontvangt de aanvrager een e-mail met het PKCS#7-bestand ( [!DNL p7b]).

De aanvrager kan de PKCS#7-inhoud uit de hoofdtekst van de e-mail kopiëren en deze opslaan in een bestand of het bestand gebruiken dat aan de e-mail is gekoppeld. Adobe raadt aan dat wanneer u het PKSC#7-bestand opslaat, u de basisnaam gebruikt die u hebt gebruikt om de persoonlijke sleutel en het CSR-bestand te genereren.

>[!NOTE]
>
>Het bestand dat naar de aanvrager wordt verzonden, bevat alleen het certificaat. Het bestand bevat geen gegevens van persoonlijke sleutels.

