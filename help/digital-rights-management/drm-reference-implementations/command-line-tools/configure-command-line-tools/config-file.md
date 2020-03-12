---
description: 'null'
seo-description: 'null'
seo-title: Ongeveer bevel-lijn hulpmiddelen configuratiedossiers
title: Ongeveer bevel-lijn hulpmiddelen configuratiedossiers
uuid: 8220921f-1fe9-439c-8134-dc16c2e3601b
translation-type: tm+mt
source-git-commit: 0143d98185b9a63ef978aba18e2f3c8728333155

---


# Ongeveer bevel-lijn hulpmiddelen configuratiedossiers{#about-command-line-tools-configuration-files}

De opdrachtregelprogramma&#39;s zoeken naar [!DNL flashaccesstools.properties] de map waarin u de gereedschappen uitvoert. U kunt de `-c` optie echter ook gebruiken wanneer u een opdrachtregelprogramma uitvoert om een andere locatie voor de standaardlocatie op te geven [!DNL flashaccesstools.properties]. U kunt ook een ander configuratiebestand opgeven `-c` .

Voor de configuratiebestanden voor opdrachtregelprogramma&#39;s wordt de indeling *Java-eigenschappenbestand* gebruikt, waarvoor de volgende regels gelden:

* Escape-backslashes met een extra backslash.

   Als u bijvoorbeeld op een Windows-computer het [!DNL C:\credentials.pfx] bestand wilt opgeven, moet u het als [!DNL C:\\credentials.pfx] of `C:/credentials.pfx`. Als u een bestand op een Windows-netwerkserver wilt opgeven, moet u `\\\\server\\folder\\filename.pfx`
* Alleen *Latijnse-1* tekens opnemen.

   Als u niet-*Latin-1* -tekens wilt gebruiken, moet u de juiste Unicode-escapereeks gebruiken. U kunt desgewenst het [!DNL native2ascii] gereedschap (dat deel uitmaakt van Java) toepassen op de items in het configuratiebestand.
