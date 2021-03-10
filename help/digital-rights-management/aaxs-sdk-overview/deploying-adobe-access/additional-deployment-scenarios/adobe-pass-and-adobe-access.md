---
title: Adobe Pass en Adobe Access
description: Adobe Pass en Adobe Access
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---


# Adobe Pass en Adobe Access {#adobe-pass-and-adobe-access}

Adobe Pass ( [](https://www.adobe.com/products/adobepass/)) biedt gebruikers-/apparaatverificatie en autorisatie voor meerdere inhoudsproviders. De gebruiker moet een geldig kabeltelevisie of satellietabonnement hebben.

<!--<a id="fig_cln_bc2_44"></a>-->

![](assets/AdobePass_web.png)

Adobe Pass kan samen met Adobe Access worden gebruikt om de media-inhoud te beschermen. In dit scenario kan de videospeler (SWF) een ander SWF-bestand met de naam *Access Enabler* laden, dat wordt gehost door Adobe Systems. *Access Enabler* wordt gebruikt om verbinding te maken met de Adobe Pass-service en om SAML SSO-integratie met MVPD&#39;s (Multichannel Video Programming Distributor)-identiteitsproviders te vergemakkelijken. Dit betekent dat de browser van de gebruiker kort naar de MVPD-aanmeldingspagina wordt omgeleid, dat een AuthN-token wordt voortgezet en dat ten slotte met een in de cache opgeslagen AuthN-sessie wordt teruggegaan naar de website van de inhoud.

Met *Access Enabler* kunt u back-end autorisaties tussen de Adobe Pass-service en de MVPD vereenvoudigen. MVPD handhaaft de bedrijfslogica en bepaalt welke inhoud de gebruiker aan heeft. De bevoegdheid wordt voortgeduurd in een extra token AuthZ voor die inhoudsbron en wordt teruggestuurd naar de client.

De authentificatie en toestemmingstokens worden ondertekend gebruikend unieke identiteitskaart en privé sleutel van de cliënt van de Toegang van de Adobe om het knoeien of het voor de gek houden te vermijden. Dit token is alleen toegankelijk via *Access Enabler*.

De videospeler kan het proces teweegbrengen door `getAuthorization` op *Toegangsmanager* te roepen. Wanneer geldige AuthN/AuthZ tokens aanwezig zijn, *AccessEnabler* geeft een callback aan de videospeler uit die een kort-levend media teken voor het spelen van de videoinhoud zal omvatten.

Adobe Pass biedt een Java-bibliotheek voor mediatoken die kan worden geïmplementeerd op een server. Wanneer u de Flash Access-server gebruikt voor inhoudsbeveiliging, kunt u de validator voor mediatoken integreren met een insteekmodule op de server-side van Adobe Access om automatisch een algemene licentie uit te geven nadat u de mediatoken hebt gevalideerd. De inhoud wordt dan gestreamd van de CDN-servers naar de client. Om een inhoudsvergunning te verwerven, kan het korte-levende media teken aan de server van de Toegang van de Adobe worden voorgelegd, waar de geldigheid van het teken wordt geverifieerd en een vergunning kan worden uitgegeven.

Het token AuthN met een lange levensduur wordt over het algemeen gebruikt door *Access Enabler* voor alle inhoudsontwikkelaars om AuthN voor die MVPD-abonnee te vertegenwoordigen. Bovendien kunnen de Adobe Access Server en de Symbolische Verifier door CDN of een dienstverlener namens de inhoudsleverancier worden in werking gesteld.
