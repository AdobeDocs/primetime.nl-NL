---
description: De eigenschappen van TVSDK worden gedreven door configuratie en door MediaPlayer uitgevoerd.
title: Het creëren van eigenschapmanagers door configuratieinformatie tot MediaPlayer over te gaan
exl-id: 47377ceb-ed3e-4dca-9b55-82e4fe6b0194
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---

# Het creëren van eigenschapmanagers door configuratieinformatie tot MediaPlayer over te gaan {#creating-feature-managers-by-passing-configuration-information-to-the-mediaplayer}

De eigenschappen van TVSDK worden gedreven door configuratie en door MediaPlayer uitgevoerd.

* De configuratie is de lijst van specifieke montages voor de eigenschap, zoals aanvankelijke beetjetarief van controle ABR en gebrek gesloten ondertitelingszicht.

   De managers van de eigenschap moeten de configuraties krijgen om het eigenschapgedrag te bepalen.

   In de Primetime verwijzingsimplementatie, wordt de configuratie opgeslagen in gedeelde voorkeur, maar u kunt de configuratie opslaan op wat voor manier voor uw milieu zinvol is.

* `MediaPlayer` is het TVSDK-mediaspelerobject dat de videobron bevat.

   De managers van de eigenschap registreren TVSDK gebeurtenisluisteraars aan dit spelervoorwerp, halen gegevens van de playbackzitting terug en brengen eigenschappen TVSDK aan de playbackzitting teweeg.

Elke eigenschap heeft een overeenkomstige configuratieinterface. Bijvoorbeeld: `CCManager` gebruik `ICCConfig` om de configuratie op te halen. `ICCConfig` bevat methodes om de configuratieinformatie met betrekking tot gesloten ondertiteling slechts te krijgen.

In het volgende voorbeeld wordt het [!DNL ICCConfig.java] bestand, geconfigureerd voor het ontvangen van informatie over zichtbaarheid van een gesloten bijschrift, letterstijl en lettertyperand vanuit de `MediaPlayer`:

```java
// Constructor of CCManager 
 
<b>public CCManager(ICCConfig ccConfig, MediaPlayer mediaPlayer) {...}</b> 
  
// ICCConfig methods 
 
<b>public interface ICCConfig {</b> 
  
    /** 
     * Get the closed captioning visibility config 
     * 
     * @return true if visibility is set to true, false otherwise 
     */ 
    
<b> public boolean getCCVisibility();</b> 
  
    /** 
     * Get the closed captioning font style 
     * 
     * @return TextFormat.Font object represents font style 
     */ 
     
<b>public TextFormat.Font getCCFont();</b>

    /** 
     * Get the closed captioning font edge 
     * 
     * @return TextFormat.FontEdge represents of font edge 
     */ 
     
<b>public TextFormat.FontEdge getCCFontEdge();</b> 
... 
}
```

Een toepassing die een eigenschap van TVSDK gebruikt kan zijn eigenschapmanager met een configuratieleverancier en een `MediaPlayer` object. Bijvoorbeeld:

```java
// This application needs to use the advertising workflow feature 
AdsManager adsManager = new AdsManagerOn();
```

API-documenten voor configuratie van functiebeheer: [Javadoc](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/package-summary.html)
