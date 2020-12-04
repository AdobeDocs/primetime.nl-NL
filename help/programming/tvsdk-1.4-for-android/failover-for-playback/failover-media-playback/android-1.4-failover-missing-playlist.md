---
description: Wanneer een volledige afspeellijst ontbreekt, bijvoorbeeld wanneer het M3U8-bestand dat in een manifestbestand op hoofdniveau is opgegeven niet wordt gedownload, probeert TVSDK het bestand te herstellen. Als het niet kan herstellen, bepaalt uw toepassing de volgende stap.
seo-description: Wanneer een volledige afspeellijst ontbreekt, bijvoorbeeld wanneer het M3U8-bestand dat in een manifestbestand op hoofdniveau is opgegeven niet wordt gedownload, probeert TVSDK het bestand te herstellen. Als het niet kan herstellen, bepaalt uw toepassing de volgende stap.
seo-title: failover van afspeellijst ontbreekt
title: failover van afspeellijst ontbreekt
uuid: 91a537f3-3e69-4669-8f84-0292c19ac209
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---


# Afspeellijst failover{#missing-playlist-failover} ontbreekt

Wanneer een volledige afspeellijst ontbreekt, bijvoorbeeld wanneer het M3U8-bestand dat in een manifestbestand op hoofdniveau is opgegeven niet wordt gedownload, probeert TVSDK het bestand te herstellen. Als het niet kan herstellen, bepaalt uw toepassing de volgende stap.

Als de afspeellijst die is gekoppeld aan de bitsnelheid met middelste resolutie ontbreekt, zoekt TVSDK naar een andere afspeellijst met dezelfde resolutie. Als dezelfde resolutie wordt gevonden, worden de afspeellijst van de variant en de segmenten vanaf de overeenkomende positie gedownload. Als TVSDK niet dezelfde afspeellijst met resolutie vindt, probeert het andere afspeellijsten met bitsnelheden en hun varianten te doorlopen. Een onmiddellijk lagere bitsnelheid is de eerste keuze, daarna de variant, enzovoort. Als alle onderste afspeellijsten met bitsnelheden en de bijbehorende varianten zijn uitgeput in de poging om een geldige afspeellijst te vinden, gaat TVSDK naar de bovenste bitsnelheid en wordt het aantal van daaruit verlaagd. Als er geen geldige afspeellijst kan worden gevonden, mislukt het proces en gaat de speler naar de status ERROR.

Uw toepassing kan bepalen hoe deze situatie wordt afgehandeld. U kunt bijvoorbeeld de speleractiviteit sluiten en de gebruiker naar de catalogusactiviteit verwijzen. De gebeurtenis van belang is de `STATE_CHANGED` gebeurtenis, en de overeenkomstige callback is de `onStateChanged` methode. Hier volgt code waarmee wordt gecontroleerd of de interne status van de speler wordt gewijzigd in ERROR:

```java
case ERROR: 
    getActivity().finish(); // this is where we close the current activity (the Player activity) 
    break;
```

Raadpleeg het bestand [!DNL PlayerFragment.java] in de SDK voor meer informatie:

```
[…]/samples/PrimetimeReference/src/PrimetimeReference/src/com/adobe/primetime/reference/ui/player/
```

Als het netwerk aan de clientzijde uitvalt, kunt u deze code gebruiken om te verifiëren.

```
psdkutils::PSDKString 
getNetworkDownVerificationUrl() const { return 
_networkDownVerificationUrl; }
```

API zal url verstrekken die wordt gebruikt om te verifiëren als het cliënt zijnetwerk neer is. Dit zou een geldige url moeten zijn, die http antwoordcode 200 op HTTP- verzoeken terugkeert.

```
psdkutils::PSDKErrorCode 
 setNetworkDownVerificationUrl(psdkutils::PSDKString value) {  
_networkDownVerificationUrl = value; return psdkutils::kECSuccess; }
```

Als setNetworkDownVerificationUrl niet wordt geplaatst, gebruikt TVSDK de MainManifest url door gebrek om te bepalen als het netwerk neer is.
