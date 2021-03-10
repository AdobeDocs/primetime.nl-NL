---
title: Een certificaataanvraag genereren (aanvrager)
description: Een certificaataanvraag genereren (aanvrager)
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---


# Een certificaataanvraag genereren (Requester) {#generate-a-certificate-signing-request-requester}

1. Een sleutelpaar genereren. Als u een hulpprogramma zoals OpenSSL wilt gebruiken, opent u een opdrachtvenster en voert u het volgende in:

   ```
   openssl genrsa -des3 -out mycompany-license.key 1024
   ```

   >[!NOTE]
   >
   >Adobe raadt aan om certificaattype (lic, pkgr, trans, trial of eval) op te nemen in de sleutelnaam. Deze naamgevingsconventie maakt het gemakkelijker om deze op uw licentieserver te implementeren. In dit voorbeeld wordt &quot;mijnbedrijf-licentie.sleutel&quot; gebruikt. Voor de Evaluatie- en proefversies gebruikt u &quot;mijnbedrijf-eval.key&quot; en &quot;mijnbedrijf-trial.key&quot;.

1. Voer een wachtwoord in om de persoonlijke sleutel te beveiligen.

   Wachtwoorden moeten ten minste 12 tekens bevatten. De tekens moeten bestaan uit een combinatie van ASCII-tekens en -cijfers in hoofdletters en kleine letters. Als u OpenSSL wilt gebruiken om een sterk wachtwoord te genereren, opent u een opdrachtvenster en voert u het volgende in:

   ```
   openssl rand -base64 8
   ```

1. Genereer een CSR (Certificate Signing Request).

   Als u OpenSSL wilt gebruiken om een CSR te genereren, opent u een opdrachtvenster en voert u het volgende in:

   ```
   openssl req -new -key mycompany-license.key -out mycompany-license.csr -batch 
   ```

1. U wordt gevraagd het wachtwoord voor de persoonlijke sleutel in te voeren.
1. Maak een reservekopie van uw persoonlijke sleutel en wachtwoord.

   Als u de persoonlijke sleutel verliest of als deze is gecompromitteerd, neemt u contact op met de beheerder van het Adobe-certificaat om uw certificaat in te trekken en een nieuw certificaat aan te vragen.

   >[!NOTE]
   >
   >Adobe raadt u aan een HSM te gebruiken om uw persoonlijke sleutel en wachtwoord te beschermen.

