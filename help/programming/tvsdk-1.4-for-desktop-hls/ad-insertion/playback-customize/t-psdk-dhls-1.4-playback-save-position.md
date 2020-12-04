---
description: U kunt de huidige afspeelpositie in een video opslaan en het afspelen op dezelfde positie in een volgende sessie hervatten.
seo-description: U kunt de huidige afspeelpositie in een video opslaan en het afspelen op dezelfde positie in een volgende sessie hervatten.
seo-title: De videopositie opslaan en later hervatten
title: De videopositie opslaan en later hervatten
uuid: 03ed5c63-008d-4dd1-9a31-baefa73b56e2
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---


# De videopositie opslaan en later hervatten{#save-the-video-position-and-resume-later}

U kunt de huidige afspeelpositie in een video opslaan en het afspelen op dezelfde positie in een volgende sessie hervatten.

Dynamisch ingevoegde advertenties verschillen per gebruikerssessie, zodat het opslaan van de positie **met** gespliceerde advertenties naar een andere positie in een toekomstige sessie verwijst. TVSDK biedt methoden om de afspeelpositie op te halen zonder gespliceerde advertenties te negeren.

1. Wanneer de gebruiker een video afsluit, wordt de positie in de video opgehaald en opgeslagen.

   >[!TIP]
   >
   >Duur van advertentie is niet inbegrepen.

   De pauzes van de toevoeging kunnen in elke zitting als toe te schrijven aan advertentiepatronen, frequentiegrenzen, etc. variëren. De huidige tijd van de video in één sessie kan in een volgende sessie anders zijn. Wanneer u een positie in de video opslaat, haalt de toepassing de lokale tijd op. Gebruik de eigenschap `localTime` om deze positie te lezen, die u kunt opslaan op het apparaat of in een database op de server.

   ```
   var resumeTime:Number = player.localTime; 
   // save the resumeTime to a persistent location
   ```

   Als de gebruiker bijvoorbeeld op de 20e minuut van de video staat en deze positie vijf minuten aan advertenties bevat, `currentTime` 1200 seconden, terwijl `localTime` op deze positie `be` 900 seconden zal duren.`be`

1. Herstel de gebruikerssessie wanneer de activiteit van de speler wordt hervat.

   TVSDK hervat het afspelen tussen TVSDK-initialisaties niet omdat het geen lokale informatie opslaat. Deze logica moet door uw toepassing worden geïmplementeerd.

   ```
   // retrieve the resumeTime from the persistent location 
   var resumeTime:Number:Number = ...;
   ```

1. De video op dezelfde positie hervatten:

   * Gebruik `seekToLocal` om het afspelen van de video vanaf de positie die is opgeslagen tijdens een vorige sessie te hervatten.

      >[!TIP]
      >
      >Deze methode wordt alleen aangeroepen met lokale tijdwaarden. Als de methode wordt aangeroepen met de huidige-tijdresultaten, treedt een onjuist gedrag op.

   * Gebruik `seek` om naar de huidige tijd te zoeken.

1. Wanneer uw toepassing de gebeurtenis `onStatusChanged` van de statusverandering ontvangt, zoek aan de bewaarde lokale tijd.
1. Geef de pagina-einden op zoals opgegeven in de interface voor advertentiebeleid.
1. Voer een douaneselecteur van het advertentiebeleid uit door de standaard uit te breiden en beleidsselecteur.
1. Geef de ad-einden op die aan de gebruiker moeten worden weergegeven door `selectAdBreaksToPlay` te implementeren.

   Wanneer de speler de status PREPARED inschakelt, worden alle advertenties al opgelost. De eigenschap `AdPolicyInfo.adBreakTimelineItem` bevat dus alle advertentieeinden vóór de lokale tijdpositie. Uw toepassing kan besluiten een pre-rol en onderbreking te spelen en aan de gespecificeerde lokale tijd te hervatten, een middenrol en onderbreking te spelen en aan de gespecificeerde lokale tijd te hervatten, of geen ad onderbrekingen te spelen.
