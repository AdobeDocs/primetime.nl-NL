---
seo-title: Replay-beveiliging
title: Replay-beveiliging
uuid: 5e6488e6-0834-4dcf-bc26-55019f5db320
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 0%

---


# Herafspeelbeveiliging{#replay-protection}

De bescherming van het spel verhindert een aanvaller een bericht van het vergunningsverzoek opnieuw te spelen en potentieel veroorzakend een ontkenning-van-dienst (Dos) aanval tegen de cliënt (een *ontkenning-van-dienst* aanval is een poging door aanvallers om wettige gebruikers van de dienst te verhinderen die dienst te gebruiken.) Bijvoorbeeld, zou een replay aanval die de het terugschroeven van prijzenteller gebruikt kunnen worden gebruikt om de Server van de Vergunning te &quot;bedriegen&quot;in het denken dat de cliënt DRM zijn staat terugwentelt, veroorzakend een opschorting van de rekening.

Zie `AbstractRequestMessage.getMessageId()` de *API-naslaggids voor Adobe toegang* voor meer informatie over afspeelbeveiliging.
