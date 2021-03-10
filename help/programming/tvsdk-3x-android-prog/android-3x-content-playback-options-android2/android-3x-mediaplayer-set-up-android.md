---
description: TVSDK beschikt over gereedschappen voor het maken van een geavanceerde videospelertoepassing (uw Primetime-speler) die u kunt integreren met andere Primetime-componenten. De klasse biedt ook een aantal functies die zijn ontworpen om de afspeelkwaliteit van video te maximaliseren.
title: De mediaspeler instellen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 0%

---


# Mediaspeler {#set-up-the-media-player} instellen

TVSDK beschikt over gereedschappen voor het maken van een geavanceerde videospelertoepassing (uw Primetime-speler) die u kunt integreren met andere Primetime-componenten. De klasse biedt ook een aantal functies die zijn ontworpen om de afspeelkwaliteit van video te maximaliseren.

<!--<a id="section_1FE83A68DE624F20B52C0959851F5699"></a>-->

Instantieer een `MediaPlayer` en plaats een mening van het in een kaderlay-out.

1. Instantiëren `MediaPlayer`, waarbij een object `android.content.Context` wordt doorgegeven aan de constructor:

   ```java
   MediaPlayer mediaPlayer = new MediaPlayer(context);
   ```

1. Geef een framelay-out ( `android.widget.FrameLayout`) op om een `ViewGroup` van `mediaPlayer` te houden:

   ```java
   FrameLayout playerFrame = (FrameLayout) _viewGroup.findViewById(R.id.playerFrame);
   ```

   >[!NOTE]
   >
   >Hieronder ziet u het codefragment dat u wilt maken `_viewGroup`.

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

   >[!NOTE]
   >
   >De `MediaPlayer` instantie ( `mediaPlayer`) is nu beschikbaar en behoorlijk gevormd om videoinhoud op het apparatenscherm te tonen.