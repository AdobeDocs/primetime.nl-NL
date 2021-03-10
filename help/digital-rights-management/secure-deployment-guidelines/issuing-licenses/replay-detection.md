---
description: De bescherming van het spel verhindert een aanvaller een bericht van het vergunningsverzoek opnieuw te spelen en potentieel veroorzakend een ontkenning-van-dienst (Dos) aanval tegen de cliënt.
title: Replay-beveiliging
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---


# Herafspeelbeveiliging{#replay-protection}

De bescherming van het spel verhindert een aanvaller een bericht van het vergunningsverzoek opnieuw te spelen en potentieel veroorzakend een ontkenning-van-dienst (Dos) aanval tegen de cliënt.

Een aanval van Dos is een poging door aanvallers om wettige gebruikers van de dienst te verhinderen die dienst te gebruiken. Bijvoorbeeld, zou een replay aanval die de het terugschroeven van prijzenteller gebruikt kunnen worden gebruikt om de Server van de Vergunning te &quot;bedriegen&quot;in het denken dat de cliënt DRM zijn staat heeft teruggedraaid, die een opschorting van de rekening veroorzaakt.

Meer over replay bescherming leren, zie [ AbstractRequestMessage.getMessageId ()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/AbstractRequestMessage.html#getMessageId()).
