---
description: Instantieer een MediaPlayer en plaats een mening van het in een kaderlay-out.
seo-description: Instantieer een MediaPlayer en plaats een mening van het in een kaderlay-out.
seo-title: De MediaPlayer instellen
title: De MediaPlayer instellen
uuid: 49c3edb9-b6e2-49f8-b4aa-f230af7de6b0
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---


# MediaPlayer {#set-up-the-mediaplayer} instellen

TVSDK beschikt over gereedschappen voor het maken van een geavanceerde videospelertoepassing (uw Primetime-speler) die u kunt integreren met andere Primetime-componenten. De klasse biedt ook een aantal functies die zijn ontworpen om de afspeelkwaliteit van video te maximaliseren.

Instantieer een MediaPlayer en plaats een mening van het in een kaderlay-out.

1. Instantiëren `MediaPlayer`, waarbij een object `android.content.Context` wordt doorgegeven aan de constructor:

   ```java
   MediaPlayer mediaPlayer = new MediaPlayer(context);
   ```

1. Geef een framelay-out ( `android.widget.FrameLayout`) op om een `ViewGroup` van `mediaPlayer` te houden:

   ```java
   FrameLayout playerFrame = (FrameLayout) _viewGroup.findViewById(R.id.playerFrame);
   ```

   Hieronder ziet u het codefragment dat u wilt maken `_viewGroup`.

   ```
   @Override 
    public ViewGroup onCreateView(LayoutInflater inflater, ViewGroup container, 
      Bundle savedInstanceState) { 
     _viewGroup = (ViewGroup) inflater.inflate( 
       R.layout.fragment_player, container, false); 
     return _viewGroup; 
    }
   ```

1. Plaats een weergave van `mediaPlayer` in de kaderlay-out:

   ```java
   playerFrame.addView(mediaPlayer.getView());
   ```

>De `MediaPlayer` instantie ( `mediaPlayer`) is nu beschikbaar en behoorlijk gevormd om videoinhoud op het apparatenscherm te tonen.