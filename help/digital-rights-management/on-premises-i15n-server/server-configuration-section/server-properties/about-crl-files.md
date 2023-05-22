---
title: Over CRL-bestanden
description: Over CRL-bestanden
copied-description: true
exl-id: 126a323d-9433-4a1e-a617-2d3bbf717cce
source-git-commit: 6a00df9c061da43f6efa49d927873db629568597
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# Over CRL-bestanden {#about-crl-files}

Individualisatie- en licentieservers moeten verschillende CRL-bestanden (Certificate Revocation List) in de cache hebben geplaatst op de schijf waarop de toepassingsserver wordt uitgevoerd (bijvoorbeeld Tomcat) om correct te kunnen functioneren. Nieuwe CRL-bestanden moeten regelmatig worden gedownload en in de cache worden geplaatst. Als de geldigheidsperiode van CRL- dossiers op schijf wordt toegestaan te verstrijken, zal de Server van de Individualisatie om cliënten te individualiseren weigeren, en de Server van de Vergunning zal weigeren om vergunningen uit te geven.

De CRLs caching aan schijf moet dossiernamen hebben die overeenkomstige URLs aanpassen. Speciale tekens zoals de slashes &#39;:&#39; en &#39;/&#39; worden in de bestandsnamen omgezet in onderstrepingstekens &#39;_&#39;.

Hieronder volgt een lijst met extern gehoste CRL&#39;s die door zowel de Individualization- als de Licentieservers worden gebruikt:

* **Tussenproduct CRL:**

   * URL: [!DNL <ht<span></span>tps://crl2.adobe.com/Adobe/FlashAccessIntermediateCA.crl>]
   * Bestand: [!DNL http___crl2.adobe.com_Adobe_FlashAccessIntermediateCA.crl]
   * Geldigheid: Goed voor ongeveer 12 maanden vanaf de aanmaak

* **Root CRL:**

   * URL: [!DNL <ht<span></span>tps://crl2.adobe.com/Adobe/FlashAccessRootCA.crl>]
   * Bestand: [!DNL http___crl2.adobe.com_Adobe_FlashAccessRootCA.crl]
   * Geldigheid: Goed voor ongeveer 5 jaar na de creatie

* **Laatste CRL:**

   * URL: [!DNL <ht<span></span>tps://crl3.adobe.com/AdobeSystemsIncorporatedFlashAccessRuntime/LatestCRL.crl>]
   * Bestand: [!DNL http___crl3.adobe.com_AdobeSystemsIncorporatedFlashAccessRuntime_LatestCRL.crl]
   * Geldigheid: Goed voor ongeveer 3 maanden na de aanmaak

Neem contact op met de Adobe Support voor informatie over de extern gehoste CRL&#39;s die door de licentieservers kunnen worden gebruikt.

<!---

Commenting out because of a security vulnerability reported in Jira PSIRT-20689. 

The following are externally hosted CRLs that are used only by the License Servers:

* URL: `https://crl2.adobe.com/Adobe/FlashAccessIndividualizationCA.crl`

* File: `http___crl2.adobe.com_Adobe_FlashAccessIndividualizationCA.crl`

* Validity: Good for approximately 3 months from creation

* URL: `https://individualization-crl.primetime.adobe.com/FlashAccessIndividualizationCA.crl`

* File: `http___individualization-crl.primetime.adobe.com_FlashAccessIndividualizationCA.crl`

* Validity: Good for approximately 3 months from creation

* URL: `https://individualization-crl.s3-website-us-east-1.amazonaws.com/FlashAccessIndividualizationCA.crl`

* File: `http___individualization-crl.s3-website-us-east-1.amazonaws.com_FlashAccessIndividualizationCA.crl`

* Validity: Good for approximately 3 months from creation

--->

Naast extern gehoste CRL&#39;s kunt u een extra CRL maken en onderhouden. Dit is de Individalization CA CRL, zoals gespecificeerd in [Individuele CA CRL maken](../../../on-premises-i15n-server/server-configuration-section/server-properties/create-i15n-ca-crl.md) van dit document.

CRL&#39;s moeten volgens de planning 45 dagen voor ze verlopen. Hierdoor hebt u voldoende tijd om nieuw gegenereerde CRL&#39;s van internet te verkrijgen en te installeren. U moet ervoor zorgen dat CRL-bestanden worden bijgewerkt voordat ze verlopen.
