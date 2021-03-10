---
title: Wachtwoordkrambler
description: Wachtwoordkrambler
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 0%

---


# Wachtwoordspaander {#password-scrambler}

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

