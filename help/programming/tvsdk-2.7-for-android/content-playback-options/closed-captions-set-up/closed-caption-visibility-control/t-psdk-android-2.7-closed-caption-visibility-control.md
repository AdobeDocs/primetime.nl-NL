---
description: U kunt de zichtbaarheid van gesloten bijschriften bepalen. Wanneer de zichtbaarheid is ingeschakeld, wordt de geselecteerde track weergegeven. Als u wijzigt welke track huidig is, blijft de zichtbaarheidsinstelling ongewijzigd.
title: Zichtbaarheid van ondertiteling beheren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---

# Overzicht {#control-closed-caption-visibility-overview}

U kunt de zichtbaarheid van gesloten bijschriften bepalen. Wanneer de zichtbaarheid is ingeschakeld, wordt de geselecteerde track weergegeven. Als u wijzigt welke track huidig is, blijft de zichtbaarheidsinstelling ongewijzigd.

>[!TIP]
>
>Als Closed Caption-tekst wordt weergegeven wanneer de speler naar de zoekmodus gaat, wordt de tekst niet meer weergegeven nadat het zoeken is voltooid. In plaats daarvan geeft TVSDK na een paar seconden de volgende Closed Caption-tekst in de video weer na de eindzoekpositie.
>
>De zichtbaarheidswaarden voor gesloten bijschriften worden gedefinieerd in `MediaPlayer.Visibility`.
>
>```java
>enum Visibility {  
>       VISIBLE,  
>       INVISIBLE 
>}
>```
>

1. Wacht op de `MediaPlayer` ten minste de status PREPARED hebben.

   Voor meer informatie, zie ui-state-prepare-wait-for.
1. Gebruik de methode getter in `MediaPlayer`, die een zichtbaarheidswaarde retourneert.

   ```java
   MediaPlayer.Visibility getCCVisibility() throws MediaPlayerException;
   ```

1. Als u de zichtbaarheid van gesloten bijschriften wilt wijzigen, gebruikt u de methode setter en geeft u een zichtbaarheidswaarde door van `MediaPlayer.Visibility`.

   Bijvoorbeeld:

   ```java
   mediaPlayer.setCCVisibility(MediaPlayer.Visibility visibility);
   ```
