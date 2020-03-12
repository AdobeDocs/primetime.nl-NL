---
seo-title: Adobe Pass en Adobe Access
title: Adobe Pass en Adobe Access
uuid: 09e75cd7-00b3-4f0f-869e-43dc4d5c3bf7
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Adobe Pass en Adobe Access {#adobe-pass-and-adobe-access}

Adobe Pass ( [](https://www.adobe.com/products/adobepass/)) biedt gebruikers-/apparaatverificatie en autorisatie voor meerdere inhoudsproviders. De gebruiker moet een geldig kabeltelevisie of satellietabonnement hebben.

<!--<a id="fig_cln_bc2_44"></a>-->

![](assets/AdobePass_web.png)

Adobe Pass kan samen met Adobe Access worden gebruikt om de media-inhoud te beschermen. In dit scenario kan de videospeler (SWF) een ander SWF-bestand laden dat *Access Enabler* wordt genoemd en dat wordt gehost door Adobe Systems. De *Toegangsfunctie* wordt gebruikt om verbinding te maken met de service Adobe Pass en om SAML SSO-integratie met MVPD&#39;s (Multichannel Video Programming Distributor)-identiteitsproviders te vergemakkelijken. Dit betekent dat de browser van de gebruiker kort naar de MVPD-aanmeldingspagina wordt omgeleid, dat een AuthN-token wordt voortgezet en dat ten slotte met een in de cache opgeslagen AuthN-sessie wordt teruggegaan naar de website van de inhoud.

Met *Access Enabler* kunt u vervolgens back-endautorisaties tussen Adobe Pass-service en MVPD vergemakkelijken. MVPD handhaaft de bedrijfslogica en bepaalt welke inhoud de gebruiker aan heeft. De bevoegdheid wordt voortgeduurd in een extra token AuthZ voor die inhoudsbron en wordt teruggestuurd naar de client.

De verificatie- en autorisatietokens worden ondertekend met de unieke id en de persoonlijke sleutel van de Adobe Access-client om te voorkomen dat er wordt geknoeid met of gesmokkeld. Deze token is alleen toegankelijk via *Access Enabler*.

De videospeler kan het proces activeren door `getAuthorization` de *Toegangsfunctie* aan te roepen. Wanneer de geldige tokens AuthN/AuthZ aanwezig zijn, geeft *AccessEnabler* een callback aan de videospeler uit die een kort-levend media teken voor het spelen van de videoinhoud zal omvatten.

Adobe Pass biedt een Java-bibliotheek voor mediatoken die kan worden geïmplementeerd op een server. Wanneer u de Flash Access-server gebruikt voor inhoudsbeveiliging, kunt u de validator voor mediatoken integreren met een Adobe Access-insteekmodule voor servers om automatisch een algemene licentie uit te geven nadat u de mediatoken hebt gevalideerd. De inhoud wordt dan gestreamd van de CDN-servers naar de client. Als u een inhoudslicentie wilt aanschaffen, kan het kortstondige media-token worden verzonden naar de Adobe Access-server, waar de geldigheid van het token wordt geverifieerd en een licentie kan worden uitgegeven.

Het token AuthN met een lange levensduur wordt over het algemeen gebruikt door *Access Enabler* voor alle inhoudsontwikkelaars om AuthN voor die MVPD-abonnee te vertegenwoordigen. Daarnaast kunnen de Adobe Access Server en de Token Verifier worden uitgevoerd door de CDN of een serviceprovider namens de contentprovider.
