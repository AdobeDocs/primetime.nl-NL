---
title: Lijst met beleidsupdates
description: Lijst met beleidsupdates
copied-description: true
exl-id: 78078e95-775e-4c64-ab0f-d8bf644f3aee
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# Lijst met beleidsupdates {#policy-update-list}

U kunt de Lijsten van de Update van het Beleid gebruiken om beleidsveranderingen aan een Server van de Vergunning mee te delen. Als een beleid wordt gewijzigd nadat het aan pakketinhoud wordt gebruikt, is het wenselijk om de Server van de Vergunning bewust van de meest recente versie van het beleid te hebben, zodat die versie kan worden gebruikt om een vergunning uit te geven.

Als u voor het eerst een lijst met beleidsupdates wilt maken, klikt u op **[!UICONTROL Add policies]** om alle beschikbare beleidsregels op de server weer te geven. Voor beleid dat is bijgewerkt sinds deze is gebruikt om inhoud te verpakken, selecteert u de optie **[!UICONTROL update]** keuzerondje.

Als u geen beleid meer wilt gebruiken om licenties af te geven en het beleid al is gebruikt om inhoud te verpakken, kunt u het beleid intrekken. Selecteer hiertoe de optie **[!UICONTROL revoke]** keuzerondje. Als het gewenste beleid is geselecteerd, kiest u **[!UICONTROL Create Policy Update List]**. Een bestand dat [!DNL PolicyUpdateList.dat] wordt opgeslagen in de [!DNL Resources] Map.

Om een bestaande Lijst van de Update van het Beleid te wijzigen, klik **[!UICONTROL Add policies]** om alle beschikbare beleidsregels op de server weer te geven. Kies het aanvullende beleid dat u wilt toevoegen of intrekken. Bestaande ingangen in de Lijst van de Update van het Beleid kunnen in de hogere sectie van het scherm worden veranderd. Beleid dat is gemarkeerd **[!UICONTROL updated]** kan worden gewijzigd in **[!UICONTROL revoked]**, maar eenmaal een beleid **[!UICONTROL revoked]** kan niet worden gewijzigd in **[!UICONTROL updated]**.

Als de gewenste wijzigingen zijn aangebracht, kiest u **[!UICONTROL Create Policy Update List]** en de [!DNL PolicyUpdateList.dat] wordt opnieuw gegenereerd. Als een beleid reeds in de lijst van de beleidsupdate is en sinds de laatste tijd werd bijgewerkt werd de lijst geproduceerd, zal de meest recente versie van het beleid worden gebruikt wanneer de Lijst van de Update van het Beleid opnieuw wordt geproduceerd.
