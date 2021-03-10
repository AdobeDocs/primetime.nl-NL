---
title: Replay-beveiliging
description: Replay-beveiliging
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 0%

---


# Herafspeelbeveiliging{#replay-protection}

De bescherming van het spel verhindert een aanvaller een bericht van het vergunningsverzoek opnieuw te spelen en potentieel veroorzakend een ontkenning-van-dienst (Dos) aanval tegen de cliënt (een *ontkenning-van-dienst* aanval is een poging door aanvallers om wettige gebruikers van de dienst te verhinderen die dienst te gebruiken.) Bijvoorbeeld, zou een replay aanval die de het terugschroeven van prijzenteller gebruikt kunnen worden gebruikt om de Server van de Vergunning te &quot;bedriegen&quot;in het denken dat de cliënt DRM zijn staat terugwentelt, veroorzakend een opschorting van de rekening.

Zie `AbstractRequestMessage.getMessageId()` de *API-naslaggids voor Adobe toegang* voor meer informatie over afspeelbeveiliging.
