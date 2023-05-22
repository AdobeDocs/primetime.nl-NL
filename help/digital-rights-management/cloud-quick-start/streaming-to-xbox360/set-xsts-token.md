---
title: Het XSTS-token instellen in de speler
description: Het XSTS-token instellen in de speler
copied-description: true
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '64'
ht-degree: 0%

---


# Het XSTS-token instellen in de speler{#set-the-xsts-token-in-your-player}

In Xbox 360 stelt u het token asynchroon in als reactie op de `MediaPlayer.RequestKeyAttribute` gebeurtenis.

Stel het XSTS-token in.

De voorbeeldtoepassing die bij de software wordt geleverd, laat zien hoe u het XSTS-token in uw speler instelt. Hier volgt het relevante codefragment van de voorbeeldspeler:

```
   MediaPlayer mMediaPlayer;  
 
mMediaPlayer.RequestKeyAttribute += Player_RequestKeyAttribute;  
 
private void Player_RequestKeyAttribute(object sender, RequestKeyAttributeEventArgs args) {  
    string token = "";  
    // XBOX XSTS Token...  
    KeyAttribute keyAttribute = new KeyAttribute(System.Text.Encoding.UTF8.GetBytes(token), null);  
    mMediaPlayer.SetKeyAttribute(args.RequestIdentifier, keyAttribute);  
} 
```

