---
description: Deze sectie behandelt de grammatica van de configuratieinput, benadrukkend geldige en ongeldige inputopties, en verklarend hoe weggelaten facultatieve gebieden worden geïnterpreteerd.
seo-description: Deze sectie behandelt de grammatica van de configuratieinput, benadrukkend geldige en ongeldige inputopties, en verklarend hoe weggelaten facultatieve gebieden worden geïnterpreteerd.
seo-title: RBOP Grammar
title: RBOP Grammar
uuid: d9064e39-593a-4767-b835-287640b4c94a
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---


# RBOP Grammar {#rbop-grammar}

Deze sectie behandelt de grammatica van de configuratieinput, benadrukkend geldige en ongeldige inputopties, en verklarend hoe weggelaten facultatieve gebieden worden geïnterpreteerd.

De op resolutie-gebaseerde grammatica van de outputbescherming wordt gedefinieerd als opeenvolging van regels, waar elke regel veelvoudige, geldige vormen kan hebben:

```
Rule ::=       
 
    Form 
     
AnotherRule ::=     
 
    DifferentForm 
```

## Grammaticaregels toepassen {#section_A7216BD585FF4EB88737B643B36C2781}

>[!NOTE]
>
>Om de leesbaarheid van de grammatica te verbeteren, worden de volgende eigenschappen niet weerspiegeld binnen de grammatica maar nog houden waar:

1. De volgorde van de paren die in de objecten zijn gedefinieerd, is niet vast. elke permutatie van de paren is dus geldig .

   Als we bijvoorbeeld een object als dit hebben gedefinieerd:

   ```
   {  
     "foo": <Foo>,  
     "bar":<Bar>,  
     "baz":<Baz>  
   }
   ```

   de volgende structuur wordt eveneens als geldig beschouwd : =

   ```
   {  
     "baz":<Baz>,  
     "foo":<Foo>,  
     "bar":<Bar> 
   }
   ```

1. Voor elk paar binnen een voorwerp, wordt verondersteld dat slechts één geval van dat paar binnen een bepaalde instantie van een bepaald voorwerp bestaat.

   Als we bijvoorbeeld een object als dit hebben gedefinieerd:

   ```
   {  
     "foo": <Foo>,  
     "bar":<Bar>,  
     "baz":<Baz>  
   }
   ```

   De volgende instantie zou dan ongeldig zijn, omdat er twee `foo` paren binnen hetzelfde object zijn:

   ```
   { 
     "foo":<Foo>,  
     "bar":<Bar>,  
     "baz":<Baz>,  
   } 
   ```

   Op dezelfde manier met twee objecten, zoals:

   ```
   {  
     "foo": <Foo>,  
     "bar":<Bar>,  
     "baz":<Baz>  
   }
   ```

   en:

   ```
   {  
     "baz":<Baz>,  
     "foo":<Foo>,  
     "bar":<Bar> 
   }
   ```

   is geldig, omdat het onafhankelijke instanties van hetzelfde object zijn.

1. Voor definities waarbij een of meer reeksen kunnen worden gekozen, behandelt u de tekenreeksen als een set, waarin dubbele items als één item worden beschouwd. `["foo", "bar", "foo", "baz"]` is bijvoorbeeld gelijk aan `["foo", "bar", "baz"]`

1. Voor het definiëren van getallen wordt een spatie gebruikt tussen de regels (bijvoorbeeld `Digit Digits`), maar deze spatie moet niet worden gebruikt bij het toepassen van de regel.

   Als we bijvoorbeeld het getal *103* per de regel NonZeroInteger uitdrukken, moet deze worden uitgedrukt als `123` in plaats van `1 2 3`, ook al bevat de regel een ruimte tussen NonZeroDigit en Cijfers.

1. Sommige regels staan meerdere formulieren toe. In deze gevallen worden de verschillende formulieren gescheiden door het teken `'|'`.

   Deze regel:

   ```
   Foo ::= "A" | "B" | "C"
   ```

   betekent dat een instantie van `Foo` kan worden vervangen door &quot;A&quot;, &quot;B&quot; of &quot;C&quot;. Dit mag niet worden verward met een formulier dat meerdere regels omvat. hiermee kunt u langere formulieren leesbaarder maken.

## De grammatica {#section_52189FD66B1A46BA9F8FDDE1D7C8E8E8}

```
PixelBasedOPConfig ::= 
      {} 
    | { "maxPixel": NonNegativeInteger } 
    | { "pixelConstraints": PixelConstraintsSeq } 
    | { "pixelConstraints": PixelConstraintsSeq, 
        "maxPixel": NonNegativeInteger } 
 
PixelConstraintsSeq ::= 
      [] 
    | [ PixelConstraints ] 
 
PixelConstraints ::= 
      PixelConstraint 
    | PixelConstraint, PixelConstraints 
 
PixelConstraint ::= 
      { "pixelCount": NonNegativeInteger } 
    | { "pixelCount": NonNegativeInteger, 
        "digital": DigitalOutputRestrictionsSeq } 
    | { "pixelCount": NonNegativeInteger, 
        "analog": AnalogOutputRestriction } 
    | { "pixelCount": NonNegativeInteger, 
        "ota": OTAOutputRestriction } 
    | { "pixelCount": NonNegativeInteger, 
        "digital": DigitalOutputRestrictionsSeq, 
        "analog": AnalogOutputRestriction } 
    | { "pixelCount": NonNegativeInteger, 
        "digital": DigitalOutputRestrictionsSeq, 
         "ota": OTAOutputRestriction } 
    | { "pixelCount": NonNegativeInteger, 
        "analog": AnalogOutputRestriction, 
        "ota": OTAOutputRestriction } 
    | { "pixelCount": NonNegativeInteger, 
        "digital": DigitalOutputRestrictionsSeq, 
        "analog": AnalogOutputRestriction, 
        "ota": OTAOutputRestriction } 
 
DigitalOutputRestrictionsSeq ::= 
      [] 
    | [ DigitalOutputRestrictions ] 
 
DigitalRestrictions ::= 
      DigitalRestriction 
    | DigitalRestriction, DigitalRestrictions 
 
DigitalRestriction ::= 
      { "output": DigitalOutputOption } 
    | { "output": DigitalOutputOption, "hdcp": HDCP } 
 
DigitalOutputOption ::= 
      "NO_PROTECTION" 
    | "USE_IF_AVAILABLE" 
    | "REQUIRED" 
    | "NO_PLAYBACK" 
 
HDCP ::= 
    { "major": PositiveInteger, "minor": NonNegativeInteger } 
 
AnalogOutputRestriction ::= 
    { "output": AnalogOutputOption } 
 
AnalogOutputOption ::= 
      "NO_PROTECTION" 
    | "USE_IF_AVAILABLE" 
    | "USE_IF_AVAILABLE_ACP" 
    | "USE_IF_AVAILABLE_CGMSA" 
    | "REQUIRED" 
    | "REQUIRED_ACP" 
    | "REQUIRED_CGMSA" 
    | "NO_PLAYBACK" 
 
OTAOutputRestriction ::= 
    { "whitelist": OTAWhitelistSeq } 
 
OTAWhitelistSeq ::= 
      [] 
    | [ OTAWhitelist ] 
 
OTAWhitelist ::= 
      OTAConnectionType 
    | OTAConnectionType, OTAWhitelist 
 
OTAConnectionType ::= 
      "MIRACAST" 
    | "AIRPLAY" 
    | "WIDI" 
    | "DLNA" 
 
NonNegativeInteger ::= 
      Digit 
    | NonZeroDigit Digits 
 
PositiveInteger ::= 
      NonZeroDigit 
    | NonZeroDigit Digits 
 
Digits ::= 
      Digit 
    | Digit Digits 
 
Digit ::= 
      0 
    | NonZeroDigit

NonZeroDigit ::= 
      1 
    | 2 
    | 3 
    | 4 
    | 5 
    | 6 
    | 7 
    | 8 
    | 9
```

## Semantiek: Geldige maar ongeldige configuraties {#section_709BE240FF0041D4A1B0A0A7544E4966}

Het *onderwerp van de Bescherming van de Output van de Steekproef* stelde een geldige configuratie samen met zijn semantische betekenis voor. De vorige sectie in *dit* onderwerp presenteerde de grammaticaregels voor configuraties. Hoewel de grammatica helpt syntactische correctheid te verzekeren, zijn er syntactisch wettige configuraties die niet semantisch correct zijn (d.w.z., zijn zij niet logisch). In deze sectie worden configuraties weergegeven die *syntactisch* legaal zijn, maar *semantisch* onjuist. Houd er rekening mee dat de voorbeelden in dit gedeelte zijn beperkt tot de minimale structuur die nodig is om het te bespreken scenario te illustreren.

* Het is niet toegestaan meerdere pixelbeperkingen met hetzelfde aantal pixels te definiëren.

   ```
   {  
     "pixelConstraints":  
       [  
         { "pixelCount": 720 }  
       ]  
    }  
   ```

* Een aantal pixels mag de opgegeven maximale pixelresolutie niet overschrijden.

   ```
   { 
     "maxPixel": 720, 
     "pixelConstraints": 
       [ 
         {"pixelCount": 1080} 
       ] 
   } 
   ```
