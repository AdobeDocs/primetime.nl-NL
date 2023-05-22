---
description: U kunt de huidige afspeelpositie in een video opslaan en het afspelen op dezelfde positie in een volgende sessie hervatten.
title: De videopositie opslaan en later hervatten
exl-id: a06897a6-bf57-4902-b1b4-e931419b56ba
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# De videopositie opslaan en later hervatten{#save-the-video-position-and-resume-later}

U kunt de huidige afspeelpositie in een video opslaan en het afspelen op dezelfde positie in een volgende sessie hervatten.

Dynamisch ingevoegde advertenties verschillen per gebruikerssessie, zodat de positie wordt opgeslagen **with** spliced advertenties verwijzen naar een andere positie in een toekomstige sessie. TVSDK biedt methoden om de afspeelpositie op te halen zonder gespliceerde advertenties te negeren.

1. Wanneer de gebruiker een video afsluit, wordt de positie in de video opgehaald en opgeslagen.

   >[!TIP]
   >
   >Duur van advertentie is niet inbegrepen.

   De pauzes van de toevoeging kunnen in elke zitting als toe te schrijven aan advertentiepatronen, frequentiegrenzen, etc. variëren. De huidige tijd van de video in één sessie kan in een volgende sessie anders zijn. Wanneer u een positie in de video opslaat, haalt de toepassing de lokale tijd op. Gebruik de `localTime` eigenschap voor het lezen van deze positie, die u kunt opslaan op het apparaat of in een database op de server.

   ```
   var resumeTime:Number = player.localTime; 
   // save the resumeTime to a persistent location
   ```

   Als de gebruiker bijvoorbeeld op de twintigste minuut van de video staat en deze positie vijf minuten aan advertenties bevat, `currentTime` zal `be` 1200 seconden, terwijl `localTime` op dit punt `be` 900 seconden.

1. Herstel de gebruikerssessie wanneer de activiteit van de speler wordt hervat.

   TVSDK hervat het afspelen tussen TVSDK-initialisaties niet omdat het geen lokale informatie opslaat. Deze logica moet door uw toepassing worden geïmplementeerd.

   ```
   // retrieve the resumeTime from the persistent location 
   var resumeTime:Number:Number = ...;
   ```

1. De video op dezelfde positie hervatten:

   * Als u het afspelen van de video wilt hervatten vanaf de positie die u tijdens een vorige sessie hebt opgeslagen, gebruikt u `seekToLocal`.

      >[!TIP]
      >
      >Deze methode wordt alleen aangeroepen met lokale tijdwaarden. Als de methode wordt aangeroepen met de huidige-tijdresultaten, treedt een onjuist gedrag op.

   * Om naar de huidige tijd te zoeken, gebruik `seek`.

1. Wanneer uw toepassing de `onStatusChanged` wijzigt de status, zoekt naar de opgeslagen lokale tijd.
1. Geef de pagina-einden op zoals opgegeven in de interface voor advertentiebeleid.
1. Voer een douaneselecteur van het advertentiebeleid uit door de standaard uit te breiden en beleidsselecteur.
1. Geef de ad-einden op die aan de gebruiker moeten worden weergegeven door de implementatie `selectAdBreaksToPlay`.

   Wanneer de speler de status PREPARED inschakelt, worden alle advertenties al opgelost, zodat de `AdPolicyInfo.adBreakTimelineItem` eigenschap bevat alle advertentie-einden vóór de lokale tijdpositie. Uw toepassing kan besluiten een pre-rol en onderbreking te spelen en aan de gespecificeerde lokale tijd te hervatten, een middenrol en onderbreking te spelen en aan de gespecificeerde lokale tijd te hervatten, of geen ad onderbrekingen te spelen.
