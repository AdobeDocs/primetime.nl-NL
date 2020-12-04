---
description: 'null'
seo-description: 'null'
seo-title: Het XSTS-token instellen in de speler
title: Het XSTS-token instellen in de speler
uuid: 8995e029-deee-4e23-9cda-a50de8c4f2c0
translation-type: tm+mt
source-git-commit: b7f52b71bde1d7bf59ef51d4f6f90dfaa07e347b
workflow-type: tm+mt
source-wordcount: '66'
ht-degree: 0%

---


# Stel het XSTS-token in uw speler in{#set-the-xsts-token-in-your-player}

In Xbox 360 stelt u het token asynchroon in als reactie op de gebeurtenis `MediaPlayer.RequestKeyAttribute`.

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

