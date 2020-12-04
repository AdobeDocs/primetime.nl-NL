---
seo-title: Het overzicht van de klasse DRMManager gebruiken
title: Het overzicht van de klasse DRMManager gebruiken
uuid: 71ce061b-75b6-4ab5-8bbd-cafe7c3e4592
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---


# De klasse DRMManager gebruiken {#using-the-drmmanager-class}

Met de klasse `DRMManager` kunt u licenties en Primetime DRM-licentieserversessies in toepassingen beheren.

**Licentiebeheer**

Wanneer een apparaat beveiligde inhoud afspeelt, haalt de runtime de licentie op die nodig is om de inhoud weer te geven en slaat deze in het cachegeheugen op. Als de toepassing de inhoud lokaal opslaat en de licentie offline afspelen toestaat, kan de gebruiker de inhoud in de toepassing weergeven zonder netwerkverbinding. Met de `DRMManager` kunt u de licentie vooraf in cache plaatsen. De toepassing hoeft niet de licentie te verkrijgen die nodig is om de inhoud weer te geven. Uw toepassing kan bijvoorbeeld het mediabestand downloaden en vervolgens de licentie verkrijgen terwijl de gebruiker nog online is.

Als u een licentie vooraf wilt laden, gebruikt u een `DRMContentData`-object. Het `DRMContentData`-object bevat de URL van de Primetime DRM-licentieserver die de licentie kan leveren en beschrijft of gebruikersverificatie vereist is. Met deze informatie, kunt u `DRMManager` `loadVoucher()` methode roepen om de vergunning te verkrijgen en in het voorgeheugen onder te brengen. De workflow voor het vooraf laden van licenties wordt meer gedetailleerd beschreven in *Licenties voor offlineafspelen vooraf laden*.

**Sessiebeheer**

U kunt de `DRMManager` ook gebruiken om de gebruiker te verifiëren bij een Primetime DRM-licentieserver en om blijvende sessies te beheren. Roep de `DRMManager` `authenticate()` methode aan om een zitting met de Primetime DRM vergunningsserver te vestigen. Wanneer de verificatie met succes is voltooid, verzendt het object `DRMManager` een object `DRMAuthenticationCompleteEvent`. Dit object bevat een sessietoken. U kunt dit token opslaan om toekomstige sessies tot stand te brengen, zodat de gebruiker zijn accountgegevens niet hoeft op te geven. Geef het token door aan de methode `setAuthenticationToken()` om een nieuwe geverifieerde sessie tot stand te brengen. (De instellingen van de server die het token heeft gegenereerd, bepalen de vervaldatum van het token en andere kenmerken).

## DRMStatus-gebeurtenissen verwerken {#handling-drmstatus-events}

Het `DRMManager` verzendt een `DRMStatusEvent` voorwerp nadat een vraag aan de `loadVoucher()` methode met succes voltooit. Als een licentie wordt verkregen, heeft de eigenschap detail van het gebeurtenisobject de waarde: `DRM.voucherObtained` en de vouchereigenschap bevat het object `DRMVoucher`. Als er geen licentie wordt verkregen, heeft de eigenschap detail nog steeds de waarde: `DRM.voucherObtained`; de eigenschap voucher is echter null. Een licentie kan niet worden verkregen als u bijvoorbeeld `LoadVoucherSetting` van `localOnly` gebruikt en er geen lokale licentie in de cache is. Als de `loadVoucher()` vraag niet met succes voltooit, misschien wegens een authentificatie of communicatie fout, dan `DRMManager` verzendt `DRMErrorEvent` of `DRMAuthenticationErrorEvent` voorwerp in plaats daarvan.

## DRMAuthenticationComplete-gebeurtenissen verwerken{#handling-drmauthenticationcomplete-events}

Het `DRMManager` verzendt een `DRMAuthenticationCompleteEvent` voorwerp wanneer een gebruiker met succes door een vraag aan de `authenticate()` methode wordt verklaard. Het `DRMAuthenticationCompleteEvent`-object bevat een herbruikbaar token dat kan worden gebruikt om de verificatie van de gebruiker tijdens toepassingssessies voort te zetten. Geef dit token door aan `DRMManager` `setAuthenticationToken()` methode om de sessie opnieuw tot stand te brengen. (De maker van het token stelt de kenmerken van het token in, zoals de vervaldatum. Adobe beschikt niet over een API voor het controleren van tokenkenmerken.)

## DRMAuthenticationError-gebeurtenissen verwerken{#handling-drmauthenticationerror-events}

Het `DRMManager` verzendt een `DRMAuthenticationErrorEvent` voorwerp wanneer een gebruiker niet met succes door een vraag aan de `authenticate()` of `setAuthenticationToken()` methodes kan worden verklaard.