---
title: Enhanced License Chaining
description: Enhanced License Chaining
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---


# Enhanced License Chaining {#enhanced-license-chaining}

Als een beleid DRM wordt gebruikt om een vergunning te produceren die vergunning het in een ketting plaatsen steunt, moet de server beslissen of om een vergunning van Leaf, de vergunning van de Wortel, of allebei uit te geven. Als u wilt bepalen welk type van vergunning ketend een beleid DRM steunt, moet u `Policy.getLicenseChainType()` gebruiken, of `Policy.getRootLicenseId()` roepen om te bepalen als het beleid DRM een wortelvergunning heeft. Met Adobe Primetime DRM 2.0-licentieketting geeft de server doorgaans een bladlicentie uit wanneer een gebruiker voor het eerst een licentie voor een bepaalde computer en daarna een hoofdlicentie aanvraagt. Als u wilt bepalen als de machine reeds een bladvergunning voor het gespecificeerde beleid heeft, moet u `LicenseRequestMessage.clientHasLeafForPolicy()` roepen.

Als de licentie in Adobe Primetime DRM 3.0 via een verbeterde certificaatketen is gekoppeld, wordt aangeraden zowel een Leaf als een Root uit te geven wanneer de gebruiker voor het eerst een licentie aanvraagt voor een bepaalde computer. Als de gebruiker reeds de vergunning van de Wortel heeft, kan de server slechts een Blad uitgeven (vraag `LicenseRequestMessage.clientHasEnhancedRootForPolicy()` om te bepalen als de cliënt reeds een 3.0 Verbeterde Woot heeft). Voor volgende licentieaanvragen geeft de client dan aan dat er al een Leaf en Root is, zodat de server een nieuwe Root-licentie moet uitgeven. Wanneer de verbeterde vergunning het in een keten plaatsen wordt gebruikt, `setRootKeyRetrievalInfo()` moet worden geroepen om de geloofsbrieven te verstrekken nodig om de sleutel van de wortelencryptie in het beleid te decrypteren DRM.

>[!NOTE]
>
>Als het beleid 3.0 Verbeterde het In de cache plaatsen van de Vergunning ondersteunt, maar de cliënt is Primetime DRM 2.0, geeft de server dan een 2.0 oorspronkelijke geketende vergunning uit. Gebruik `LicenseRequestMessage.getClientVersion()` om de clientversie te bepalen.

