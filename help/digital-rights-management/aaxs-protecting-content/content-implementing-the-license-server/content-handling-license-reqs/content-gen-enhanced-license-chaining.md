---
title: Enhanced License Chaining
description: Enhanced License Chaining
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---


# Enhanced License Chaining {#enhanced-license-chaining}

Als de licentie in Adobe Access 3.0 via een verbeterde certificaatketen is gekoppeld, wordt aanbevolen zowel een Leaf als een Root uit te geven wanneer de gebruiker voor het eerst een licentie aanvraagt voor een bepaalde computer. Als de gebruiker reeds de vergunning van de Wortel heeft, kan de server slechts een Blad uitgeven (vraag `LicenseRequestMessage.clientHasEnhancedRootForPolicy()` om te bepalen als de cliënt reeds een 3.0 Verbeterde Woot heeft). Voor volgende licentieaanvragen geeft de client aan dat de client al een Leaf en Root heeft. De server moet dus een nieuwe Root-licentie uitgeven. Wanneer de verbeterde vergunning het ketenen wordt gebruikt, `setRootKeyRetrievalInfo()` moet worden geroepen om de geloofsbrieven te verstrekken nodig om de sleutel van de wortelencryptie in het beleid te decrypteren.

>[!NOTE]
>
>Als het beleid 3.0 Verbeterde het In de cache plaatsen van de Vergunning steunt, maar de cliënt is Adobe Access 2.0, zal de server een 2.0 originele geketineerde vergunning uitgeven. Gebruik LicenseRequestMessage.getClientVersion() om de clientversie te bepalen.

