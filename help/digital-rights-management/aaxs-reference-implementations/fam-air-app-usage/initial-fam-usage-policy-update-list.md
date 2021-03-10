---
title: Lijst met beleidsupdates
description: Lijst met beleidsupdates
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---


# Lijst met beleidsupdates {#policy-update-list}

U kunt de Lijsten van de Update van het Beleid gebruiken om beleidsveranderingen aan een Server van de Vergunning mee te delen. Als een beleid wordt gewijzigd nadat het aan pakketinhoud wordt gebruikt, is het wenselijk om de Server van de Vergunning bewust van de meest recente versie van het beleid te hebben, zodat die versie kan worden gebruikt om een vergunning uit te geven.

Als u voor het eerst een lijst met beleidsupdates wilt maken, klikt u op **[!UICONTROL Add policies]** om alle beschikbare beleidsregels op de server weer te geven. Selecteer het keuzerondje **[!UICONTROL update]** voor beleidsregels die zijn bijgewerkt sinds deze zijn gebruikt om inhoud te verpakken.

Als u geen beleid meer wilt gebruiken om licenties af te geven en het beleid al is gebruikt om inhoud te verpakken, kunt u het beleid intrekken. Selecteer hiertoe het keuzerondje **[!UICONTROL revoke]**. Wanneer het gewenste beleid is geselecteerd, kiest u **[!UICONTROL Create Policy Update List]**. Een bestand met de naam [!DNL PolicyUpdateList.dat] wordt opgeslagen in de map [!DNL Resources].

Om een bestaande Lijst van de Update van het Beleid te wijzigen, klik **[!UICONTROL Add policies]** om al beschikbaar beleid op de server te bekijken. Kies het aanvullende beleid dat u wilt toevoegen of intrekken. Bestaande ingangen in de Lijst van de Update van het Beleid kunnen in de hogere sectie van het scherm worden veranderd. Beleidsregels die **[!UICONTROL updated]** zijn gemarkeerd, kunnen worden gewijzigd in **[!UICONTROL revoked]**, maar als een beleid **[!UICONTROL revoked]** is, kan het niet worden gewijzigd in **[!UICONTROL updated]**.

Als de gewenste wijzigingen zijn aangebracht, kiest u **[!UICONTROL Create Policy Update List]** en wordt het bestand [!DNL PolicyUpdateList.dat] opnieuw gegenereerd. Als een beleid reeds in de lijst van de beleidsupdate is en sinds de laatste tijd werd bijgewerkt werd de lijst geproduceerd, zal de meest recente versie van het beleid worden gebruikt wanneer de Lijst van de Update van het Beleid opnieuw wordt geproduceerd.
