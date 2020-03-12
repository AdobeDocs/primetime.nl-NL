---
description: U kunt ervoor kiezen om standaard en gedrag te gebruiken.
seo-description: U kunt ervoor kiezen om standaard en gedrag te gebruiken.
seo-title: Standaardgedrag voor afspelen gebruiken
title: Standaardgedrag voor afspelen gebruiken
uuid: 7139384c-167a-4cab-816a-c02fb723a5cb
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Standaardgedrag voor afspelen gebruiken{#use-the-default-playback-behavior}

U kunt ervoor kiezen om standaard en gedrag te gebruiken.

Standaardgedrag gebruiken:

    * Als u uw eigen klasse &quot;ContentFactory&quot;uitvoert, keer een nieuw geval van &quot;DefaultAdPolicySelector&quot;in uw implementatie van &quot;doRetrieveAdPolicySelector&quot;terug.
    
    &quot;
    public class CustomContentFactory extends ContentFactory {
    
    //...
    // uw aangepaste code voor advertentieklassen
    //...
    
    /**
    * @inheritDoc
    */
    override protected
    functiondoRetrieveAdPolicySelector(item:MediaPlayerItem):AdPolicySelector {
    return new DefaultAdPolicySelector(item);
    }
    &quot;
    
    
    * Als u geen aangepaste implementatie voor de klasse ContentFactory hebt, gebruikt TVSDK DefaultAdPolicySelector`.