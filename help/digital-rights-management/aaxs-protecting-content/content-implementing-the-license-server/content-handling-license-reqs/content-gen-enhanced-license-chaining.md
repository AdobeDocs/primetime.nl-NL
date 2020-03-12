---
seo-title: Enhanced License Chaining
title: Enhanced License Chaining
uuid: dc0e0a46-d3cd-44e8-a45d-3e22787be44e
translation-type: tm+mt
source-git-commit: da8736769f7b47318dbd955aa854f83ae64d6d7b

---


# Enhanced License Chaining {#enhanced-license-chaining}

Als de licentie in Adobe Access 3.0 via een verbeterde certificaatketen is gekoppeld, wordt het aanbevolen zowel een Leaf als een Root uit te geven wanneer de gebruiker voor het eerst een licentie aanvraagt voor een bepaalde computer. Als de gebruiker reeds de vergunning van de Wortel heeft, kan de server slechts een Blad uitgeven (vraag `LicenseRequestMessage.clientHasEnhancedRootForPolicy()` om te bepalen als de cliënt reeds een 3.0 Verbeterde Woot heeft). Voor volgende licentieaanvragen geeft de client aan dat de client al een Leaf en Root heeft. De server moet dus een nieuwe Root-licentie uitgeven. Wanneer de verbeterde vergunning het ketenen wordt gebruikt, `setRootKeyRetrievalInfo()` moet worden geroepen om de geloofsbrieven te verstrekken nodig om de sleutel van de wortelencryptie in het beleid te decrypteren.

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>Als het beleid 3.0 Enhanced License Chaining ondersteunt, maar de client Adobe Access 2.0 is, geeft de server een oorspronkelijke geketende licentie van 2.0 uit. Gebruik LicenseRequestMessage.getClientVersion() om de clientversie te bepalen.

