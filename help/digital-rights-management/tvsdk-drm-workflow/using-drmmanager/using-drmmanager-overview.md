---
title: Het overzicht van de klasse DRMManager gebruiken
description: Het overzicht van de klasse DRMManager gebruiken
copied-description: true
exl-id: 941a69fb-3085-45d6-9176-08ebb93cada4
source-git-commit: be43bbbd1051886c8979ff590a3197b2a7249b6a
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# De klasse DRMManager gebruiken {#using-the-drmmanager-class}

Gebruik de `DRMManager` klasse voor het beheren van licenties en sessies van Primetime DRM-licentieservers in toepassingen.

**Licentiebeheer**

Wanneer een apparaat beveiligde inhoud afspeelt, haalt de runtime de licentie op die nodig is om de inhoud weer te geven en slaat deze in het cachegeheugen op. Als de toepassing de inhoud lokaal opslaat en de licentie offline afspelen toestaat, kan de gebruiker de inhoud in de toepassing weergeven zonder netwerkverbinding. Met de `DRMManager`, kunt u de licentie vooraf in cache plaatsen. De toepassing hoeft niet de licentie te verkrijgen die nodig is om de inhoud weer te geven. Uw toepassing kan bijvoorbeeld het mediabestand downloaden en vervolgens de licentie verkrijgen terwijl de gebruiker nog online is.

Als u een licentie vooraf wilt laden, gebruikt u een `DRMContentData` object. De `DRMContentData` Het object bevat de URL van de Primetime DRM-licentieserver die de licentie kan leveren en beschrijft of gebruikersverificatie vereist is. Met deze informatie kunt u de `DRMManager` `loadVoucher()` methode om de licentie te verkrijgen en in cache te plaatsen. De workflow voor het vooraf laden van licenties wordt in meer detail beschreven *Licenties vooraf laden voor offline afspelen*.

**Sessiebeheer**

U kunt ook de opdracht `DRMManager` om de gebruiker te verifiëren bij een Primetime DRM-licentieserver en om blijvende sessies te beheren. Roep de `DRMManager` `authenticate()` methode om een sessie tot stand te brengen met de Primetime DRM-licentieserver. Wanneer de verificatie is voltooid, wordt de `DRMManager` verzendt een `DRMAuthenticationCompleteEvent` object. Dit object bevat een sessietoken. U kunt dit token opslaan om toekomstige sessies tot stand te brengen, zodat de gebruiker zijn accountgegevens niet hoeft op te geven. Geef het token door aan de `setAuthenticationToken()` methode om een nieuwe voor authentiek verklaarde zitting te vestigen. (De instellingen van de server die het token heeft gegenereerd, bepalen de vervaldatum van het token en andere kenmerken).

## DRMStatus-gebeurtenissen verwerken {#handling-drmstatus-events}

De `DRMManager` verzendt een `DRMStatusEvent` object na een aanroep van de `loadVoucher()` wordt voltooid. Als een licentie wordt verkregen, heeft de eigenschap detail van het gebeurtenisobject de waarde: `DRM.voucherObtained`en bevat de eigenschap voucher de eigenschap `DRMVoucher` object. Als er geen licentie wordt verkregen, heeft de eigenschap detail nog steeds de waarde: `DRM.voucherObtained`; de eigenschap voucher is echter null. U kunt geen licentie verkrijgen als u bijvoorbeeld de `LoadVoucherSetting` van `localOnly` en er is geen lokaal in cache geplaatste licentie . Als de `loadVoucher()` de vraag niet met succes voltooit, misschien wegens een authentificatie of communicatie fout, dan `DRMManager` verzendt een `DRMErrorEvent` of `DRMAuthenticationErrorEvent` in plaats daarvan.

## DRMAuthenticationComplete-gebeurtenissen verwerken{#handling-drmauthenticationcomplete-events}

De `DRMManager` verzendt een `DRMAuthenticationCompleteEvent` object wanneer een gebruiker met succes is geverifieerd via een aanroep van de `authenticate()` methode. De `DRMAuthenticationCompleteEvent` Het object bevat een herbruikbaar token dat kan worden gebruikt om de gebruikersverificatie tijdens toepassingssessies voort te zetten. Geef deze token door aan `DRMManager` `setAuthenticationToken()` methode om de sessie opnieuw tot stand te brengen. (De maker van het token stelt de kenmerken van het token in, zoals de vervaldatum. Adobe beschikt niet over een API voor het controleren van tokenkenmerken.)

## DRMAuthenticationError-gebeurtenissen afhandelen{#handling-drmauthenticationerror-events}

De `DRMManager` verzendt een `DRMAuthenticationErrorEvent` object wanneer een gebruiker niet kan worden geverifieerd via een aanroep van de `authenticate()` of `setAuthenticationToken()` methoden.
