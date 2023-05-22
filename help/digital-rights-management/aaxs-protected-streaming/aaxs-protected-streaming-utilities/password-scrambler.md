---
title: Wachtwoordkrambler
description: Wachtwoordkrambler
copied-description: true
exl-id: ceedd61e-918b-453f-8d21-628b2d8713ff
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 0%

---

# Wachtwoordkrambler {#password-scrambler}

Met het hulpprogramma Password Scrambler wordt een wachtwoord gecodeerd, zodat dit in de Adobe Access Server kan worden gebruikt voor beveiligde streamingconfiguratiebestanden. Voer de opdracht uit om de schuifregelaar uit te voeren:

```
Scrambler.bat password 
```

of de opdracht:

```
java -jar libs/flashaccess-scrambler.jar password  
```

Het nut output het volgende bericht:

```
Encrypted password: scrambled-password 
```

Alle wachtwoorden die in flashaccess-global.xml en flashaccess-huurder.xml worden opgegeven, moeten worden gecodeerd.

>[!NOTE]
>
>Het hulpprogramma Password Scrambler in de Adobe Access Server for Protected Streaming is niet uitwisselbaar met de schuifregelaar die wordt geleverd bij de Referentie-implementatielicentieserver.
