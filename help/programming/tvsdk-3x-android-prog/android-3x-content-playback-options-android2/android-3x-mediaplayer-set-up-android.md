---
description: TVSDK beschikt over gereedschappen voor het maken van een geavanceerde videospelertoepassing (uw Primetime-speler) die u kunt integreren met andere Primetime-componenten. De klasse biedt ook een aantal functies die zijn ontworpen om de afspeelkwaliteit van video te maximaliseren.
title: De mediaspeler instellen
exl-id: 99fdc4c1-0c67-4de5-87a5-b42d76f43ae9
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 0%

---

# De mediaspeler instellen {#set-up-the-media-player}

TVSDK beschikt over gereedschappen voor het maken van een geavanceerde videospelertoepassing (uw Primetime-speler) die u kunt integreren met andere Primetime-componenten. De klasse biedt ook een aantal functies die zijn ontworpen om de afspeelkwaliteit van video te maximaliseren.

<!--<a id="section_1FE83A68DE624F20B52C0959851F5699"></a>-->

Instantiëren van een `MediaPlayer` en plaats er een weergave van in een kaderlay-out.

1. Instantiëren `MediaPlayer`, een `android.content.Context` object naar de constructor:

   ```java
   MediaPlayer mediaPlayer = new MediaPlayer(context);
   ```

1. Een kaderlay-out bieden ( `android.widget.FrameLayout`) om een `ViewGroup` van `mediaPlayer`:

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

1. Een weergave plaatsen van `mediaPlayer` in de kaderlay-out:

   ```java
   playerFrame.addView(mediaPlayer.getView());
   ```

   >[!NOTE]
   >
   >De `MediaPlayer` instance ( `mediaPlayer`) is nu beschikbaar en correct geconfigureerd voor het weergeven van video-inhoud op het apparaatscherm.
