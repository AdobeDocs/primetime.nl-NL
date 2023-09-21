---
title: Adobe Primetime-verificatie en Adobe Primetime DRM
description: Adobe Primetime-verificatie en Adobe Primetime DRM
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# Adobe Primetime-verificatie en Adobe Primetime DRM {#adobe-primetime-authentication-and-adobe-primetime-drm}

Adobe Primetime-verificatie ( [https://www.adobe.com/products/adobepass/](https://www.adobe.com/products/adobepass/)) biedt gebruikers-/apparaatverificatie en autorisatie voor meerdere inhoudsproviders. De gebruiker moet een geldig kabeltelevisie of satellietabonnement hebben.

<!--<a id="fig_cln_bc2_44"></a>-->

![](assets/AdobePass_web.png)

Adobe Primetime-verificatie kan samen met Adobe Primetime DRM worden gebruikt om de media-inhoud te beschermen. In dit scenario kan de videospeler (SWF) een andere SWF laden die de *Toegangsfunctie*, dat wordt gehost door Adobe Systems. De *Toegangsfunctie* wordt gebruikt om met de de authentificatieservice van Adobe Primetime te verbinden, en de integratie van SAML SSO met (Multichannel Video Programming Distributor) de identiteitsleverancierssystemen van MVPD te vergemakkelijken. Dit betekent dat de browser van de gebruiker kort naar de MVPD-aanmeldingspagina wordt omgeleid, dat een AuthN-token wordt voortgezet en dat ten slotte met een in de cache opgeslagen AuthN-sessie wordt teruggegaan naar de website van de inhoud.

De *Toegangsfunctie* kan achterste vergunningen tussen de authentificatiedienst van Adobe Primetime en MVPD dan vergemakkelijken. MVPD handhaaft de bedrijfslogica en bepaalt welke inhoud de gebruiker aan heeft. De bevoegdheid wordt voortgeduurd in een extra token AuthZ voor die inhoudsbron en wordt teruggestuurd naar de client.

De verificatie- en autorisatietokens worden ondertekend met de unieke id en de persoonlijke sleutel van de Primetime DRM-client om te voorkomen dat er wordt geknoeid met of geknoeid met de computer. Deze token is alleen toegankelijk via de *Toegangsfunctie*.

De videospeler kan het proces activeren door `getAuthorization` op de *Toegangsfunctie*. Als er geldige AuthN/AuthZ-tokens aanwezig zijn, worden de *AccessEnabled* geeft een callback aan de videospeler uit die een kort-levend media teken voor het spelen van de videoinhoud zal omvatten.

Adobe Primetime-verificatie biedt een Java-bibliotheek voor mediatoken-validatie die kan worden geïmplementeerd op een server. Wanneer u de Primetime DRM-server gebruikt voor inhoudsbeveiliging, kunt u de mediatoken-validator integreren met een Primetime DRM-plug-in voor servers om automatisch een algemene licentie uit te geven nadat u de mediatoken hebt gevalideerd. De inhoud wordt dan gestreamd van de CDN-servers naar de client. Als u een inhoudslicentie wilt aanschaffen, kan het kortstondige media-token worden verzonden naar de Primetime DRM-server, waar de geldigheid van het token wordt geverifieerd en een licentie kan worden uitgegeven.

Het lange levende teken AuthN wordt over het algemeen gebruikt door *Toegangsfunctie* over alle inhoudsontwikkelaars om AuthN voor die MVPD abonnee te vertegenwoordigen. Bovendien kunnen de Server Primetime DRM en de Symbolische Verifier door CDN of een dienstverlener namens de inhoudsleverancier worden in werking gesteld.
