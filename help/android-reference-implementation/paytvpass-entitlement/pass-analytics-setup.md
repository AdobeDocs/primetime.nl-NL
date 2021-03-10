---
description: U kunt de Reference Implementation instellen om Adobe Analytics-rapporten te gebruiken.
title: Adobe Analytics-rapportage configureren
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---


# Adobe Analytics-rapportage {#configure-adobe-analytics-reporting} configureren

U kunt de Reference Implementation instellen om Adobe Analytics-rapporten te gebruiken.

De Reference Implementation is geconfigureerd om Primetime-verificatiegebeurtenisgegevens naar Adobe Analytics te verzenden met de Adobe Mobile Library die in de Primetime SDK is gebundeld. Als u de gebeurtenisgegevens die vanuit de toepassing zijn verzonden wilt inschakelen en gebruiken, moet u eerst een Adobe Analytics-account maken. Zodra de account is gemaakt:

1. Configureer de toepassing met uw accountgegevens. en
1. Maak verwerkingsregels om aan te passen hoe de gebeurtenisgegevens in uw rapporten worden weergegeven.

De onderstaande tabel bevat de gegevens die naar Adobe Analytics zijn verzonden:

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

   Als u het verzenden van Primetime Primetime-verificatiegegevens naar Adobe Analytics wilt inschakelen, moet een [!DNL `ADBMobileConfig.json`]-configuratiebestand bij compilatie worden toegevoegd aan de Reference Implementation. Merk op dat dit precies het zelfde configuratiedossier is dat door Primetime SDK wordt gebruikt om de gegevens van de Analyse van de Video naar de Marketing Cloud te verzenden. Raadpleeg de [Adobe Marketing Cloud documentatie](https://microsite.omniture.com/t2/help/en_US/reference/) voor meer informatie over het configureren van een toepassing met uw Adobe Analytics-account.
1. Verwerkingsregels maken.

   De gegevens van de Primetime-verificatiegebeurtenis die door de Reference Implementation worden verzonden, worden niet automatisch weergegeven in uw analyserapporten. U moet eerst de gegevens gebruiken door verwerkingsregels te maken. Raadpleeg de [Adobe Analytics-documentatie over het maken van verwerkingsregels](https://microsite.omniture.com/t2/help/en_US/reference/processing_rules.html).
