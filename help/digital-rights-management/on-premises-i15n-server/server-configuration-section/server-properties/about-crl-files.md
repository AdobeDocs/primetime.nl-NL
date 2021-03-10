---
title: Over CRL-bestanden
description: Over CRL-bestanden
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '305'
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

Hieronder vindt u extern gehoste CRL&#39;s die alleen door de licentieservers worden gebruikt:

* URL: [!DNL <ht<span></span>tps://crl2.adobe.com/Adobe/FlashAccessIndividualizationCA.crl>]
* Bestand: [!DNL http___crl2.adobe.com_Adobe_FlashAccessIndividualizationCA.crl]
* Geldigheid: Goed voor ongeveer 3 maanden na de aanmaak

* URL: [!DNL <ht<span></span>tps://individualization-crl.primetime.adobe.com/FlashAccessIndividualizationCA.crl>]
* Bestand: [!DNL http___individualization-crl.primetime.adobe.com_FlashAccessIndividualizationCA.crl]
* Geldigheid: Goed voor ongeveer 3 maanden na de aanmaak

* URL: [!DNL <ht<span></span>tps://individualization-crl.s3-website-us-east-1.amazonaws.com/FlashAccessIndividualizationCA.crl]
* Bestand: [!DNL http___individualization-crl.s3-website-us-east-1.amazonaws.com_FlashAccessIndividualizationCA.crl]
* Geldigheid: Goed voor ongeveer 3 maanden na de aanmaak

Naast de bovengenoemde CRLs, moet u een extra CRL creëren en handhaven. Dit is de Individualisatie CA CRL, zoals gespecificeerd in [Create Individualization CA CRL](../../../on-premises-i15n-server/server-configuration-section/server-properties/create-i15n-ca-crl.md) sectie van dit document.

CRL&#39;s moeten volgens de planning 45 dagen voor ze verlopen. Hierdoor hebt u voldoende tijd om nieuw gegenereerde CRL&#39;s van internet te verkrijgen en te installeren. U moet ervoor zorgen dat CRL-bestanden worden bijgewerkt voordat ze verlopen.
