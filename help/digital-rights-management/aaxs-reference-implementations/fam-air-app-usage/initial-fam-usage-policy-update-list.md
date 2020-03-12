---
seo-title: Lijst met beleidsupdates
title: Lijst met beleidsupdates
uuid: ecc74b66-5b53-4ec3-9641-8b78929e2932
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Lijst met beleidsupdates {#policy-update-list}

U kunt de Lijsten van de Update van het Beleid gebruiken om beleidsveranderingen aan een Server van de Vergunning mee te delen. Als een beleid wordt gewijzigd nadat het aan pakketinhoud wordt gebruikt, is het wenselijk om de Server van de Vergunning bewust van de meest recente versie van het beleid te hebben, zodat die versie kan worden gebruikt om een vergunning uit te geven.

Als u voor het eerst een lijst met beleidsupdates wilt maken, klikt u **[!UICONTROL Add policies]** om alle beschikbare beleidsregels op de server weer te geven. Selecteer het **[!UICONTROL update]** keuzerondje voor alle beleidsregels die zijn bijgewerkt nadat deze zijn gebruikt om inhoud te verpakken.

Als u geen beleid meer wilt gebruiken om licenties af te geven en het beleid al is gebruikt om inhoud te verpakken, kunt u het beleid intrekken. Selecteer hiertoe het **[!UICONTROL revoke]** keuzerondje. Kies **[!UICONTROL Create Policy Update List]** wanneer het gewenste beleid is geselecteerd. Een geroepen dossier [!DNL PolicyUpdateList.dat] zal in de [!DNL Resources] Folder worden bewaard.

Om een bestaande Lijst van de Update van het Beleid te wijzigen, klik **[!UICONTROL Add policies]** om al beschikbaar beleid op de server te bekijken. Kies het aanvullende beleid dat u wilt toevoegen of intrekken. Bestaande ingangen in de Lijst van de Update van het Beleid kunnen in de hogere sectie van het scherm worden veranderd. Het gemarkeerde beleid **[!UICONTROL updated]** kan veranderen in **[!UICONTROL revoked]**, maar wanneer een beleid eenmaal is **[!UICONTROL revoked]**, kan het niet meer worden veranderd in **[!UICONTROL updated]**.

Wanneer de gewenste wijzigingen zijn aangebracht, kiest u **[!UICONTROL Create Policy Update List]** en wordt het [!DNL PolicyUpdateList.dat] bestand opnieuw gegenereerd. Als een beleid reeds in de lijst van de beleidsupdate is en sinds de laatste tijd werd bijgewerkt werd de lijst geproduceerd, zal de meest recente versie van het beleid worden gebruikt wanneer de Lijst van de Update van het Beleid opnieuw wordt geproduceerd.
