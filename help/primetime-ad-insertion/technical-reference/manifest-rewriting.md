---
title: Manifest Rewriting and Ad-Fetching Rules
description: 'Manifest Rewriting and Ad-Fetching Rules '
translation-type: tm+mt
source-git-commit: d5e948992d7c59e80b530c8f4619adbffc3c03d8
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---


# Duidelijke Regels voor herschrijven en ophalen {#manifest-rewriting}

Primetime Ad Insertion kan fragmenten herschrijven en elementen ophalen met behulp van eenvoudige regels voor zoeken en vervangen.  Dit kan worden gebruikt om https neer-om te zetten in HTTP- verzoeken, die prestaties zouden verbeteren door de handslangen van TLS te verwijderen.  Dit kan ook worden gebruikt om advertentie-elementen en cdn-elementen van dezelfde CDN te leveren.

Regels worden gedefinieerd als zoeken/vervangen van reguliere expressies en kunnen worden gebruikt om URL&#39;s te transformeren voordat ze worden verzonden en nadat ze in een manifest zijn ingevoegd.

Met deze voorbeeldregel worden alle advertentieverzoeken naar domain.com gedownconverteerd van https naar http.

```
find: "https://domain.com/(.*)"
replace: "http://domain.com/$1"
```

De volgende regel gebruikt de inhoud-CDN om advertenties te leveren die zich op Adobe-opslag-CDN bevinden.

```
find: "https?://primetime-a.akamaihd.net/(.*)"
replace: "http://mycdn.com/ad-mapping-pathname/$1"
```

Regels kunnen worden genoemd en toegelaten/onbruikbaar gemaakt door de `ptprotoswitch` parameter in Bootstrap API te wijzigen, die een komma gescheiden lijst van uit te voeren regels is.  Deze twee regels kunnen bijvoorbeeld allebei worden uitgevoerd door `ptprotoswitch=adfetch_rule1,adfetch_rule2` in te stellen:

```
<ruleSet>
    <rule name="rule1">
        <find><![CDATA[...]]></find>
        <replace><![CDATA[...]]></replace>
    </rule>
    <rule name="rule2">
        <find><![CDATA[...]]></find>
        <replace><![CDATA[...]]></replace>
    </rule>
</ruleSet>
```

Neem contact op met uw technische ondersteuning om deze regels voor uw account te maken/in te schakelen.