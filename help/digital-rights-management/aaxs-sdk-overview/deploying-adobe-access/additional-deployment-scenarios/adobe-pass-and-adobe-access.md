---
title: Adobe Pass en Adobe Access
description: Adobe Pass en Adobe Access
copied-description: true
exl-id: b9a90297-da24-416f-91de-6a31322f35fb
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# Adobe Pass en Adobe Access {#adobe-pass-and-adobe-access}

Adobe Pass ( [](https://www.adobe.com/products/adobepass/)) biedt gebruikers-/apparaatverificatie en autorisatie voor meerdere inhoudsproviders. De gebruiker moet een geldig kabeltelevisie of satellietabonnement hebben.

<!--<a id="fig_cln_bc2_44"></a>-->

![](assets/AdobePass_web.png)

Adobe Pass kan samen met Adobe Access worden gebruikt om de media-inhoud te beschermen. In dit scenario kan de videospeler (SWF) een andere SWF laden die de *Toegangsfunctie*, dat wordt gehost door Adobe Systems. De *Toegangsfunctie* wordt gebruikt om met de dienst van Adobe Pass te verbinden, en de integratie van SAML SSO met (Multichannel Video Programming Distributor) de identiteitsleverancierssystemen van MVPD te vergemakkelijken. Dit betekent dat de browser van de gebruiker kort naar de MVPD-aanmeldingspagina wordt omgeleid, dat een AuthN-token wordt voortgezet en dat ten slotte met een in de cache opgeslagen AuthN-sessie wordt teruggegaan naar de website van de inhoud.

De *Toegangsfunctie* kan achterste vergunningen tussen de dienst van Adobe Pass en MVPD dan vergemakkelijken. MVPD handhaaft de bedrijfslogica en bepaalt welke inhoud de gebruiker aan heeft. De bevoegdheid wordt voortgeduurd in een extra token AuthZ voor die inhoudsbron en wordt teruggestuurd naar de client.

De authentificatie en toestemmingstokens worden ondertekend gebruikend unieke identiteitskaart en privé sleutel van de cliënt van de Toegang van de Adobe om het knoeien of het voor de gek houden te vermijden. Deze token is alleen toegankelijk via de *Toegangsfunctie*.

De videospeler kan het proces activeren door `getAuthorization` op de *Toegangsfunctie*. Als er geldige AuthN/AuthZ-tokens aanwezig zijn, worden de *AccessEnabler* geeft een callback aan de videospeler uit die een kort-levend media teken voor het spelen van de videoinhoud zal omvatten.

Adobe Pass biedt een Java-bibliotheek voor mediatoken die kan worden geïmplementeerd op een server. Wanneer u de Flash Access-server gebruikt voor inhoudsbeveiliging, kunt u de validator voor mediatoken integreren met een insteekmodule op de server-side van Adobe Access om automatisch een algemene licentie uit te geven nadat u de mediatoken hebt gevalideerd. De inhoud wordt dan gestreamd van de CDN-servers naar de client. Om een inhoudsvergunning te verwerven, kan het korte-levende media teken aan de server van de Toegang van de Adobe worden voorgelegd, waar de geldigheid van het teken wordt geverifieerd en een vergunning kan worden uitgegeven.

Het lange levende teken AuthN wordt over het algemeen gebruikt door *Toegangsfunctie* over alle inhoudsontwikkelaars om AuthN voor die MVPD abonnee te vertegenwoordigen. Bovendien kunnen de Adobe Access Server en de Symbolische Verifier door CDN of een dienstverlener namens de inhoudsleverancier worden in werking gesteld.
