---
title: Manifest Rewriting and Ad-Fetching Rules
description: Manifest Rewriting and Ad-Fetching Rules
exl-id: 3750abc1-da60-4faf-ba85-37914f33641f
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# Manifest Rewriting and Ad-Fetching Rules {#manifest-rewriting}

Primetime Ad Insertion kan fragmenten herschrijven en elementen ophalen met behulp van eenvoudige regels voor zoeken en vervangen.  Dit kan worden gebruikt om https aan HTTP- verzoeken neer-om te zetten, die prestaties zouden verhogen door handshakes van TLS te verwijderen.  Dit kan ook worden gebruikt om advertentie-elementen en cdn-elementen van dezelfde CDN te leveren.

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

De regels kunnen worden genoemd en worden toegelaten/onbruikbaar gemaakt door te wijzigen `ptprotoswitch` in de Bootstrap API. Dit is een door komma&#39;s gescheiden lijst met regels die moeten worden uitgevoerd.  Deze twee regels kunnen bijvoorbeeld allebei worden uitgevoerd door `ptprotoswitch=adfetch_rule1,adfetch_rule2`:

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
