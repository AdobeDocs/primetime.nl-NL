---
description: 'U moet ervoor zorgen dat u licenties op veilige wijze afgeeft. Overweeg deze beste praktijken om de Server van de Vergunning te beschermen '
seo-description: 'U moet ervoor zorgen dat u licenties op veilige wijze afgeeft. Overweeg deze beste praktijken om de Server van de Vergunning te beschermen '
seo-title: De licentieserver beschermen
title: De licentieserver beschermen
uuid: 7b5de17d-d0a7-41df-9651-4ff51c9965c6
translation-type: tm+mt
source-git-commit: 58bb3bedc5b0ac63afd96eb6101d9ad779e6deed
workflow-type: tm+mt
source-wordcount: '1200'
ht-degree: 0%

---


# De licentieserver beschermen {#protecting-the-license-server}

U moet ervoor zorgen dat u licenties op veilige wijze afgeeft. Overweeg de volgende aanbevolen procedures om de licentieserver te beschermen:

## Lokaal gegenereerde CRL&#39;s gebruiken {#consuming-locally-generated-crls}

Als u lokaal gegenereerde lijsten met certificaatintrekking (CRL&#39;s) en beleidsupdate wilt gebruiken, gebruikt u Adobe Primetime DRM API&#39;s om de handtekening te verifiëren.

Met de volgende API&#39;s wordt gecontroleerd of er niet met de lijsten is geknoeid en of de lijsten zijn ondertekend door de juiste licentieserver:

* Roep [RevocationList.verifySignature](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationList.html#verifySignature(java.security.cert.X509Certificate)) aan om de handtekening te controleren voordat u de [RevocationList](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationList.html) aan om het even welke APIs verstrekt.

   Zie [RevocationListFactory voor meer informatie](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationListFactory.html).

* Roep [PolicyUpdateList.verifySignature](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/policyupdate/PolicyUpdateList.html#verifySignature(java.security.cert.X509Certificate)) aan om de handtekening te controleren voordat u de handtekening aanbiedt `PolicyUpdateList` aan API&#39;s.

   Voor meer informatie, zie [PolicyUpdateList](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/policyupdate/PolicyUpdateList.html).

## CRL&#39;s gebruiken die zijn gepubliceerd door Adobe{#consuming-crls-published-by-adobe}

De SDK downloadt periodiek CRL&#39;s die door Adobe worden gepubliceerd. U moet ervoor zorgen dat de toegang tot deze dossiers niet wordt geblokkeerd of de handhaving van deze CRLs niet wordt verhinderd.

De SDK heeft een configuratieoptie om fouten te negeren bij het ophalen van Adobe CRL&#39;s. U kunt deze optie alleen toepassen in ontwikkelomgevingen. In productieomgevingen moet de licentieserver de CRL&#39;s ophalen van Adobe. Als de licentieserver geen geldige CRL kan verkrijgen, is er een fout opgetreden.

## CRL&#39;s genereren als aanvulling op de publicaties van Adobe{#generating-crls-to-supplement-those-published-by-adobe}

Met Adobe Primetime DRM kunt u CRL&#39;s maken die een aanvulling vormen op de computer-CRL die door Adobe wordt gepubliceerd.

De Primetime DRM SDK controleert en handhaaft Adobe CRLs. U kunt echter aanvullende clientcomputers weigeren door een CRL te maken dat aanvullende computergegevens herroept door het CRL door te geven aan de Primetime DRM SDK. Wanneer u een licentie geeft, controleert de SDK Adobe CRL en uw CRL.

Om CRLs te produceren, zie [RevocationListFactory](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationListFactory.html).

## Terugdraaidetectie {#rollback-detection}

Als in uw implementatie van Adobe Primetime DRM bedrijfsregels worden gebruikt die de client vereisen om de status te behouden (bijvoorbeeld het interval voor het afspeelvenster), raadt Adobe aan dat de server de terugdraaiteller bijhoudt en dat AIR of SWF het weergeven van lijsten toestaat.

De rollback teller wordt verzonden naar de server in de meeste verzoeken van de cliënt. Als voor uw implementatie van Primetime DRM de terugdraaiteller niet nodig is, kan deze worden genegeerd. Anders raadt Adobe aan dat de server de willekeurige machine-id opslaat, die wordt verkregen met [MachineToken.getUniqueId()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getUniqueId()), en de huidige tellerwaarde in een database.

Voor meer informatie over hoe te om de het terugschroeven van prijzenteller te verhogen en te volgen, zie [CliëntState](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/ClientState.html) en de opsporing van het Terugschroeven van prijzen.

## Aantal machines bij afgifte van vergunningen {#machine-count-when-issuing-licenses}

Als de bedrijfsregels vereisen dat het aantal machines voor een gebruiker wordt gevolgd, moet de Server van de Vergunning of de Server van het Domein machine IDs opslaan die met de gebruiker worden geassocieerd.

De meest robuuste manier om machine IDs te volgen is de waarde op te slaan die door de [MachineId.getBytes ()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getBytes()) methode in een gegevensbestand is teruggekeerd. Wanneer een nieuwe aanvraag wordt ontvangen, vergelijkt u de machine-id in de aanvraag met de bekende machine-id&#39;s met [MachineId.match()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#matches(com.adobe.flashaccess.sdk.cert.MachineId)).

[MachineId.match()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#matches(com.adobe.flashaccess.sdk.cert.MachineId)) voert een vergelijking van id&#39;s uit om te bepalen of de id&#39;s dezelfde computer vertegenwoordigen. Deze vergelijking is alleen praktisch als er een klein aantal machine-id&#39;s is. Als gebruikers bijvoorbeeld vijf computers in hun domein mogen hebben, kunt u in de database zoeken naar de machine-id&#39;s die aan de gebruikersnaam van de gebruiker zijn gekoppeld en een kleine set gegevens ter vergelijking verkrijgen.

Deze vergelijking is niet praktisch voor plaatsingen die anonieme toegang toestaan. In dit geval kan [MachineId.getUniqueID()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getUniqueId()) worden gebruikt. Deze id kan echter niet hetzelfde zijn als de gebruiker toegang krijgt tot inhoud van Flash en Adobe AIR®-runtimes.

>[!NOTE]
>
>De id overblijft niet als de gebruiker de vaste schijf opnieuw formatteert.

## Replay-beveiliging {#replay-protection}

De bescherming van het spel verhindert een aanvaller een bericht van het vergunningsverzoek opnieuw te spelen en potentieel veroorzakend een ontkenning-van-dienst (Dos) aanval tegen de cliënt.

Een aanval van Dos is een poging door aanvallers om wettige gebruikers van de dienst te verhinderen die dienst te gebruiken. Bijvoorbeeld, zou een replay aanval die de het terugschroeven van prijzenteller gebruikt kunnen worden gebruikt om de Server van de Vergunning te &quot;bedriegen&quot;in het denken dat de cliënt DRM zijn staat heeft teruggedraaid, die een opschorting van de rekening veroorzaakt.

Zie [ AbstractRequestMessage.getMessageId()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/AbstractRequestMessage.html#getMessageId())voor meer informatie over afspeelbeveiliging.

## Een lijst van gewenste personen van vertrouwde-inhoudpakketten onderhouden {#maintain-a-allowlist-of-trusted-content-packagers}

Een lijst van gewenste personen is een lijst met vertrouwde entiteiten.

Voor inhoudspakketten zijn de entiteiten organisaties die door de eigenaar van de inhoud worden vertrouwd om de videobestanden te verpakken (of te coderen) en DRM-beveiligde inhoud te maken. Wanneer u Adobe Primetime DRM implementeert, moet u een lijst van gewenste personen van vertrouwde inhoudspakketten onderhouden. U moet ook de identiteit verifiëren van de inhoudspakket in de DRM-metagegevens van een DRM-beveiligd bestand voordat u een licentie afgeeft.

Zie [V2ContentMetaData.getPackagerInfo()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/media/drm/keys/v2/V2ContentMetaData.html#getPackagerInfo())voor informatie over de entiteit die de inhoud in een pakket heeft opgenomen.

## Time-out voor verificatietokens{#timeout-for-authentication-tokens}

Alle verificatietokens die door de Adobe Primetime DRM SDK worden gegenereerd, hebben een time-outinterval om de toepassingsbeveiliging te beschermen.

De vervaldatum voor het authentificatietoken wordt gespecificeerd gebruik Primetime DRM SDK wanneer het behandelen van een authentificatieverzoek. Nadat deze is verlopen, is het token niet meer geldig en moet de gebruiker opnieuw worden geverifieerd met de licentieserver.

Meer over authentificatieverzoeken leren, zie [AuthenticationHandler](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/authentication/AuthenticationHandler.html).

## Beleidsopties overschrijven {#overriding-policy-options}

Wanneer u een licentie geeft, kan de licentieserver de gebruiksregels negeren die in het beleid zijn opgegeven.

Als het beleid een begindatum specificeert, wordt geen vergunning geproduceerd vóór die begindatum. U kunt echter een toekomstige begindatum in de licentie instellen nadat de licentie is gegenereerd. Deze optie moet met voorzichtigheid worden gebruikt omdat de client niet kan voorkomen dat de gebruiker de systeemtijd vooruit verplaatst om de begindatum te omzeilen.