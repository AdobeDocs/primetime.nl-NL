---
description: Deze sectie behandelt de grammatica van de configuratieinput, benadrukkend geldige en ongeldige inputopties, en verklarend hoe weggelaten facultatieve gebieden worden geïnterpreteerd.
title: RBOP Grammar
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '461'
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

1. De volgorde van de paren die in de objecten zijn gedefinieerd, is niet vast. Elke permutatie van de paren is dus geldig.

   Als we bijvoorbeeld een object als dit hebben gedefinieerd:

   ```
   {  
     "foo": <Foo>,  
     "bar":<Bar>,  
     "baz":<Baz>  
   }
   ```

   de volgende structuur wordt ook als geldig beschouwd: =

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

   dan is de volgende instantie ongeldig, omdat er twee zijn `foo` paren binnen hetzelfde object:

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

1. Voor definities waarbij een of meer reeksen kunnen worden gekozen, behandelt u de tekenreeksen als een set, waarin dubbele items als één item worden beschouwd. Bijvoorbeeld: `["foo", "bar", "foo", "baz"]` is gelijk aan `["foo", "bar", "baz"]`

1. Voor het definiëren van getallen wordt een spatie tussen de regels gebruikt (bijvoorbeeld `Digit Digits`), maar bij toepassing van de regel mag deze ruimte niet worden gebruikt.

   Als we bijvoorbeeld het getal uitdrukken *123* volgens de regel NonZeroInteger moet deze worden uitgedrukt als `123` eerder dan `1 2 3`, ook al bevat de regel ruimte tussen NonZeroDigit en Cijfers.

1. Sommige regels staan meerdere formulieren toe. In deze gevallen worden de verschillende formulieren gescheiden door de `'|'` teken.

   Deze regel:

   ```
   Foo ::= "A" | "B" | "C"
   ```

   betekent dat een `Foo` kunnen worden vervangen door &quot;A&quot;, &quot;B&quot; of &quot;C&quot;. Dit mag niet worden verward met een formulier dat meerdere regels omvat. Dat is een functie waarmee langere formulieren beter leesbaar worden gemaakt.

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

## Semantica: geldige maar ongeldige configuraties {#section_709BE240FF0041D4A1B0A0A7544E4966}

De *Voorbeeld van configuratie voor uitvoerbeveiliging* onderwerp voorlegde een geldige configuratie samen met zijn semantische betekenis voor. De vorige sectie in *dit* het onderwerp voorlegde de grammaticaregels voor configuraties voor. Hoewel de grammatica helpt syntactische correctheid te verzekeren, zijn er syntactisch wettige configuraties die niet semantisch correct zijn (d.w.z., zijn zij niet logisch). Deze sectie stelt configuraties voor die *syntactisch* wettelijk, maar *semantisch* onjuist. Houd er rekening mee dat de voorbeelden in dit gedeelte zijn beperkt tot de minimale structuur die nodig is om het te bespreken scenario te illustreren.

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
