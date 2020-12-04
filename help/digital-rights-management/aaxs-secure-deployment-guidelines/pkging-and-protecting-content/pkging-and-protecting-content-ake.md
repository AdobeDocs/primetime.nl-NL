---
seo-title: Asymmetrische sleutelversleuteling
title: Asymmetrische sleutelversleuteling
uuid: 0aae25f1-a609-4c73-9aef-13f8ae63f6e1
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---


# Asymmetrische sleutelencryptie{#asymmetric-key-encryption}

Bij asymmetrische sleutelversleuteling (ook wel versleuteling met een openbare sleutel genoemd) worden sleutelparen gebruikt. Eén sleutel wordt gebruikt voor versleuteling. de andere voor ontsleuteling. De decryptiesleutel wordt geheim gehouden, en wordt bedoeld als *privé sleutel*. De encryptiesleutel, die als *openbare sleutel* wordt bedoeld, wordt ter beschikking gesteld aan iedereen die wordt gemachtigd om inhoud te coderen. Iedereen met toegang tot de openbare sleutel kan inhoud coderen, maar alleen iemand met toegang tot de persoonlijke sleutel kan de inhoud decoderen. De persoonlijke sleutel kan niet opnieuw worden opgebouwd op basis van de openbare sleutel.

Bij het verpakken van inhoud wordt de openbare sleutel van de Server van de Vergunning gebruikt om de sleutel van de inhoudsencryptie (CEK) in de meta-gegevens te coderen DRM. U moet ervoor zorgen dat alleen de licentieserver toegang heeft tot de persoonlijke sleutel van de licentieserver. als iemand anders over de sleutel beschikt, kan hij de inhoud decoderen en bekijken.

***Let op:**zorg ervoor dat u het certificaat van de Server van de Vergunning (die de openbare sleutel bevat) van een vertrouwde bron verkrijgt zodat u zeker kunt zijn het de sleutel van de Server van de Vergunning, en niet een schurken openbare sleutel is. Als een aanvaller zijn openbare sleutel voor de sleutel van de Server van de Vergunning moest vervangen, zouden zij uw inhoud kunnen decrypteren.*

Voor meer informatie over het verpakken van inhoud, zie *Gebruikend de Adobe Toegang SDK voor het Beschermen van Inhoud*.
