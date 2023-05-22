---
title: Replay-beveiliging
description: Replay-beveiliging
copied-description: true
exl-id: 1e6ad730-b150-4e8f-9e79-e6b4fe006bf8
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 0%

---

# Replay-beveiliging{#replay-protection}

De bescherming van het spel verhindert een aanvaller een bericht van het vergunningsverzoek opnieuw te spelen en potentieel veroorzakend een ontkenning-van-dienst (Dos) aanval tegen de cliënt (A *denial-of-service* de aanval is een poging door aanvallers om wettige gebruikers van de dienst te verhinderen die dienst te gebruiken.) Bijvoorbeeld, zou een replay aanval die de het terugschroeven van prijzenteller gebruikt kunnen worden gebruikt om de Server van de Vergunning te &quot;bedriegen&quot;in het denken dat de cliënt DRM zijn staat terugwentelt, veroorzakend een opschorting van de rekening.

Ga voor meer informatie over replay-beveiliging naar `AbstractRequestMessage.getMessageId()` de *Referentie voor Adobe Access API*.
