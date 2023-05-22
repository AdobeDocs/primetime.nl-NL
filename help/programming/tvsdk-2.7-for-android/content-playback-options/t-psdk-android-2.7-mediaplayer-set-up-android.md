---
description: Instantieer een MediaPlayer en plaats een mening van het in een kaderlay-out.
title: De MediaPlayer instellen
exl-id: e8fb6527-154b-4f7e-a128-525b5a3b3474
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---

# De MediaPlayer instellen {#set-up-the-mediaplayer}

TVSDK beschikt over gereedschappen voor het maken van een geavanceerde videospelertoepassing (uw Primetime-speler) die u kunt integreren met andere Primetime-componenten. De klasse biedt ook een aantal functies die zijn ontworpen om de afspeelkwaliteit van video te maximaliseren.

Instantieer een MediaPlayer en plaats een mening van het in een kaderlay-out.

1. Instantiëren `MediaPlayer`, een `android.content.Context` object naar de constructor:

   ```java
   MediaPlayer mediaPlayer = new MediaPlayer(context);
   ```

1. Een kaderlay-out bieden ( `android.widget.FrameLayout`) om een `ViewGroup` van `mediaPlayer`:

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

1. Een weergave plaatsen van `mediaPlayer` in de kaderlay-out:

   ```java
   playerFrame.addView(mediaPlayer.getView());
   ```

>De `MediaPlayer` instance ( `mediaPlayer`) is nu beschikbaar en correct geconfigureerd voor het weergeven van video-inhoud op het apparaatscherm.
