---
description: U kunt de Reference Implementation zo instellen dat de rapportage van Adobe Analytics wordt gebruikt.
seo-description: U kunt de Reference Implementation zo instellen dat de rapportage van Adobe Analytics wordt gebruikt.
seo-title: Adobe Analytics-rapportage configureren
title: Adobe Analytics-rapportage configureren
uuid: bdf8bb7f-a0c8-48a2-a632-0b872687f3fe
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Adobe Analytics-rapportage configureren {#configure-adobe-analytics-reporting}

U kunt de Reference Implementation zo instellen dat de rapportage van Adobe Analytics wordt gebruikt.

De Reference Implementation is geconfigureerd voor het verzenden van Primetime-verificatie-gebeurtenisgegevens naar Adobe Analytics met behulp van de Adobe Mobile-bibliotheek die is gebundeld in de Primetime SDK. Als u de gebeurtenisgegevens die vanuit de toepassing zijn verzonden, wilt inschakelen en gebruiken, moet u eerst een Adobe Analytics-account maken. Zodra de account is gemaakt:

1. Configureer de toepassing met uw accountgegevens. en
1. Maak verwerkingsregels om aan te passen hoe de gebeurtenisgegevens in uw rapporten worden weergegeven.

In de onderstaande tabel worden de gegevens weergegeven die naar Adobe Analytics zijn verzonden:

| Naam van handeling | `a.media.pass.event.MvpdSelection` | De gebruiker selecteerde een Multichannel Video Programming Distiller (MVPD) in een selectiedialoog |
|---|---|---|
| Contextgegevens | `a.media.pass.MvpdId (String)` | De door de gebruiker geselecteerde MVPD |
|  | `a.media.pass.ClientType` | (String) Het clienttype is &quot;flash&quot;, &quot;html5&quot;, &quot;ios&quot; of &quot;android&quot; |
|  |  |  |
| Naam van handeling | `a.media.pass.event.AuthenticationDetection` | Een verificatieworkflow voltooid |
| Contextgegevens | `a.media.pass.Successful` | (Boolean) Of de token-aanvraag succesvol was, true of false |
|  | `a.media.pass.MvpdId` | (Tekenreeks) De door de gebruiker geselecteerde MVPD |
|  | `a.media.pass.Guid` | (Tekenreeks) Een id voor bijhouden |
|  | `a.media.pass.Cached` | (Boolean) Token bevindt zich al in cache, waar of onwaar |
|  | `a.media.pass.ClientType` | (String) Het clienttype is &quot;flash&quot;, &quot;html5&quot;, &quot;ios&quot; of &quot;android&quot; |
|  |  |  |
| Naam van handeling | `a.media.pass.event.AuthorizationDetection` | Een workflow voor autorisatie is voltooid |
| Contextgegevens | `a.media.pass.Successful` | (Boolean) Of de token-aanvraag succesvol was, true of false |
|  | `a.media.pass.MvpdId` | (String) De gebruiker heeft MVPD geselecteerd |
|  | `a.media.pass.Guid` | (Tekenreeks) Een id voor bijhouden |
|  | `a.media.pass.Cached` | (Boolean) Token bevindt zich al in cache, waar of onwaar |
|  | `a.media.pass.Error` | (String) De fout als de autorisatiepoging is mislukt |
|  | `a.media.pass.ErrorDetails` | (String) Meer informatie over fouten |
|  | `a.media.pass.ClientType` | (String) Het clienttype is &quot;flash&quot;, &quot;html5&quot;, &quot;ios&quot; of &quot;android&quot; |

1. Configureer de toepassing voor gebruik met Adobe Marketing Cloud.

   Als u het verzenden van Primetime Primetime-verificatiegegevens naar Adobe Analytics wilt inschakelen, moet bij compilatie een [!DNL `ADBMobileConfig.json`] configuratiebestand worden toegevoegd aan de Reference Implementation. Dit is precies hetzelfde configuratiebestand dat door de Primetime SDK wordt gebruikt om gegevens van Video Analytics naar de Marketing Cloud te verzenden. Raadpleeg de documentatie [van](https://microsite.omniture.com/t2/help/en_US/reference/) Adobe Marketing Cloud voor meer informatie over het configureren van een toepassing met uw Adobe Analytics-account.
1. Verwerkingsregels maken.

   De gegevens van de Primetime-verificatiegebeurtenis die door de Reference Implementation worden verzonden, worden niet automatisch weergegeven in uw analyserapporten. U moet eerst de gegevens gebruiken door verwerkingsregels te maken. Raadpleeg de documentatie bij [Adobe Analytics over het maken van verwerkingsregels](https://microsite.omniture.com/t2/help/en_US/reference/processing_rules.html).
