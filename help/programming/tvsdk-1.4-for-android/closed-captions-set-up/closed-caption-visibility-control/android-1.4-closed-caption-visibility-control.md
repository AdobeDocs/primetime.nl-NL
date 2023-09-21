---
description: U kunt de zichtbaarheid van gesloten bijschriften bepalen. Wanneer de zichtbaarheid is ingeschakeld, wordt de geselecteerde track weergegeven. Als u wijzigt welke track huidig is, blijft de zichtbaarheidsinstelling ongewijzigd.
title: Zichtbaarheid van ondertiteling beheren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---

# Overzicht {#control-closed-caption-visibility}

U kunt de zichtbaarheid van gesloten bijschriften bepalen. Wanneer de zichtbaarheid is ingeschakeld, wordt de geselecteerde track weergegeven. Als u wijzigt welke track huidig is, blijft de zichtbaarheidsinstelling ongewijzigd.

>[!TIP]
>
>Als Closed Caption-tekst wordt weergegeven wanneer de speler de zoekmodus opent, wordt de tekst niet meer weergegeven nadat de zoekactie is voltooid. In plaats daarvan geeft TVSDK na een paar seconden de volgende Closed Caption-tekst in de video weer na de eindzoekpositie.

>[!NOTE]
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

1. Wacht op MediaPlayer om minstens de VOORBEREIDENDE staat te hebben (zie [Wacht op een geldige status](../../../tvsdk-1.4-for-android/ui-configure/android-1.4-ui-state-prepared-wait-for.md)).
1. Als u de huidige zichtbaarheidsinstelling voor gesloten bijschriften wilt ophalen, gebruikt u de methode getter in MediaPlayer, die een zichtbaarheidswaarde retourneert.

   ```java
   Visibility getCCVisibility() throws IllegalStateException;
   ```

1. Als u de zichtbaarheid van gesloten bijschriften wilt wijzigen, gebruikt u de methode setter en geeft u een zichtbaarheidswaarde door van `MediaPlayer.Visibility`.

   Bijvoorbeeld:

   ```java
   mediaPlayer.setCCVisibility(Visibility.VISIBLE);
   ```
